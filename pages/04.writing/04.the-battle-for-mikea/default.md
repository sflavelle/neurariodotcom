---
title: 'The Battle for Mikea'
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
    'article:published_time': '2020-11-18T06:10:45+00:00'
    'article:modified_time': '2020-11-18T06:10:45+00:00'
    'article:author': 'Neurario Dot Com'
---

# The Battle for Mikea

>The journeys of the immigrating Userpedia colony, a subcommunity of the major city of the now-destroyed Mario Wiki's Great Library, as they search for a new home away from their destroyed lands.

A *Guild Wars*-inspired Super Mario Wiki fanon (Userpedia) story circa 2010-2011.

Userpedia is (was, the site is now gone) a wiki site that hosted stories, comics and other media about its various users, and users from the Super Mario Wiki which many of its users were also part of. Many of its stories involved multiple users and some sort of adventure or journey.

I had just gotten deep into Guild Wars with friends outside of the site and my imagination wanted to do something inspired by the first 'part' of the Prophecies campaign, with a similar fantasy setting but also setting the Super Mario Wiki and Userpedia as a real place

The story as published can be read in its entirety here. It was previously hosted on Userpedia, unfortunately the site has been shut down as of 2019.

## Parts
<ul>
{% for p in page.collection %}
    {% set children = p.children %}
{% if p.header.metadata.current is defined and p.header.metadata.current == 'true' %}
    <li><strong><a href="{{ p.url|e }}">{{ p.title|e }}</a></strong> ({{ p.children.count() }} chapters)<br />
        <em><strong><span style="color:green;">In progress</span></strong>, last update: {{ p.children.nth(p.children.count()-1).date|date("d/m/Y") }}</em><br />
{% else %}
    <li><strong><a href="{{ p.url|e }}">{{ p.title|e }}</a></strong> ({{ p.children.count() }} chapters)<br />
{% endif %}
    <em>{{ p.summary|raw|striptags('<br><p>') }}</em></li>
{% endfor %}
</ul>