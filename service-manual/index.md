---
title: Service Manual App
---

<dom-module id="dorelio-app">
  <template>
    <iron-pages>
        <div class="page">

        {% comment %}
            *
            * The following section loops through the folders in service-manual
            * and includes all files in both draft and live
            *
        {% endcomment %}

        {% assign categories = site.pages | group_by:"category" | sort: "title" | reverse %}

        <!--ul class="list-manuals not-enum"-->
        <iron-grid class="ui-pages-overview">

            {% assign categoriesSort = categories | sort: "name" %}

            {% for category in categoriesSort %}

            {% if category.name != '' %}

                <div class="xs12 s6 m4 vtop">

                <span class="list-title">{{ category.name }}</span>

                <ul class="list-manuals not-enum">

                    {% assign sitepages = site.pages | sort: "title" %}

                    {% for page in sitepages %}

                    {% if page.category == category.name %}

                        {% if page.draft == true %}

                        <li class="draft"><span>{{ page.title }} (coming soon)</span></li>
                        <!-- keep this url in comment for dev reference: -->
                        <!-- a href=".{{ page.url }}">{{ page.title }}</a-->

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

            
            <!--div class="xs12 s6 m4">

            <a href="mailto:{{ site.data.info | map: 'email' }}" class="block-contact-info">
                <div class="container-contact-info">
                <span>Interested in contributing to the service design manual or have questions?</span>
                <span>Feel free to <u>Contact Us</u></span>
                </div>
                <paper-ripple recenters></paper-ripple>
            </a>
            </div-->

        </iron-grid>
        <!--/ul-->

        </div>
    </iron-pages>
  </template>
  <script>
    Polymer({
      is: 'dorelio-app',
      properties: {
        page: {
          type: String,
          reflectToAttribute: true,
          observer: '_pageChanged'
        }
      },
      _pageChanged: function(page) {
        // Load page import on demand. Show 404 page if fails
        //console.log('load', page);
        //var resolvedPageUrl = this.resolveUrl('my-' + page + '.html');
        //this.importHref(resolvedPageUrl, null, this._showPage404, true);
      },
    });
  </script>
</dom-module>