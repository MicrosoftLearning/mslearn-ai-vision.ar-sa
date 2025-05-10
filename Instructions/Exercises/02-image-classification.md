<div class="Box-sc-g0xbh4-0 eoaCFS js-snippet-clipboard-copy-unpositioned undefined" data-hpc="true"><article class="markdown-body entry-content container-lg" itemprop="text"><div dir="rtl"><markdown-accessiblity-table data-catalyst=""><table>
  <thead>
  <tr>
  <th>lab</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="auto"><table>
  <thead>
  <tr>
  <th>title</th>
  <th>module</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="auto">تصنيف الصور باستخدام نموذج الذكاء الاصطناعي في Azure Vision المخصص</div></td>
  <td><div dir="auto">Module 2 - Develop computer vision solutions with Azure AI Vision</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">تصنيف الصور باستخدام نموذج الذكاء الاصطناعي في Azure Vision المخصص</h1><a id="user-content-تصنيف-الصور-باستخدام-نموذج-الذكاء-الاصطناعي-في-azure-vision-المخصص" class="anchor" aria-label="Permalink: تصنيف الصور باستخدام نموذج الذكاء الاصطناعي في Azure Vision المخصص" href="#تصنيف-الصور-باستخدام-نموذج-الذكاء-الاصطناعي-في-azure-vision-المخصص"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">يمكنك الذكاء الاصطناعي في Azure Vision من تدريب نماذج مخصصة لتصنيف العناصر واكتشافها باستخدام التسميات التي تحددها. في هذا التمرين المعملي، سنبني نموذج تصنيف صور مخصص لتصنيف صور الفاكهة.</p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">استنساخ المستودع لهذه الدورة التدريبية</h2><a id="user-content-استنساخ-المستودع-لهذه-الدورة-التدريبية" class="anchor" aria-label="Permalink: استنساخ المستودع لهذه الدورة التدريبية" href="#استنساخ-المستودع-لهذه-الدورة-التدريبية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا لم تكن قد استنسخت بالفعل مستودع التعليمات البرمجية <strong>الذكاء الاصطناعي في Azure Vision</strong> في البيئة التي تعمل فيها في هذا التمرين المعملي، فاتبع هذه الخطوات لتنفيذ ذلك. بخلاف ذلك، افتح المجلد المستنسخ في تعليمة Visual Studio البرمجية.</p>
