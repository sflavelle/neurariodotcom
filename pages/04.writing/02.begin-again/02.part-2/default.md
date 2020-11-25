---
title: 'Part 2: Legacy'
process:
    markdown: true
    twig: true
aura:
    pagetype: website
content:
    items: '@self.children'
metadata:
    'og:url': 'http://site.neurario.com/writing/begin-again/part-2'
    'og:type': website
    'og:title': 'Part 2: Legacy | Neurario Dot Com'
    'og:author': 'Neurario Dot Com'
    'twitter:card': summary_large_image
    'twitter:title': 'Part 2: Legacy | Neurario Dot Com'
    'twitter:site': '@splatsune'
    'twitter:creator': '@splatsune'
    'article:published_time': '2020-11-25T08:31:14+00:00'
    'article:modified_time': '2020-11-25T08:39:03+00:00'
    'article:author': 'Neurario Dot Com'
---

>Pearl doesn't believe in coincidence. She and her bandmate Marina, and their new friends Captain Cuttlefish, and Agents Three and Eight of the New Squidbeak Splatoon, just saved the world from humanity's creation. Suddenly all of the ancient tech falling from the sky, and the Inkling girl that seems to be collecting them, looks a lot more suspicious and sinister. Could she be connected to the human organisation 'NILS'?
>
>Lily has been living in Inkopolis for about a month and has begun training with Lorne (Agent 4) in Turf War battles. She's also ex-human, after being flung far into the future from her own time. She just wants to settle in and make the best of her new life. Too bad she's about to be found out.

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