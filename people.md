---
layout: page
title: People
lede: The principal investigator and lab members.
lede_zh: 课题组长与实验室成员。
---

{% for person in site.data.members %}
  {% if person.pi %}
    {% include member-card.html member=person featured=true %}
  {% endif %}
{% endfor %}

<div class="member-grid">
  {% for person in site.data.members %}
    {% unless person.pi %}
      {% include member-card.html member=person %}
    {% endunless %}
  {% endfor %}
</div>

<p class="edit-hint">Add or edit people in <code>_data/members.yml</code>. Each entry has <code>photo</code>, <code>name</code>, <code>role</code>, and <code>links</code>. Put portraits in <code>assets/images/people/</code>.</p>
