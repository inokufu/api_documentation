---
description: >-
  This endpoint returns a list of the Bloom objectives currently supported by
  the API.
---

# Bloom taxonomy

## Request

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

## Response

### Response parameters

| Parameter     | Description                                                                                               |
| ------------- | --------------------------------------------------------------------------------------------------------- |
| `bloom`       | Name of the Bloom objectives to be used in the `/search` endpoint to filter LO with the `bloom` parameter |
| `description` | Short description of this Bloom objectives                                                                |

### Response example

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

