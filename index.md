---
title: تمارين رؤية الذكاء الاصطناعي في Azure
permalink: index.html
layout: home
---

# تمارين رؤية الذكاء الاصطناعي في Azure

تم تصميم التدريبات التالية لدعم الوحدات النمطية على Microsoft Learn.


{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Exercises'" %}

{% للأنشطة في المعامل %} 
  - [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) {% endfor %}
