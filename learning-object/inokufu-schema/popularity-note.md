# Popularity note

This is a number from -1 to 1 that indicates how popular the learning object is.

The popularity note is generated automatically from -1 to 0.79 by our algorithms based on the popularity metadata we collect for each learning object. The nature and availability of the popularity metadata differ from one provider to another: likes and views for YouTube videos, enrolment and 5-star reviews for MOOCs, comments, reviews, etc

As a result our algorithms normalise these popularity data in two steps: first compared to all the learning objects of the same provider and then compared to all learning objects in our index. This ends up in a value comprised between -1 and 0.79.&#x20;

Some exceptional learning object have a popularity note above 0.8. A value above 0.8 can only be awarded by one of our trained Pedagogical Auditors.

Inokufu's Learning Object API only exposes learning objects with a popularity note above 0.

Here is a guideline to better understand the range of popularity value:&#x20;

* 0 = unknown quality&#x20;
* 0.01 to 0.49 = good &#x20;
* 0.50 to 0.79 = very good &#x20;
* 0.80 to 0.89 = stunning &#x20;
* 0.90 to 1 = among the best LO for this topic

{% hint style="info" %}
While our R\&D team is working on other quality indicators, popularity note is the only one available in our API as of today.
{% endhint %}
