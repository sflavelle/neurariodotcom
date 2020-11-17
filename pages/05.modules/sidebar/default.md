---
title: Sidebar
process:
    markdown: true
    twig: true
never_cache_twig: true
aura:
    pagetype: website
metadata:
    'og:url': 'http://site.neurario.com/modules/sidebar'
    'og:type': website
    'og:title': 'Sidebar | Neurario Dot Com'
    'og:author': 'Neurario Dot Com'
    'twitter:card': summary_large_image
    'twitter:title': 'Sidebar | Neurario Dot Com'
    'twitter:site': '@splatsune'
    'twitter:creator': '@splatsune'
    'article:published_time': '2020-11-17T05:20:17+00:00'
    'article:modified_time': '2020-11-17T05:20:17+00:00'
    'article:author': 'Neurario Dot Com'
---

{% if '/writing/begin-again' in page.url %}
[plugin:content-inject](/writing/begin-again/navigation)
{% endif %}