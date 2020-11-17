---
title: 'Begin Again: Chronicles of an Ex-Human in Inkopolis'
taxonomy:
    category:
        - Story
    tag:
        - Splatoon
menu: 'Begin Again'
process:
    markdown: true
    twig: true
never_cache_twig: true
visible: true
aura:
    pagetype: website
hero_classes: ''
hero_image: ''
content:
    items: '@self.children'
    filter:
        visible: true
metadata:
    'og:url': 'http://site.neurario.com/writing/begin-again'
    'og:type': website
    'og:title': 'Begin Again: Chronicles of an Ex-Human in Inkopolis | Neurario Dot Com'
    'og:author': 'Neurario Dot Com'
    'twitter:card': summary_large_image
    'twitter:title': 'Begin Again: Chronicles of an Ex-Human in Inkopolis | Neurario Dot Com'
    'twitter:site': '@splatsune'
    'twitter:creator': '@splatsune'
    'article:published_time': '2020-11-17T23:33:32+00:00'
    'article:modified_time': '2020-11-17T23:33:32+00:00'
    'article:author': 'Neurario Dot Com'
---

# Begin Again
## Chronicles of an Ex-Human in Inkopolis

>_A human finds themselves transformed and left twelve thousand years in the future, when humans are extinct and marine life has taken their place._

A *Splatoon* AU.

The story as published can be read here, or on [FanFiction.net](https://www.fanfiction.net/s/13397436/1/Begin-Again-Chronicles-of-an-Ex-Human-In-Inkopolis) as one entry.

## Parts
<ul>
{% for p in page.collection %}
    {% set children = p.children %}
{% if p.header.metadata.current is defined and p.header.metadata.current == 'true' %}
    <li><strong><a href="{{ p.url|e }}">{{ p.title|e }}</a></strong> ({{ p.children.count() }} chapters)<br />
        <strong><span style="color:green;">in progress</span></strong>, last update: {{ p.children.nth(p.children.count()-1).date|date("d/m/Y") }})<br />
{% else %}
    <li><strong><a href="{{ p.url|e }}">{{ p.title|e }}</a></strong> ({{ p.children.count() }} chapters)<br />
{% endif %}
    <em>{{ p.summary|raw|striptags('<br><p>') }}</em></li>
{% endfor %}
</ul>