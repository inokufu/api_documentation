---
description: This endpoint enables you to send us feedback about specific learning objects.
---

# Feedback

## Request

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

### Body

This endpoint requires the parameters to be sent in the body, formatted as JSON. Parameters are described in the table below.

| Parameter    | Type   | Required | Description                                                                                                                                                  |
| ------------ | ------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `url`        | string | Yes      | Url of the learning object you want to give feedback on.                                                                                                     |
| `comment`    | string | No       | Enter any comment associated to the learning object.                                                                                                         |
| `request_id` | string | Yes      | Enter the request id of the initial request that sent you this learning object in the response. It will help us identify any issue related with the request. |
| `email`      | email  | Yes      | Email of the feedback's author.                                                                                                                              |
| `source`     | string | Yes      | URL of the website or application or location from which the feedback is being sent.                                                                         |

