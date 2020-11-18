---
title: 'Part 3: Down Under'
process:
    markdown: true
    twig: true
never_cache_twig: true
aura:
    pagetype: website
    metadata:
        current: 'true'
content:
    items: '@self.children'
metadata:
    'og:url': 'http://site.neurario.com/writing/begin-again/part-3'
    'og:type': website
    'og:title': 'Part 3: Down Under | Neurario Dot Com'
    'og:author': 'Neurario Dot Com'
    'twitter:card': summary_large_image
    'twitter:title': 'Part 3: Down Under | Neurario Dot Com'
    'twitter:site': '@splatsune'
    'twitter:creator': '@splatsune'
    'article:published_time': '2020-11-17T04:39:05+00:00'
    'article:modified_time': '2020-11-17T04:48:19+00:00'
    'article:author': 'Neurario Dot Com'
    current: 'true'
---

>A year after Lily's arrival in Inkopolis, she's prouder than ever to call herself an Inkling. And as the Chaos v. Order Splatfest looms ever closer, her friends have gotten her some gifts to mark the anniversary, including a part in the final concert, clothes, inkling oddities - even DJ Octavio got her a pair of shades!
>
>Oh no.
<!--
---

>CQ Cumber, train conductor and former co-owner of Kamabo Co., still has troubled thoughts about the Deepsea Metro Testing Track, of which he was part of for decades. Last year, two strange creatures exposed the lie of Kamabo's Metro, and escaped - and then the Testing Track was switched off for good.
>
>So who can he call when odd things start to happen around the Metro once again?
-->
===

### Chapters

<ul>
{% for p in page.collection %}
    <li><strong><a href="{{ p.url|e }}">#{{ p.currentPosition+1 }} - {{ p.title|e }}</a></strong>
        ({{ p.content|readingtime({'format': '{minutes_short_count} {minutes_text}'}) }} to read)<br />
        <em>{{ p.summary|raw|striptags }}</em>
    </li>
{% endfor %}
</ul>