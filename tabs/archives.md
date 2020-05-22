---
title: Archives

# The Archives of posts.
# v2.0
# https://github.com/cotes2020/jekyll-theme-chirpy
# © 2017-2019 Cotes Chung
# MIT License
---

<div id="archives" class="pl-xl-2">
{% for post in site.posts %}
  {% capture this_year %}{{ post.date | date: "%Y" }}{% endcapture %}
  {% capture pre_year %}{{ post.previous.date | date: "%Y" }}{% endcapture %}
  {% if forloop.first %}
    {% assign last_day = "" %}
    {% assign last_month = "" %}
  <span class="lead">{{this_year}}</span>
  <ul class="list-unstyled">
  {% endif %}
    <li>
      <div>
        {% capture this_day %}{{ post.date | date: "%d" }}{% endcapture %}
        {% capture this_month %}{% assign m = page.date | date: "%-m" %}{% case m %}
          {% when '1' %}Janv
          {% when '2' %}Fevr
          {% when '3' %}Mars
          {% when '4' %}Avr
          {% when '5' %}Mai
          {% when '6' %}Juin
          {% when '7' %}Juil
          {% when '8' %}Août
          {% when '9' %}Sept
          {% when '10' %}Oct
          {% when '11' %}Nov
          {% when '12' %}Déc
        {% endcase %}{% endcapture %}
        <span class="date day">{{ this_day }}</span>
        <span class="date month small text-muted">{{ this_month }}</span>
        <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
      </div>
    </li>
  {% if forloop.last %}
  </ul>
  {% elsif this_year != pre_year %}
  </ul>
  <span class="lead">{{pre_year}}</span>
  <ul class="list-unstyled">
    {% assign last_day = "" %}
    {% assign last_month = "" %}
  {% endif %}
{% endfor %}
</div>