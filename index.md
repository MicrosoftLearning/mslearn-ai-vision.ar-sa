---
title: تمارين رؤية الذكاء الاصطناعي في Azure
permalink: index.html
layout: home
---

# تمارين رؤية الذكاء الاصطناعي في Azure

تم تصميم التدريبات التالية لدعم الوحدات النمطية على Microsoft Learn.


{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Exercises'" %}

{% for activity in labs  %} {% if activity.lab.title contains "Azure AI Custom Vision" %}  
    {% continue %}  
  {% endif %} 
  - [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) {% endfor %}
