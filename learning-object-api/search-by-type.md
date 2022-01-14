---
description: >-
  This endpoint returns a list of learning objects (LO) that matches specific
  keywords, language and type (format).
---

# Search by type

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
| `publisher`          |          | List of publishers associated with this LO. Publishers are the organization(s) that offer and/or sell the LO. For`mooc`, `distance learning` or `training` this can be an university, a school or a training organization.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `author`             |          | List of authors associated with this LO. Authors are the people that make the LO. For `mooc`,`distance learning` or `training` this can be a teacher or `trainer`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
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

