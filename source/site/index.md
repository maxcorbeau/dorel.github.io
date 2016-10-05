---
layout: home
title: Welcome to dorel.io
---

<iron-grid>
  <div class="s6">

    <h1>What do you want to achieve?</h1>

    {% comment %}
        *
        *   The following includes lets you loop through the collection to list
        *   all entries in that collection.
        *   
        *   If you set »published: true« in front matter of a collection page
        *   the page becomes a link in the loop meaning that it's available to the public
        *
    {% endcomment %}

    <ul class="list-manuals">
    
      {% for collection in site.collections %}
        <li>
          <p class="list-title"><strong>{{ collection.label }}</strong></p>
          <ul>
              {% for manual in site[collection.label] %}

                {% if manual.published == null %} 
                  <li class="draft">
                    <p>{{ manual.title }} (coming soon)</p>
                    <!-- keep this url in comment for dev reference: -->
                    <!-- a href="{{ site.url }}{{ manual.url }}">{{ manual.title }}</a-->
                {% else %}
                  <li>
                    <a href="{{ site.url }}{{ manual.url }}">{{ manual.title }}</a>
                {% endif %}

                </li>

              {% endfor %}
          </ul>
        </li>
      {% endfor %}

    </ul>

    {% if site.technology != null %}
    {% endif %}
        
  </div>
  <div class="s6">
      
    <p>At Dorel we believe in the credo that everybody is a designer. Everybody within Dorel is welcome to contribute to the service design manuel for a topic in her or his expertise. You can read how to write a contribution here.</p>

    <p>We also believe that all future services are digital, this might be the app a team creates for our customers, the Powerpoints you use for presentations or the software that control the robots in our factories. That is why we define everything from a digital perspecitve.</p>

  </div>
</iron-grid>