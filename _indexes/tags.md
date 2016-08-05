---
layout: page
title: Tags
permalink: /tags/
---
{% for tag in site.tags %}
{% capture tag_name %}{{ tag | first }}{% endcapture %}
## [ {{ tag_name | capitalize }} ]( {{ root_url }}/tags/#{{ tag_name|slugize }} )
{% for post in site.tags[tag_name] %}
* [ {{ post.title }} ]({{ root_url }}{{ post.url }}){% if post.lead %} -- {{ post.lead }}{% endif %} ( _{{ post.date | date: "%b, %Y" }}_ )

{% endfor %}
{% unless forloop.last %}
* * *
{% endunless %}
{% endfor %}