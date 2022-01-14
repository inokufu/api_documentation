---
description: >-
  This endpoint returns a list of learning objects (LO) that matches specific
  keywords, language and provider.
---

# Search by provider

## Request

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

### Headers

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

### Query Parameters

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
| `publisher`       |           |               |    No    | Publishers are the organization(s) that offer and/or sell the LO. For`mooc`, `distance learning` or `training` this can be an university, a school or a training organization.                                                                                                                                                                                          |
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

### Code examples

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

## Response

### Response parameters

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
| `publisher`          |          | List of publishers associated with this LO. Publishers are the organization(s) that offer and/or sell the LO. For`mooc`, `distance learning` or `training` this can be an university, a school or a training organization.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `author`             |          | List of authors associated with this LO. Authors are the people that make the LO. For `mooc`,`distance learning` or `training` this can be a teacher or `trainer`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `PriceSpecification` |          | <p>Informations about the pricing of the LO, which includes:</p><ul><li><code>price</code> is the offer price of the LO as a decimal number.</li><li><code>priceCurrency</code>is the currency of the price of the LO as a symbol (<code>$</code>, <code>€</code> , etc)</li><li><code>price-free</code> is a boolean that is <code>true</code> when the LO can be accessed without paying, and <code>false</code> when the LO requires payment to be accessed.</li></ul><p>Beware some <code>providers</code>such as Coursera offer all their <code>mooc</code> in both free and paid version. In this case the price of the LO will be not null while marked as <code>price-free=true</code></p> |

### Response example

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

