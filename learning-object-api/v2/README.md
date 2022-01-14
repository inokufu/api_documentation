---
description: Find the best learning objects in a flash ⚡
---

# Learning Object v2

## Introduction

This page shows you how to access our Learning Objects Index of more than 2.5M+ learning objects (LO) from various sources such as YouTube, Coursera, edX, Apple podcasts, Google Play store, etc.

You can view shell, python, php and JavaScript code examples in the dark areas.

## Authentication

Inokufu API Cloud uses API keys to allow access to our APIs. You can access this API in two ways:

* **Rapid API**: this is recommended for small to medium usage. You'll need to create a Rapid API account [here](https://rapidapi.com/auth/sign-up?referral=/organization/inokufu-search), then to subscribe to one of our plan [here](https://rapidapi.com/inokufu-search-api/api/learning-objects-v2/pricing). Rapid API will then provide you with your Developer API key
* **Direct customer**: this is reserved for very high usage and custom needs. If you want to know more about our enterprise plans, please feel free to contact our [Inokufu sales team](mailto:sales@inokufu.com).

Inokufu APIs expects for the API key to be included in API requests to the server in a header that looks like the following:

{% tabs %}
{% tab title="Rapid API" %}
```
"x-rapidapi-key": "SAY-FRIEND-AND-ENTER"
```
{% endtab %}

{% tab title="Direct customer" %}
```
"x-api-key": "SAY-FRIEND-AND-ENTER"
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
Make sure to replace SAY-FRIEND-AND-ENTER with your own Developer API key.
{% endhint %}

### Code examples

See [here](https://rapidapi.com/inokufu-search-api/api/learning-objects-v2/) for **Rapid API** codes example.

See below for **Direct customer** access:

{% tabs %}
{% tab title="Shell" %}
```bash
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "x-api-key: SAY-FRIEND-AND-ENTER"
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
url = 'api_endpoint_here'
headers = {'x-api-key': 'SAY-FRIEND-AND-ENTER'}
r = requests.get(url, headers=headers)
r.json()
```
{% endtab %}

{% tab title="PHP" %}
```php
$key = 'SAY-FRIEND-AND-ENTER';
$curl = curl_init('api_endpoint_here');
curl_setopt($curl,CURLOPT_CAINFO,__DIR__ . DIRECTORY_SEPARATOR . 'certInokufu.cer');
curl_setopt($curl, CURLOPT_HTTPHEADER, array('x-api-key:'.$key));
$data = curl_exec($curl);
if($data===false){
    var_dump(curl_error($curl));
};
```
{% endtab %}

{% tab title="Javascript" %}
```javascript
apiKeySecured = 'SAY-FRIEND-AND-ENTER';
const search = async () => {fetch('api_endpoint_here', {headers: {"x-api-key": apiKeySecured}} ).then(function(response) {
  if(response.ok) {
      response.json().then(function(json) { 
        const resJson = JSON.stringify(json)
        //console.log(resJson);
        return resJson;
})}})};
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
For Demo purpose, you can use this API key : `demo29331806e87fe8d34d03ddaad2b1b454b58a5b9d4f1385d4f86bb321` but beware both request speed and number of daily calls are limited with this key.
{% endhint %}

### Usage plans

