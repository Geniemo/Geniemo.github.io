---
title: "Code Complete"
permalink: /categories/CodeComplete/
layout: archive
author_profile: true
taxonomy: Code Complete
sidebar_main: true
---

{% assign posts = site.categories['Code Complete'] %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}