# Shopping list: a worked example of the blocks API

A core aim for the StreamField development is to allow content blocks to be nested to any depth. To achieve this, each block will implement a common API that defines how that block is inserted into the edit page, along with any Javascript or other resources that it depends on. Basic block types such as text fields and image choosers will implement this; this then opens up the possibility of creating 'structural' block types such as StructBlock - which embeds a collection of sub-blocks and presents them as a single block - ListBlock, which allows a sub-block to repeated any number of times - and StreamBlock, which provides the main mechanic of StreamField by embedding a collection of sub-blocks that can be repeated and mixed freely.

As long as these structural types accept any kind of sub-block that conforms to the blocks API, and expose the blocks API themselves, it's possible to nest these structures to any depth. Unfortunately, achieving this level of flexibility (and in particular, supporting arbitrarily complex Javascript at each level of recursion) demands a rather complicated API. (Be prepared to encounter the phrase "meta-initialiser function" below...)

This document illustrates the blocks API by showing how to implement 'shopping list' as a block type, from first principles - this is a dynamically extendable list of products (each of which is a text box labelled "Product"). In practice, a Wagtail site implementer will never need to go to this trouble to define a type like this - they would just define it as a special case of ListBlock. Rather, this document introduces the concepts that will be required to implement ListBlock itself (along with the other structural types). It will not cover recursive inclusion of blocks (here our Product text boxes will just be plain `<input>` fields, not blocks themselves) or how this example can be generalised to any kind of list without the need to write new Javascript on a case-by-case basis - I believe this API provides everything we need to accomplish that, though.

So let's get started...

## Block factories and block options

Implementing a block type is a matter of defining a 'block factory' object, which knows how to generate the HTML and Javascript for a block of any value. (Here, a 'value' consists of basic Python data types, of the sort that can be serialised to JSON - for a shopping list, this might be `['peas', 'carrots', 'toothpaste']`). The information needed to set up a block factory comes from two places:

