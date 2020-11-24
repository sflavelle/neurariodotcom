---
title: Home
body_classes: 'title-center title-h1h2'
process:
    markdown: true
    twig: true
never_cache_twig: true
aura:
    pagetype: website
metadata:
    'og:url': 'http://site.neurario.com/home'
    'og:type': website
    'og:title': 'Home | Neurario Dot Com'
    'og:author': 'Neurario Dot Com'
    'twitter:card': summary_large_image
    'twitter:title': 'Home | Neurario Dot Com'
    'twitter:site': '@splatsune'
    'twitter:creator': '@splatsune'
    'article:published_time': '2020-11-17T08:32:01+00:00'
    'article:modified_time': '2020-11-17T08:32:01+00:00'
    'article:author': 'Neurario Dot Com'
---

# Hi, I'm Neurario
## Or Splatsune
## ...Simon Says
## Whatever

{# Just going to calculate my own age because fuck it #}
**I'm a {{ 'December 13, 1991' | time_diff }} year old Australian mashup DJ, programmer, and casual fanfic author**, often dabbling in other things on the site

* [Squidbeat Splatitudes (Splatoon Mashup Album)](/mashups/squidbeat-splatitudes)
* **And yes, I'm working on a way to get all my mashups up and downloadable**
* [Begin Again (Splatoon Fanfic Because Why Not)](/writing/begin-again)
* [Neubott](https://github.com/sflavelle/neubott)
* [YouTube Channel for misc stuff](https://www.youtube.com/channel/UC0sfamZ9PWIHv76RF9B2l_g)

### Recent Writing

!! This will look like something eventually!

<ul>
{% for post in pages.order('date', 'desc').slice(0, 5) %}
    <li class="recent-posts">
        <strong><a href="{{ post.url }}">{{ post.title }}</a></strong> (<em>{{ post.date|date("d/m/Y") }}</em>)
    </li>
{% endfor %}
</ul>

### Recent Blog Posts
<ul>
{% for post in page.find('/blog').children.order('date', 'desc').slice(0, 5) %}
    <li class="recent-posts">
        <strong><a href="{{ post.url }}">{{ post.title }}</a></strong> (<em>{{ post.date|date("d/m/Y") }}</em>)
    </li>
{% endfor %}
</ul>