---
layout: page
title: Namaste
tagline: love != control
---
{% include JB/setup %}


__Some of my projects__

* [YogArkana](http://www.yogarkana.com): instruction cards for your Yoga poses (in French)
* [QSOS](/QSOS/about.html): how to evaluate, compare and select open source components?
* [Garous](http://garous.semeteys.org): free RPG to roleplay semi humans in a contemporary universe (in French)
* Waxtaan: social network of former students of french schools in Senegal (since 1999! But out of order today...)

__If you're already bored...__

Who is the World Wide Spider?

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
