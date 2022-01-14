---
description: This endpoint returns a list of the languages currently supported by the API.
---

# Lang

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

