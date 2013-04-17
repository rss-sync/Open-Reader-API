---
title: Subscription
---

# Subscription

* TOC
{:toc}

You’ve just created a new nanoc site. The page you are looking at right now is the home page for your site. To get started, consider replacing this default homepage with your own customized homepage. Some pointers on how to do so:

- **Change this page’s content** by editing the “index.html” file in the “content” directory. This is the actual page content, and therefore doesn’t include the header, sidebar or style information (those are part of the layout).
- **Change the layout**, which is the “default.html” file in the “layouts” directory, and create something unique (and hopefully less bland).

If you need any help with customizing your nanoc web site, be sure to check out the documentation (see sidebar), and be sure to subscribe to the discussion group (also see sidebar). Enjoy!


## List Subscriptions

List all subscriptions for the current authenticated user

    GET /subscription/list

Nullam id dolor id nibh ultricies vehicula ut id elit. Donec sed odio dui. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent commodo cursus magna, vel scelerisque nisl consectetur et. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit.

Cras mattis consectetur purus sit amet fermentum. Maecenas faucibus mollis interdum. Praesent commodo cursus magna, vel scelerisque nisl consectetur et. Maecenas faucibus mollis interdum. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean lacinia bibendum nulla sed consectetur. Nullam quis risus eget urna mollis ornare vel eu leo.

### Parameters

client
: `application name`

ck
: `timestamp`

source
: - `RECOMMENDATION`: subscribed from recommendation
- `SUBSCRIBE_BUTTON`: when you clicked the subscribe button

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
