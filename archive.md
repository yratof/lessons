---
layout: page
title: Archive
permalink: /archive/
---

<section id="archive">

  <div id="{{ site.time | date: "%B" }}">
    <h3>{{ site.time | date: "%B" }}</h3>
    {%for post in site.posts %}
    {% unless post.next %}
    <ul class="this">
      {% else %}
      {% capture month %}{{ post.date | date: '%B' }}{% endcapture %}
      {% capture nmonth %}{{ post.next.date | date: '%B' }}{% endcapture %}
      {% if month != nmonth %}
    </ul>
  </div>

  <div id="{{ post.date | date: '%B' }}">
    <h3>{{ post.date | date: '%B' }}</h3>
    <ul class="past">
      {% endif %}
      {% endunless %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
      {% endfor %}
    </ul>
  </div>

</section>