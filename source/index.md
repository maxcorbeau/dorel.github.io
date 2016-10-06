---
layout: home
title: Welcome to dorel.io
---

<iron-grid>

  <div class="s6">
  
    <h2>What do you want to achieve?</h2>

    {% comment %}
        *
        * The following section loops through the folders in service-manual
        * and includes all files in both draft and live
        *
    {% endcomment %}

    {% assign categories = site.pages | group_by:"category" %}

    <ul class="list-manuals">

      {% for category in categories %}

        {% if category.name != '' %}

          <li>
            <p class="list-title"><strong>{{ category.name }}</strong></p>
            
            {% for page in site.pages %}

              {% if page.category == category.name %}

                {% if page.draft == true %}

                  <ul class="draft">{{ page.title }} (coming soon)</ul>
                  <!-- keep this url in comment for dev reference: -->
                  <!-- a href="{{ site.url }}{{ manual.url }}">{{ manual.title }}</a-->

                {% else %}

                  <ul><a href="{{ site.url }}{{ page.url }}">{{ page.title }}</a></ul>

                {% endif %}

              {% endif %}

            {% endfor %}

          </li>

        {% endif %}

      {% endfor %}

    </ul>

  </div>

  <div class="s6">
    
    <h2>How we design services</h2>

    <p>At Dorel, we believe in the credo that everybody is a designer. Everybody within Dorel is welcome to contribute to the service design manual for a topic in her or his expertise. You can read how to write a contribution here.</p>

    <p>We also believe that all future services are <i>digital by default</i>, this might be the app a team creates for our customers, the Powerpoints you use for presentations or the software that controls the robots in our factories. This is the reason why we look at everything from a digital perspective.</p>

    <p><iframe src="https://player.vimeo.com/video/88455206" width="100%" height="100%" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe></p>

    <p>If you want to work on your own service design manual, you can take a look at ours on <a href="https://github.com/dorel/dorel.github.io" target="_blank">Github</a>. Or we would like to advice you to take a look at the service design manual of the <a href="https://www.gov.uk/service-manual" target="_blank">UK government</a>, which was a huge inspiration for us.</p>

  </div>

</iron-grid>