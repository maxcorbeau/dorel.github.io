---
layout: default
title: Welcome to dorel.io
---

<div>

  {% comment %}
      *
      *   The following includes lets you loop through the collection to list
      *   all entries in that collection.
      *   
      *   If you set »published: true« in front matter of a collection page 
      *   the page becomes a link in the loop meaning that it's available to the public
      *
  {% endcomment %}

  {% for collection in site.collections %}

    <p>{{ collection.label }}</p>
    <ul>
        {% for manual in site[collection.label] %}

          {% if manual.published == null %} 
            <li class="draft">
              <p>{{ manual.title }}</p>
              <!-- keep this url in comment for dev reference: -->
              <!-- a href="{{ site.url }}{{ manual.url }}">{{ manual.title }}</a-->
          {% else %}
            <li>
              <a href="{{ site.url }}{{ manual.url }}">{{ manual.title }}</a>
          {% endif %}

          </li>

        {% endfor %}
    </ul>

  {% endfor %}

{% if site.technology != null %}
{% endif %}

</div>