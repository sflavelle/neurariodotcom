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
    'article:published_time': '2020-11-28T22:00:16+00:00'
    'article:modified_time': '2020-11-28T22:00:16+00:00'
    'article:author': 'Neurario Dot Com'
---

# Begin Again
## Chronicles of an Ex-Human in Inkopolis

>_Lily is an odd Inkling who's learning to live in the big city of Inkopolis among other marine life. She's also ex-human, after being flung far into the future from her own time. But it's hard to keep a secret like that from the New Squidbeak Splatoon, who found her, Off the Hook, who think she's connected to the NILS facility, and DJ Octavio, who wants her and her history for himself._

A *Splatoon* AU.

After finally playing Splatoon's Hero Mode in 2018, and the Octo Expansion shortly after, I got really immersed into the lore and world building of Nintendo's franchise. I ended up beginning to daydream during work about being dropped as-is into that universe. After daydreaming this for about a week I decided I needed to write this down: to document the adventure playing out in my head that I didn't want to forget, and as a means to improve my creative writing processes.

After that, writing led to daydreaming more led to writing more and suddenly I have 100,000+ words on a cringy story idea. Fuck it. The fiction translates a number of in-game mechanics into plausible in-universe devices, or details.

This has been written with the assumption that the reader may already know the Splatoon series - I don't know if it's readable to those who don't know the games.

The story as published can be read here, at [Fanfiction Online](https://fanfiction.online/story/430427), or on [FanFiction.net](https://www.fanfiction.net/s/13397436/1/Begin-Again-Chronicles-of-an-Ex-Human-In-Inkopolis).

## Parts
<ul>
{% for p in page.collection %}
    {% set children = p.children %}
    {% set chapter_content = p.children | map(p => (p.content|slice(p.summary|length))) | join(' ') %}
    {% set chapter_wordcount = chapter_content | split(' ') | length | number_format(0, '.', ',')  %}
{% if p.header.metadata.current is defined and p.header.metadata.current == 'true' %}
    <li><strong><a href="{{ p.url|e }}">{{ p.title|e }}</a></strong> ({{ p.children.count() }} chapters, {{ chapter_wordcount }} words)<br />
        <em><strong><span style="color:green;">In progress</span></strong>, last update: {{ p.children.nth(p.children.count()-1).date|date("d/m/Y") }}</em><br />
{% else %}
    <li><strong><a href="{{ p.url|e }}">{{ p.title|e }}</a></strong> ({{ p.children.count() }} chapters,  {{ chapter_wordcount }} words)<br />
{% endif %}
    <em>{{ p.summary|raw|striptags('<br><p>') }}</em></li>
{% endfor %}
</ul>