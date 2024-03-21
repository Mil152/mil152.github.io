---
layout: archive
title: "Sitemap"
permalink: /sitemap/
author_profile: true
---

{% include base_path %}

A list of all the posts and pages found on the site. For you robots out there is an [XML version]({{ base_path }}/sitemap.xml) available for digesting as well.

## Main Sections

Here are the main sections of my website for quick navigation:

- [Publications]({{ site.baseurl }}/publications/)
- [CV]({{ site.baseurl }}/cv/)
- [Projects]({{ site.baseurl }}/talks/)

## Pages

<ul>
{% for page in site.pages %}
  {% if page.title %}
  <li><a href="{{ site.baseurl }}{{ page.url }}">{{ page.title }}</a></li>
  {% endif %}
{% endfor %}
</ul>

## Posts

<ul>
{% for post in site.posts %}
  <li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>

## Collections

{% capture written_label %}'None'{% endcapture %}
{% for collection in site.collections %}
  {% unless collection.output == false or collection.label == "posts" %}
    {% capture label %}{{ collection.label | capitalize }}{% endcapture %}
    {% if label != written_label %}
    <h2>{{ label }}</h2>
    <ul>
    {% capture written_label %}{{ label }}{% endcapture %}
    {% endif %}
    {% for doc in collection.docs %}
      <li><a href="{{ site.baseurl }}{{ doc.url }}">{{ doc.title }}</a></li>
    {% endfor %}
    </ul>
  {% endunless %}
{% endfor %}
