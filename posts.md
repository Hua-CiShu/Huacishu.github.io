---
layout: default
title: 文章
permalink: /posts/
---

<h1>所有文章</h1>
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <small>（{{ post.date | date: "%Y-%m-%d" }}）</small>
    </li>
  {% empty %}
    <li>还没有文章哦～ 在 <code>_posts/</code> 目录里新建一篇。</li>
  {% endfor %}
</ul>
