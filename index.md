---
---
<ul>
  {% for post in site.posts limit:6 %}
    <li class="post">
      <h2><a href="{{ post.url }}">{{ post.title }} - {{ post.date | date: '%Y-%m-%d' }}</a></h2>
      {{ post.content }}
    </li>
  {% endfor %}
</ul>
<h2><a href="/posts">Post Archive</a></h2>