---
layout: page
title: Contact
lede: Write to the principal investigator, or open the lab GitHub organization.
lede_zh: 可通过邮件联系课题组长，或访问实验室的 GitHub 组织。
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
          <a href="{{ site.data.lab.pi_site }}">{{ site.data.lab.pi_name }} <span lang="zh-Hans">{{ site.data.lab.pi_name_zh }}</span></a>
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
    <p class="affiliation-name">{{ site.data.lab.affiliation.name_en }}</p>
    <p class="affiliation-name" lang="zh-Hans">{{ site.data.lab.affiliation.name_zh }} <span class="muted">({{ site.data.lab.affiliation.short }})</span></p>
    <dl class="contact-facts">
      <div{% if site.data.lab.affiliation.unit_placeholder %} class="is-placeholder-field"{% endif %}>
        <dt>
          Unit
          {% if site.data.lab.affiliation.unit_placeholder %}<span class="badge">Placeholder · 占位</span>{% endif %}
        </dt>
        <dd>{{ site.data.lab.affiliation.unit_en }}</dd>
        <dd lang="zh-Hans">{{ site.data.lab.affiliation.unit_zh }}</dd>
      </div>
      <div{% if site.data.lab.affiliation.address_placeholder %} class="is-placeholder-field"{% endif %}>
        <dt>
          Address
          {% if site.data.lab.affiliation.address_placeholder %}<span class="badge">Placeholder · 占位</span>{% endif %}
        </dt>
        <dd>{{ site.data.lab.affiliation.address_en }}</dd>
        <dd lang="zh-Hans">{{ site.data.lab.affiliation.address_zh }}</dd>
      </div>
    </dl>
  </section>
</div>

<p class="edit-hint">The university name is filled from the <code>ncepu.edu.cn</code> email domain and from public author affiliations on the S2DA-GO paper. Department and street address are still placeholders. Edit the wording in <code>_data/lab.yml</code> before treating it as official.</p>
<p class="edit-hint" lang="zh-Hans">学校名称来自 <code>ncepu.edu.cn</code> 邮箱域名，以及 S2DA-GO 论文中的公开作者单位。院系与通信地址仍是占位内容。如需修改官方表述，请编辑 <code>_data/lab.yml</code>。</p>
