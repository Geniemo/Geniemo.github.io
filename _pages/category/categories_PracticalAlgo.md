---
title: "Practical Algo"
permalink: /categories/PracticalAlgorithm/
layout: archive
author_profile: true
taxonomy: Practical Algo
sidebar_main: true
---

{% assign posts = site.categories['Practical Algo'] %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}