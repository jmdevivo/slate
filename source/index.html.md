---
title: Snapshot API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell: cURL

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---
# Snapshot API

### Version information
Version : 1.0.0

### Contact information
Contact : Kasisto
Contact Email : info@kasisto.com


# Introduction

Welcome to Snapshot. Snapshot is an API used for obtaining screenshots of user-specified websites. The user provides the `url` of the webpage they wish to get an image of as well as the `width` and `height` (in pixels) of the desired image. A png image file will then be provided as the response to the user.


# Screenshots


## Request a screenshot (GET)

These endpoints request a screenshot

### HTTP Request


`GET https://snapshot.kitsys.net/create_snap`

>An Example of a call to take a 1000x1000 screenshot of the google homepage would look like this

```shell
curl https://snapshot.kitsys.net/create_snap?url=http://google.com&width=1000&height=1000
```

### Query Parameters

Parameter | Description
--------- | -----------
url | the URL of the requested webpage
width | the width (in pixels) of the requested screenshot
height | the height (in pixels) of the requested screenshot

## Request a screenshot (POST)

### HTTP Request

`POST https://snapshot.kitsys.net/create_snap`

>An Example of a call to take a 1000x1000 screenshot of the google homepage would look like this

```shell
curl --request POST \
  --url 'https://snapshot.kitsys.net/create_snap?=,' \
  --header 'content-type: multipart/form-data' \
  --form url=http://google.com \
  --form width=1000 \
  --form height=1000 \
  --form localmode=false
```

>Unlike the GET request which returns a png, the POST request will return a json string containing the status code and url of the screenshot in Amazon S3

```json
{
  "file_url": "https://s3.amazonaws.com/kaisnapshots/65808744-64b1-443e-85f3-e48c8125913d.png",
  "status": "success"
}
```
### Query Parameters

Parameter | Description
--------- | -----------
url | the URL of the requested webpage
width | the width (in pixels) of the requested screenshot
height | the height (in pixels) of the requested screenshot
localmode | indicates snapshot is running in local mode, should normally be set to false


