# Under Construction

* [Kode](https://docs.google.com/document/d/1J5YzXeR3DysPkzXioFvRnaAyMHvTbTKk1hAvmNx2dNo/edit#)
* [Class Details](./kode.html)

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>