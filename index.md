---
title: تطوير حلول الرؤية الحاسوبية في Azure
permalink: index.html
layout: home
---

تم تصميم التمارين التالية لتزويدك بتجربة تعليمية عملية تستكشف فيها المهام الشائعة التي يقوم بها المطورون عند إنشاء حلول الرؤية الحاسوبية على Microsoft Azure.

> **ملاحظة**: لاستكمال التدريبات، ستحتاج إلى اشتراك Azure الذي تتمتع فيه بالأذونات والحصة النسبية الكافية لتوفير موارد Azure ونماذج الذكاء الاصطناعي التوليدي اللازمة. إذا لم يكن لديك حسابًا مسبقًا، فيمكنك التسجيل للحصول على [حساب Azure](https://azure.microsoft.com/free). هناك خيار تجريبي مجاني للمستخدمين الجدد يتضمن رصيدًا لأول 30 يومًا.

## التدريبات

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Labs'" %} {% for activity in labs  %}
<hr>
### [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) {{activity.lab.description}} {% endfor %}

> **ملاحظة**: على الرغم من أنه يمكنك إكمال هذه التدريبات بمفردها، إلا أنها مصممة لاستكمال الوحدات الموجودة على [Microsoft Learn](https://learn.microsoft.com/training/paths/create-computer-vision-solutions-azure-ai/)؛ حيث ستجد تعمقًا في بعض المفاهيم الأساسية التي تستند إليها هذه التدريبات.
