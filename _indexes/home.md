---
layout: page
title: Home
permalink: /
---
{% for post in site.posts limit:5 %}

{% if forloop.first %}
# [ {{ post.title }} ]({{ post.url }})
{% else %}
## [ {{ post.title }} ]({{ post.url }})
{% endif %}
{% if post.lead %}
  {{ post.lead }}
{% elsif post.content contains '<!--more-->' %}
  {{ post.content | split:'<!--more-->' | first | strip_html }}
{% elsif post == site.posts.first %}
  {{ post.content | strip_html | truncatewords: 40 , "  .." }}
{% else %}
  {{ post.content | strip_html | truncatewords: 16 , "  .." }}
{% endif %}
{{ post.date | date_to_string }} ► [{{ site.data.categories[post.category].name }}]({{ site.baseurl }}all/{{ post.category }})
{% unless forloop.last %}
* * *
{% endunless %}
{% endfor %}

###### &copy; {{ site.time | date: '%Y' }} [{{site.author.name}}]({{site.baseurl}}about/#copyright--licensing)