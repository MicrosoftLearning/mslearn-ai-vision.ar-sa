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
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="auto">تصنيف الصور باستخدام Azure AI Custom Vision</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">تصنيف الصور باستخدام Azure AI Custom Vision</h1><a id="user-content-تصنيف-الصور-باستخدام-azure-ai-custom-vision" class="anchor" aria-label="Permalink: تصنيف الصور باستخدام Azure AI Custom Vision" href="#تصنيف-الصور-باستخدام-azure-ai-custom-vision"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">تمكنك خدمة <strong>Azure AI Custom Vision</strong> من إنشاء نماذج رؤية الكمبيوتر المدربة على صورك الخاصة. يمكنك استخدامه لتدريب <em>تصنيف الصور</em> ونماذج <em>الكشف عن الكائنات</em>؛ والتي يمكنك بعد ذلك نشرها واستهلاكها من التطبيقات.</p>
<p dir="auto">في هذا التمرين، ستستخدم خدمة Custom Vision لتدريب نموذج تصنيف الصور الذي يمكنه اكتشاف ثلاث فئات من الفاكهة (التفاح والموز والبرتقال).</p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">استنساخ المستودع لهذه الدورة التدريبية</h2><a id="user-content-استنساخ-المستودع-لهذه-الدورة-التدريبية" class="anchor" aria-label="Permalink: استنساخ المستودع لهذه الدورة التدريبية" href="#استنساخ-المستودع-لهذه-الدورة-التدريبية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا لم تكن قد استنسخت بالفعل باستنساخ مستودع التعليمات البرمجية <strong>mslearn-ai-vision</strong> في البيئة التي تعمل فيها في هذا التمرين المعملي، فاتبع هذه الخطوات لتنفيذ بذلك. بخلاف ذلك، افتح المجلد المستنسخ في تعليمة Visual Studio البرمجية.</p>
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
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إنشاء موارد الرؤية المخصصة</h2><a id="user-content-إنشاء-موارد-الرؤية-المخصصة" class="anchor" aria-label="Permalink: إنشاء موارد الرؤية المخصصة" href="#إنشاء-موارد-الرؤية-المخصصة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">قبل أن تتمكن من تدريب نموذج، ستحتاج إلى موارد Azure <em>للتدريب</em> و<em>التنبؤ</em>. يمكنك إنشاء موارد <strong>Custom Vision</strong> لكل من هذه المهام، أو يمكنك إنشاء مورد <strong>خدمات Azure AI</strong> واحد واستخدامه إما (أو كليهما).</p>
<p dir="auto">في هذا التمرين، ستقوم بإنشاء موارد <strong>Custom Vision</strong> للتدريب والتنبؤ بحيث يمكنك إدارة الوصول والتكاليف لأحمال العمل هذه بشكل منفصل.</p>
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
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إنشاء مشروع Custom Vision</h2><a id="user-content-إنشاء-مشروع-custom-vision" class="anchor" aria-label="Permalink: إنشاء مشروع Custom Vision" href="#إنشاء-مشروع-custom-vision"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لتدريب نموذج تصنيف الصورة، تحتاج إلى إنشاء مشروع رؤية معدلة بناءً على مورد التدريب الخاص بك. للقيام بذلك، ستستخدم مدخل Custom Vision.</p>
<ol dir="rtl">
<li>في Visual Studio Code، اعرض صور التدريب في مجلد <strong>LabFiles/07-custom-vision-image-classification/training-images</strong> حيث قمت بنسخ المستودع. يحتوي هذا المجلد على مجلدات فرعية من صور التفاح والموز والبرتقال.</li>
<li>في علامة تبويب متصفح أخرى، افتح مدخل Custom Vision على <code>https://customvision.ai</code>. إذا طُلب منك ذلك، قم بتسجيل الدخول باستخدام حساب Microsoft المرتبط باشتراك Azure الخاص بك ووافق على شروط الخدمة.</li>
<li>في مدخل Custom Vision، أنشئ مشروعًا جديدًا بالإعدادات التالية:
<ul dir="rtl">
<li><strong>الاسم</strong>: تصنيف الفاكهة</li>
<li><strong>الوصف</strong>: تصنيف الصورة للفاكهة</li>
<li><strong>المورد</strong>: * مورد Custom Vision الذي أنشأته مسبقًا*</li>
<li><strong>أنواع المشاريع</strong>: التصنيف</li>
<li><strong>أنواع التصنيف</strong>: متعدد الفئات (علامة واحدة لكل صورة)</li>
<li><strong>المَجالات</strong>: الغذاء</li>
</ul>
</li>
<li>في المشروع الجديد، انقر على <strong>[+]إضافة صور</strong>، وحدد جميع الملفات في مجلد <strong>LabFiles/07-custom-vision-image-classification/training-images/apple</strong> الذي قمت بعرضه سابقًا. ثم قم بتحميل ملفات الصور، مع تحديد العلامة <em>تفاحة</em>، على النحو التالي:</li>
</ol>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/upload_apples.jpg"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/upload_apples.jpg" alt="تحميل التفاح مع علامة التفاح" style="max-width: 100%;"></a></p>
<ol start="5" dir="auto">
<li>كرر الخطوة السابقة لتحميل الصور في مجلد <strong>الموز</strong> مع <em>الموز</em>العلامة، والصور في المجلد <strong>البرتقالي</strong> مع علامة <em>البرتقالي</em>.</li>
<li>استكشف الصور التي قمت بتحميلها في مشروع Custom Vision - يجب أن يكون هناك 15 صورة لكل فصل، على النحو التالي:</li>
</ol>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/fruit.jpg"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/fruit.jpg" alt="صور مميزة للفاكهة - 15 تفاحة و 15 موزة و 15 برتقالة" style="max-width: 100%;"></a></p>
<ol start="7" dir="auto">
<li>في مشروع Custom Vision، فوق الصور، انقر فوق <strong>"تدريب"</strong> لتدريب نموذج تصنيف باستخدام الصور ذات العلامات. حدد خيار <strong>"تدريب سريع"</strong>، ثم انتظر حتى يكتمل تكرار التدريب (قد يستغرق ذلك دقيقة أو نحو ذلك).</li>
<li>عند تدريب تكرار النموذج، راجع مقاييس الأداء <em>الدقة**والاستدعاء</em>و<em>AP</em> - تقيس هذه دقة التنبؤ لنموذج التصنيف، ويجب أن تكون جميعها عالية.</li>
</ol>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: تستند مقاييس الأداء إلى حد احتمال 50% لكل تنبؤ (بمعنى آخر، إذا كان النموذج يحسب احتمالاً بنسبة 50% أو أعلى أن تكون الصورة من فئة معينة، فسيتم التنبؤ بهذه الفئة). يمكنك ضبط هذا في أعلى يسار الصفحة.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">اختبار النموذج</h2><a id="user-content-اختبار-النموذج" class="anchor" aria-label="Permalink: اختبار النموذج" href="#اختبار-النموذج"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن دربت النموذج، يمكنك اختباره.</p>
<ol dir="rtl">
<li>فوق مقاييس الأداء، انقر فوق <strong>اختبار سريع</strong>.</li>
<li>في المربع <strong>URL للصورة،</strong> اكتب <code>https://aka.ms/apple-image</code> وانقر فَوق ➔</li>
<li>اعرض التوقعات التي يعرضها نموذجك - يجب أن تكون درجة احتمالية <em>تفاحة</em> أعلى، كما يلي:</li>
</ol>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/test-apple.jpg"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/test-apple.jpg" alt="صورة مَع التنبؤ الطبقي بالتفاح" style="max-width: 100%;"></a></p>
<ol start="4" dir="auto">
<li>أغلق نافذة <strong>اختبار سريع</strong>.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">عرض إعدادات المشروع</h2><a id="user-content-عرض-إعدادات-المشروع" class="anchor" aria-label="Permalink: عرض إعدادات المشروع" href="#عرض-إعدادات-المشروع"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">تم تعيين معرف فريد للمشروع الذي قمت بإنشائه، والذي ستحتاج إلى تحديده في أي تعليمة برمجية تتفاعل معه.</p>
<ol dir="rtl">
<li>انقر فوق أيقونة <em>الإعدادات</em> (⚙) في أعلى يمين صفحة <strong>الأداء</strong> لعرض إعدادات المشروع.</li>
<li>ضمن <strong>عام</strong> (على اليسار)، لاحظ <strong>معرف المشروع</strong> لذي يعرف هذا المشروع بشكل فريد.</li>
<li>على اليمين، ضمن <strong>الموارد</strong> لاحظ أنه يتم عرض المفتاح ونقطة النهاية. هذه هي تفاصيل مورد * التدريب* (يمكنك أيضًا الحصول على هذه المعلومات عن طريق عرض المورد في مدخل Microsoft Azure).</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">استخدام واجهة برمجة تطبيقات <em>التدريب</em></h2><a id="user-content-استخدام-واجهة-برمجة-تطبيقات-التدريب" class="anchor" aria-label="Permalink: استخدام واجهة برمجة تطبيقات التدريب" href="#استخدام-واجهة-برمجة-تطبيقات-التدريب"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">يوفر مدخل Custom Vision واجهة مستخدم ملائمة يمكنك استخدامها لتحميل الصور ووضع علامات عليها وتدريب النماذج. ومع ذلك، في بعض السيناريوهات قد ترغب في أتمتة تدريب النموذج باستخدام واجهة برمجة تطبيقات تدريب Custom Vision.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: في هذا التمرين، يمكنك اختيار استخدام واجهة برمجة التطبيقات إما من <strong>#C</strong> أو <strong>Python</strong> SDK. في الخطوات الواردة أدناه، نفذ الإجراءات المناسبة للغتك المفضلة.</p>
</blockquote>
<ol dir="rtl">
<li>في Visual Studio Code، في جزء <strong>Explorer</strong>، انتقِل إلى المجلد <strong>07-custom-vision-image-classification</strong> وقم بتوسيع المجلد <strong>CSharp</strong> أو <strong>Python</strong> حسب تفضيل اللغة لديك.</li>
<li>انقر بزر الماوس الأيمن فوق مجلد <strong>train-classifier</strong> وافتح وحدة طرفية متكاملة. ثم قم بتثبيت حزمة تدريب Custom Vision عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Microsoft.Azure.CognitiveServices.Vision.CustomVision.Training --version 2.0.0
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Microsoft.Azure.CognitiveServices.Vision.CustomVision.Training --version 2.0.0" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>Python</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>pip install azure-cognitiveservices-vision-customvision==3.1.0
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="pip install azure-cognitiveservices-vision-customvision==3.1.0" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<ol start="3" dir="auto">
<li>
<p dir="auto">اعرض محتويات مجلد <strong>train-classifier</strong>، ولاحظ أنه يحتوي على ملف لإعدادات التكوين:</p>
<ul dir="rtl">
<li><strong>C#</strong>: appsettings.json</li>
<li><strong>Python</strong>: .env</li>
</ul>
<p dir="auto">افتح ملف التكوين وقم بتحديث قيم التكوين التي يحتوي عليها لتعكس نقطة النهاية والمفتاح لمورد <em>تدريب</em> Custom Vision لديك ومعرّف المشروع لمشروع التصنيف الذي قمت بإنشائه مسبقًا. احفظ تغييراتك.</p>
</li>
<li>
<p dir="auto">لاحظ أن مجلد <strong>train-classifier</strong> يحتوي على ملف تعليمات برمجية لتطبيق العميل:</p>
<ul dir="rtl">
<li><strong>C#</strong>: Program.cs</li>
<li><strong>Python</strong>: train-classifier.py</li>
</ul>
<p dir="auto">افتح ملف التعليمات البرمجية وراجع التعليمات البرمجية التي يحتوي عليها، مع ملاحظة التفاصيل التالية:</p>
<ul dir="rtl">
<li>يتم استيراد مساحات الأسماء من الحزمة التي قمت بتثبيتها</li>
<li>تسترد الدالة <strong>Main</strong> إعدادات التكوين، وتستخدم المفتاح ونقطة النهاية لإنشاء <strong>CustomVisionTrainingClient</strong> مصدق عليه، والذي يتم استخدامه بعد ذلك مع معرف المشروع لإنشاء مرجع <strong>مشروع</strong> إلى مشروعك.</li>
<li>تسترد الدالة <strong>Upload_Images</strong> العلامات المعرفة في مشروع Custom Vision ثم تقوم بتحميل ملفات الصور من المجلدات المسماة المقابلة إلى المشروع، مع تعيين معرف العلامة المناسب.</li>
<li>تنشئ الدالة <strong>Train_Model</strong> تكراراً تدريبياً جديداً للمشروع وتنتظر اكتمال التدريب.</li>
</ul>
</li>
<li>
<p dir="auto">أعد الوحدة الطرفية المتكاملة للمجلد <strong>train-classifier</strong>، وأدخل الأمر التالي لتشغيل البرنامج:</p>
</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet run
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet run" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>Python</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python train-classifier.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python train-classifier.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<ol start="6" dir="auto">
<li>انتظر حتى ينتهي البرنامج. ثم ارجع إلى المستعرض الخاص بك واعرض صفحة <strong>صور التدريب</strong> لمشروعك في مدخل Custom Vision (قم بتحديث المتصفح إذا لزم الأمر).</li>
<li>تحقق من إضافة بعض الصور ذات العلامات الجديدة إلى المشروع. ثم اعرض صفحة <strong>الأداء</strong> وتحقق من إنشاء تكرار جديد.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">نَشر نموذج تصنيف الصور</h2><a id="user-content-نَشر-نموذج-تصنيف-الصور" class="anchor" aria-label="Permalink: نَشر نموذج تصنيف الصور" href="#نَشر-نموذج-تصنيف-الصور"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">أنت الآن جاهز لنشر نموذجك المدرّب بحيث يمكن استخدامه من تطبيق عميل.</p>
<ol dir="rtl">
<li>في مدخل Custom Vision، في صفحة <strong>الأداء</strong>، انقر فوق <strong>🗸 نشر</strong> لنشر النموذج المُدرب بالإعدادات التالية:
<ul dir="rtl">
<li><strong>اسم النموذج</strong>: مصنف الفاكهة</li>
<li><strong>مورد التنبؤ</strong>: <em>مورد <strong>التنبؤ</strong> الذي أنشأته سابقًا والذي ينتهي بـ "-Prediction" (ليس هو مورد التدريب)</em>.</li>
</ul>
</li>
<li>في الجزء العلوي الأيسر من صفحة <strong>إعدادات المشروع</strong>، انقر فوق أيقونة <em>معرض المشاريع</em> (👁) للعودة إلى الصفحة الرئيسية لمدخل Custom Vision، حيث يتم إدراج مشروعك الآن.</li>
<li>في الصفحة الرئيسية لمدخل Custom Vision، في أعلى اليمين، انقر فوق أيقونة *الإعدادات * (⚙) لعرض إعدادات خدمة Custom Vision الخاصة بك. ثم، ضمن <strong>الموارد</strong>، ابحث عن مورد * التنبؤ *الذي ينتهي بـ "-Prediction" (وليس مورد التدريب) لتحديد قيم ** المفتاح **** ونقطة النهاية الخاصة به **(يمكنك أيضًا الحصول على هذه المعلومات عن طريق عرض المورد في مدخل Microsoft Azure).</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">استخدام مصنف الصور من تطبيق عميل</h2><a id="user-content-استخدام-مصنف-الصور-من-تطبيق-عميل" class="anchor" aria-label="Permalink: استخدام مصنف الصور من تطبيق عميل" href="#استخدام-مصنف-الصور-من-تطبيق-عميل"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن قمت بنشر نموذج تصنيف الصور، يمكنك استخدامه من تطبيق عميل. مرة أخرى، يمكنك اختيار استخدام <strong>#C</strong> أو <strong>Python</strong>.</p>
<ol dir="rtl">
<li>في Visual Studio Code، في المجلد <strong>07-custom-vision-image-classification</strong>، في المجلد الفرعي للغة المفضلة لديك (<strong>C-Sharp</strong> أو <strong>Python</strong>)، إلى اليمين- المجلد <strong>test-classifier</strong> وافتح وحدة طرفية متكاملة. ثم أدخل الأمر التالي الخاص بـ SDK لتثبيت حزمة تنبؤ Custom Vision:</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Microsoft.Azure.CognitiveServices.Vision.CustomVision.Prediction --version 2.0.0
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Microsoft.Azure.CognitiveServices.Vision.CustomVision.Prediction --version 2.0.0" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>Python</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>pip install azure-cognitiveservices-vision-customvision==3.1.0
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="pip install azure-cognitiveservices-vision-customvision==3.1.0" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: تتضمن حزمة Python SDK كلا من حزم التدريب والتنبؤ، وقد تكون مثبتة بالفعل.</p>
</blockquote>
<ol start="2" dir="auto">
<li>قم بتوسيع مجلد <strong>test-classifier</strong> لعرض الملفات التي يحتوي عليها، والتي تستخدم لتنفيذ تطبيق عميل اختبار لنموذج تصنيف الصور.</li>
<li>افتح ملف التكوين لتطبيق العميل الخاص بك (<em>appsettings.json</em> لـ #C أو <em>.env</em> لـ Python) وقم بتحديث قيم التكوين التي يحتوي عليها لتعكس نقطة النهاية والمفتاح لمورد <em>توقع</em> Custom Vision ومعرف المشروع لمشروع التصنيف واسم النموذج المنشور (الذي يجب أن يكون <em>fruit-detector</em>). احفظ تغييراتك.</li>
<li>افتح ملف التعليمات البرمجية لتطبيق العميل الخاص بك (<em>Program.cs</em> لـ #C، <em>test-classification.py</em> لـ Python) وراجع التعليمات البرمجية التي يحتوي عليها، مع ملاحظة التفاصيل التالية:
<ul dir="rtl">
<li>يتم استيراد مساحات الأسماء من الحزمة التي قمت بتثبيتها</li>
<li>تسترد الدالة ** Main** إعدادات التكوين، وتستخدم المفتاح ونقطة النهاية لإنشاء <strong>CustomVisionPredictionClient</strong> مصدّق عليه.</li>
<li>يتم استخدام كائن عميل التنبؤ للتنبؤ بفئة لكل صورة في مجلد <strong>test-images</strong>، مع تحديد معرف المشروع واسم النموذج لكل طلب. يتضمن كل توقع احتمالاً لكل فئة ممكنة، ويتم عرض العلامات المتوقعة التي تحتوي على احتمال أكبر من 50% فقط.</li>
</ul>
</li>
<li>أعد الوحدة الطرفية المتكاملة للمجلد <strong>test-classifier</strong>، وأدخل الأمر الخاص بـ SDK التالي لتشغيل البرنامج:</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet run
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet run" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>Python</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python test-classifier.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python test-classifier.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<ol start="6" dir="auto">
<li>عرض التسمية (العلامة) ودرجات الاحتمال لكل تنبؤ. يمكنك عرض الصور في مجلد <strong>test-images</strong> للتحقق من أن النموذج قد صنفها بشكل صحيح.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">مزيد من المعلومات</h2><a id="user-content-مزيد-من-المعلومات" class="anchor" aria-label="Permalink: مزيد من المعلومات" href="#مزيد-من-المعلومات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لمزيد من المعلومات حول تصنيف الصور باستخدام خدمة Custom Vision، راجع <a href="https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/" rel="nofollow">وثائق Custom Vision</a>.</p>
</article></div></div>
