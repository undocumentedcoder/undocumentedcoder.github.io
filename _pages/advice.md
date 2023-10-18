---
layout: page
title: advice
permalink: /advice/
description: Tips for undocumented undergraduate/graduate students studying computer science.
nav: true
nav_order: 2
display_categories: [succeeding in college, succeeding in graduate school]
horizontal: false
---

<!-- pages/advice.md -->
<div class="advice">
{%- if site.enable_advice_categories and page.display_categories %}
  <!-- Display categorized advice -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_advice = site.advice | where: "category", category -%}
  {%- assign sorted_advice = categorized_advice | sort: "importance" %}
  <!-- Generate cards for each advice -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for advice in sorted_advice -%}
      {% include advice_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for advice in sorted_advice -%}
      {% include advice.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display advice without categories -->
  {%- assign sorted_advice = site.advice | sort: "importance" -%}
  <!-- Generate cards for each advice -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for advice in sorted_advice -%}
      {% include advice_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for advice in sorted_advice -%}
      {% include advice.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
