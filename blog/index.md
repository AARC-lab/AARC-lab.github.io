---
title: Blog
nav:
  order: 4
  tooltip: Musings, news, and tutorials
---

# {% include icon.html icon="fa-solid fa-feather-pointed" %}Blog

Musings, commentary, blogs, and latest news from our reserach group

{% include section.html %}

{% include search-box.html %}

{% include tags.html tags=site.tags %}

{% include search-info.html %}

{% include list.html data="posts" component="post-excerpt" %}
