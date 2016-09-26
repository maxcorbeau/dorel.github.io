---
layout: default
title: Welcome to dorel.io
---

<p>Thanks for paying attention. This is indeed Dorel.io. We will populate content in the next months.</p>

<div style="display:none;">

	<h2>Service manual:</h2>

	<ul class="servicemanual">
	{% for manual in site.service-manual %}

		<li>servicemanual title: {{ manual.title }}</li>

	{% endfor %}
	</ul>

</div>