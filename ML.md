---
layout: page
title: "ML"
permalink: /posts/ML/

main_nav: false
---
ML 공부 전반에 대한 포스팅입니다.
---

{% for category in site.categories %}
  {% capture cat%}{{category|first}}{% endcapture %}
  {% if cat==page.title %}
  <ul class="posts-list">
  {% for post in site.categories[cat] %}
    <li>
      <strong>
        <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      </strong>
      <span class="post-date">- {{ post.date | date_to_long_string }}</span>
    </li>
  {% endfor %}
  </ul>
  {% if forloop.last == false %}<hr>{% endif %}
  {% endif %}
{% endfor %}
<br>


<!--
{% for category in site.categories %}
  <ul class="categories">
    {% for categoryName in category[0] %}
      <li>
      	<span><a href="/posts/{{categoryName}}">
	{{ categoryName }}
	</a></span>
	<span class="count">{{category[1].size}}</span>
	
	</li>
    {% endfor %}
</ul>
{% endfor %}
-->
