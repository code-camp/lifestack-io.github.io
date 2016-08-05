---
layout: page
title: Archive
permalink: /all/
---
{% for post in site.posts %}
{% unless post.next %}
#### {{ post.date | date: "%B, %Y" }}
{% else %}
{% capture year %}{{ post.date | date: '%Y %b' }}{% endcapture %}
{% capture nyear %}{{ post.next.date | date: '%Y %b' }}{% endcapture %}
{% if year != nyear %}
#### {{ post.date | date: "%B, %Y" }}
{% endif %}
{% endunless %}
{% assign d = post.date | date: "%-d" %}
* [ {{ post.title }} ]({{ root_url }}{{ post.url }})
{% if post.lead %} -- {{ post.lead }}{% endif %}
{% unless forloop.last %}
* * *
{% endunless %}
{% endfor %}