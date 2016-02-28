---
layout: page
title: Archive
permalink: /archive/
---

<section id="archive">

  <div id="{{ site.time | date: "%B" }}">
    <h2>{{ site.time | date: "%B" }}</h2>
    {%for post in site.posts %}
    {% unless post.next %}
    <ul class="featured__list this">
      {% else %}
      {% capture month %}{{ post.date | date: '%B' }}{% endcapture %}
      {% capture nmonth %}{{ post.next.date | date: '%B' }}{% endcapture %}
      {% if month != nmonth %}
    </ul>
  </div>

  <div id="{{ post.date | date: '%B' }}">
    <h2>{{ post.date | date: '%B' }}</h2>
    <ul class="featured__list past">
      {% endif %}
      {% endunless %}
        <li class="featured__list--item {{ post.meta.highlight }}">
          <a href="{{ site.baseurl }}/archive#{{ post.date | date: "%B" }}" class="note featured">
            {% if post.meta.highlight %}
              {{ post.meta.highlight | capitalize }}
            {% else %}
              {{ post.date | date: "%B" }}
            {% endif %}
          </a>
          <div class="note-nudge">
            <strong>{{ post.author }}</strong>
            <h2>
              <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">
                {{ post.title | truncatewords: 10 }}
              </a>
            </h2>
          </div>
        </li>
      {% endfor %}
    </ul>
  </div>

</section>

<section id="archive" class="archive">
  <ul class="featured__list">
    {% for post in site.posts offset: 1 %}

      <li class="featured__list--item {{ post.meta.highlight }}">
        <a href="{{ site.baseurl }}/archive#{{ post.date | date: "%B" }}" class="note featured">
          {% if post.meta.highlight %}
            {{ post.meta.highlight | capitalize }}
          {% else %}
            {{ post.date | date: "%B" }}
          {% endif %}
        </a>
        <div class="note-nudge">
          <strong>{{ post.author }}</strong>
          <h2>
            <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">
              {{ post.title | truncatewords: 10 }}
            </a>
          </h2>
        </div>
      </li>
    {% endfor %}
  </ul>
</section>