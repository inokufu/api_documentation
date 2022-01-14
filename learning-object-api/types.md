---
description: This endpoint returns a list of the types currently supported by the API.
---

# Types

## Supported types

The API currently supports 13 types of learning objects as follows:

| Type                | Example of providers                             |
| ------------------- | ------------------------------------------------ |
| `video`             | YouTube, Dailymotion, Vimeo                      |
| `mooc`              | edX, Coursera, OpenClassrooms, Linkedin Learning |
| `podcast`           | ApplePodcasts, SoundCloud                        |
| `app`               | App Store, Google Play Store                     |
| `article`           | Wikipedia, Medium                                |
| `book`              | Amazon books, Google books                       |
| `ebook`             | Apple Books, Google books                        |
| `career profile`    | ONISEP, Oriane, Pôle Emploi                      |
| `distance learning` | MIT, Stanford, MonCompteFormation                |
| `training`          | MonCompteFormation, Pôle Emploi                  |
| `safety sheet`      | OSHA, INRS                                       |
| `tutorial`          | WikiHow, Instructables                           |
| `website`           | Code Academy, Apprendre TV5 Monde                |

> We are in the process of indexing additional types of learning objects such as exercise, XR/VR/AR, scientific articles, reports, etc. When available, these types will be added to the supported list.

You can access to the list of supported types using the `/type` endpoint as described below.

## Request

{% tabs %}
{% tab title="Rapid API" %}
```bash
GET https://learning-objects-v2.p.rapidapi.com/type
```
{% endtab %}

{% tab title="Direct customer" %}
```
GET https://api.inokufu.com/learningobject/v2/type
```
{% endtab %}
{% endtabs %}

### Headers

This endpoint does not require any API key authentication in the header.

### Query Parameters

This endpoint does not require any query parameter.

### Code examples

See [here](https://rapidapi.com/inokufu-search-api/api/learning-objects-v2/) for **Rapid API** codes examples.

See below for **Direct customer** access:

{% tabs %}
{% tab title="Shell" %}
```bash
curl "https://api.inokufu.com/learningobject/v2/type"
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
r = requests.get('https://api.inokufu.com/learningobject/v2/type')
r.json()
```
{% endtab %}

{% tab title="php" %}
```php
$curl = curl_init('https://api.inokufu.com/learningobject/v2/type');
//Download the certificate from 'https://api.inokufu.com/' to avoid SSL errors and replace 'certInokufu.cer' with the name of your downloaded file
curl_setopt($curl,CURLOPT_CAINFO,__DIR__ . DIRECTORY_SEPARATOR . 'certInokufu.cer');
$data = curl_exec($curl);
if($data===false){
   var_dump(curl_error($curl));
};
```
{% endtab %}

{% tab title="Javascript" %}
```javascript
const type = async () => {fetch('https://api.inokufu.com/learningobject/v2/type' ).then(function(response) {
  if(response.ok) {
    response.json().then(function(json) { 
      const resJson = JSON.stringify(json)
      return resJson;
})}})};
```
{% endtab %}
{% endtabs %}

## Response

### Response parameters

| Parameter     | Description                                                                                        |
| ------------- | -------------------------------------------------------------------------------------------------- |
| `type`        | Name of the type of LO to be used in the `/search` endpoint to filter LO with the `type` parameter |
| `description` | Short description of this type                                                                     |

### Response example

Here is an example of the JSON structured response provided by this endpoint.

```javascript
[
    {
        "type": "app",
        "description": "Educational apps or apps that may be useful for learning a new skill or job, from providers such as App Store, Google Play Store, etc."
    },
    {
        "type": "article",
        "description": "Articles that may be useful for learning a new skill or job from providers such as Wikipedia, Medium, etc. "
    },
    {
        "type": "book",
        "description": "Textbooks and other educational books from providers such as Amazon books, Google books, etc. "
    },
    {
        "type": "career profile",
        "description": " Career profiles in various form from providers such as ONISEP, Oriane, Pôle Emploi, Fichemetier.fr, etc…"
    },
    {
        "type": "distance learning",
        "description": " Remote trainings or degrees from providers such as MIT, Stanford, MonCompteFormation, etc."
    },
    {
        "type": "ebook",
        "description": "Electronic textbooks and other educational ebooks from providers such as Apple Books, Google books, etc"
    },
    {
        "type": "mooc",
        "description": "Massive Open Online Courses (MOOC) from providers such as edX, Coursera, OpenClassrooms, Linkedin Learning, etc."
    },
    {
        "type": "podcast",
        "description": "Educational audio files from providers such as Apple Podcasts, SoundCloud, etc."
    },
    {
        "type": "safety sheet",
        "description": "Safety data sheets from providers such as OSHA, INRS, etc."
    },
    {
        "type": "serious game",
        "description": "Educational games from providers such as Google play store, App store, etc."
    },
    {
        "type": "training",
        "description": "In-person trainings or degrees from providers such as MonCompteFormation, Pôle Emploi, etc. "
    },
    {
        "type": "tutorial",
        "description": "Tutorials and others step by step instructions from providers such à WikiHow, Instructables, etc."
    },
    {
        "type": "video",
        "description": "Educational videos from providers such as YouTube, Nebula, Vimeo, etc."
    },
    {
        "type": "website",
        "description": "Websites that gather content on a specific topic, from providers such as, etc"
    }
]
```

