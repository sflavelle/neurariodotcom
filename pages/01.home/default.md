---
title: Home
body_classes: 'title-center title-h1h2'
process:
    markdown: true
    twig: true
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
    'article:published_time': '2020-12-04T23:20:54+00:00'
    'article:modified_time': '2020-12-04T23:26:18+00:00'
    'article:author': 'Neurario Dot Com'
writing:
    items:
        '@page.descendants': /writing/
    filter:
        published: true
---

# Hi, I'm Neurario
## Or Splatsune
## ...Simon Says
## Whatever

_autistic ~ full-time factory worker ~ techy ~ trying to do too much_

{# Just going to calculate my own age because fuck it #}
**I'm a {{ 'December 13, 1991' | time_diff | split(' ')[0] }} year old Australian mashup DJ, programmer, and casual fanfic author**, often dabbling in other things on the side!

You can find me in various places on the internet!

[[fa=twitter /] @Splatsune](https://twitter.com/Splatsune) &bull; [[fa=youtube /] Neurario](https://www.youtube.com/channel/UC0sfamZ9PWIHv76RF9B2l_g) (music/misc) &bull; [[fa=youtube /] Splatsune](https://www.youtube.com/user/SimonSaysLPs) (gaming) &bull; [[fa=github /] sflavelle](https://github.com/sflavelle)

### Projects

* [Squidbeat Splatitudes (Splatoon Mashup Album)](/mashups/squidbeat-splatitudes)
	* **And yes, I'm working on a way to get all my mashups up and downloadable**
* [Begin Again (Splatoon Fanfic Because Why Not)](/writing/begin-again)
* [Neubott](https://github.com/sflavelle/neubott)

### Recent Writing

{% set writing_collection = page.collection('writing') %}

<ul>
{% for post in writing_collection.ofType('item').order('date', 'desc').slice(0, 5) %}
    {% if post.parent.title | split(' ')[0] == 'Part' %}
    <li class="recent-posts">
        <strong><a href="{{ post.url }}">{{ post.parent.parent.title | split(':')[0] }}: {{ post.parent.title | split(':')[0] }} #{{ post.currentPosition+1 }}: {{ post.title }}</a></strong> (<em>{{ post.date|date("d/m/Y") }}</em>)
    </li>
    {% else %}
        <li class="recent-posts">
        <strong><a href="{{ post.url }}">{{ post.parent.title | split(':')[0] }}: {{ post.title }}</a></strong> (<em>{{ post.date|date("d/m/Y") }}</em>)
    </li>
    {% endif %}
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