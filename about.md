---
layout: page
title: About Me
---

{% comment %}
  This inserts the "about" photo and text from `_config.yml`.
  You can edit it there (jekyll needs restart!) or remove it and provide your own photo/text.
  Don't forget to add the `me` class to the photo, like this: `![alt](src){:.me}`.
{% endcomment %}

{% if site.author.photo %}
  ![{{ site.author.name }}]({{ site.author.photo }}){:.me}
{% endif %}

{{ site.author.about }}

[write something about self]

***

### Images Reference
*  Blog: Sangluan Tie(丧乱帖) by [Wang Xizhi(王羲之)](https://en.wikipedia.org/wiki/Wang_Xizhi)
*  Project: Pipa Xing(琵琶行) by [Wen Zhengming(文徵明)](https://en.wikipedia.org/wiki/Wen_Zhengming)
*  About me: [Dr. Pozzi Comes Home](https://hammer.ucla.edu/blog/2014/10/dr-pozzi-comes-home/) by [John Singer Sargent](https://en.wikipedia.org/wiki/John_Singer_Sargent), 1881
