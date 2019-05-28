---
layout: single
title: "Teaching"
permalink: /teaching/
author_profile: true
---

{% include base_path %}

I am (or I will be, for the upcoming programme) doing \*some kind\* of teaching in the following courses:

## FER3 (upcoming) programme

{% assign sorted = site.teaching | sort:"order" %}
{% for post in sorted %}
    {% if post.programme == "FER3" %}
        {% include archive-single.html %}
    {% endif %}
{% endfor %}

## FER2 (old) programme

{% for post in sorted %}
    {% if post.programme == "FER2" %}
        {% include archive-single.html %}
    {% endif %}
{% endfor %}

