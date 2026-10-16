---
layout: page
title: News
lede: Announcements, papers, and other lab updates.
---

{% include news-list.html %}

{% assign known_urls = "|" %}
{% for item in site.data.news %}
{% if item.url and item.url != "" %}
{% assign known_urls = known_urls | append: item.url | append: "|" %}
{% endif %}
{% endfor %}

{% assign extra_posts = false %}
{% for post in site.posts %}
{% unless known_urls contains post.url %}
{% assign extra_posts = true %}
{% endunless %}
{% endfor %}

{% if extra_posts %}
<h2 class="year-heading">From the notebook</h2>
<ol class="news-list">
{% for post in site.posts %}
{% unless known_urls contains post.url %}
<li class="news-item">
<time datetime="{{ post.date | date: '%Y-%m-%d' }}">{{ post.date | date: "%-d %b %Y" }}</time>
<div>
<h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
<p>{{ post.excerpt | strip_html | truncate: 220 }}</p>
</div>
</li>
{% endunless %}
{% endfor %}
</ol>
{% endif %}

<p class="edit-hint">Short items belong in <code>_data/news.yml</code> and appear on the home page. Longer notes are Markdown files in <code>_posts/</code>. Point a news entry’s <code>url</code> at a post to link them. A post with no data entry is listed on this page only.</p>
