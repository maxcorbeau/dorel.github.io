---
layout: home
title: Welcome to dorel.io
---

<div class="page">

  <iron-grid>
    <header class="page-header xs12">
      <h2 class="type-ui-secondary">What do you want to achieve?</h2>
    </header>
  </iron-grid>

  {% comment %}
      *
      * The following section loops through the folders in service-manual
      * and includes all files in both draft and live
      *
  {% endcomment %}

  {% assign categories = site.pages | group_by:"category" | sort: "title" | reverse %}

  <!--ul class="list-manuals not-enum"-->
  <iron-grid>

    {% for category in categories %}

      {% if category.name != '' %}

        <div class="xs12 s6 m4 vtop">

          <p class="list-title">{{ category.name }}</p>

          <ul class="list-manuals not-enum">

            {% assign sitepages = site.pages | sort: "title" %}

            {% for page in sitepages %}

              {% if page.category == category.name %}

                {% if page.draft == true %}

                  <li class="draft"><span>{{ page.title }} (coming soon)</span></li>
                  <!-- keep this url in comment for dev reference: -->
                  <!-- a href="{{ site.url }}{{ manual.url }}">{{ manual.title }}</a-->

                {% else %}

                  <li>
                    <a href="{{ site.url }}{{ page.url }}" class="animate-next">
                      <span class="text">{{ page.title }}</span>
                      <div>
                      <iron-icon icon="icons:arrow-forward" size="16"></iron-icon>
                      </div>
                    </a>
                  </li>

                {% endif %}

              {% endif %}

            {% endfor %}

          </ul>
        </div>

      {% endif %}

    {% endfor %}

    
    <div class="xs12 s6 m4">

      <a href="mailto:{{ site.data.info | map: 'email' }}" class="block-contact-info">
        <div class="container-contact-info">
          <span>Interested in contributing to the service design manual or have questions?</span>
          <span>Feel free to <u>Contact Us</u></span>
        </div>
        <paper-ripple recenters></paper-ripple>
      </a>
    </div>

  </iron-grid>
  <!--/ul-->

</div>