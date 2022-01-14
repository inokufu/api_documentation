---
description: Inokufu API Cloud uses API keys to allow access to our APIs.
---

# Authentication

You can access this API in two ways:

* **Rapid API**: this is recommended for small to medium usage. You'll need to create a Rapid API account [here](https://rapidapi.com/auth/sign-up?referral=/organization/inokufu-search), then to subscribe to one of our plan [here](https://rapidapi.com/inokufu-search-api/api/learning-objects-v2/pricing). Rapid API will then provide you with your Developer API key
* **Direct customer**: this is reserved for very high usage and custom needs. If you want to know more about our enterprise plans, please feel free to contact our [Inokufu sales team](mailto:sales@inokufu.com).

## Rapid API

### API key in header

Inokufu APIs expects for the API key to be included in API requests to the server in a header that looks like the following:

{% tabs %}
{% tab title="Rapid API" %}
```
"x-rapidapi-key": "SAY-FRIEND-AND-ENTER"
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
Make sure to replace SAY-FRIEND-AND-ENTER with your own Developer API key.
{% endhint %}

### Code examples

See [here](https://rapidapi.com/inokufu-search-api/api/learning-objects-v2/) for **Rapid API** codes example.

## Direct Customer

### API key in header

Inokufu APIs expects for the API key to be included in API requests to the server in a header that looks like the following:

{% tabs %}
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

