# Best efforts

Our mission is to help you find the best learning objects out there. While we are working hard on this ambitious goal, we are still at the beginning of this journey and we have not indexed the whole educational content available on internet (yet). At this stage, we can't guaranty 100% accuracy of our results, nor that we will be able to find learning objects on any topic or any set of query parameters.

**Results returned by the API are our best efforts to match your query.**

Each response returned by endpoints `search` or `search-provider` contains a message (`msg`) that tells you how good we think our answer to your query is. Messages currently returned by the API are shown in the table below.

| Code |                         Message                         |                                                                Meaning                                                                |
| ---- | :-----------------------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------: |
| A00  | These results are our best effort to answer your query. |                           We are pretty confident that these results closely match what you are looking for.                          |
| B00  |     These results does not match exactly your query.    |  We have some results to show you that may be close enough to your query but still it's not exactly what you asked for, so you know.  |
| C00  |           No result to display for this query.          | We have found no result we are confident enough to show you based on what you are looking for. Try again with less strict parameters. |

{% hint style="success" %}
You can adjust how strict you want the results to match your query. The API offers two parameters for this purpose: `match` and `model`.&#x20;

* `match` is used to indicate how stricly you want the results to match your query parameters (excluding `keywords`parameter).
* `model`is used to indicate how strictly you want the results to match the `keywords`parameter.&#x20;
{% endhint %}

