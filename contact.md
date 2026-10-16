---
layout: page
title: Contact
lede: Write to the principal investigator, or open the lab GitHub organization.
---

<div class="contact-grid">
  <section class="card" aria-labelledby="reach-heading">
    <h2 id="reach-heading">Reach the lab</h2>
    <dl class="contact-facts">
      <div>
        <dt>Email</dt>
        <dd><a href="mailto:{{ site.data.lab.email }}">{{ site.data.lab.email }}</a></dd>
      </div>
      <div>
        <dt>Principal investigator</dt>
        <dd>
          <a href="{{ site.data.lab.pi_site }}">{{ site.data.lab.pi_name }}</a>
        </dd>
      </div>
      <div>
        <dt>GitHub</dt>
        <dd><a href="{{ site.data.lab.github }}">{{ site.data.lab.github_label }}</a></dd>
      </div>
    </dl>
  </section>

  <section class="card" aria-labelledby="affiliation-heading">
    <h2 id="affiliation-heading">Affiliation</h2>
    <p class="affiliation-name">{{ site.data.lab.affiliation.name_en }} <span class="muted">({{ site.data.lab.affiliation.short }})</span></p>
    {% assign affiliation_units = site.data.lab.affiliation.units %}
    {% assign affiliation_address = site.data.lab.affiliation.address_en | default: "" | strip %}
    {% if affiliation_units and affiliation_units.size > 0 or affiliation_address != "" %}
    <dl class="contact-facts">
      {% if affiliation_units and affiliation_units.size > 0 %}
      <div class="affiliation-units">
        <dt>{% if affiliation_units.size > 1 %}Units{% else %}Unit{% endif %}</dt>
        {% for unit in affiliation_units %}
          <dd>{{ unit }}</dd>
        {% endfor %}
      </div>
      {% endif %}
      {% if affiliation_address != "" %}
      <div>
        <dt>Address</dt>
        <dd>{{ affiliation_address }}</dd>
      </div>
      {% endif %}
    </dl>
    {% endif %}
  </section>
</div>
