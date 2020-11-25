---
title: 'Part 2.5: Stories of an Ex-Human in Inkopolis'
process:
    markdown: true
    twig: true
aura:
    pagetype: website
content:
    items: '@self.children'
metadata:
    'og:url': 'http://site.neurario.com/writing/begin-again/part-2-5'
    'og:type': website
    'og:title': 'Part 2.5: Stories of an Ex-Human in Inkopolis | Neurario Dot Com'
    'og:author': 'Neurario Dot Com'
    'twitter:card': summary_large_image
    'twitter:title': 'Part 2.5: Stories of an Ex-Human in Inkopolis | Neurario Dot Com'
    'twitter:site': '@splatsune'
    'twitter:creator': '@splatsune'
    'article:published_time': '2020-11-25T08:30:03+00:00'
    'article:modified_time': '2020-11-25T08:38:42+00:00'
    'article:author': 'Neurario Dot Com'
---

>Life hasn't been normal for Lily ever since she arrived in Inkopolis from twelve thousand years ago, and touched the lives of the New Squidbeak Splatoon and the musical duo Off the Hook. But now that she knows the truth behind her arrival, and has gained some closure on her old life, she has a chance to establish a new life, turn a previous hobby into a career, and experience the world's offerings in the name of preserving what's left of the human era.

===

### Stories

<ul>
{% for p in page.collection %}
    {% set wordcount = (p.content|slice(p.summary|length)) | join(' ') | split(' ') | length | number_format(0, '.', ',') %}
    <li><strong><a href="{{ p.url|e }}">#{{ p.currentPosition+1 }} - {{ p.title|e }}</a></strong>
        ({{ wordcount }} words, {{ p.content|readingtime({'format': '{minutes_short_count} {minutes_text}'}) }} to read)<br />
        <em>{{ p.summary|raw|striptags }}</em>
    </li>
{% endfor %}
</ul>