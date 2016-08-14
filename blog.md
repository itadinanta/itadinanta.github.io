---
title: Blog
---

### All posts
{% for post in site.posts %}
#### {{post.title}} - {{post.date|date: '%B %d, %Y'}}

{{post.excerpt}} [+]({{post.url}})

{% endfor %}
