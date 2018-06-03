---
layout: default
---
<ul>
  {% for post in site.posts %}
    <li>
      <small>{{ post.date | date: "%-d %B %Y" }}</small>
      <h1>{{ post.title }}</h1>
      <p class="view">by {{ post.author | default: site.author }}</p>
      {{post.content}}
      {% if post.tags %}
        <small>tags: <em>{{ post.tags | join: "</em> - <em>" }}</em></small>
      {% endif %}
    </li>
  {% endfor %}
</ul>
