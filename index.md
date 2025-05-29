---
layout: default
---

Welcome to my security blog!

### Recent Posts:
{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }}) ({{ post.date | date: "%b %d, %Y" }})
{% endfor %}
