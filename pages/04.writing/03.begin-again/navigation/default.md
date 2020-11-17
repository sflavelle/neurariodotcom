---
title: Navigation
process:
    markdown: true
    twig: true
never_cache_twig: true
twig_first: true
visible: false
aura:
    pagetype: website
content:
    items:
        '@page': /writing/begin-again
    filter:
        visible: true
metadata:
    'og:url': 'http://site.neurario.com/writing/begin-again/navigation'
    'og:type': website
    'og:title': 'Navigation | Neurario Dot Com'
    'og:author': 'Neurario Dot Com'
    'twitter:card': summary_large_image
    'twitter:title': 'Navigation | Neurario Dot Com'
    'twitter:site': '@splatsune'
    'twitter:creator': '@splatsune'
    'article:published_time': '2020-11-17T05:12:04+00:00'
    'article:modified_time': '2020-11-17T05:28:50+00:00'
    'article:author': 'Neurario Dot Com'
---

<ul>
    <li><strong><a href="/writing/begin-again">Begin Again</a></strong></li>
{% for p in page.collection %}
    <li style="list-style-type:none">
        <ul>
            <li><strong><a href="{{ p.url|e }}">{{ p.title|e }}</a></strong></li>
            <li style="list-style-type:none">
                <ol style="line-height:80%">
	    {% for c in p.children %}
            {% if page == chapters.current() %}
                    <li><strong><a href="{{ c.url|e }}">{{ c.title|e }}</a></strong></li>
	        {% else %}
                    <li><a href="{{ c.url|e }}">{{ c.title|e }}</a></li>
            {% endif %}
        {% endfor %}
                </ol>
        </ul>
    </li>
{% endfor %}
</ul>