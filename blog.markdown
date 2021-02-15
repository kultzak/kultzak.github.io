---
layout: default
title: Adriano Kultzak | Blog
permalink: /blog
lang: en
ref: blo
---

<section>

	{% assign posts=site.posts | where:"lang", page.lang %}
	{% for post in posts %}
		{% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
		{% if year != nyear %}
			<h3 class="code">{{ post.date | date: '%Y' }}</h3>
			{% capture nyear %}{{ year }}{% endcapture %}
		{% endif %}



		<ul>
			<li>
				<div class="post-date code">
					<span>{{ post.date | date: "%b %d" }}</span>
				</div>
				<div class="title">
					<a href="{{ post.url | prepend: site.baseurl | prepend: site.url }}">{{ post.title }}</a>
				</div>
			</li>
		</ul>

	{% endfor %}

</section>
