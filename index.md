---
layout: default
---
{% for post in site.posts %}
<div>
    <small>{{ post.date | date: "%-d %B %Y" }}</small>
    <h1><b>{{ post.title }}</b></h1>
    <p class="view"><i>by {{ post.author | default: site.author }}</i></p>
    {{post.content}}
    <!-- {% if post.tags %}
        <small>tags: <em>{{ post.tags | join: "</em> - <em>" }}</em></small>
    {% endif %} -->
    <br><hr>
</div>
{% endfor %}
