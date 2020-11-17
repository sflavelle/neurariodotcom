---
title: Home
body_classes: 'title-center title-h1h2'
process:
    markdown: true
    twig: true
never_cache_twig: true
aura:
    pagetype: website
metadata:
    'og:url': 'http://site.neurario.com/home'
    'og:type': website
    'og:title': 'Home | Neurario Dot Com'
    'og:author': 'Neurario Dot Com'
    'twitter:card': summary_large_image
    'twitter:title': 'Home | Neurario Dot Com'
    'twitter:site': '@splatsune'
    'twitter:creator': '@splatsune'
    'article:published_time': '2020-11-17T08:10:53+00:00'
    'article:modified_time': '2020-11-17T08:10:53+00:00'
    'article:author': 'Neurario Dot Com'
---

# Hi, I'm Neurario
## Or Splatsune
### Simon Says
#### Whatever




I'm slowly working out how I want to display anything here.

In the meantime, here is all of my things:

* Twitter: [@Splatsune](https://twitter.com/Splatsune)
* Twitch: [Splatsune](https://www.twitch.tv/splatsune)

* [Squidbeat Splatitudes (Splatoon Mashup Album)](/mashups/squidbeat-splatitudes)
* **And yes, I'm working on a way to get all my mashups up and downloadable**
* [Begin Again (Splatoon Fanfic Because Why Not)](/writing/begin-again)
* [Neubott](https://github.com/sflavelle/neubott)
* [YouTube Channel for misc stuff](https://www.youtube.com/channel/UC0sfamZ9PWIHv76RF9B2l_g)

### Recent Writing

!! This will look like something eventually!

<ul>
{% for post in pages.order('date', 'desc').slice(0, 5) %}
    <li class="recent-posts">
        <strong><a href="{{ post.url }}">{{ post.title }}</a></strong> (<em>{{ post.date|date("d/m/Y") }}</em>)
    </li>
{% endfor %}
</ul>

### Recent Blog Posts
<ul>
{% for post in page.find('/blog').children.order('date', 'desc').slice(0, 5) %}
    <li class="recent-posts">
        <strong><a href="{{ post.url }}">{{ post.title }}</a></strong> (<em>{{ post.date|date("d/m/Y") }}</em>)
    </li>
{% endfor %}
</ul>