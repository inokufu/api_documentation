---
description: Explore our guides and examples to integrate the Inokufu web services APIs.
---

# Overview

## Welcome to the **Inokufu web services APIs**

The **Inokufu web services APIs** allow you to programmatically access Inokufu data and tools. You can use these APIs to retrieve information about learning objects, search for learning objects meeting specific criteria, explore domains of competency and more.

Inokufu APIs are divided into two distinct APIs: **Learning Object** and **Competency**. Each of these services has its own page in this documentation. The documentation for each API is structured by _endpoints_. An endpoint is a specific method within an API that performs one action and is located at a specific URL.

The **Learning Object API** gives you access to our ever-increasing index of 3M+ learning objects from various providers such as YouTube, Coursera, edX, Openclassrooms, Apple podcasts, Google Play Store, Apple Books, Amazon Books, Instructables, Medium, etc.

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

The **Competency API** enables you to explore and connect skills, occupations or domains of knowledge from various taxonomies and frameworks such as Wikipedia, ESCO classification, ROME codes from Pôle Emploi, Formacode®, etc.

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

## Reading this documentation

Each API endpoint in this documentation is described using several parts:

* **The HTTP method.** Includes `GET`, `POST`, `PUT`, `PATCH`, `DELETE`.
* **The base path.** URLs referenced in the documentation have a base path such as`https://api.inokufu.com/learningobject/v2` . This base path goes _before_ the endpoint path. Note that if you use [RapidAPI](https://rapidapi.com/organization/inokufu-search) to connect to our APIs, you should use the base URL provided by RapidAPI, such as `https://learning-objects-v2.p.rapidapi.com`
* **The endpoint path.** This path goes after the base path and enable you to access the specific endpoint you need. For example, to access the Search endpoint of the Learning object API v2, you must add `/search` to the base path:`https://api.inokufu.com/learningobject/v2/search`
* **Required parameters.** These parameters must be included in a request. Query parameters are added to the end of the URL with [query string encoding](https://en.wikipedia.org/wiki/Query\_string). In the example above, `lang=en` and `type=video` are required parameters.
* **Optional parameters.** These parameters can be included in a request to customize the query.
* **Authentication.** If an API endpoint requires authentication, the API key must be included in the request header.
* **Code examples.** Each endpoint has example requests in cURL, python, php and javascript format.

## API versioning

Each Inokufu API has a version string that is specified in the base URL. The version string for a given Inokufu API can be incremented independently from other Inokufu APIs. We encourage you to use the newest available version of the Inokufu APIs.

#### Backwards compatible changes <a href="#backwards-compatible-changes" id="backwards-compatible-changes"></a>

The following changes to a Inokufu API are considered _backwards compatible_. The version string of an API will not be incremented if we:

* Add properties to JSON objects.
* Change the number of items returned in a single listing request.
* Change rate limiting thresholds.
* Change the structure or length of identifiers generated by the API.
* Change error messages.

#### Backwards incompatible changes <a href="#backwards-incompatible-changes" id="backwards-incompatible-changes"></a>

The following changes are considered _backwards incompatible_. The version string of an API will be incremented if we:

* Remove properties from JSON objects.
* Change an API's URL structure.

If we deprecate an API or API endpoint that you are using, we will email you to give you at least 90 days' notice.

## Rate limits

Each Inokufu API has rate limits that cap the number of requests you can make against an endpoint. If you exceed a rate limit, your request will be throttled, and you will receive a `HTTP 429 Too Many Requests` response from the API.

If you need a rate limit that is higher than the default, please consider upgrading to a higher paid plan or contacting our [Inokufu sales team](mailto:sales@inokufu.com).

## URL length limits

The maximum URL length that our APIs accept before returning a HTTP `414 URI too long` response status code is an 8,192 byte limit. Note that some APIs accept `POST` requests with the query parameters in the request body as a workaround for this limitation. The documentation for each endpoint indicates which HTTP request methods it accepts.

## HTTPS

We recommend that all access to Inokufu APIs is over HTTPS. Requests initiated over HTTP are automatically upgraded to HTTPS.

## Pagination

Pagination lets you list many objects from an API by using more than one request.

In the Inokufu API endpoints that support pagination, the optional `max` parameter specifies the maximum number of objects to return. The API will try to return the requested number of objects.

## Timeout

You may experience timeout during the first calls to our endpoints after a long period of inactivity when using demo or free keys. Don't worry, wait a few minutes and make your call again, everything should work as usual. There is no cold start issue when using a paid key.

## Questions? Need Help? Found a bug?

If you've got questions about our API, found a bug or just want to chat with our developers, please feel free to email us at [support@inokufu.com](mailto:support@inokufu.com)!
