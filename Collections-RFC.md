# Collections

## Introduction

'Collections' (or possibly 'Libraries'; name TBC) are a concept for organising images, documents and potential future entities. This is expected to be particularly useful for multi-site implementations, and should support the following scenarios:

- A user in group 'Site X editors' can use, add, edit and delete images from 'Collection X' and 'Global Collection' but not 'Collection Y'.
- A user in group 'Site Y editors' can use images in 'Collection X' and 'Global Collection', but can only add, edit or delete images in 'Collection Y'.
- A user in 'Site Z editors' can only see and use images in 'Collection Z'.

## Structure

Collections are non-hierarchical groups with unique names. Items cannot be shared between collections. Collections can be used for multiple types of content (currently images and documents).

## New sites

New Wagtail sites will have a single, default collection enabled. Collections will be created and edited through an admin-only interface, under a new 'Collections' item in the Settings menu. 

## Collection management UI

Administrators will be able to add, edit (the name of) and remove collections. Non-empty collections should not be deletable. Administrators will be able to assign the following group permissions to collections, through the 'Groups' area under the Settings menu:

- Use documents from
- Use images from
- Add documents to
- Add images to
- Edit documents in
- Edit images in

## Adding / editing images and documents

If a user has 'add' permission on two or more collections, the 'add image' and 'add document' forms will include a field for the user to specify which collection the item is to be added to. In the case of the multiple image uploader, a set of images uploaded in one go will all be assigned to the same collection.

When editing an image or document, the form will include a 'collection' field allowing the user to move the item to any other collection that they have 'add' or 'edit' permission on.

## Search

Users will only see search results for the contents of collections they have view/use permissions on. Users with view/use permissions on multiple collections will be able to filter search results by collection. If there are multiple collections, the collection assigned to each image or document will be indicated in the search results.

## Migrations

Upgraded sites will have all existing images and documents moved into a single, default collection, which inherits the object permissions for images and documents.

## Single-collection implementations

Collections should be as invisible as possible for Wagtail implementations which only need one. In particular, users should never have to 'choose' a collection where only one exists, e.g. when uploading or searching for images and documents.

## Notes

- As with the current implementation, granting 'add' permission also provides users with the ability to edit items that they added themselves.
- Likewise, edit and delete permissions are not distinguished; if users can edit items, they can also delete them.
- While the option to _select_ items in the editor interface will be limited by permissions, the _use_ of an image or document in the page will not be validated when saving pages.