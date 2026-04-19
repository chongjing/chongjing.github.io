---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

<p style="font-size: 1.05rem; color: #555; margin-bottom: 1.5rem;">
  {{ site.publications | size }} publications organised by research area. 
  <a href="https://scholar.google.com/citations?user=nU0lJq4AAAAJ&hl=en" target="_blank">View on Google Scholar →</a>
</p>

<div style="margin-bottom: 1.5rem; padding: 1rem; background: #f8f9fa; border-radius: 8px; border-left: 4px solid #007bff;">
  <strong>Legend:</strong>
  <span style="margin-left: 1rem;">⭐ First Author</span>
  <span style="margin-left: 1rem;">📌 Corresponding Author</span>
  <span style="margin-left: 1rem;">👥 Co-author</span>
</div>

{% assign grouped = site.publications | group_by: "category" | sort: "name" %}

{% for group in grouped %}
<h2 id="{{ group.name | slugify }}" style="margin-top: 2rem; padding-bottom: 0.5rem; border-bottom: 2px solid #eee;">
  {{ group.name }}
  <span style="font-size: 0.8rem; font-weight: normal; color: #888;">({{ group.items | size }} papers)</span>
</h2>

{% assign sorted_items = group.items | sort: "date" | reverse %}

{% for post in sorted_items %}
<div style="padding: 1rem 0; border-bottom: 1px solid #f0f0f0;">
  <div style="display: flex; align-items: flex-start; gap: 0.75rem;">
    <div style="flex-shrink: 0; margin-top: 2px;">
      {% if post.role == "first-author" or post.role == "first-corresponding" %}
        <span title="First Author" style="font-size: 1.1rem;">⭐</span>
      {% endif %}
      {% if post.role == "corresponding" or post.role == "first-corresponding" %}
        <span title="Corresponding Author" style="font-size: 1.1rem;">📌</span>
      {% endif %}
      {% if post.role == "co-first" %}
        <span title="Co-first Author" style="font-size: 1.1rem;">⭐</span>
      {% endif %}
      {% if post.role == "co-author" %}
        <span title="Co-author" style="font-size: 1.1rem;">👥</span>
      {% endif %}
    </div>
    <div>
      <h3 style="margin: 0 0 0.3rem 0; font-size: 1rem; line-height: 1.4;">
        <a href="{{ post.paperurl }}" target="_blank" style="color: #333; text-decoration: none;">{{ post.title }}</a>
      </h3>
      <p style="margin: 0 0 0.25rem 0; font-size: 0.88rem; color: #666; line-height: 1.4;">
        {{ post.authors }}
      </p>
      <p style="margin: 0; font-size: 0.85rem;">
        <em style="color: #555;">{{ post.venue }}</em>
        <span style="color: #999;"> · {{ post.date | date: "%Y" }}</span>
        {% if post.pdfurl %}
          <a href="{{ post.pdfurl }}" target="_blank" style="margin-left: 0.75rem; color: #007bff; text-decoration: none;">📄 PDF</a>
        {% endif %}
        <a href="{{ post.paperurl }}" target="_blank" style="margin-left: 0.5rem; color: #007bff; text-decoration: none;">🔗 DOI</a>
      </p>
    </div>
  </div>
</div>
{% endfor %}
{% endfor %}
