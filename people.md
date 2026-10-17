---
layout: page
title: People
lede: The principal investigator and lab members.
---

{% for person in site.data.members %}
  {% if person.pi %}
    {% include member-card.html member=person featured=true %}
  {% endif %}
{% endfor %}

{% assign other_members = false %}
{% for person in site.data.members %}
  {% unless person.pi %}
    {% assign other_members = true %}
  {% endunless %}
{% endfor %}
{% if other_members %}
<div class="member-grid">
  {% for person in site.data.members %}
    {% unless person.pi %}
      {% include member-card.html member=person %}
    {% endunless %}
  {% endfor %}
</div>
{% endif %}
