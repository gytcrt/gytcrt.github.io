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

I grew up in Chongqing, China. Guangzhou, Shenzhen, California, North Carolina, Mexico City are the places I’ve lived in for more than 3 months. Currently, I try to stay in NYC for most of my weekends.

I am

* a developer/data scientist/consultant at Boston Consulting Group
* an advocate of women’s right and LGBT rights
* a Chinese calligrapher and art lover


I create this blog to share and connect:) Hopefully, you will be somewhat inspired or find a way to debug your code here.


***

# Contact

* Hit me up at the bottom left corner of this page
* Shoot me an email at gaoandrea7@gmail.com

***

### Images Reference
*  Blog: Sangluan Tie(丧乱帖) by [Wang Xizhi(王羲之)](https://en.wikipedia.org/wiki/Wang_Xizhi){:target="_blank"}
*  Project: Pipa Xing(琵琶行) by [Wen Zhengming(文徵明)](https://en.wikipedia.org/wiki/Wen_Zhengming){:target="_blank"}
*  About me: [John the Baptist](https://en.wikipedia.org/wiki/John_the_Baptist_(Caravaggio)){:target="_blank"} by [Caravaggio](https://en.wikipedia.org/wiki/Caravaggio){:target="_blank"}, 1604
