---
title: Subscription
---

# Subscription

* TOC
{:toc}

## List Subscriptions

    GET /subscription/list

### Authentication

    Required

### Request Parameters

ck
: `timestamp`: Current timestamp to prevent caching issues.

client
: `application name`: String that identifies the client used.

### Response

    {
      "subscriptions": [
        {
          "id": "feed/http://feeds.feedburner.com/MyMicro-isv",
          "title": "47 Hats",
          "categories": [],
          "sortid": "FB039968",
          "firstitemmsec": "1252975023032"
        },
        {
          "id": "feed/http://www.amazon.com/rss/new-releases/books/5/ref=pd_nr_rss_link",
          "title": "Amazon.com: Hot New Releases in Books > Computers & Internet",
          "categories": [],
          "sortid": "77E40AE6",
          "firstitemmsec": "1262159994543"
        },
        {
          "id": "feed/http://blog.cartercole.com/feeds/posts/default?orderby=updated",
          "title": "Carter Cole's Blog",
          "categories": [],
          "sortid": "0B6626E4",
          "firstitemmsec": "1280455399985"
        },
        {
          "id": "feed/http://feed.feedsky.com/CWUfeed",
          "title": "China Web Updates",
          "categories": [],
          "sortid": "E53C4858",
          "firstitemmsec": "1252598589828"
        },
        {
          "id": "feed/http://feeds.feedburner.com/cwr",
          "title": "China Web2.0 Review",
          "categories": [],
          "sortid": "2EF2197E",
          "firstitemmsec": "1239983501546"
        }
      ]
    }

## Edit Subscription

    POST /subscription/edit

### Authentication

    Required

### Request Parameters

ck
: `timestamp`: Current timestamp to prevent caching issues.

client
: `application name`: String that identifies the client used.

### Post Parameters

s
: `stream id`: The feed that is to be edited.

T
: `token`: Authentication token

ac
: Action to perform: `subscribe`, `unsubscribe`, or `edit`.

a
: `tag`: Add a new tag

r
: `tag`: Remove an existing tag

t
: `feed title`

### Response

    OK

## Quick Add Subscription

This endpoint allows the quick subscription of a feed where no title or tags are specified.

    POST /subscription/quickadd

### Authentication

    Required

### Request Parameters

ck
: `timestamp`: Current timestamp to prevent caching issues.

client
: `application name`: String that identifies the client used.

### Post Parameters

quickadd
: `stream id`: The feed that is to be subscribed to.

T
: `token`: Authentication token

### Response

    OK

## Export Subscriptions

    GET /subscriptions/export

### Authentication

    Required

### Response

OPML file of all subscriptions belonging to the authenticated user.

## Check Subscribed Status

Check if a user is subscribed to a specific feed already.

    GET /subscribed

### Request Parameters

s
: `stream id`: The feed that is to be checked.

### Response

    Boolean
