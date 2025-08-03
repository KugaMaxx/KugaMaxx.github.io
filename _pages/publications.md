---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

<style>
.year-section {
  margin-bottom: 3em;
}

.year-header {
  border-bottom: 2px solid #6F767F;
  padding-bottom: 10px;
  margin-bottom: 25px;
  color: #6F767F;
  font-size: 1.0em;
  font-weight: bold;
}
</style>

{% assign papers_by_year = site.publications | group_by_exp: "post", "post.date | date: '%Y'" | sort: "name" | reverse %}

{% for year_group in papers_by_year %}
<div class="year-section">
  <h2 class="year-header">{{ year_group.name }}</h2>
  
  {% assign sorted_papers = year_group.items | sort: "date" | reverse %}
  {% for paper in sorted_papers %}

<div class='paper-box'>
  <div class='paper-box-image'>
    <div>
      <img src='{{ paper.image }}' alt="{{ paper.title }}" width="100%">
    </div>
  </div>
  <div class='paper-box-text' markdown="1">

## {{ paper.title }}

{{ paper.excerpt }}

{% comment %} Display URLs if they exist {% endcomment %}
{% if paper.urls %}
{{ paper.urls }}
{% endif %}

  </div>
</div>

  {% endfor %}
</div>
{% endfor %}
