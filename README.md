# Under Construction

* [Kode](https://docs.google.com/document/d/1J5YzXeR3DysPkzXioFvRnaAyMHvTbTKk1hAvmNx2dNo/edit#)
* [Class Details](./kode.html)

<h1>Latest Posts</h1>

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>