<ol dir="rtl">
<li>
<p dir="auto">ابدأ تشغيل Visual Studio Code.</p>
</li>
<li>
<p dir="auto">افتح لوحة (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع <code>https://github.com/MicrosoftLearning/mslearn-ai-vision</code> إلى مجلد محلي (لا يُهم أي مجلد).</p>
</li>
<li>
<p dir="auto">عند استنساخ المستودع، افتح المجلد في تعليمة Visual Studio البرمجية.</p>
</li>
<li>
<p dir="auto">انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية #C في المستودع.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: إذا جرت مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد <strong>ليس الآن</strong>. إذا جرت مطالبتك برسالة <em>اكتشاف مشروع وظيفة Azure في المجلد</em>، يمكنك إغلاق هذه الرسالة بأمان.</p>
</blockquote>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تزويد موارد Azure</h2><a id="user-content-تزويد-موارد-azure" class="anchor" aria-label="Permalink: تزويد موارد Azure" href="#تزويد-موارد-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا لم يكن لديك بالفعل مورداً في اشتراكك، فسيتعين عليك توفير مورد <strong>خدمات الذكاء الاصطناعي في Azure</strong>.</p>
<ol dir="rtl">
<li>
<p dir="auto">افتح مدخل Azure على <code>https://portal.azure.com</code>، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.</p>
</li>
<li>
<p dir="auto">في شريط البحث العلوي، ابحث عن <em>خدمات الذكاء الاصطناعي في Azure</em>، وحدد <strong>خدمات الذكاء الاصطناعي في Azure</strong>، وأنشئ مورد حساب متعدد الخدمات لخدمات الذكاء الاصطناعي في Azure بالإعدادات التالية:</p>
<ul dir="rtl">
<li><strong>Subscription</strong>: <em>اشتراكك في Azure</em></li>
<li><strong>مجموعة الموارد</strong>: <em>اختر أو أنشئ مجموعة موارد (إذا كنت تستخدم اشتراكاً مقيداً، فقد لا يكون لديك إذن لإنشاء مجموعة موارد جديدة - استخدم المجموعة المتوفرة)</em></li>
<li><strong>المنطقة</strong>: <em>اختر من بين منطقة شرق الولايات المتحدة وأوروبا الغربية وغرب الولايات المتحدة 2*</em></li>
<li><strong>الاسم</strong>: <em>أدخل اسماً فريداً</em></li>
<li><strong>مستوى التسعير</strong>: قياسي S0</li>
</ul>
<p dir="auto">*تتوفر علامات النماذج المخصصة الذكاء الاصطناعي في Azure Vision 4.0 حالياً في هذه المناطق فقط.</p>
</li>
<li>
<p dir="auto">حدد مربعات الاختيار المطلوبة ثم أنشئ المورد.</p>
</li>
</ol>

<p dir="auto">نحتاج أيضاً إلى حساب تخزين لتخزين صور التدريب.</p>
<ol dir="rtl">
<li>
<p dir="auto">في مدخل Microsoft Azure، ابحث عن <strong>حسابات التخزين</strong> وحددها، وأنشئ حساب تخزين جديداً بالإعدادات التالية:</p>
<ul dir="rtl">
<li><strong>Subscription</strong>: <em>اشتراكك في Azure</em></li>
<li><strong>مجموعة الموارد</strong>: <em>اختر مجموعة الموارد نفسها التي أنشئت مورد خدمة الذكاء الاصطناعي في Azure بها في</em></li>
<li><strong>اسم حساب التخزين</strong>: customclassifySUFFIX
<ul dir="rtl">
<li><em>ملاحظة: استبدل الرمز المميز <code>SUFFIX</code> بالأحرف الأولى من اسمك أو قيمة أخرى للتأكد من أن اسم المورد فريد عالمياً.</em></li>
</ul>
</li>
<li><strong>المنطقة</strong>: <em>اختر المنطقة نفسها التي استخدمتها لمورد خدمة الذكاء الاصطناعي في Azure</em></li>
<li><strong>الخدمة الأساسية</strong>: تخزين Azure الكائن الثنائي كبير الحجم BLOB أوAzure Data Lake Storage Gen 2</li>
<li><strong>حمل العمل الأساسي</strong>: غير ذلك</li>
<li><strong>الأداء:</strong> قياسي</li>
<li><strong>التكرار</strong>: التخزين المتكرر محلياً (LRS)</li>
</ul>
</li>
<li>
<p dir="auto">خلال إنشاء حساب التخزين الخاص بك، انتقل إلى تعليمة Visual studio البرمجية ووسع مجلد <strong>Labfiles/02-image-classification</strong>.</p>
</li>
<li>
<p dir="auto">في ذلك المجلد، حدد <strong>replace.ps1</strong> وراجع التعليمة البرمجية. سترى أنه يستبدل اسم حساب التخزين الخاص بك للعنصر النائب في ملف JSON (ملف COCO) الذي نستخدمه في خطوة لاحقة. استبدل العنصر النائب <em>في السطر الأول فقط</em> من الملف باسم حساب التخزين الخاص بك. حفظ الملف.</p>
</li>
<li>
<p dir="auto">انقر بزر الماوس الأيمن على المجلد <strong>02-image-classification</strong> وافتح الوحدة الطرفية المتكاملة. قم بتشغيل الأمر التالي.</p>
</li>
<div class="highlight highlight-source-powershell notranslate position-relative overflow-auto" dir="auto"><pre><code>./replace.ps1</code></pre></div>

<li>
<p dir="auto">يمكنك مراجعة ملف COCO للتأكد من وجود اسم حساب التخزين الخاص بك. حدد <strong>training-images/training_labels.json</strong> واعرض الإدخالات القليلة الأولى. في الحقل <em>absolute_url</em>، يجب أن ترى شيئاً مشابهاً لـ <em>"<a href="https://myStorage.blob.core.windows.net/fruit/" rel="nofollow">https://myStorage.blob.core.windows.net/fruit/</a>...</em>. إذا لم يكن التغيير متوقعاً، فتأكد من تحديث العنصر النائب الأول فقط في البرنامج النصي PowerShell.</p>
</li>
<li>
<p dir="auto">أغلق كل من ملف JSON وPowerShell، وارجع إلى نافذة المستعرض لديك.</p>
</li>
<li>
<p dir="auto">يجب أن يكون حساب التخزين الخاص بك كاملاً. انتقل إلى حساب التخزين الخاص بك.</p>
</li>
<li>
<p dir="auto">تمكين الوصول العام إلى حساب التخزين. في الجزء الأيمن، انتقل إلى <strong>التكوين</strong> في مجموعة <strong>الإعدادات</strong>، وبوسعك تمكين <em>السماح بالوصول المجهول لكائن ثنائي كبير الحجم</em>. حدد <strong>حفظ</strong></p>
</li>
<li>
<p dir="auto">في الجزء الأيسر، في <strong>تخزين البيانات</strong>، حدد <strong>الحاويات</strong> وقم بإنشاء حاوية جديدة باسم <code>fruit</code>، واضبط <strong>مستوى الوصول المجهول</strong> على <em>الحاوية (إمكانية وصول القراءة فقط بشكل مجهول للحاويات والكائنات)</em>.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: إذا تعطل <strong>مستوى الوصول المجهول</strong>، فعليك تحديث صفحة المستعرض.</p>
</blockquote>
</li>
<li>
<p dir="auto">انتقل إلى <code>fruit</code>، وحدد <strong>تحميل</strong>، ثم قم بتحميل الصور (وملف JSON واحد) في <strong>Labfiles/02-image-classification/training-images</strong> إلى تلك الحاوية.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إنشاء مشروع تدريب نموذج مخصص</h2><a id="user-content-إنشاء-مشروع-تدريب-نموذج-مخصص" class="anchor" aria-label="Permalink: إنشاء مشروع تدريب نموذج مخصص" href="#إنشاء-مشروع-تدريب-نموذج-مخصص"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">بعد ذلك، ستنشئ مشروع تدريب جديد لتصنيف الصور المخصصة في Vision Studio.</p>
<ol dir="rtl">
<li>في مستعرض الويب، انتقل إلى <code>https://portal.vision.cognitive.azure.com/</code> وسجل الدخول باستخدام حساب Microsoft حيث أنشأت مورد الذكاء الاصطناعي في Azure.</li>
<li>حدد مربع <strong>تخصيص النماذج باستخدام الصور</strong> (يمكن العثور عليه في علامة التبويب <strong>تحليل الصورة</strong> إذا لم يظهر في العرض الافتراضي لديك).</li>
<li>حدد مورد خدمة الذكاء الاصطناعي في Azure الذي قمت بإنشائه للتو.</li>
<li>في مشروعك، حدد <strong>إضافة مجموعة بيانات جديدة</strong> في الأعلى. تكوين بالإعدادات التالية:
<ul dir="rtl">
<li><strong>اسم مجموعة البيانات</strong>: training_images</li>
<li><strong>نوع النموذج</strong>: تصنيف الصور</li>
<li><strong>حدد حاوية تخزين كائن ثنائي كبير الحجم من Azure</strong>: حدد <strong>تحديد حاوية</strong>
<ul dir="rtl">
<li><strong>Subscription</strong>: <em>اشتراكك في Azure</em></li>
<li><strong>حساب التخزين</strong>: <em>حساب التخزين الذي أنشأته</em></li>
<li><strong>حاوية كائن ثنائي كبير الحجم</strong>: فاكهة</li>
</ul>
</li>
<li>حدد المربع "السماح لـ Vision Studio بالقراءة والكتابة في وحدة تخزين الكائن الثنائي الكبير الخاص بك"</li>
</ul>
</li>
<li>حدد مجموعة بيانات <strong>training_images</strong>.</li>
</ol>
<p dir="auto">في هذه المرحلة من إنشاء المشروع، عادةً ما تحدد إنشاء <strong>مشروع تسمية بيانات Azure ML</strong> وتسمية صورك، ما يؤدي إلى إنشاء ملف COCO. نشجعك على تجربة ذلك إذا كان لديك الوقت، ولكن لأغراض هذا الدرس التطبيقي، سمينا بالفعل الصور لك ووفرنا ملف COCO الناتج.</p>
<ol dir="rtl">
<li>تحديد <strong>إضافة ملف COCO</strong></li>
<li>في القائمة المنسدلة، حدد <strong>استيراد ملف COCO من حاوية كائن ثنائي كبير الحجم</strong></li>
<li>نظرا لأنك قمت بالفعل بتوصيل الحاوية الخاصة بك باسم <code>fruit</code>، يبحث Vision Studio عن ملف COCO. حدد <strong>training_labels.json</strong> من القائمة المنسدلة، وأضف ملف COCO.</li>
<li>انتقل إلى <strong>النماذج المخصصة</strong> على اليسار، وحدد <strong>تدريب نموذج جديد</strong>. استخدم الإعدادات التالية:
<ul dir="rtl">
<li><strong>اسم النموذج</strong>: classifyfruit</li>
<li><strong>نوع النموذج</strong>: تصنيف الصور</li>
<li><strong>اختيار مجموعة بيانات التدريب</strong>: training_images</li>
<li>اترك الباقي كإعداد افتراضي، ثم حدد <strong>نموذج القطار</strong></li>
</ul>
</li>
</ol>
<p dir="auto">يمكن أن يستغرق التدريب بعض الوقت - الميزانية الافتراضية تصل إلى ساعة، ولكن بالنسبة لمجموعة البيانات الصغيرة هذه عادة ما تكون أسرع بكثير من ذلك. حدد زر <strong>التحديث</strong> كل دقيقتين حتى <em>نجاح</em> حالة المهمة. حدد النموذج.</p>
<p dir="auto">هنا يمكنك عرض أداء وظيفة التدريب. راجع دقة النموذج المدرب وضبطه المحكم.</p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تجربة نموذجك المخصص</h2><a id="user-content-تجربة-نموذجك-المخصص" class="anchor" aria-label="Permalink: تجربة نموذجك المخصص" href="#تجربة-نموذجك-المخصص"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">النموذج الخاص بك مدرب وأصبح جاهزاً للاختبار.</p>
<ol dir="rtl">
<li>في أعلى الصفحة الخاصة بالنموذج المخصص، حدد <strong>تجربته</strong>.</li>
<li>حدد نموذج <strong>classifyfruit</strong> من القائمة المنسدلة التي تحدد النموذج الذي تريد استخدامه، ثم انتقل إلى المجلد <strong>02-image-classification\test-images</strong>.</li>
<li>حدد كل صورة واعرض النتائج. حدد علامة التبويب <strong>JSON</strong> في مربع النتائج لفحص استجابة JSON الكاملة.</li>
</ol>

<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تنظيف الموارد</h2><a id="user-content-تنظيف-الموارد" class="anchor" aria-label="Permalink: تنظيف الموارد" href="#تنظيف-الموارد"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا كنت لا تستخدم موارد Azure التي أنشأتها في هذا المختبر لوحدات التدريب الأخرى، فيمكنك حذفها لتجنب تكبد المزيد من الرسوم.</p>
<ol dir="rtl">
<li>
<p dir="auto">افتح مدخل Azure في <code>https://portal.azure.com</code>، وفي شريط البحث العلوي، ابحث عن الموارد التي أنشأتها في هذا المختبر.</p>
</li>
<li>
<p dir="auto">في صفحة المورد، حدد <strong>حذف</strong> واتبع الإرشادات لحذف المورد. بدلاً من ذلك، يمكنك حذف مجموعة الموارد بأكملها لتنظيف جميع الموارد في الوقت نفسه.</p>
</li>
</ol>
</article></div></div>
