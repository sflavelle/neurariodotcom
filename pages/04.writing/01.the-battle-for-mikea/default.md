---
title: 'The Battle for Mikea'
process:
    markdown: true
    twig: true
content:
    items: '@self.children'
aura:
    pagetype: website
metadata:
    'og:url': 'http://site.neurario.com/writing/the-battle-for-mikea'
    'og:type': website
    'og:title': 'The Battle for Mikea | Neurario Dot Com'
    'og:author': 'Neurario Dot Com'
    'twitter:card': summary_large_image
    'twitter:title': 'The Battle for Mikea | Neurario Dot Com'
    'twitter:site': '@splatsune'
    'twitter:creator': '@splatsune'
    'article:published_time': '2020-11-18T06:48:59+00:00'
    'article:modified_time': '2020-11-18T06:49:30+00:00'
    'article:author': 'Neurario Dot Com'
---

# The Battle for Mikea

>The journeys of the immigrating Userpedia colony, a subcommunity of the major city of the now-destroyed Mario Wiki's Great Library, as they search for a new home away from their destroyed lands.

A *Guild Wars*-inspired Super Mario Wiki fanon (Userpedia) story circa 2010-2011.

Userpedia is (was, the site is now gone) a wiki site that hosted stories, comics and other media about its various users, and users from the Super Mario Wiki which many of its users were also part of. Many of its stories involved multiple users and some sort of adventure or journey.

I had just gotten deep into Guild Wars with friends outside of the site and my imagination wanted to do something inspired by the first 'part' of the Prophecies campaign, with a similar fantasy setting but also setting the Super Mario Wiki and Userpedia as a real place

The story as published can be read in its entirety here. It was previously hosted on Userpedia, unfortunately the site has been shut down as of 2019.

### Chapters

<ul>
{% for p in page.collection %}
    <li><strong><a href="{{ p.url|e }}">#{{ p.currentPosition+1 }} - {{ p.title|e }}</a></strong>
        ({{ p.content|readingtime({'format': '{minutes_short_count} {minutes_text}'}) }} to read)<br />
        <em>{{ p.summary|raw|striptags }}</em>
    </li>
{% endfor %}
</ul>