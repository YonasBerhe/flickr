Flickr
======

A simple wrapper around the [Flickr JSONP API][flickrapi]. No scripts from
Flickr are required in advance since they provide a raw JSONP service; it is up
to clients how they want to consume it.

[flickrapi]: http://www.flickr.com/services/api/response.json.html

Usage
-----

Instantiate a client using your Flickr API key:

    client = new Flickr.Client('63bb4efae64c3c04510c484dcdaef263');

The client provides convenience methods for calling various feeds, for example:

    client.getGroupPhotos('52240328087@N01', function(feed) {
        for (var i = 0, n = feed.length; i < n; i++)
            alert(feed[i].getTitle());
    });

See the `Flickr.Client` and `Flickr.Photo` classes for more information.


API
---

### `Flickr.Client`

Instances of the `Flickr.Client` class have the following methods available.
They all have two required arguments: an `id` value and a `callback`. They
also accept a `scope` parameter, which allows you to set the value of the
`this` keyword inside the callback.

#### Wrapped methods

These methods wrap photo objects in `Flickr.Photo` objects, which have a more
convenient API (detailed below).

* `getGroupPhotos` calls the callback function with the group's photos.
* `getFavourites` calls the callback with the group's favourite photos.

#### Unwrapped methods

* `groupBrowse` calls the callback with a list of photos from the group.
* `groupInfo` calls the callback with information about the group.
* `groupDiscuss` calls the callback with recent discussion from that group.
* `groupPool` is the unwrapped version of `getGroupPhotos`.
* `photoFavourites` is the unwrapped version of `getFavourites`.

### `Flickr.Photo`

Instances of the `Flickr.Photo` class have the following methods available.
They have no parameters and return strings, except where noted.

* `getTags` returns the tags for that photo as an array.
* `getThumbnail` returns the location of the photo's thumbnail.
* `getAuthor` returns the name of the photo's author.
* `getAuthorId` returns the ID of the photo's author.
* `getDateTaken` returns the date the photo was taken.
* `getDescription` returns a description of the photo.
* `getLink` returns the link to the photo page.
* `getPublished` returns the date the photo was published.
* `getTitle` returns the title of the photo.
