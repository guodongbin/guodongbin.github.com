---
layout: page
title: Archive
---

<section>
  {% if site.posts[0] %}

    {% capture currentyear %}{{ 'now' | date: "%Y年" }}{% endcapture %}
    {% capture firstpostyear %}{{ site.posts[0].date | date: '%Y年' }}{% endcapture %}
    {% if currentyear == firstpostyear %}
        <h3>今年发表</h3>
    {% else %}  
        <h3>{{ firstpostyear }}</h3>
    {% endif %}

    {%for post in site.posts %}
      {% unless post.next %}
        <ul>
      {% else %}
        {% capture year %}{{ post.date | date: '%Y年' }}{% endcapture %}
        {% capture nyear %}{{ post.next.date | date: '%Y年' }}{% endcapture %}
        {% if year != nyear %}
          </ul>
          <h3>{{ post.date | date: '%Y年' }}</h3>
          <ul>
        {% endif %}
      {% endunless %}
        <li><time>{{ post.date | date:"%d %b" }} - </time>
          <a href="{{ post.url | prepend: site.baseurl | replace: '//', '/' }}">
            {{ post.title }}
          </a>
        </li>
    {% endfor %}
    </ul>

  {% endif %}
</section>