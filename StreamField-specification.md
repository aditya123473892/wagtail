## Motivation

A common requirement for Wagtail sites is the ability to create ‘freeform’ content consisting of different content types arranged in any order: headings, paragraphs, images, video, and potentially others, including custom types specific to that site. The current go-to solution for this is the rich text area, but this is undesirable for several reasons:

* It encourages people to disregard separation of content and design
* Browser support for ‘contenteditable’ elements is often quirky, particularly when dealing with floated elements or blocks of non-editable text, and fixing the resulting bugs is either impossible or requires digging into hallo.js code
* It is difficult to extend to support new content types (resulting in developers adopting less-than-ideal solutions like permitting arbitrary blobs of HTML within the field)

This spec proposes a new mechanism named StreamField, inspired by Wagtail’s existing ‘InlinePanel’ model along with [Sir Trevor](http://madebymany.github.io/sir-trevor-js/) and Tumblr, which allows editing freeform content as a sequence of interchangeable content blocks.

## Scope

* A component for the page editor that allows building a mixed sequence of content types, that serialises to a single JSON field in the database
* A straightforward way to output the entire chunk of content on a template, using HTML representations defined by each content type
* A clean API for building new content types for use within this component

## Out of scope

* Nested StreamFields (for multi-column arrangements of content)
* Native database representation of the content (e.g. giving each content item its own database record)
* Interaction between different items in the sequence (e.g. cursor movement between adjacent paragraphs; pressing enter at the end of a paragraph block to spawn another paragraph block)

## Functionality

A page type incorporating a StreamField might be defined like this (NB names and syntax are subject to change):

    BlogPage.content_panels = [
        FieldPanel('title'),
        StreamFieldPanel('content', block_types=[
            ('heading', HeadingBlock()),
            ('paragraph', ParagraphBlock()),
            ('side-image', ImageBlock(formats=['left', 'right'])),
            ('lead-image', ImageBlock(formats=['full-width'])),
        ])
    ]

This will provide an interface functionally equivalent to http://madebymany.github.io/sir-trevor-js/example.html, with four block types available:

* a 'heading' block, consisting of a single (non-rich) text field;
* a 'paragraph' block, consisting of a rich text area with limited formatting capabilities such as bold / italic text and links, but not image embedding or heading types;
* a 'side image' block, consisting of an image chooser, a text field to specify alt text, and a select box (or pair of radio buttons) to specify whether it will be left or right justified;
* a 'lead image' block, consisting of an image chooser and a text field to specify alt text (there is no format select box, since there is only one option available).

On submitting the form, these fields will be validated according to each block type's validation rules, if any. If validation succeeds, the data will be written to the 'content' field of the model as a JSON string:

    [
        {'type': 'heading', 'value': 'Fish found on moon'},
        {'type': 'lead-image', 'value': {'id': 123, 'alt': 'a fish', 'format': 'full-width'}},
        {'type': 'paragraph', 'value': 'A fish of species <i>verasper variegetus</i> was found on the moon yesterday.'},
        {'type': 'paragraph', 'value': 'NASA were unavailable for comment.'}
    ]

The 'type' field indicates which of the block types (as specified within the StreamFieldPanel definition) is responsible for this content block; 'value' is an arbitrary JSON value assigned and understood by that specific block type.

It will be possible to render the content on a template simply by using the tag `{{ self.content }}`. Each block type defines a way to render its data in HTML form (e.g. as a suitably-styled `<img>` element for ImageBlock), and the HTML rendering for the StreamField as a whole simply loops over these renderings. It will also be possible to loop over the blocks manually if more control over the output is required:

    {% for block in self.content %}
        <div class="content-block {% cycle 'odd' 'even' %}">
            {{ block }}
        </div>
    {% endfor %}

As well as providing their own HTML representation, blocks will also expose the raw data for templates to display using their own rendering. This might look something like:

    {% streamfield self.content %}
        {% blocktype 'heading' %}
            <h2 class="subtitle">{{ heading.text }}</h2>
        {% endblocktype %}
        {% blocktype 'side-image' as image %}
            <img src="{{ image.url }}" class="inline-image">
        {% endblocktype %}
        {# all block types not mentioned here fall back on their default HTML renderings #}
    {% endstreamfield %}

Here `{% streamfield %}` and `{% blocktype %}` are custom tags that act as a kind of switch/case statement, invoking the appropriate section for each content block in the sequence depending on its type.

Wagtail site implementers will be able to create custom block types. We will provide a number of abstract 'block type' base classes on top of which developers will be able to implement block-specific behaviours, such as: the rendering of the field(s) within the edit form; form validation; the block's default HTML rendering; the way it is serialised and deserialised to and from JSON; and the styling of the button within the StreamField's toolbar.