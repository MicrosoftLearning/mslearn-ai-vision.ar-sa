<div class="Box-sc-g0xbh4-0 eoaCFS js-snippet-clipboard-copy-unpositioned undefined" data-hpc="true"><article class="markdown-body entry-content container-lg" itemprop="text"><div dir="auto"><div dir="rtl"><markdown-accessiblity-table data-catalyst=""><table>
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
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="auto">كشف العانصر في الصور باستخدام الرؤية المخصصة في الذكاء الاصطناعي في Azure</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>
<div dir="auto"><div class="markdown-heading" dir="auto"><h1 tabindex="-1" dir="auto" class="heading-element">كشف العانصر في الصور باستخدام الرؤية المخصصة في الذكاء الاصطناعي في Azure</h1><a id="user-content-كشف-العانصر-في-الصور-باستخدام-الرؤية-المخصصة-في-الذكاء-الاصطناعي-في-azure" class="anchor" aria-label="Permalink: كشف العانصر في الصور باستخدام الرؤية المخصصة في الذكاء الاصطناعي في Azure" href="#كشف-العانصر-في-الصور-باستخدام-الرؤية-المخصصة-في-الذكاء-الاصطناعي-في-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div><a id="user-content-كشف-العانصر-في-الصور-باستخدام-الرؤية-المخصصة-في-الذكاء-الاصطناعي-في-azure" aria-label="Permalink: كشف العانصر في الصور باستخدام الرؤية المخصصة في الذكاء الاصطناعي في Azure" href="#كشف-العانصر-في-الصور-باستخدام-الرؤية-المخصصة-في-الذكاء-الاصطناعي-في-azure"></a></div>
<p dir="auto">في هذا التمرين، ستستخدم خدمة Custom Vision لتدريب *نموذج * الكشف عن العناصر الذي يمكنه اكتشاف وتحديد موقع ثلاث فئات من الفاكهة (التفاح والموز والبرتقال) في صورة.</p>
<div dir="auto"><div class="markdown-heading" dir="auto"><h2 tabindex="-1" dir="auto" class="heading-element">استنساخ المستودع لهذه الدورة التدريبية</h2><a id="user-content-استنساخ-المستودع-لهذه-الدورة-التدريبية" class="anchor" aria-label="Permalink: استنساخ المستودع لهذه الدورة التدريبية" href="#استنساخ-المستودع-لهذه-الدورة-التدريبية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div><a id="user-content-استنساخ-المستودع-لهذه-الدورة-التدريبية" aria-label="Permalink: استنساخ المستودع لهذه الدورة التدريبية" href="#استنساخ-المستودع-لهذه-الدورة-التدريبية"></a></div>
<p dir="auto">إذا استنسخت بالفعل مستودع التعليمات البرمجية <strong>mslearn-ai-vision</strong> إلى البيئة التي تعمل فيها في هذا التمرين المعملي، فافتحه في تعليمة Visual Studio البرمجية؛ بخلاف ذلك، اتبع هذه الخطوات لاستنساخه الآن.</p>
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
<p dir="auto"><strong>ملاحظة</strong>: في حالة مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد <strong>ليس الآن</strong>.</p>
</blockquote>
</li>
</ol>
<div dir="auto"><div class="markdown-heading" dir="auto"><h2 tabindex="-1" dir="auto" class="heading-element">إنشاء موارد الرؤية المخصصة</h2><a id="user-content-إنشاء-موارد-الرؤية-المخصصة" class="anchor" aria-label="Permalink: إنشاء موارد الرؤية المخصصة" href="#إنشاء-موارد-الرؤية-المخصصة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div><a id="user-content-إنشاء-موارد-الرؤية-المخصصة" aria-label="Permalink: إنشاء موارد الرؤية المخصصة" href="#إنشاء-موارد-الرؤية-المخصصة"></a></div>
<p dir="auto">إذا كان لديك بالفعل موارد <strong>رؤية مخصصة</strong> للتدريب والتوقع في اشتراك Azure الخاص بك، فيمكنك استخدامها في هذا التدريب. إذا لم يكن لديك ذلك، فاستخدم الإرشادات التالية لإنشائها.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: إذا كنت تستخدم حسابًا متعدد الخدمات، فسيكون المفتاح ونقطة النهاية متشابهين لكل من التدريب والتوقع.</p>
</blockquote>
<ol dir="rtl">
<li>
<p dir="auto">في علامة تبويب جديدة لمستعرض، افتح مدخل Azure في <code>https://portal.azure.com</code>، ثم سجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure لديك.</p>
</li>
<li>
<p dir="auto">اضغط على زر <strong>&amp;#65291، إنشاء مورد</strong>وابحث عن<em>custom vision</em>، وأنشئ مورد** Custom Vision** باستخدام الإعدادات التالية:</p>
<ul dir="rtl">
<li><strong>إنشاء خيارات</strong>: كلاهما</li>
<li><strong>Subscription</strong>: <em>اشتراكك في Azure</em></li>
<li><strong>مجموعة الموارد</strong>: <em>اختر أو أنشئ مجموعة موارد (إذا كنت تستخدم اشتراكًا مقيدًا، فقد لا يكون لديك إذن لإنشاء مجموعة موارد جديدة - استخدم المجموعة المتوفرة)</em></li>
<li><strong>المنطقة</strong>: <em>اختر أي منطقة متوفرة</em></li>
<li><strong>الاسم</strong>: <em>أدخل اسماً فريداً</em></li>
<li><strong>مستوى أسعار التدريب:</strong> F0</li>
<li><strong>مستوى أسعار التنبؤ</strong>: F0</li>
</ul>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: إذا كانت لديك خدمة رؤية معدلة F0 في اشتراكك مسبقًا، فاختر <strong>S0</strong> لأجل هذا.</p>
</blockquote>
</li>
<li>
<p dir="auto">انتظر حتى يتم إنشاء الموارد، ثم اعرض تفاصيل التوزيع ولاحظ أنه يتم توفير موردين لـ Custom Vision؛ مورد للتدريب، ومورد آخر للتنبؤ (الذي يتجلى عن طريق لاحقة <strong>-التنبؤ</strong> ). يمكنك عرض هذا من خلال الانتقال إلى مجموعة الموارد حيث قمت بإنشائها.</p>
</li>
</ol>
<blockquote>
<p dir="auto"><strong>مهم</strong>: لكل مورد * نقطة نهاية <em>و</em>مفاتيح<em>خاصة به، والتي تستخدم لإدارة الوصول من التعليمات البرمجية الخاصة بك. لتدريب نموذج تصنيف الصور، يجب أن تستخدم التعليمات البرمجية لديك مورد * التدريب</em> (بنقطة النهاية والمفتاح الخاص بها)؛ ولاستخدام النموذج المدرب للتنبؤ بفئات الصور، يجب أن تستخدم التعليمات البرمجية لديك مورد* التنبؤ* (باستخدام نقطة النهاية والمفتاح الخاص بها).</p>
</blockquote>
<div dir="auto"><div class="markdown-heading" dir="auto"><h2 tabindex="-1" dir="auto" class="heading-element">إنشاء مشروع Custom Vision</h2><a id="user-content-إنشاء-مشروع-custom-vision" class="anchor" aria-label="Permalink: إنشاء مشروع Custom Vision" href="#إنشاء-مشروع-custom-vision"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div><a id="user-content-إنشاء-مشروع-custom-vision" aria-label="Permalink: إنشاء مشروع Custom Vision" href="#إنشاء-مشروع-custom-vision"></a></div>
<p dir="auto">لتدريب نموذج اكتشاف العنصر، تحتاج إلى إنشاء مشروع رؤية مخصصة بناءً على مورد التدريب الخاص بك. للقيام بذلك، ستستخدم مدخل Custom Vision.</p>
<ol dir="rtl">
<li>في علامة تبويب مستعرض جديدة، افتح مدخل "Custom Vision" في <code>https://customvision.ai</code>، ثم سجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.</li>
<li>إنشاء مشروع جديد بالإعدادات التالية:
<ul dir="rtl">
<li><strong>الاسم</strong>: كشف الفاكهة</li>
<li><strong>الوصف</strong>: الكشف عن العناصر للفاكهة.</li>
<li><strong>المورد</strong>: * مورد Custom Vision الذي أنشأته مسبقًا*</li>
<li><strong>أنواع المشروع</strong>: الكشف عن الكائنات</li>
<li><strong>النطاقات</strong>: عام</li>
</ul>
</li>
<li>انتظر المشروع إلى إنشاء وفتح في المستعرض.</li>
</ol>
<div dir="auto"><div class="markdown-heading" dir="auto"><h2 tabindex="-1" dir="auto" class="heading-element">إضافة الصور ووضع علامة لها</h2><a id="user-content-إضافة-الصور-ووضع-علامة-لها" class="anchor" aria-label="Permalink: إضافة الصور ووضع علامة لها" href="#إضافة-الصور-ووضع-علامة-لها"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div><a id="user-content-إضافة-الصور-ووضع-علامة-لها" aria-label="Permalink: إضافة الصور ووضع علامة لها" href="#إضافة-الصور-ووضع-علامة-لها"></a></div>
<p dir="auto">لتدريب نموذج اكتشاف الكائن، تحتاج إلى تحميل الصور التي تحتوي على الفئات التي تريد أن يحددها النموذج، وتمييزها للإشارة إلى المربعات المحيطة لكل مثيل كائن.</p>
<ol dir="rtl">
<li>
<p dir="auto">في تعليمة Visual Studio البرمجية، اطلع على صور التدريب في مجلد** 03-object-detection/training-images** حيث قمت باستنساخ المستودع. يحتوي هذا المجلد على صور للفاكهة.</p>
</li>
<li>
<p dir="auto">في منصة الرؤية المعدلة في مشروع الكشف عن الأشياء، اختر <strong>إضافة الصور</strong> وحمل جميع الصور من الملف المستخرج.</p>
</li>
<li>
<p dir="auto">بعد تحميل الصور، حدد أول صورة تفتحها.</p>
</li>
<li>
<p dir="auto">ضع الماوس فوق أي كائن في الصورة حتى يتم عرض المنطقة المكتشفة تلقائيًا مثل الصورة أدناه. ثم حدد الكائن، وإذا لزم الأمر، قم بتغيير حجم المنطقة المحيطة به.</p>
<p dir="auto"><a href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/object-region.jpg"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/raw/OLPRODLOC/Instructions/media/object-region.jpg" alt="المنطقة الافتراضية لكائن" style="max-width: 100%;"></a></p>
<p dir="auto">بدلاً من ذلك، يمكنك ببساطة السحب حول الكائن لإنشاء منطقة.</p>
</li>
<li>
<p dir="auto">عندما تحيط المنطقة بالكائن، أضف علامة جديدة بنوع الكائن المناسب (<em>التفاح</em> أو <em>الموز</em> أو <em>البرتقال</em>) كما هو موضح هنا:</p>
<p dir="auto"><a href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/object-tag.jpg"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/raw/OLPRODLOC/Instructions/media/object-tag.jpg" alt="كائن معلم في صورة" style="max-width: 100%;"></a></p>
</li>
<li>
<p dir="auto">حدد كل كائن آخر في الصورة وقم بتمييزه، وقم بتغيير حجم المناطق وإضافة علامات جديدة حسب الحاجة.</p>
<p dir="auto"><a href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/object-tags.jpg"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/raw/OLPRODLOC/Instructions/media/object-tags.jpg" alt="كائنان معلمان في صورة" style="max-width: 100%;"></a></p>
</li>
<li>
<p dir="auto">استخدم الرابط <strong>&gt;</strong> الموجود على اليمين للانتقال إلى الصورة التالية، ووضع علامة على كائناتها. ثم استمر في العمل من خلال مجموعة الصور بأكملها، ووضع علامات على كل تفاحة وموز وبرتقال.</p>
</li>
<li>
<p dir="auto">عند الانتهاء من وضع علامات على الصورة الأخيرة، أغلق محرر ** تفاصيل الصورة**. في صفحة <strong>تدريب الصور</strong>، ضمن <strong>العلامات</strong>، حدد <strong>الصور ذات العلامات</strong> لمشاهدة جميع الصور ذات العلامات:</p>
</li>
</ol>
<p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/tagged-images.jpg"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/raw/OLPRODLOC/Instructions/media/tagged-images.jpg" alt="الصور ذات العلامات في مشروع" style="max-width: 100%;"></a></p>
<div dir="auto"><div class="markdown-heading" dir="auto"><h2 tabindex="-1" dir="auto" class="heading-element">استخدام واجهة برمجة تطبيقات التدريب لتحميل الصور</h2><a id="user-content-استخدام-واجهة-برمجة-تطبيقات-التدريب-لتحميل-الصور" class="anchor" aria-label="Permalink: استخدام واجهة برمجة تطبيقات التدريب لتحميل الصور" href="#استخدام-واجهة-برمجة-تطبيقات-التدريب-لتحميل-الصور"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div><a id="user-content-استخدام-واجهة-برمجة-تطبيقات-التدريب-لتحميل-الصور" aria-label="Permalink: استخدام واجهة برمجة تطبيقات التدريب لتحميل الصور" href="#استخدام-واجهة-برمجة-تطبيقات-التدريب-لتحميل-الصور"></a></div>
<p dir="auto">يمكنك استخدام UI في بوابة الرؤية المخصصة لوضع علامة على صورك، ولكن العديد من فرق التطوير الذكاء الاصطناعي تستخدم أدوات أخرى تنشئ ملفات تحتوي على معلومات حول العلامات ومناطق العناصر في الصور. في سيناريوهات مثل هذه، يمكنك استخدام واجهة برمجة تطبيقات تدريب Custom Vision لتحميل الصور ذات العلامات إلى المشروع.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: في هذا التمرين، يمكنك اختيار استخدام واجهة برمجة التطبيقات إما <strong>من #C</strong> أو <strong>Python</strong> SDK. في الخطوات الواردة أدناه، نفذ الإجراءات المناسبة للغتك المفضلة.</p>
</blockquote>
<ol dir="rtl">
<li>انقر فوق أيقونة <em>الإعدادات</em> (#9881;) في الجزء العلوي الأيمن من صفحة<strong>صور التدريب</strong> في مدخل Custom Vision لعرض إعدادات المشروع.</li>
<li>ضمن <strong>عام</strong> (على اليسار)، لاحظ <strong>معرف المشروع</strong> لذي يعرف هذا المشروع بشكل فريد.</li>
<li>على اليمين، ضمن <strong>الموارد</strong> لاحظ أنه يتم عرض المفتاح ونقطة النهاية. هذه هي تفاصيل مورد * التدريب* (يمكنك أيضًا الحصول على هذه المعلومات عن طريق عرض المورد في مدخل Microsoft Azure).</li>
<li>في تعليمة Visual Studio البرمجية، ضمن مجلد<strong>03-object-detection</strong>، قم بتوسيع مجلد** C-Sharp**أو <strong>Python</strong>استنادًا إلى تفضيلات اللغة.</li>
<li>انقر بزر الماوس الأيمن فوق مجلد <strong>train-detector</strong> وافتح وحدة طرفية متكاملة. ثم قم بتثبيت حزمة تدريب Custom Vision عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto"><div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Microsoft.Azure.CognitiveServices.Vision.CustomVision.Training --version 2.0.0
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Microsoft.Azure.CognitiveServices.Vision.CustomVision.Training --version 2.0.0" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div><div dir="auto">
    
      
    

      
    

    
  </div></div>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto"><div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>pip install azure-cognitiveservices-vision-customvision==3.1.1
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="pip install azure-cognitiveservices-vision-customvision==3.1.1" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div><div dir="auto">
    
      
    

      
    

    
  </div></div>
<ol start="6" dir="rtk">
<li>
<p dir="rtl">اعرض محتويات مجلد <strong>train-detector</strong>، ولاحظ أنه يحتوي على ملف لإعدادات التكوين:</p>
<ul dir="rtl">
<li><strong>C#</strong>: appsettings.json</li>
<li><strong>Python</strong>: .env</li>
</ul>
<p dir="auto">افتح ملف التكوين وقم بتحديث قيم التكوين التي يحتوي عليها لتعكس نقطة النهاية والمفتاح لمورد تدريب* Custom Vision *لديك ومعرّف المشروع لمشروع الكشف عن العناصر الذي قمت بإنشائه مسبقًا. احفظ تغييراتك.</p>
</li>
<li>
<p dir="auto">في مجلد ** train-detector**، افتح <strong>tagged-images.json</strong> وافحص ملف JSON الذي يحتوي عليه. يحدد JSON قائمة بالصور، كل منها تحتوي على منطقة واحدة أو أكثر ذات علامات. تتضمن كل منطقة ذات علامة اسم علامة، والإحداثيات العلوية واليسرى وأبعاد العرض والارتفاع لمربع الإحاطة الذي يحتوي على الكائن ذي علامة.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: تشير الإحداثيات والأبعاد في هذا الملف إلى نقاط نسبية على الصورة. على سبيل المثال، تشير قيمة* الارتفاع* 0.7 إلى مربع يمثل 70% من ارتفاع الصورة. تنشئ بعض أدوات وضع العلامات تنسيقات أخرى من الملفات حيث تمثل قيم الإحداثيات والأبعاد وحدات البكسل أو البوصة أو وحدات القياس الأخرى.</p>
</blockquote>
</li>
<li>
<p dir="auto">لاحظ أن مجلد ** train-detector** يحتوي على مجلد فرعي يتم فيه تخزين ملفات الصور المشار إليها في ملف JSON.</p>
</li>
<li>
<p dir="auto">لاحظ أن مجلد <strong>train-detector</strong> يحتوي على ملف تعليمات برمجية لتطبيق العميل:</p>
<ul dir="rtl">
<li><strong>C#</strong>: Program.cs</li>
<li><strong>Python</strong>: train-detector.py</li>
</ul>
<p dir="auto">افتح ملف التعليمات البرمجية وراجع التعليمات البرمجية التي يحتوي عليها، مع ملاحظة التفاصيل التالية:</p>
<ul dir="rtl">
<li>يتم استيراد مساحات الأسماء من الحزمة التي قمت بتثبيتها</li>
<li>تسترد الدالة ** Main** إعدادات التكوين، وتستخدم المفتاح ونقطة النهاية لإنشاء <strong>CustomVisionTrainingClient</strong> مصدق عليه، والذي يتم استخدامه بعد ذلك مع معرف المشروع لإنشاء مرجع** مشروع** إلى مشروعك.</li>
<li>تستخرج الدالة ** Upload_Images** معلومات المنطقة ذات العلامات من ملف JSON وتستخدمها لإنشاء مجموعة من الصور مع المناطق، والتي تقوم بتحميلها بعد ذلك إلى المشروع.</li>
</ul>
</li>
<li>
<p dir="auto">أعد الوحدة الطرفية المتكاملة للمجلد <strong>train-detector</strong>، وأدخل الأمر التالي لتشغيل البرنامج:</p>
<p dir="rtl"><strong>#C</strong></p>
</li>
<div dir="auto"><div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet run
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet run" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div><div dir="auto">
    
      
    

      
    

    
  </div></div>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto"><div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python train-detector.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python train-detector.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div><div dir="auto">
    
      
    

      
    

    
  </div></div>
</li>
<li>
<p dir="auto">انتظر حتى ينتهي البرنامج. ثم ارجع إلى المستعرض الخاص بك واعرض صفحة <strong>صور التدريب</strong> لمشروعك في مدخل Custom Vision (قم بتحديث المتصفح إذا لزم الأمر).</p>
</li>
<li>
<p dir="auto">تحقق من إضافة بعض الصور ذات العلامات الجديدة إلى المشروع.</p>
</li>
</ol>
<div dir="auto"><div class="markdown-heading" dir="auto"><h2 tabindex="-1" dir="auto" class="heading-element">تدريب واختبار نموذج</h2><a id="user-content-تدريب-واختبار-نموذج" class="anchor" aria-label="Permalink: تدريب واختبار نموذج" href="#تدريب-واختبار-نموذج"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div><a id="user-content-تدريب-واختبار-نموذج" aria-label="Permalink: تدريب واختبار نموذج" href="#تدريب-واختبار-نموذج"></a></div>
<p dir="auto">الآن بعد أن قمت بتمييز الصور في مشروعك، فأنت جاهز لتدريب نموذج. أنت</p>
<ol dir="rtl">
<li>في مشروع Custom Vision، انقر فوق <strong>Train</strong> لتدريب نموذج اكتشاف كائن باستخدام الصور ذات العلامات. حدد خيار <strong>Quick Training</strong></li>
<li>انتظر حتى يكتمل التدريب (قد يستغرق عشر دقائق أو نحو ذلك)، ثم قم بمراجعة مقاييس أداء <em>الدقة</em> و<em>الاستدعاء</em> و<em>mAP</em>، والتي تقيس دقة التنبؤ لنموذج التصنيف، ويجب أن تكون جميعها عالية.</li>
<li>في أعلى يمين الصفحة، انقر فوق <strong>Quick Test</strong>، ثم في المربع <strong>Image URL</strong> أدخل <code>https://aka.ms/apple-orange</code> واعرض التوقع الذي تم إنشاؤه. ثم أغلق نافذة <strong>Quick Test</strong>.</li>
</ol>
<div dir="auto"><div class="markdown-heading" dir="auto"><h2 tabindex="-1" dir="auto" class="heading-element">نشر نموذج الكشف عن الكائنات</h2><a id="user-content-نشر-نموذج-الكشف-عن-الكائنات" class="anchor" aria-label="Permalink: نشر نموذج الكشف عن الكائنات" href="#نشر-نموذج-الكشف-عن-الكائنات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div><a id="user-content-نشر-نموذج-الكشف-عن-الكائنات" aria-label="Permalink: نشر نموذج الكشف عن الكائنات" href="#نشر-نموذج-الكشف-عن-الكائنات"></a></div>
<p dir="auto">أنت الآن جاهز لنشر نموذجك المدرّب بحيث يمكن استخدامه من تطبيق عميل.</p>
<ol dir="rtl">
<li>في مدخل Custom Vision، في صفحة <strong>الأداء</strong>، انقر فوق <strong>🗸 نشر</strong> لنشر النموذج المُدرب بالإعدادات التالية:
<ul dir="rtl">
<li><strong>اسم النموذج</strong>: fruit-detector</li>
<li><strong>مورد التنبؤ</strong>: <em>مورد <strong>التنبؤ</strong> الذي أنشأته سابقًا والذي ينتهي بـ "-Prediction" (ليس هو مورد التدريب)</em>.</li>
</ul>
</li>
<li>في الجزء العلوي الأيسر من صفحة <strong>إعدادات المشروع</strong>، انقر فوق أيقونة <em>معرض المشاريع</em> (👁) للعودة إلى الصفحة الرئيسية لمدخل Custom Vision، حيث يتم إدراج مشروعك الآن.</li>
<li>في الصفحة الرئيسية لمدخل Custom Vision، في أعلى اليمين، انقر فوق أيقونة *الإعدادات * (⚙) لعرض إعدادات خدمة Custom Vision الخاصة بك. ثم، ضمن <strong>الموارد</strong>، ابحث عن مورد * التنبؤ *الذي ينتهي بـ "-Prediction" (وليس مورد التدريب) لتحديد قيم ** المفتاح **** ونقطة النهاية الخاصة به **(يمكنك أيضًا الحصول على هذه المعلومات عن طريق عرض المورد في مدخل Microsoft Azure).</li>
</ol>
<div dir="auto"><div class="markdown-heading" dir="auto"><h2 tabindex="-1" dir="auto" class="heading-element">استخدام مصنف الصور من تطبيق عميل</h2><a id="user-content-استخدام-مصنف-الصور-من-تطبيق-عميل" class="anchor" aria-label="Permalink: استخدام مصنف الصور من تطبيق عميل" href="#استخدام-مصنف-الصور-من-تطبيق-عميل"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div><a id="user-content-استخدام-مصنف-الصور-من-تطبيق-عميل" aria-label="Permalink: استخدام مصنف الصور من تطبيق عميل" href="#استخدام-مصنف-الصور-من-تطبيق-عميل"></a></div>
<p dir="auto">الآن بعد أن قمت بنشر نموذج تصنيف الصور، يمكنك استخدامه من تطبيق عميل. مرة أخرى، يمكنك اختيار استخدام <strong>#C</strong> أو <strong>Python</strong>.</p>
<ol dir="rtl">
<li>في تعليمة Visual Studio البرمجية استعرض للوصول إلى مجلد<strong>03-object-detection</strong> وفي المجلد للغة المفضلة لديك (<strong>C-Sharp</strong> أو <strong>Python</strong>)، قم بتوسيع مجلد<strong>test-detector</strong>.</li>
<li>انقر بزر الماوس الأيمن فوق مجلد <strong>test-detector</strong> وافتح وحدة طرفية متكاملة. ثم أدخل الأمر التالي الخاص بـ SDK لتثبيت حزمة تنبؤ Custom Vision:</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto"><div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Microsoft.Azure.CognitiveServices.Vision.CustomVision.Prediction --version 2.0.0
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Microsoft.Azure.CognitiveServices.Vision.CustomVision.Prediction --version 2.0.0" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div><div dir="auto">
    
      
    

      
    

    
  </div></div>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto"><div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>pip install azure-cognitiveservices-vision-customvision==3.1.1
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="pip install azure-cognitiveservices-vision-customvision==3.1.1" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div><div dir="auto">
    
      
    

      
    

    
  </div></div>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: تتضمن حزمة Python SDK كلا من حزم التدريب والتنبؤ، وقد تكون مثبتة بالفعل.</p>
</blockquote>
<ol start="3" dir="auto">
<li>افتح ملف التكوين لتطبيق العميل الخاص بك (<em>appsettings.json</em> لـ #C أو <em>.env</em> لـ Python) وقم بتحديث قيم التكوين التي يحتوي عليها لتعكس نقطة النهاية والمفتاح لمورد توقع* Custom Vision ومعرف* المشروع لمشروع الكشف عن العناصر واسم النموذج المنشور (الذي يجب أن يكون <em>fruit-detector</em>). احفظ تغييراتك.</li>
<li>افتح ملف التعليمات البرمجية لتطبيق العميل الخاص بك (<em>Program.cs</em> لـ #C، <em>test-detector.py</em> لـ Python) وراجع التعليمات البرمجية التي يحتوي عليها، مع ملاحظة التفاصيل التالية:
<ul dir="rtl">
<li>يتم استيراد مساحات الأسماء من الحزمة التي قمت بتثبيتها</li>
<li>تسترد الدالة ** Main** إعدادات التكوين، وتستخدم المفتاح ونقطة النهاية لإنشاء <strong>CustomVisionPredictionClient</strong> مصدّق عليه.</li>
<li>يتم استخدام عنصر عميل التنبؤ للحصول على تنبؤات الكشف عن العناصر للصورة <strong>produce.jpg</strong>، مع تحديد معرف المشروع واسم النموذج في الطلب. ثم يتم رسم المناطق ذات العلامات المتوقعة على الصورة، وتُحفظ النتيجة على أنها <strong>output.jpg</strong>.</li>
</ul>
</li>
<li>أعد الوحدة الطرفية المتكاملة للمجلد <strong>test-detector</strong>، وأدخل الأمر التالي لتشغيل البرنامج:</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto"><div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet run
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet run" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div><div dir="auto">
    
      
    

      
    

    
  </div></div>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto"><div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python test-detector.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python test-detector.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div><div dir="auto">
    
      
    

      
    

    
  </div></div>
<ol start="6" dir="auto">
<li>بعد اكتمال البرنامج، اعرض ملف <strong>output.jpg</strong> الناتج للاطلاع على العناصر المكتشفة في الصورة.</li>
</ol>
<div dir="auto"><div class="markdown-heading" dir="auto"><h2 tabindex="-1" dir="auto" class="heading-element">مزيد من المعلومات</h2><a id="user-content-مزيد-من-المعلومات" class="anchor" aria-label="Permalink: مزيد من المعلومات" href="#مزيد-من-المعلومات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div><a id="user-content-مزيد-من-المعلومات" aria-label="Permalink: مزيد من المعلومات" href="#مزيد-من-المعلومات"></a></div>
<p dir="auto">لمزيد من المعلومات حول الكشف عن العناصر باستخدام خدمة Custom Vision، راجع وثائق <a href="https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/" rel="nofollow">Custom Vision</a>.</p>
</div></div>
</article></div>
