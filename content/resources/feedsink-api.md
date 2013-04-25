---
title: FeedSink API
---
# FeedSink API

by Avi Flax <avif@arc90.com> of [Arc90](http://arc90.com)

This document is copyright © 2013 Arc90, Inc. — but APIs themselves are not subject to copyright, so feel free to implement
or reuse the actual API design for any purpose.

This document is licensed to anyone to do anything with. No rights reserved.

## Authentication
TBD

## Use Cases

### As a client, I was just launched, so I want to retrieve all the changes the user made since the last time I checked

#### Request

* Send a GET request to the resource “a user’s changes since {date-time}”
    * example path: `/users/{user-id}/changes-since-2013-03-18T21:34:22-04:00`
* The request header `Accept` must be `application/json; schema=feedsink.user-changes.v.1.0`

#### Success Response

* The response header `Content-Type` will be `application/json; schema=feedsink.user-changes.v1.0`

The response entity will be a JSON object which looks like this:

    {
        "feeds": {
            "added": [
                {
                    uri: "http://aviflax.com/feed",
                    name: "Avi’s Rad Blog",
                    "tags": ["racing" "friends"]
                },
                {
                    uri: "http://aviflax.com/feed",
                    name: "Avi’s Rad Blog",
                    "tags": ["racing" "friends"]
                }
            ],
            "deleted": [
                "http//feed.zombo.com/"
            ],
            "updated": [
                {
                    uri: "http://aviflax.com/feed",
                    name: "Avi’s Rad Blog",
                    "tags": ["racing" "friends"]
                },
                {
                    uri: "http://aviflax.com/feed",
                    name: "Avi’s Rad Blog",
                    "tags": ["racing" "friends"]
                }
            ]
        },
        "feed-entries": {
            "http://aviflax.com/feed": {
                "read": [
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a'
                ],
                "unread": [
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a'
                ],
                "starred": [
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a'
                ],
                "unstarred": [
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a'
                ]
            },
            "http://arc90.com/blog/entries?format=atom": {
                "read": [
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a'
                ],
                "unread": [
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a'
                ],
                "starred": [
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a'
                ],
                "unstarred": [
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a'
                ]
            }
        }
    }


#### Error Responses
TBD


### As a client, I just downloaded new entries from one of a user’s feeds, and I want to check whether any of them have been read already, so that I don’t show the user entries they already read

#### Request

* Send a GET request to the resource “a user’s read entries for feed {uri}”
    * example path: `/users/{user-id}/feeds/{uri}/entries/read`
* The request header `Accept` must be `application/json; schema=feedsink.read-entries.v1.0`

#### Success Response

* The response header `Content-Type` will be `application/json; schema=feedsink.read-entries.v1.0`

The response entity will be a JSON object which looks like this:

    {
        "read_entries": [
            'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
            'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
            'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a'
        ]
    }


#### Error Responses
TBD


### Set the read/unread/starred/unstarred status for entries from one of a user’s feeds

* so their status is the preserved if they switch to a different device or app

#### Request

* Send a POST request to the resource “a user’s entries for feed {uri}”
    * example path: `/users/{user-id}/feeds/{uri}/entries`
* The value of the request header `Content-Type` must be `application/json; schema=feedsink.statuschanges.v1.0`

The request entity should be a JSON object which looks like this:

    {
        "read": [
            // tuples of entry_id and user_action_date
            [
                'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                '2013-03-12T23:22:11-04:00'
            ],
            [
                'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                '2013-03-12T23:22:11-04:00'
            ]
        ],  
        "unread": [
            // tuples of entry_id and user_action_date
            [
                'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                '2013-03-12T23:22:11-04:00'
            ],
            [
                'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                '2013-03-12T23:22:11-04:00'
            ]
        ],
        "starred": [
            // tuples of entry_id and user_action_date
            [
                'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                '2013-03-12T23:22:11-04:00'
            ],
            [
                'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                '2013-03-12T23:22:11-04:00'
            ]
        ],
        "unstarred": [
            // tuples of entry_id and user_action_date
            [
                'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                '2013-03-12T23:22:11-04:00'
            ],
            [
                'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                '2013-03-12T23:22:11-04:00'
            ]
        ],
    }


* The entity should not include all entries for the feed, rather only those which the client wishes to set the status of
* `user_action_date` is included so the service can discard user actions which it recieves out of order.
* The elements of the arrays `read` and `unread` are tuples rather than objects so as to minimize data size
    * mobile clients will be uploading this representation and it’s important to try to keep the uploads small
    * most (maybe all) HTTP client libraries don’t support compressing request entities

#### Success Response

* If the request is successful, you will receive either a 204 or 202 response

#### Error Responses
TBD


### Retrieve the list of all of a user’s feeds

* Each feed should include a list of the N most recent read entries so they can be filtered out without making a ton of additional requests

#### Request

* Send a GET request to the resource “a user’s feeds”
    * example path: `/users/{user-id}/feeds`
* The request header `Accept` must be `application/json; schema=feedsink.feed-list.v1.0`

#### Success Response

The response header `Content-Type` will be `application/json; schema=feedsink.feed-list.v1.0`

The response entity will be a JSON object which looks like this:

    {
        "feeds": [
            {
                "uri": "http://aviflax.com/feed",
                "name": "Avi’s Silly Blog",
                "tags": ["favorites"],
                "read_entries": [
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a'
                ]
            },
            {
                "uri": "http://arc90.com/feed",
                "name": "Arc90 Blog",
                "tags": ["river", "arc"],
                "read_entries": [
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a',
                    'urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a'
                ]
            }
        ]
    }

#### Error Responses
TBD


### Add a feed to a user’s list of feeds

#### Request

* Send a PUT request to the resource “the feed {uri} of a user”
    * example path: `/users/{user-id}/feeds/{feed-uri}`
* The request header `Content-Type` must be `application/json; schema=feedsink.feed.v1.0`

The request entity should be a JSON object which looks like this:

    {
        "uri": "http://aviflax.com/feed",
        "name": "Avi’s Silly Blog",
        "tags": ["river", "arc/staff"],
    }

Please note that a tag may contain `/` to denote that it is heirarchical.

#### Success Response

* The status code will be either 201 or 202
* There will be no entity

#### Error Responses
* TBD


### Remove a feed from a user’s list of feeds

#### Request

* Send a DELETE request to the resource “the feed {uri} of user {user-id}”
    * example path: `/users/{user-id}/feeds/{feed-uri}`
* The request header [`If-Unmodified-Since`](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.28) must be included
    * the value should be the date-time at which the user initiated the deletion

#### Success Response

* The status code will be either 202 or 204
* There will be no entity

#### Error Responses
TBD


### Add multiple feeds to a user’s list of feeds

* This is intended for the “import” use-case wherein a user is adopting the API for the first time, and wishes to import their feed list from another application or service
* Clients are recommended to use this method only when they have a significant number of feeds to add at once
    * Otherwise, PUT requests to the resource “the feed {uri} of user {user-id}” are recommended, as they are idempotent and therefore less likely to result in an undesired outcome, as in the case of an error they can be safely resent

#### Request

* Send a POST request to the resouce “a user’s feeds”
    * example path: `/users/{user-id}/feeds`
* The request header `Content-Type` must be `application/json; schema=feedsink.feed-list.v1.0`

The request entity should be a JSON object which looks like this:

    {
        "feeds": [
            {
                "uri": "http://aviflax.com/feed",
                "name": "Avi’s Silly Blog",
                "tags": ["favorites"]
            },
            {
                "uri": "http://arc90.com/feed",
                "name": "Arc90 Blog",
                "tags": ["river", "arc"]
            }
        ]
    }

#### Success Response

* The status code will be either 200, 202, or 204
* There will be no entity

#### Error Responses
* TBD


### Change the name or tags of a user’s feed

#### Request

* Send a PUT request to the resource “the feed {uri} of a user”
    * example path: `/users/{user-id}/feeds/{feed-uri}`
* The request header `Content-Type` must be `application/json; schema=feedsink.feed.v1.0`
* The request header [`If-Unmodified-Since`](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.28) must be included
    * the value should be the date-time at which the user entered the changes

The request entity should be a JSON object which looks like this:

    {
        "uri": "http://aviflax.com/feed",
        "name": "Avi’s Silly Blog",
        "tags": ["river", "arc/staff"],
    }

* A tag may contain `/` to denote that it is heirarchical
* If the value of `uri` does not match the path segment `feed-uri` of the target resource URI path, the request will be rejected

#### Success Response

* The status code will be 200 or 202
* There will be no entity

#### Error Responses
TBD
