---
title: 'Part 1 - Fish Out of Water'
process:
    markdown: true
    twig: true
aura:
    pagetype: website
content:
    items: '@self.children'
metadata:
    'og:url': 'http://site.neurario.com/writing/begin-again/part-1'
    'og:type': website
    'og:title': 'Part 1 - Fish Out of Water | Neurario Dot Com'
    'og:author': 'Neurario Dot Com'
    'twitter:card': summary_large_image
    'twitter:title': 'Part 1 - Fish Out of Water | Neurario Dot Com'
    'twitter:site': '@splatsune'
    'twitter:creator': '@splatsune'
    'article:published_time': '2020-11-25T08:31:33+00:00'
    'article:modified_time': '2020-11-25T08:39:23+00:00'
    'article:author': 'Neurario Dot Com'
---

>Some cosmic bad luck and a little bit of magic resulted in a human waking up in another body, in a time where squids rule the earth. As they acclimate to their new surroundings, they find themselves on a journey to reclaim the remnants of their past, and adjust to their new life in Inkopolis.

===

### Chapters

<ul>
{% for p in page.collection %}
    {% set wordcount = (p.content|slice(p.summary|length)) | join(' ') | split(' ') | length | number_format(0, '.', ',') %}
    <li><strong><a href="{{ p.url|e }}">#{{ p.currentPosition+1 }} - {{ p.title|e }}</a></strong>
        ({{ wordcount }} words, {{ p.content|readingtime({'format': '{minutes_short_count} {minutes_text}'}) }} to read)<br />
        <em>{{ p.summary|raw|striptags }}</em>
    </li>
{% endfor %}
</ul>