Search backend implementation notes
===================================

The SearchBackend class
-----------------------

Each search backend module defines a `SearchBackend` class which serves as the entry point for all code interfacing with `wagtail.search`. A search backend is obtained through the `get_search_backend` function:

`wagtail.search.backends.get_search_backend(backend_name='default', **kwargs)`

This instantiates the named backend as listed in WAGTAILSEARCH_BACKENDS, passing the (backend-specific) configuration options from there.

The `reset_index`, `add_type`, `refresh_index`, `add`, `add_bulk` and `delete` methods on SearchBackend are obsolete, and replaced by Rebuilder objects.


Indexing
--------

Indexing (as performed by the `update_index` management command) is handled by the rebuilder class given by `backend.rebuilder_class`. If this is None, this backend does not require indexing (e.g. the database backend).

An Index object represents a storage location where we store the searchable data for some subset of the project's models. There can be multiple indexes, and the details of how models are allocated to indexes (and, indeed, what the concept of an index means for a particular backend implementation) is internal to that backend. For Postgres, there is a single index for all models; for Elasticsearch there is one index per base model class (Page, Document, Image etc). The index for a given model can be retrieved with `backend.get_index_for_model(model)`.

To insert data into an index, `update_index` makes the following sequence of method calls:

    # Perform initialisation so that the index is ready to receive data
    rebuilder = backend.rebuilder_class(index)
    index = rebuilder.start()

    # Configure the index to accept data for a given model
    index.add_model(model)

    # Insert data for a queryset (or other iterable) of model instances; update_index takes care of
    # doing this in appropriately sized batches
    index.add_items(model, items)

    # Perform any necessary cleanup / finalisation after all data has been inserted
    rebuilder.finish()

Indexing - Elasticsearch-specific notes
---------------------------------------

The main logic of `index.add_model` / `index.add_items` is delegated to an internal ElasticsearchMapping class which wraps an individual model's `search_fields` configuration and serves as an adapter between that model and Elasticsearch:

* `add_model(model)` calls the adapter's `get_mapping()` method, which returns an Elasticsearch-readable JSON configuration
* `add_item(item)` calls the adapter's `get_document(item)` method, which returns a JSON representation of the indexable data.

The ElasticsearchMapping object will also be used when constructing search queries.


Indexing - PostgreSQL-specific notes
------------------------------------

Postgres search only allows text to be indexed under one of four boost levels labelled A, B, C and D (which are assigned numeric values at query time), so extra logic is required at index time to inspect all boost values defined across all models' `search_fields` definitions and select a suitable set of four.

Support for field length normalisation (to give matches in shorter fields higher weighting than matches in longer ones) is also limited - we are only able to normalise against the length of the full indexed content, not an individual field. [PR #6013](https://github.com/wagtail/wagtail/pull/6013/) works around this by special-casing fields named 'title' and placing them in their own index field.