1. Options passed in through the page's panel definitions, such as `classname='polkadot'` in the following:

        ShoppingListPage.content_panels = [
            StreamField('content', block_types=[
                ('shopping_list', ShoppingListBlock(classname='polkadot'))
            ])
        ]

  (This is a page consisting of a StreamField where the only block type that's available to be inserted is a shopping list.)

2. The context in which the `ShoppingListBlock` definition is placed. In the above code, the fact that our ShoppingListBlock has been given the name `shopping_list` is relevant, as is the fact that it's a child of the block called `content`. (This is because we'll need to allocate a namespace like `def-content-shopping_list` for the IDs  - this namespace needs to be distinct from any other polka-dotted shopping lists that might exist elsewhere on the page. In addition, we might want to munge the name `shopping_list` into the human-friendly string "Shopping list" for use as a label when the site implementer hasn't explicitly provided one.)

Because the definition `ShoppingListBlock(classname='polkadot')` is not very usable in isolation without that extra context, this object is essentially just a mundane bundle of properties. This is referred to as a 'block options' object. The constructor for this object can take whatever args/kwargs it likes - Wagtail does not impose any restrictions here.

The logic within wagtailadmin (or, to be exact, the parent StreamField) will then take care of building a block factory object based on these options and the relevant context information. This will be done with the following call:

    ShoppingListFactory(block_options, name='shopping_list', definition_prefix='def-content-shopping_list')

where the ShoppingListFactory class is obtained from `block_options.factory`.

Therefore, implementing a new block type involves defining a 'block options' class such as ShoppingListBlock - which is the one that a site implementer will include their panel definitions - and a 'block factory' class such as ShoppingListFactory which does the actual work. The only requirement for a 'block options' object is that it provides a `factory` attribute pointing to the block factory class. The requirements for a factory object are a bit more onerous...

## The block factory API

Block factory objects need to provide the following attributes/methods:

### media

A [Django media object](https://docs.djangoproject.com/en/1.7/topics/forms/media/#media-objects) specifying any external static JS/CSS files required by this block definition. The actual low-level Javascript implementation (such as making an 'add new' button that spawns a new "Product" text field when clicked) would usually be written here - in a file called 'shopping_list.js', say.

### html_declaration(self)

Returns a (possibly empty) string of HTML. This HTML will be included on the edit page - ONCE per block definition, regardless of how many occurrences of the block there are on the page - and it will appear in a non-specific place on the page. Any element IDs within this block of HTML must be prefixed by the factory's definition_prefix.

Typically this will be used to define snippets of HTML within `<script type="text/x-template"></script>` blocks, for our Javascript code to work with. For example, our shopping list block type might define this snippet to be dynamically inserted when you click the 'add new' button:

    <script type="text/x-template" id="{{ self.definition_prefix }}-shoppinglistitem">
        <label for="__PREFIX__">Product:</label> <input type="text" id="__PREFIX__" name="__PREFIX__" value="">
    </script>

> **A short aside about ID prefixing:**
> 
> To avoid running into naming collisions when dealing with repeated or nested blocks, any 'id' or 'name' attributes on HTML elements generated by a block must be contained within a specific namespace that we pass to the block. When we say that IDs must be prefixed by "foo", we mean that the IDs must be either:
> * "foo" itself, or
> * "foo" followed by a '-' followed by zero or more further characters (subject to the usual validity rules for HTML identifiers).
> 
> The hyphen is important: a block which is given the prefix "foo" cannot use "foot" as an identifier.
>
> In the case of complex blocks that have child blocks nested inside them, the parent block is responsible for allocating a subset of its namespace to each child, and ensuring that this doesn't create any name collisions. (In particular, it should avoid mixing its own internal identifiers with user-defined child ones: for example, if a block had a 'count' field and an arbitrary set of named child blocks, it cannot use the names "myprefix-count" and "myprefix-{childname}", in case there happens to be a child named "count".)

### render(self, value, prefix)

Return the HTML for an instance of this block with the content given by 'value'. All element IDs and names must be prefixed by the given prefix. (This is not the same as definition_prefix; here the prefix has to be unique for each individual block instance that appears in the form.) For example, `render(['peas', 'carrots', 'toothpaste'], 'matts-shopping-list')` would return something like:

    <ul id="matts-shopping-list-ul" class="polkadot">
        <li>
            <label for="matts-shopping-list-item-0">Product:</label>
            <input type="text" id="matts-shopping-list-item-0" name="matts-shopping-list-item-0" value="peas">
        </li>
        <li>
            <label for="matts-shopping-list-item-1">Product:</label>
            <input type="text" id="matts-shopping-list-item-1" name="matts-shopping-list-item-1" value="carrots">
        </li>
        <li>
            <label for="matts-shopping-list-item-2">Product:</label>
            <input type="text" id="matts-shopping-list-item-2" name="matts-shopping-list-item-2" value="toothpaste">
        </li>
        <li>
            <input type="button" id="matts-shopping-list-addnew" value="Add new">
        </li>
    </ul>

Any associated Javascript will typically not be rendered at this point (although for simple scripts that don't involve nesting blocks, an inline `<script>` tag will work).

### js_declaration(self)

Returns a Javascript expression string, or None if this block does not require any Javascript behaviour. This expression will be evaluated ONCE per block definition, regardless of how many occurrences of the block there are on the page. This expression evaluates to a "meta-initializer function".

In the case of our shopping list, we ultimately want a function that can take a chunk of dumb HTML, consisting of some list items, text inputs and a button labelled "Add new", and turn it into a beautiful, fully-functional dynamic shopping list. This function is going to have the signature:

    doAwesomeAjaxyStuff('matts-shopping-list')

where 'matts-shopping-list' is the prefix that we've used on all our element names and IDs - namely, the text inputs and the buttons - when rendering that dumb HTML.

So, we just need to define doAwesomeAjaxyStuff inside shopping_list.js, and we're done, right?

Unfortunately not. We can't get away with a single doAwesomeAjaxyStuff function that covers all possible shopping lists - it's possible that Matt's shopping list might require a different set of JS behaviours to Karl's shopping list. For example, suppose we added autocompletion to each text input. Matt's shopping list might have 3 items and Karl's shopping list has 2 items, so the JS initializer has different work to do for the two lists.

(Sure, we could handle this by getting doAwesomeAjaxyStuff to inspect the HTML and find out how many text inputs there are. But that's not possible in the general case. Trust me on this.)

So, it's a two-stage process:

    initializeMattsShoppingList = generateShoppingListInitializer({'itemCount': 3});
    initializeMattsShoppingList('matts-shopping-list');

    initializeKarlsShoppingList = generateShoppingListInitializer({'itemCount': 2});
    initializeKarlsShoppingList('karls-shopping-list');

> **Q.** If initializeMattsShoppingList is a function that only works for this one particular shopping list, why do we need to pass in the prefix in a separate function call? Why can't we just do

>     initializeMattsShoppingList = generateShoppingListInitializer({'itemCount': 3, 'prefix': 'matts-shopping-list'});
>     initializeMattsShoppingList();

> ...or for that matter

>     initializeShoppingList({'itemCount': 3, 'prefix': 'matts-shopping-list'});

> ?

> **A.** The entity that we refer to as "this one particular shopping list" might appear multiple times on the page, with different prefixes each time. "Matt's shopping list" and "Karl's shopping list" are shopping lists that will only ever appear once, but "the empty shopping list" is one that we might render any number of times. This situation occurs when our shopping list block appears within a parent block that allows repeats, as StreamField does:

>     ShoppingListPage.content_panels = [
>         StreamField('content', block_types=[
>             ('shopping_list', ShoppingListBlock())
>         ])
>     ]

> To implement this, StreamField will render an empty shopping list within a `<script type="text/x-template"></script>` block, and prepare an initializer function that can be used on the empty list each time it is inserted into the page (with some crafty prefix rewriting each time):

>     initializeEmptyShoppingList = generateShoppingListInitializer({'itemCount': 0});
>     ...
>     initializeEmptyShoppingList('shopping_lists-child-0');
>     initializeEmptyShoppingList('shopping_lists-child-1');
>     initializeEmptyShoppingList('shopping_lists-child-2');

generateShoppingListInitializer is a function for generating initializer functions for specific blocks, so we call it a meta-initializer function. So *that's* what we define in shopping_list.js, right?

Almost, but not quite. The logic within generateShoppingListInitializer needs to access the `<script type="text/x-template"></script>` block that we inserted from html_declaration. This script element has an ID derived from definition_prefix, so we don't know this ID in advance when we're writing shopping_list.js. Instead, we have to write a function that takes the definition_prefix and returns generateShoppingListInitializer.

In shopping_list.js:

    function ShoppingList(definitionPrefix) {

        /*
            Set up all the global stuff generateShoppingListInitializer needs -
            specifically, fetch the HTML snippet that will be used when spawning new shopping list items.
        */
        var newItemHtml = $('#' + definitionPrefix + '-shoppinglistitem').html();

        var generateShoppingListInitializer = function(contentParams) {

            /* Set up the stuff initializeShoppingList depends on */
            var itemCount = contentParams['itemCount'];

            var initializeShoppingList = function(htmlPrefix) {
                /* Set up the Javascript behaviours for a shopping list with 'itemCount' initial items */

                /* Attach autocomplete to each existing field */
                for (var i = 0; i < itemCount; i++) {
                    $('#' + htmlPrefix + '-item-' + i).autocomplete();
                }

                /* Make the 'add new' button work */
                $('#' + htmlPrefix + '-addnew').click(function() {
                    $('#' + htmlPrefix + '-ul').append(newItemHtml);
                    /* not shown here: fiddling the identifiers in newItemHtml to assign a new unique ID */
                });
            };

            return initializeShoppingList;
        };

        return generateShoppingListInitializer;
    }

In summary:

* `metaInit = ShoppingList("{{ definition_prefix }}")` will give you back a meta-initializer function that can tell you how to initialize any shopping list that we might encounter.
* `init = metaInit({itemCount: 3})` will give you back an initializer function to tell you how to initialize a shopping list of length 3.
* `init('matts-shopping-list')` will initialize the Javascript behaviour for the 3-item shopping list whose HTML elements begin with 'matts-shopping-list'.

So, back in Python world, we come back to js_initializer:

### js_declaration(self)

Returns a Javascript expression string, or None if this block does not require any Javascript behaviour. This expression will be evaluated ONCE per block definition, regardless of how many occurrences of the block there are on the page. This expression evaluates to a "meta-initializer function".

In other words: this method supplies the Javascript function call that kicks this whole sequence of events off: `'ShoppingList("{{ self.definition_prefix }}")'`.

If the block definition has parameters that affect Javascript behaviour - for example, if the block was declared as:

    ShoppingListPage.content_panels = [
        StreamField('shopping_lists', [ShoppingListBlock(autocomplete=True)])
    ]

then these will be passed to the Javascript at this point too:

    ShoppingList(
        "{{ self.definition_prefix }}",
        {'autocomplete': {% if self.block_options.autocomplete %}true{% else %}false{% endif %}}
    )

### js_declaration_params(self, value)

Return the Javascript parameter list (a string consisting of zero or more JS expressions separated by commas) that should be passed to the meta-initializer function for a block whose content is 'value'. In other words: this picks out any characteristics of the value that we know will have a bearing on the initialiser code, and packages them up as something we can pass to the meta-initializer. For our shopping list example, the length of the list is one such characteristic (i.e. different length lists will need different initializer functions). Therefore: if 'value' is a list of length 3 then js_declaration_params should return `"{itemCount: 3}"`.

> **Q.** Can't we just stick our Javascript initialization code inline after the HTML blocks that need it, and avoid this whole chain of initializer functions?
> **A.** No - this approach breaks down when we have nested lists. We would end up with one `<script type="text/x-template"></script>` block embedded in another - which is not a problem in itself as long as we consistently escape the `<script>` tags. The problem comes when we replace the `"__PREFIX__"` strings in the template content, since we need to keep any occurrences of `__PREFIX__` within the inner template intact - and that isn't possible with naive string replacement.

### default

The default value for blocks of this type; used as the initial value for newly-created instances of this block. For our shopping list, this is `[]`.

## Addendum

Implementation details that should be covered here (but aren't totally set in stone yet):

* Javascript API refactor - rather than two levels of indirection (meta-initialiser and initialiser), there's just an initialiser function that takes js_declaration_param and prefix as its two parameters
* BoundBlock as a helper; calls to js_declaration_param should be done as block_factory.bind(val, prefix).js_declaration_param() rather than block_factory.js_declaration_param(val) so that blocks can potentially subclass BoundBlock to carry extra data around
