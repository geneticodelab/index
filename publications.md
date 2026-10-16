---
layout: page
title: Publications
lede: Papers from the lab, grouped by year.
---

{% assign groups = site.data.publications | group_by: "year" | sort: "name" | reverse %}
{% for group in groups %}
  <section class="year-block" aria-labelledby="year-{{ group.name }}">
    <h2 id="year-{{ group.name }}" class="year-heading">{{ group.name }}</h2>
    {% for pub in group.items %}
      {% include publication.html pub=pub %}
    {% endfor %}
  </section>
{% endfor %}

<p class="edit-hint">Add papers in <code>_data/publications.yml</code>. They are grouped by the <code>year</code> field automatically. A commented template is at the bottom of that file.</p>
