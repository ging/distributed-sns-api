# API for distributed social network sites

This document describes an API for distributed social network sites based on [Activity Streams](http://activitystrea.ms). Social network sites send messages between them to communicate the actions of their users. Activities may have side-effects, modifying the social graph, creating new content, etc.

## Activity Streams

The API uses the following specifications from Activity Streams:

* [JSON Activity Streams 1.0](http://activitystrea.ms/specs/json/1.0/)
* [Audience Targeting for JSON Activity Streams](http://activitystrea.ms/specs/json/targeting/1.0/)
* [Responses for Activity Streams](http://activitystrea.ms/specs/json/replies/1.0/)

## Activities endpoint

Sites offer one activities endpoint for other sites to post their activities. The activity endpoint is discovered using [Web Host Metadata](http://tools.ietf.org/html/draft-hammer-hostmeta-17). Using the "activities" link. 

	<Link rel='activities' href='http://example.com/activities' />

## Creating an activity

Activities between sites are created posting Activity Streams formated JSON to the activity endpoint:

  POST /activities HTTP/1.1
  Host: example.com
  Authorization: Bearer mF.9.B5f-4.1JqM
  Content-Type: application/json

  {
    "id": "http://example.net/activities-n",
    "actor": {
        "id": "acct:bob@example.net",
        "displayName": "Bob",
        "objectType": "person",
        "url": "http://example.net/bob"
    },
    "verb": "post",
    "object": {
        "id": "http://example.net/notes/hello-world",
        "content": "Hello, World!"
        "objectType": "note"
    },
    "published": "1973-01-01T00:00:00"
  }

## Authentication

Sites are authenticated using OAuth 
