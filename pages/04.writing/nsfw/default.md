---
title: 'Not Safe For Work Writing'
date: '00:00 29-11-2020'
process:
    markdown: true
    twig: true
aura:
    pagetype: website
author: Splatsune
metadata:
    'og:url': 'http://site.neurario.com/writing/nsfw'
    'og:type': website
    'og:title': 'Not Safe For Work Writing | Neurario Dot Com'
    'og:author': 'Neurario Dot Com'
    'twitter:card': summary_large_image
    'twitter:title': 'Not Safe For Work Writing | Neurario Dot Com'
    'twitter:site': '@splatsune'
    'twitter:creator': '@splatsune'
    'article:published_time': '2020-11-29T00:00:00+00:00'
    'article:modified_time': '2020-11-29T00:40:04+00:00'
    'article:author': 'Neurario Dot Com'
content:
    items: '@self.children'
    order:
        by: date
        dir: desc
---

You know what you want.

### Stories

<ul>
{% for p in page.collection.published() %}
    <li><strong><a href="{{ p.url|e }}">#{{ p.date|date("d/m/Y") }} - {{ p.title|e }}</a></strong>
        ({{ p.content|readingtime({'format': '{minutes_short_count} {minutes_text}'}) }} to read)<br />
        <em>{{ p.summary|raw|striptags }}</em>
    </li>
{% endfor %}
</ul>