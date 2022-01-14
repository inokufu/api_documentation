---
description: >-
  This endpoint returns a list of the major providers currently supported by the
  API.
---

# Providers

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