Free Developer API keys are available through our **Rapid API** portal [here](https://rapidapi.com/inokufu-search-api/api/learning-objects-v2/pricing).

Several usage plans are available depending on your needs.

| Usage plan                  |          Basic         |           Pro           |           Ultra           |       Direct customer      |
| --------------------------- | :--------------------: | :---------------------: | :-----------------------: | :------------------------: |
| Requests included           |       500 /month       |      10 000 /month      |       100 000 /month      |      >> 100 000 /month     |
| Rate Limit                  | 10 requests per second | 100 requests per second |  100 requests per second  | >> 100 requests per second |
| Support                     |            x           |          email          |       priority email      |    email + phone (24h/7)   |
| Monthly pricing             |            0           |           $99           |            $799           |          On quote          |
| Cost per additional request |      + $0.08 each      |       + $0.02 each      | <p>+ $0.01</p><p>each</p> |          On quote          |

If you have specific requirement for your use case, we can offer you tailored usage plan. If you want to know more about our enterprise plans, please feel free to contact our [Inokufu sales team](mailto:contact@inokufu.com?subject=Inokufu%20API%20Key%20request\&body=Hi,%0D%0A%20%0D%0A%20I%20found%20your%20awesome%20Inokufu%20API%20Cloud%20and%20I%20would%20be%20very%20intersted%20to%20get%20a%20Key!%0D%0A%20%0D%0A%20My%20name%20is%20....%20and%20I%27d%20like%20to%20get%20a%20free%20API%20key%20for%20testing%20purpose%20/%20paid%20API%20key%20for%20integrating%20it%20in%20my%20app/project.%20%0D%0A%20%0D%0A%20Regards,%20%0D%0A%20...).

{% hint style="info" %}
We also have an academic access program for researchers and academics that would like to build and experiment with this API.
{% endhint %}

## Best efforts

Our mission is to help you find the best learning objects out there. While we are working hard on this ambitious goal, we are still at the begining of this journey and we have not indexed the whole educational content available on internet (yet). At this stage, we can't guaranty 100% accuracy of our results, nor that we will be able to find learning objects on any topic or any set of query parameters.

**Results returned by the API are our best efforts to match your query.**

Each response returned by endpoints `search` or `search-provider` contains a message (`msg`) that tells you how good we think our answer to your query is. Messages currently returned by the API are shown in the table below.

| Code |                         Message                         |                                                                Meaning                                                                |
| ---- | :-----------------------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------: |
| A00  | These results are our best effort to answer your query. |                           We are pretty confident that these results closely match what you are looking for.                          |
| B00  |     These results does not match exactly your query.    |  We have some results to show you that may be close enough to your query but still it's not exactly what you asked for, so you know.  |
| C00  |           No result to display for this query.          | We have found no result we are confident enough to show you based on what you are looking for. Try again with less strict parameters. |

{% hint style="success" %}
You can adjust how strict you want the results to match your query. The API offers two parameters for this purpose: `match` and `model`. 

* `match` is used to indicate how stricly you want the results to match your query parameters (excluding `keywords`parameter).
* `model`is used to indicate how strictly you want the results to match the `keywords`parameter. 
{% endhint %}

## Search

This endpoint returns a list of learning objects (LO) that matches specific keywords, language and type (format).

### Request

{% tabs %}
{% tab title="Rapid API" %}
```
GET https://learning-objects-v2.p.rapidapi.com/search
```
{% endtab %}

{% tab title="Direct customer" %}
```
GET https://api.inokufu.com/learningobject/v2/search
```
{% endtab %}
{% endtabs %}

#### Headers

The API key must be included in the header.

{% tabs %}
{% tab title="Rapid API" %}
```
"x-rapidapi-key": "SAY-FRIEND-AND-ENTER"
```
{% endtab %}

{% tab title="Direct customer" %}
```
"x-api-key": "SAY-FRIEND-AND-ENTER"
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
Make sure to replace SAY-FRIEND-AND-ENTER with your own Developer API key.
{% endhint %}

#### Query Parameters

Query parameters must be included in the URL.

| Parameter         | Type      |    Default    | Required | Description                                                                                                                                                                                                                                                                                                                                                             |
| ----------------- | --------- | :-----------: | :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `keywords`        | _string_  |               |    Yes   | Keywords help you refine the topic of the learning objects. Best results are obtained when using the most commonly used designation for a skill, a competency or a job.                                                                                                                                                                                                 |
| `lang`            | _string_  |      `en`     |    Yes   | Language of the LO such as `en` (english), `fr`(french), etc. Use the `/lang`endpoint to get the full list of languages currently supported by the API.                                                                                                                                                                                                                 |
| `type`            | _string_  |    `video`    |    Yes   | Type of the LO such as `video`, `mooc`, `book`, etc. Use the `/type`endpoint to get the full list of types currently supported by the API.                                                                                                                                                                                                                              |
| `sort`            | _string_  |  `popularity` |    Yes   | Currently supported sorting order are `random` or `popularity`. If empty, response will be sorted by `popularity`.                                                                                                                                                                                                                                                      |
| `match`           | _string_  | `best-effort` |    Yes   | <p>How strict the query parameters are applied. Two matches are currently supported:</p><ul><li><code>strict</code> match gives you less results but strictly apply all your query parameters.</li><li><code>best-effort</code> match gives you more results but your query parameters will be loosely applied.</li></ul>                                               |
| `model`           | _string_  |    `strict`   |    Yes   | <p>The model used by the API to determine if a LO is relevant based on the provided keywords. Two models are currently supported:</p><ul><li><code>strict</code> model gives you less results but is usually more relevant (less false positive).</li><li><code>extended</code> model gives you more results but with a higher probability of false positive.</li></ul> |
| `max`             | _integer_ |       10      |    Yes   | Maximum number of LO returned per page. Value must be between 1 to 20.                                                                                                                                                                                                                                                                                                  |
| `page`            | _integer_ |       0       |    Yes   | The number of returned page, starting at 0.                                                                                                                                                                                                                                                                                                                             |
| `bloom`           | _string_  |               |    No    | <p><a href="https://en.wikipedia.org/wiki/Bloom&#x27;s_taxonomy">Bloom objective</a> of the LO such as <code>discover</code>, <code>understand</code>, <code>do</code>, etc.</p><p>Use the <code>/bloom</code>endpoint to get the full list of Bloom objectives currently supported by the API.</p>                                                                     |
| `ageMax`          | _integer_ |               |    No    | The maximum age associated to the LO. For example, if you want to see videos for kids only you can set `ageMax=10`.                                                                                                                                                                                                                                                     |
| `ageMin`          | _integer_ |               |    No    | The minimum age associated to the LO. For example, if you want to see textbooks for adult only you can set `ageMin=18`.                                                                                                                                                                                                                                                 |
| `learningTimeMax` | _integer_ |               |    No    | The maximum length of the LO in minute (`video` only). For example, if you want to see 5 min or less videos only, you can set `learningTimeMax=5`.                                                                                                                                                                                                                      |
| `learningTimeMin` | _integer_ |               |    No    | The minimum length of the LO in minute (`video` only). For example, if you want to see 1h or more videos only, you can set `learningTimeMin=60`.                                                                                                                                                                                                                        |
| `levelMax`        | _decimal_ |               |    No    | The maximum level of the LO. The level is indicated as decimal number ranging from -1 (beginner) to 1 (advanced). For example, if you want to see a MOOC with a level for beginner, you can set `levelMax=-0.5`.                                                                                                                                                        |
| `levelMin`        | _decimal_ |               |    No    | The minimum level of the LO. The level is indicated as decimal number ranging from -1 (beginner) to 1 (advanced). For example, if you want to see a MOOC with a level for intermediate or above, you can set `levelMin=0.2`.                                                                                                                                            |
| `popularityMin`   | _decimal_ |               |    No    | Popularity is an indicator of the popularity of the LO as measured by its number of likes, stars, views, etc. This parameter enables you to set a threshold to filter out LO below a certain popularity. This value ranges from 0 (low popularity) to 1 (exceptionally popular).                                                                                        |
| `address`         | _string_  |               |    No    | The address around which you want to search. Works only for geolocated learning objects (eg `training`). Used in conjuction with `distanceMax.`                                                                                                                                                                                                                         |
| `distanceMax`     | _integer_ |               |    No    | The maximum distance within which you want to search. Works only for geolocated learning objects (eg `training`). Used in conjuction with `address.`                                                                                                                                                                                                                    |
| `free`            | _bool_    |               |    No    | This allows you to filter by free content only (`free=true`) or paid content only (`free=false`). If empty, you'll get both free and paid contents.                                                                                                                                                                                                                     |

{% hint style="info" %}
If you want to enforce strictly one specific query paremeter, you can add `!important` after it. This parameter wil be applied strictly even if the global `match` parameter is set to `best-effort`.
{% endhint %}

#### Code examples

See [here](https://rapidapi.com/inokufu-search-api/api/learning-objects-v2/) for **Rapid API** codes examples.

See below for **Direct customer** access:

{% tabs %}
{% tab title="Shell" %}
```bash
curl "https://api.inokufu.com/learningobject/v2/search?keywords=python&type=mooc&lang=en&max=2"
-H "x-api-key: SAY-FRIEND-AND-ENTER"
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
url = 'https://api.inokufu.com/learningobject/v2/search?keywords=python&type=mooc&lang=en&max=2'
headers = {'x-api-key': 'x-api-key: SAY-FRIEND-AND-ENTER'}
r = requests.get(url, headers=headers)
r.json()
```
{% endtab %}

{% tab title="php" %}
```php
$key = 'SAY-FRIEND-AND-ENTER';
$curl = curl_init('https://api.inokufu.com/learningobject/v2/search?keywords=python&type=mooc&lang=en&max=2');
//Download the certificate from 'https://api.inokufu.com/' to avoid SSL errors and replace 'certInokufu.cer' with the name of your downloaded file
curl_setopt($curl,CURLOPT_CAINFO,__DIR__ . DIRECTORY_SEPARATOR . 'certInokufu.cer');
curl_setopt($curl, CURLOPT_HTTPHEADER, array('x-api-key:'.$key));
$data = curl_exec($curl);
if($data===false){
    var_dump(curl_error($curl));
};
```
{% endtab %}

{% tab title="Javascript" %}
```javascript
apiKeySecured = 'SAY-FRIEND-AND-ENTER';
const search = async () => {fetch('https://api.inokufu.com/learningobject/v2/search?keywords=python&type=mooc&lang=en&max=2', {headers: {"x-api-key": apiKeySecured}} ).then(function(response) {
  if(response.ok) {
      response.json().then(function(json) { 
        const resJson = JSON.stringify(json)
        //console.log(resJson);
        return resJson;
})}})};
```
{% endtab %}
{% endtabs %}

### Response

#### Response parameters

| Parameter            | Required | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| -------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `title`              | Yes      | Title of the LO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `url`                | Yes      | Link to access the LO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `description`        |          | Short description of the LO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `picture`            |          | Link to the thumbnail picture of the LO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `provider`           |          | Name of the provider associated with this LO. Provider is the organization that hosts the LO.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `bloom`              |          | List of the Bloom objectives associated with this LO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `type`               |          | List of the type associated to this LO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `level`              |          | The level is indicated as decimal number ranging from -1 (beginner) to 1 (advanced)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `learningTimeValue`  |          | Length associated to the LO (based on the unit provided accordingly)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `learningTimeUnit`   |          | Unit of the length associated to the LO (`h` for hour, `min` for minute, `p` for page)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `address`            |          | Postal address where the learning objects is located (eg `training`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `publisher`          |          | List of publishers associated with this LO. Publishers are the organization(s) that offer and/or sell the LO. For`mooc`, `distance learning `or `training` this can be an university, a school or a training organization.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `author`             |          | List of authors associated with this LO. Authors are the people that make the LO. For `mooc`,`distance learning `or `training` this can be a teacher or `trainer`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `PriceSpecification` |          | <p>Informations about the pricing of the LO, which includes:</p><ul><li><code>price</code> is the offer price of the LO as a decimal number.</li><li><code>priceCurrency</code>is the currency of the price of the LO as a symbol (<code>$</code>, <code>€</code> , etc)</li><li><code>price-free</code> is a boolean that is <code>true</code> when the LO can be accessed without paying, and <code>false</code> when the LO requires payment to be accessed.</li></ul><p>Beware some <code>providers</code>such as Coursera offer all their <code>mooc</code> in both free and paid version. In this case the price of the LO will be not null while marked as <code>price-free=true</code></p> |

#### Response example

Here is an example of the JSON structured response provided by this endpoint.

```javascript
{
    "statusCode": 200,
    "request": {
        "keywords": "python",
        "lang": "en",
        "type": "MOOC",
        "sort": "popularity",
        "max": 2,
        "bloom": "",
        "model": "strict",
        "address": "",
        "distanceMax": "",
        "ageMin": "",
        "ageMax": "",
        "popularityMin": 0,
        "levelMin": "",
        "levelMax": "",
        "learningTimeMin": "",
        "learningTimeMax": "",
        "publisher": "",
        "author": "",
        "free": "",
        "page": 0,
        "id": "36b1af96-6e1d-483f-a3c8-b86da8926382"
    },
    "response": {
        "content": [
            {
                "title": "Python Basics for Data Science",
                "url": "https://www.edx.org/course/python-basics-for-data-science-2",
                "description": "Is cancer partly preventable through a healthy diet? Cancer has overtaken cardiovascular disease (CVD) as the leading cause of death in many parts of the world. It causes one in eight deaths worldwide. Global trends show that the majority of all cancer deaths occur in the low- and middle-income coun...",
                "picture": "https://prod-discovery.edx-cdn.org/media/course/image/381a0046-5d78-4790-8776-74620d59f48e-48611c7ca556.small.png",
                "provider": "edX",
                "bloom": [
                    "understand"
                ],
                "type": [
                    "MOOC"
                ],
                "publisher": [
                    {
                        "name": "IBM"
                    },
                    {
                        "name": "edX"
                    }
                ],
                "author": [
                    {
                        "name": "Joseph Santarcangelo"
                    }
                ],
                "level": -1.0,
                "learningTimeValue": 40,
                "learningTimeUnit": "h",
                "PriceSpecification": {
                    "@context": "https://schema.org/",
                    "@type": "PriceSpecification",
                    "price": 39.0,
                    "priceCurrency": "$",
                    "price-free": true
                }
            },
            {
                "title": "Analyzing Data with Python",
                "url": "https://www.edx.org/course/data-analysis-with-python",
                "description": "- Once you complete this course, continue onto Building Interactive Prototypes using JavaScript to enhance your prototype as you learn how to use JavaScript to allow interaction on your webpages.",
                "picture": "https://prod-discovery.edx-cdn.org/media/course/image/29a1e3b8-3e84-4b14-b60d-0fa97512e420-cea90db44606.small.png",
                "provider": "edX",
                "bloom": [
                    "understand"
                ],
                "type": [
                    "MOOC"
                ],
                "publisher": [
                    {
                        "name": "IBM"
                    },
                    {
                        "name": "edX"
                    }
                ],
                "author": [
                    {
                        "name": "Joseph Santarcangelo"
                    }
                ],
                "level": 0.5,
                "learningTimeValue": 200,
                "learningTimeUnit": "h",
                "PriceSpecification": {
                    "@context": "https://schema.org/",
                    "@type": "PriceSpecification",
                    "price": 39.0,
                    "priceCurrency": "$",
                    "price-free": true
                }
            }
        ],
        "metadata": {
            "page": 0,
            "number item per page": 2,
            "total number item": 2402,
            "hasMore": true
        },
        "msg": "A00 - These results are our best effort to answer your query."
    }
}
```

## Search by provider

This endpoint returns a list of learning objects (LO) that matches specific keywords, language and provider.

### Request

{% tabs %}
{% tab title="Rapid API" %}
```
GET https://learning-objects-v2.p.rapidapi.com/search-provider
```
{% endtab %}

{% tab title="Direct customer" %}
```
GET https://api.inokufu.com/learningobject/v2/search-provider
```
{% endtab %}
{% endtabs %}

#### Headers

The API key must be included in the header.

{% tabs %}
{% tab title="Rapid API" %}
```
"x-rapidapi-key": "SAY-FRIEND-AND-ENTER"
```
{% endtab %}

{% tab title="Direct customer" %}
```
"x-api-key": "SAY-FRIEND-AND-ENTER"
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
Make sure to replace SAY-FRIEND-AND-ENTER with your own Developer API key.
{% endhint %}

#### Query Parameters

Query parameters must be included in the URL.

| Parameter         | Type      |    Default    | Required | Description                                                                                                                                                                                                                                                                                                                                                             |
| ----------------- | --------- | :-----------: | :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `keywords`        | _string_  |               |    Yes   | Keywords help you refine the topic of the learning objects. Best results are obtained when using the most commonly used designation for a skill, a competency or a job.                                                                                                                                                                                                 |
| `lang`            | _string_  |      `en`     |    Yes   | Language of the LO such as `en` (english), `fr`(french), etc. Use the `/lang`endpoint to get the full list of languages currently supported by the API.                                                                                                                                                                                                                 |
| `provider`        | _string_  |   `youtube`   |    Yes   | Provider of the LO such as `youtube`, `coursera`, `applebooks`, etc. Use the `/provider`endpoint to get the list of the providers currently supported by this endpoint.                                                                                                                                                                                                 |
| `sort`            | _string_  |  `popularity` |    Yes   | Currently supported sorting order are `random` or `popularity`. If empty, response will be sorted by `popularity`.                                                                                                                                                                                                                                                      |
| `match`           | _string_  | `best-effort` |    Yes   | <p>How strict the query parameters are applied. Two matches are currently supported:</p><ul><li><code>strict</code> match gives you less results but strictly apply all your query parameters.</li><li><code>best-effort</code> match gives you more results but your query parameters will be loosely applied.</li></ul>                                               |
| `model`           | _string_  |    `strict`   |    Yes   | <p>The model used by the API to determine if a LO is relevant based on the provided keywords. Two models are currently supported:</p><ul><li><code>strict</code> model gives you less results but is usually more relevant (less false positive).</li><li><code>extended</code> model gives you more results but with a higher probability of false positive.</li></ul> |
| `max`             | _integer_ |       10      |    Yes   | Maximum number of LO returned per page. Value must be between 1 to 20.                                                                                                                                                                                                                                                                                                  |
| `page`            | _integer_ |       0       |    Yes   | The number of returned page, starting at 0.                                                                                                                                                                                                                                                                                                                             |
| `publisher`       |           |               |    No    | Publishers are the organization(s) that offer and/or sell the LO. For`mooc`, `distance learning `or `training` this can be an university, a school or a training organization.                                                                                                                                                                                          |
| `ageMax`          | _integer_ |               |    No    | The maximum age associated to the LO. For example, if you want to see videos for kids only you can set `ageMax=10`.                                                                                                                                                                                                                                                     |
| `ageMin`          | _integer_ |               |    No    | The minimum age associated to the LO. For example, if you want to see textbooks for adult only you can set `ageMin=18`.                                                                                                                                                                                                                                                 |
| `learningTimeMax` | _integer_ |               |    No    | The maximum length of the LO in minute (`video` only). For example, if you want to see 5 min or less videos only, you can set `learningTimeMax=5`.                                                                                                                                                                                                                      |
| `learningTimeMin` | _integer_ |               |    No    | The minimum length of the LO in minute (`video` only). For example, if you want to see 1h or more videos only, you can set `learningTimeMin=60`.                                                                                                                                                                                                                        |
| `levelMax`        | _decimal_ |               |    No    | The maximum level of the LO. The level is indicated as decimal number ranging from -1 (beginner) to 1 (advanced). For example, if you want to see a MOOC with a level for beginner, you can set `levelMax=-0.5`.                                                                                                                                                        |
| `levelMin`        | _decimal_ |               |    No    | The minimum level of the LO. The level is indicated as decimal number ranging from -1 (beginner) to 1 (advanced). For example, if you want to see a MOOC with a level for intermediate or above, you can set `levelMin=0.2`.                                                                                                                                            |
| `popularityMin`   | _decimal_ |               |    No    | Popularity is an indicator of the popularity of the LO as measured by its number of likes, stars, views, etc. This parameter enables you to set a threshold to filter out LO below a certain popularity. This value ranges from 0 (low popularity) to 1 (exceptionally popular).                                                                                        |
| `address`         | _string_  |               |    No    | The address around which you want to search. Works only for geolocated learning objects (eg `training`). Used in conjuction with `distanceMax.`                                                                                                                                                                                                                         |
| `distanceMax`     | _integer_ |               |    No    | The maximum distance within which you want to search. Works only for geolocated learning objects (eg `training`). Used in conjuction with `address.`                                                                                                                                                                                                                    |
| `free`            | _bool_    |               |    No    | This allows you to filter by free content only (`free=true`) or paid content only (`free=false`). If empty, you'll get both free and paid contents.                                                                                                                                                                                                                     |

{% hint style="info" %}
If you want to enforce strictly one specific query paremeter, you can add `!important` after it. This parameter wil be applied strictly even if the global `match` parameter is set to `best-effort`.
{% endhint %}

#### Code examples

See [here](https://rapidapi.com/inokufu-search-api/api/learning-objects-v2/) for **Rapid API** codes examples.

See below for **Direct customer** access:

{% tabs %}
{% tab title="Shell" %}
```bash
curl "https://api.inokufu.com/learningobject/v2/search-provider?keywords=python&provider=coursera&lang=en&max=2"
-H "x-api-key: SAY-FRIEND-AND-ENTER"
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
url = 'https://api.inokufu.com/learningobject/v2/search-provider?keywords=python&provider=coursera&lang=en&max=2'
headers = {'x-api-key': 'x-api-key: SAY-FRIEND-AND-ENTER'}
r = requests.get(url, headers=headers)
r.json()
```
{% endtab %}

{% tab title="php" %}
```php
$key = 'SAY-FRIEND-AND-ENTER';
$curl = curl_init('https://api.inokufu.com/learningobject/v2/search-provider?keywords=python&provider=coursera&lang=en&max=2');
//Download the certificate from 'https://api.inokufu.com/' to avoid SSL errors and replace 'certInokufu.cer' with the name of your downloaded file
curl_setopt($curl,CURLOPT_CAINFO,__DIR__ . DIRECTORY_SEPARATOR . 'certInokufu.cer');
curl_setopt($curl, CURLOPT_HTTPHEADER, array('x-api-key:'.$key));
$data = curl_exec($curl);
if($data===false){
    var_dump(curl_error($curl));
};
```
{% endtab %}

{% tab title="Javascript" %}
```javascript
apiKeySecured = 'SAY-FRIEND-AND-ENTER';
const search = async () => {fetch('https://api.inokufu.com/learningobject/v2/search-provider?keywords=python&provider=coursera&lang=en&max=2', {headers: {"x-api-key": apiKeySecured}} ).then(function(response) {
  if(response.ok) {
      response.json().then(function(json) { 
        const resJson = JSON.stringify(json)
        //console.log(resJson);
        return resJson;
})}})};
```
{% endtab %}
{% endtabs %}

### Response

#### Response parameters

| Parameter            | Required | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| -------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `title`              | Yes      | Title of the LO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `url`                | Yes      | Link to access the LO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `description`        |          | Short description of the LO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `picture`            |          | Link to the thumbnail picture of the LO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `provider`           |          | Name of the provider associated with this LO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `bloom`              |          | List of the Bloom objectives associated with this LO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `type`               |          | List of the type associated with this LO                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `level`              |          | The level is indicated as decimal number ranging from -1 (beginner) to 1 (advanced)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `learningTimeValue`  |          | Length associated to the LO (based on the unit provided accordingly)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `learningTimeUnit`   |          | Unit of the length associated to the LO (`h` for hour, `min` for minutes)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `address`            |          | Postal address where the learning objects is located (eg `training`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `publisher`          |          | List of publishers associated with this LO. Publishers are the organization(s) that offer and/or sell the LO. For`mooc`, `distance learning `or `training` this can be an university, a school or a training organization.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `author`             |          | List of authors associated with this LO. Authors are the people that make the LO. For `mooc`,`distance learning `or `training` this can be a teacher or `trainer`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `PriceSpecification` |          | <p>Informations about the pricing of the LO, which includes:</p><ul><li><code>price</code> is the offer price of the LO as a decimal number.</li><li><code>priceCurrency</code>is the currency of the price of the LO as a symbol (<code>$</code>, <code>€</code> , etc)</li><li><code>price-free</code> is a boolean that is <code>true</code> when the LO can be accessed without paying, and <code>false</code> when the LO requires payment to be accessed.</li></ul><p>Beware some <code>providers</code>such as Coursera offer all their <code>mooc</code> in both free and paid version. In this case the price of the LO will be not null while marked as <code>price-free=true</code></p> |

#### Response example

Here is an example of the JSON structured response provided by this endpoint.

```yaml
{
    "statusCode": 200,
    "request": {
        "keywords": "python",
        "lang": "en",
        "provider": "Coursera",
        "sort": "popularity",
        "max": 2,
        "model": "strict",
        "address": "",
        "distanceMax": "",
        "ageMin": "",
        "ageMax": "",
        "popularityMin": 0,
        "levelMin": "",
        "levelMax": "",
        "learningTimeMin": "",
        "learningTimeMax": "",
        "publisher": "",
        "author": "",
        "free": "",
        "page": 0,
        "id": "f0d6f275-87b2-4f93-b050-d41d81855b86"
    },
    "response": {
        "content": [
            {
                "title": "Data Analysis with Python",
                "url": "https://www.coursera.org/learn/data-analysis-with-python",
                "description": "Learn how to analyze data using Python. This course will take you from the basics of Python to exploring many",
                "picture": "https://s3.amazonaws.com/coursera-course-photos/1e/bccef0386611e889ebf7c982548ca6/Screen-Shot-2018-04-04-at-8.13.17-PM.png",
                "provider": "Coursera",
                "bloom": [
                    "Understand"
                ],
                "type": [
                    "MOOC"
                ],
                "level": -1.0,
                "lang": "en",
                "learningTimeValue": 11,
                "learningTimeUnit": "h",
                "PriceSpecification": {
                    "@context": "https://schema.org/",
                    "@type": "PriceSpecification",
                    "price": 38.0,
                    "priceCurrency": "$",
                    "price-free": true
                }
            },
            {
                "title": "An Introduction to Interactive Programming in Python (Part 2)",
                "url": "https://www.coursera.org/learn/interactive-python-2",
                "description": "This two-part course is designed to help students with very little or no computing background learn the basics of",
                "picture": "https://s3.amazonaws.com/coursera/topics/interactivepython/large-icon.png",
                "provider": "Coursera",
                "bloom": [
                    "Understand"
                ],
                "type": [
                    "MOOC"
                ],
                "level": -1.0,
                "lang": "en",
                "learningTimeValue": 19,
                "learningTimeUnit": "h",
                "PriceSpecification": {
                    "@context": "https://schema.org/",
                    "@type": "PriceSpecification",
                    "price": 0.0,
                    "price-free": true
                }
            }
        ],
        "metadata": {
            "page": 0,
            "number item per page": 2,
            "total number item": 96,
            "hasMore": true
        },
        "msg": "A00 - These results are our best effort to answer your query."
    }
}
```

## Lang

This endpoint returns a list of the languages currently supported by the API.

### Request

{% tabs %}
{% tab title="Rapid API" %}
```bash
GET https://learning-objects-v2.p.rapidapi.com/lang
```
{% endtab %}

{% tab title="Direct customer" %}
```
GET https://api.inokufu.com/learningobject/v2/lang
```
{% endtab %}
{% endtabs %}

#### Headers

This endpoint does not require any API key authentication in the header.

#### Query Parameters

This endpoint does not require any query parameter.

#### Code examples

See [here](https://rapidapi.com/inokufu-search-api/api/learning-objects-v2/) for **Rapid API** codes examples.

See below for **Direct customer** access:

{% tabs %}
{% tab title="Shell" %}
```bash
curl "https://api.inokufu.com/learningobject/v2/lang"
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
r = requests.get('https://api.inokufu.com/learningobject/v2/lang')
r.json()
```
{% endtab %}

{% tab title="php" %}
```php
$curl = curl_init('https://api.inokufu.com/learningobject/v2/lang');
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
const type = async () => {fetch('https://api.inokufu.com/learningobject/v2/lang' ).then(function(response) {
  if(response.ok) {
    response.json().then(function(json) { 
      const resJson = JSON.stringify(json)
      return resJson;
})}})};
```
{% endtab %}
{% endtabs %}

### Response

#### Response parameters

| Parameter     | Description                                                                                             |
| ------------- | ------------------------------------------------------------------------------------------------------- |
| `lang`        | Two-letter code of the language to be used in `/search` endpoint to filter LO with the `lang` parameter |
| `description` | Short description of this language                                                                      |

#### Response example

Here is an example of the JSON structured response provided by this endpoint.

```javascript
[
    {
        "lang": "en",
        "description": "Use this code for LO in english language."
    },
    {
        "lang": "fr",
        "description": "Use this code for LO in french language (français)."
    }
]
```

## Type

This endpoint returns a list of the types currently supported by the API.

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

### Request

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

#### Headers

This endpoint does not require any API key authentication in the header.

#### Query Parameters

This endpoint does not require any query parameter.

#### Code examples

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

### Response

#### Response parameters

| Parameter     | Description                                                                                        |
| ------------- | -------------------------------------------------------------------------------------------------- |
| `type`        | Name of the type of LO to be used in the `/search` endpoint to filter LO with the `type` parameter |
| `description` | Short description of this type                                                                     |

#### Response example

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

## Bloom

This endpoint returns a list of the [Bloom objectives](https://en.wikipedia.org/wiki/Bloom's_taxonomy) currently supported by the API.

### Request

{% tabs %}
{% tab title="Rapid API" %}
```bash
GET https://learning-objects-v2.p.rapidapi.com/bloom
```
{% endtab %}

{% tab title="Direct customer" %}
```
GET https://api.inokufu.com/learningobject/v2/bloom
```
{% endtab %}
{% endtabs %}

#### Headers

This endpoint does not require any API key authentication in the header.

#### Query Parameters

This endpoint does not require any query parameter.

#### Code examples

See [here](https://rapidapi.com/inokufu-search-api/api/learning-objects-v2/) for **Rapid API** codes examples.

See below for **Direct customer** access:

{% tabs %}
{% tab title="Shell" %}
```bash
curl "https://api.inokufu.com/learningobject/v2/bloom"
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
r = requests.get('https://api.inokufu.com/learningobject/v2/bloom')
r.json()
```
{% endtab %}

{% tab title="php" %}
```php
$curl = curl_init('https://api.inokufu.com/learningobject/v2/bloom');
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
const type = async () => {fetch('https://api.inokufu.com/learningobject/v2/bloom' ).then(function(response) {
  if(response.ok) {
    response.json().then(function(json) { 
      const resJson = JSON.stringify(json)
      return resJson;
})}})};
```
{% endtab %}
{% endtabs %}

### Response

#### Response parameters

| Parameter     | Description                                                                                               |
| ------------- | --------------------------------------------------------------------------------------------------------- |
| `bloom`       | Name of the Bloom objectives to be used in the `/search` endpoint to filter LO with the `bloom` parameter |
| `description` | Short description of this Bloom objectives                                                                |

#### Response example

Here is an example of the JSON structured response provided by this endpoint.

```javascript
[
    {
        "bloom": "discover",
        "description": "These LO are the first step to discover a job or a skill. You'll be able to talk about it, to know the basics. You'll have all the knowledge to decide wether it's for you or not."
    },
    {
        "bloom": "understand",
        "description": "These LO help you better understand this job or skill, in details. You'll dive deeper in the theory. You'll be able to explain, estimate, At the end, you'll be a master of the theoretical aspects."
    },
    {
        "bloom": "do",
        "description": "These LO help you put into practice what you have learned. You'll make, manipulate, simulate. You are applying what you learn."
    },
    {
        "bloom": "degree",
        "description": "These LO train you to a specific job or skill at a professional level. From Discovery, Understanding to Doing, at the end you are a Pro."
    }
]
```

## Provider

This endpoint returns a list of the major providers currently supported by the API.

### Request

{% tabs %}
{% tab title="Rapid API" %}
```bash
GET https://learning-objects-v2.p.rapidapi.com/provider
```
{% endtab %}

{% tab title="Direct customer" %}
```
GET https://api.inokufu.com/learningobject/v2/provider
```
{% endtab %}
{% endtabs %}

#### Headers

This endpoint does not require any API key authentication in the header.

#### Query Parameters

This endpoint does not require any query parameter.

#### Code examples

See [here](https://rapidapi.com/inokufu-search-api/api/learning-objects-v2/) for **Rapid API** codes examples.

See below for **Direct customer** access:

{% tabs %}
{% tab title="Shell" %}
```bash
curl "https://api.inokufu.com/learningobject/v2/provider"
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
r = requests.get('https://api.inokufu.com/learningobject/v2/provider')
r.json()
```
{% endtab %}

{% tab title="php" %}
```php
$curl = curl_init('https://api.inokufu.com/learningobject/v2/provider');
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
const type = async () => {fetch('https://api.inokufu.com/learningobject/v2/provider' ).then(function(response) {
  if(response.ok) {
    response.json().then(function(json) { 
      const resJson = JSON.stringify(json)
      return resJson;
})}})};
```
{% endtab %}
{% endtabs %}

### Response

#### Response parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`      | Identifier of the provider to be used in the `/search-provider` endpoint to filter LO with the `provider` parameter                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `name`    | Pretty name of the provider as returned in enpoints response                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `logo`    | <p>For each providers returned, by this endpoint, we offer 4 versions of their logo:</p><ul><li><code>url</code> is the offer price of the LO as a decimal number.</li><li><code>colorScheme</code>is the color of the background for which the corresponding logo is better suited, either for<code>dark</code>thbackground or for<code>light</code> background.</li><li><code>aspectRatio</code> is the aspect Ratio of the corresponding logo, either the <code>landscape</code>version or the <code>square</code>version</li></ul> |
| `url`     | URL of the homepage of the provider.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `license` | License and/or branding page of this provider.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

#### Response example

Here is an example of the JSON structured response provided by this endpoint.

```javascript
{
    "statusCode": 200,
    "response": [
        {
            "@context": "https://schema.org/",
            "@type": "provider",
            "id": "moncompteformation",
            "name": "MonCompteFormation",
            "logo": [
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/moncompteformation/logo_moncompteformation_blanc.png",
                    "colorScheme": "dark",
                    "aspectRatio": "landscape"
                },
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/moncompteformation/logo_moncompteformation_rvb.png",
                    "colorScheme": "light",
                    "aspectRatio": "landscape"
                },
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/moncompteformation/square/logo_moncompteformation_blanc.png",
                    "colorScheme": "dark",
                    "aspectRatio": "square"
                },
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/moncompteformation/square/logo_moncompteformation_rvb.png",
                    "colorScheme": "light",
                    "aspectRatio": "square"
                }
            ],
            "url": "https://www.moncompteformation.gouv.fr",
            "license": "https://www.of.moncompteformation.gouv.fr/espace-public/sites/default/files/2019-09/MonCompteFormation-guide-utilisation-logo-OF.pdf"
        },
        {
            "@context": "https://schema.org/",
            "@type": "provider",
            "id": "medium",
            "name": "Medium",
            "logo": [
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/medium/medium-dark.png",
                    "colorScheme": "dark",
                    "aspectRatio": "landscape"
                },
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/medium/medium-light.png",
                    "colorScheme": "light",
                    "aspectRatio": "landscape"
                },
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/medium/square/medium-dark-square.png",
                    "colorScheme": "dark",
                    "aspectRatio": "square"
                },
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/medium/square/medium-light-square.png",
                    "colorScheme": "light",
                    "aspectRatio": "square"
                }
            ],
            "url": "https://medium.com",
            "license": "https://medium.design/logos-and-brand-guidelines-f1a01a733592"
        },
        {
            "@context": "https://schema.org/",
            "@type": "provider",
            "id": "youtube",
            "name": "YouTube",
            "logo": [
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/youtube/yt_logo_rgb_dark.png",
                    "colorScheme": "dark",
                    "aspectRatio": "landscape"
                },
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/youtube/yt_logo_rgb_light.png",
                    "colorScheme": "light",
                    "aspectRatio": "landscape"
                },
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/youtube/square/yt_icon_mono_dark.png",
                    "colorScheme": "dark",
                    "aspectRatio": "square"
                },
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/youtube/square/yt_icon_rgb.png",
                    "colorScheme": "light",
                    "aspectRatio": "square"
                }
            ],
            "url": "https://www.youtube.com",
            "license": "https://www.youtube.com/about/brand-resources/#logos-icons-colors"
        },
        {
            "@context": "https://schema.org/",
            "@type": "provider",
            "id": "udemy",
            "name": "Udemy",
            "logo": [
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/udemy/udemy-dark.png",
                    "colorScheme": "dark",
                    "aspectRatio": "landscape"
                },
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/udemy/udemy-light.png",
                    "colorScheme": "light",
                    "aspectRatio": "landscape"
                },
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/udemy/square/udemy-dark-square.png",
                    "colorScheme": "dark",
                    "aspectRatio": "square"
                },
                {
                    "url": "https://raw.githubusercontent.com/MattSonnati/logo/main/provider/udemy/square/udemy-light-square.png",
                    "colorScheme": "light",
                    "aspectRatio": "square"
                }
            ],
            "url": "https://www.udemy.com",
            "license": "https://www.udemy.com/ourbrand"
        }
        
}
```

## Feedback

This endpoint enables you to send us feedback about specific learning objects.

### Request

{% tabs %}
{% tab title="Rapid API" %}
```bash
POST https://learning-objects-v2.p.rapidapi.com/feedback
```
{% endtab %}

{% tab title="Direct customer" %}
```
POST https://api.inokufu.com/learningobject/v2/feedback
```
{% endtab %}
{% endtabs %}

#### Headers

The API key must be included in the header.

{% tabs %}
{% tab title="Rapid API" %}
```
"x-rapidapi-key": "SAY-FRIEND-AND-ENTER"
```
{% endtab %}

{% tab title="Direct customer" %}
```
"x-api-key": "SAY-FRIEND-AND-ENTER"
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
Make sure to replace SAY-FRIEND-AND-ENTER with your own Developer API key.
{% endhint %}

#### Body

This endpoint requires the parameters to be sent in the body, formatted as JSON. Parameters are described in the table below.

| Parameter    | Type   | Required | Description                                                                                                                                                  |
| ------------ | ------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `url`        | string | Yes      | Url of the learning object you want to give feedback on.                                                                                                     |
| `comment`    | string | No       | Enter any comment associated to the learning object.                                                                                                         |
| `request_id` | string | Yes      | Enter the request id of the initial request that sent you this learning object in the response. It will help us identify any issue related with the request. |
| `email`      | email  | Yes      | Email of the feedback's author.                                                                                                                              |
| `source`     | string | Yes      | URL of the website or application or location from which the feedback is being sent.                                                                         |