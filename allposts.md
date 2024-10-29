---
layout: default
title: All Posts
permalink: /allposts/
---

# All Posts

Here you can find a list of all my blog posts:

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ site.baseurl }}/{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%B %d, %Y" }}
    </li>
  {% endfor %}
</ul>

[Back to Home]({{ site.baseurl }}/)

