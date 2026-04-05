---
layout: page
title: Categories
permalink: /categories/
---

{%- assign sorted_categories = site.categories | sort -%}

<div class="category-index">
  <p><strong>All categories:</strong></p>
  <p>
    {%- for category in sorted_categories -%}
      <a class="category-link" href="#{{ category[0] | slugify }}">
        {{ category[0] }} <span class="category-count">({{ category[1].size }})</span>
      </a>
    {%- unless forloop.last -%} · {%- endunless -%}
    {%- endfor -%}
  </p>
</div>

<hr>

{%- for category in sorted_categories -%}
  <section class="category-section">
    <h2 id="{{ category[0] | slugify }}">{{ category[0] }}</h2>
    <ul class="post-list">
      {%- for post in category[1] -%}
        <li>
          <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
          <h3>
            <a class="post-link" href="{{ post.url | relative_url }}">
              {{ post.title | escape }}
            </a>
          </h3>
        </li>
      {%- endfor -%}
    </ul>
  </section>
{%- endfor -%}
