---
title: "python"
permalink: /categories/python/
layout: archive
author_profile: true
taxonomy: python
sidebar_main: true
---

{% assign posts = site.categories['python'] %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}