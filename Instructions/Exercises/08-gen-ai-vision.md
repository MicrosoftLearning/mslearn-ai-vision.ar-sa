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
  <th>description</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="auto">تطوير تطبيق دردشة يدعم الرؤية</div></td>
  <td><div dir="auto">تعرّف على كيفية استخدام Azure AI Foundry لبناء تطبيق ذكاء اصطناعي توليدي يدعم إدخال الصور.</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">تطوير تطبيق دردشة يدعم الرؤية</h1><a id="user-content-تطوير-تطبيق-دردشة-يدعم-الرؤية" class="anchor" aria-label="Permalink: تطوير تطبيق دردشة يدعم الرؤية" href="#تطوير-تطبيق-دردشة-يدعم-الرؤية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">في هذا التمرين، يمكنك استخدام نموذج الذكاء الاصطناعي التوليدي <em>Phi-4-multimodal-instruct</em> لتوليد ردود للمطالبات التي تتضمن صورًا. ستطوّر تطبيقًا يقدّم مساعدات ذكاء اصطناعي تتعلق بالمنتجات الطازجة في متجر بقالة باستخدام Azure AI Foundry وخدمة استدلال نماذج Azure AI.</p>
<p dir="auto">سيستغرق هذا التدريب حوالي <strong>30</strong> دقيقة.</p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إنشاء مشروع في مصنع الذكاء الاصطناعي في Azure</h2><a id="user-content-إنشاء-مشروع-في-مصنع-الذكاء-الاصطناعي-في-azure" class="anchor" aria-label="Permalink: إنشاء مشروع في مصنع الذكاء الاصطناعي في Azure" href="#إنشاء-مشروع-في-مصنع-الذكاء-الاصطناعي-في-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">دعنا نبدأ بإنشاء مشروع في مصنع الذكاء الاصطناعي في Azure.</p>
<ol dir="rtl">
<li>
<p dir="auto">في متصفح الويب، افتح <a href="https://ai.azure.com" rel="nofollow">مدخل Azure AI Foundry</a> على <code>https://ai.azure.com</code> وسجّل الدخول باستخدام بيانات اعتماد Azure الخاصة بك. أغلق أية تلميحات أو أجزاء تشغيل سريع يتم فتحها عندما تقوم بتسجيل الدخول، وإذا لزم الأمر، استخدم شعار <strong>مصنع الذكاء الاصطناعي في Azure</strong> في أعلى اليسار للانتقال إلى الصفحة الرئيسية، والتي تبدو مشابهة للصورة التالية:</p>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/ai-foundry-home.png"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/ai-foundry-home.png" alt="لقطة شاشة لمدخل Azure AI Foundry." style="max-width: 100%;"></a></p>
</li>
<li>
<p dir="auto">في الصفحة الرئيسية، حدد <strong>+ إنشاء مشروع</strong>.</p>
</li>
<li>
<p dir="auto">في معالج** إنشاء مشروع**، أدخل اسمًا مناسبًا لمشروعك وإذا تم اقتراح مركز موجود، فحدد خيار إنشاء مركز جديد. ثم راجع موارد Azure التي سيتم إنشاؤها تلقائيًا لدعم مركزك ومشروعك.</p>
</li>
<li>
<p dir="auto">حدد <strong>تخصيص</strong> وحدد الإعدادات التالية لمركزك:</p>
<ul dir="rtl">
<li><strong>اسم المركز</strong>: <em>اسم صالح لمركزك</em></li>
<li><strong>Subscription</strong>: <em>اشتراكك في Azure</em></li>
<li><strong>Resource group</strong>: <em>إنشاء مجموعة موارد أو تحديدها</em></li>
<li><strong>الموقع</strong>: حدد أيًا من المناطق التالية*:
<ul dir="rtl">
<li>شرق الولايات المتحدة</li>
<li>East US 2</li>
<li>وسط شمال الولايات المتحدة</li>
<li>South Central US</li>
<li>منطقة السويد الوسطى</li>
<li>غرب الولايات المتحدة</li>
<li>غرب الولايات المتحدة الأمريكية 3</li>
</ul>
</li>
<li><strong>توصيل خدمات Azure AI أو Azure OpenAI</strong>: <em>إنشاء مورد جديد لخدمات الذكاء الاصطناعي</em></li>
<li><strong>الاتصال بـ Azure AI Search</strong>: تخطي الاتصال</li>
</ul>
<blockquote>
<p dir="auto">* في وقت كتابة هذا الدليل، يتوفر نموذج Microsoft <em>Phi-4-multimodal-instruct</em> الذي سنستخدمه في هذا التمرين في هذه المناطق. يمكنك التحقق من أحدث توفر إقليمي لنماذج معينة في <a href="https://learn.microsoft.com/azure/ai-foundry/how-to/deploy-models-serverless-availability#region-availability" rel="nofollow">وثائق Azure AI Foundry</a>. في حال تم الوصول إلى الحد الأقصى للحصة الإقليمية لاحقًا في التمرين، قد تحتاج إلى إنشاء مورد آخر في منطقة مختلفة.</p>
</blockquote>
</li>
<li>
<p dir="auto">حدد <strong>التالي</strong> لمراجعة التكوين الخاص بك. ثم حدد <strong>إنشاء</strong> وانتظر حتى تكتمل العملية.</p>
</li>
<li>
<p dir="auto">عند إنشاء مشروعك، أغلق أي تلميحات يتم عرضها وراجع صفحة المشروع في مدخل مصنع الذكاء الاصطناعي في Azure، والذي يجب أن يبدو مشابهة للصورة التالية:</p>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/ai-foundry-project.png"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/ai-foundry-project.png" alt="لقطة شاشة توضح تفاصيل مشروع ذكاء اصطناعي في Azure في مدخل مصنع الذكاء الاصطناعي في Azure." style="max-width: 100%;"></a></p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">توزيع نموذج متعدد الوسائط</h2><a id="user-content-توزيع-نموذج-متعدد-الوسائط" class="anchor" aria-label="Permalink: توزيع نموذج متعدد الوسائط" href="#توزيع-نموذج-متعدد-الوسائط"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">أنت الآن جاهز لتوزيع نموذج متعدد الوسائط يمكنه دعم الإدخال المستند إلى الصور. هناك العديد من النماذج التي يمكنك الاختيار من بينها، بما في ذلك نموذج OpenAI <em>gpt-4o</em>. في هذا التمرين، سنستخدم نموذج <em>Phi-4-multimodal-instruct</em> الذي يدعم المطالبات التي تتضمن صورًا.</p>
<ol dir="rtl">
<li>في شريط الأدوات الموجود في أعلى يمين من صفحة مشروع مصنع الذكاء الاصطناعي في Azure، استخدم أيقونة** ميزات المعاينة**(<strong>⏿</strong>) للتأكد من تمكين ميزة <strong>نشر النماذج في خدمة استنتاج نموذج Azure AI</strong>. تضمن هذه الميزة توفّر توزيع النموذج الخاص بك لخدمة الاستدلال بالذكاء الاصطناعي في Azure، والتي ستستخدمها في كود التطبيق الخاص بك.</li>
<li>في الجزء الموجود على يسار مشروعك، في قسم <strong>أصولي</strong>، حدد صفحة <strong>النماذج + نقاط النهاية</strong>.</li>
<li>في صفحة <strong>النماذج + نقاط النهاية</strong>، في علامة التبويب <strong>عمليات توزيع النماذج</strong>، في القائمة <strong>+ نشر النموذج</strong>، حدّد <strong>توزيع النموذج الأساسي</strong>.</li>
<li>ابحث عن نموذج <strong>Phi-4-multimodal-instruct</strong> في القائمة، ثم حدده وأكّده.</li>
<li>وافق على اتفاقية الترخيص إذا طلب منك ذلك، ثم وزّع النموذج بالإعدادات التالية عن طريق تحديد <strong>تخصيص</strong> في تفاصيل التوزيع:
<ul dir="rtl">
<li><strong>اسم التوزيع</strong>: <em>اسم صالح توزيع نموذجك</em></li>
<li><strong>نوع النشر</strong>: معيار عالمي</li>
<li><strong>تفاصيل التوزيع</strong>: <em>استخدام الإعدادات الافتراضية</em></li>
</ul>
</li>
<li>انتظر حتى تصبح حالة التزويد للتوزيع <strong>مكتملة</strong>.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">اختبر النموذج في مساحة التجربة</h2><a id="user-content-اختبر-النموذج-في-مساحة-التجربة" class="anchor" aria-label="Permalink: اختبر النموذج في مساحة التجربة" href="#اختبر-النموذج-في-مساحة-التجربة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن أصبح لديك توزيع نموذج متعدد الوسائط، يمكنك اختباره باستخدام مطالبة قائمة على الصورة في بيئة الدردشة.</p>
<ol dir="rtl">
<li>
<p dir="auto">في جزء التنقل على اليسار، حدد صفحة <strong>مساحات التجربة</strong> وافتح مساحة تجربة <strong>الدردشة</strong></p>
</li>
<li>
<ol dir="rtl">
<li>في علامة تبويب المتصفح الجديدة، نزّل الملف <a href="https://github.com/MicrosoftLearning/mslearn-ai-vision/raw/refs/heads/main/Labfiles/08-gen-ai-vision/mango.jpeg">mango.jpeg</a> من <code>https://github.com/MicrosoftLearning/mslearn-ai-vision/raw/refs/heads/main/Labfiles/08-gen-ai-vision/mango.jpeg</code> واحفظه في مجلد على نظام الملفات المحلي لديك.</li>
</ol>
</li>
<li>
<p dir="auto">في صفحة بيئة الدردشة، في جزء <strong>الإعداد</strong>، تأكد من تحديد توزيع نموذج <strong>Phi-4-multimodal-instruct</strong> الخاص بك.</p>
</li>
<li>
<p dir="auto">في لوحة جلسة الدردشة الرئيسية، أسفل مربع إدخال الدردشة، استخدم زر الإرفاق (<strong>📎</strong>) لتحميل ملف الصورة <em>mango.jpeg</em>، ثم أضف النص <code>What desserts could I make with this fruit?</code> وأرسل المطالبة.</p>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/chat-playground-image.png"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/chat-playground-image.png" alt="لقطة شاشة لبيئة الدردشة مع مطالبة قائمة على صورة." style="max-width: 100%;"></a></p>
</li>
<li>
<p dir="auto">راجع الرد، والذي من المفترض أن يوفر لك إرشادات ذات صلة بالحلويات التي يمكنك صنعها باستخدام المانجو.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">أنشئ تطبيق عميل</h2><a id="user-content-أنشئ-تطبيق-عميل" class="anchor" aria-label="Permalink: أنشئ تطبيق عميل" href="#أنشئ-تطبيق-عميل"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن نشرت النموذج، يمكنك استخدام النشر في تطبيق عميل.</p>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: يمكنك اختيار تطوير الحل باستخدام لغة Python أو Microsoft #C <em>(قريبًا)</em>. اتبع الإرشادات في القسم المناسب للغة التي اخترتها.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">إعداد تكوين التطبيق</h3><a id="user-content-إعداد-تكوين-التطبيق" class="anchor" aria-label="Permalink: إعداد تكوين التطبيق" href="#إعداد-تكوين-التطبيق"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="auto">في مدخل مصنع الذكاء الاصطناعي في Azure، اعرض صفحة <strong>النظرة العامة</strong> لمشروعك.</p>
</li>
<li>
<p dir="auto">في منطقة <strong>تفاصيل المشروع</strong>، لاحظ <strong>سلسلة الاتصال للمشروع</strong>. ستستخدم سلسلة الاتصال هذه للاتصال بمشروعك في تطبيق العميل.</p>
</li>
<li>
<p dir="auto">افتح علامة تبويب جديدة للمتصفح (مع إبقاء مدخل مصنع الذكاء الاصطناعي في Azure مفتوحًا في علامة التبويب الموجودة). بعد ذلك في علامة التبويب الجديدة، انتقل إلى <a href="https://portal.azure.com" rel="nofollow">بوابة Azure</a> على <code>https://portal.azure.com</code>؛ وسجّل الدخول باستخدام بيانات اعتماد Azure الخاصة بك إذا طُلب منك ذلك.</p>
<p dir="auto">أغلق أي إشعارات ترحيبية لرؤية الصفحة الرئيسية لبوابة Azure.</p>
</li>
<li>
<p dir="auto">استخدم الزر <strong>[&gt;_]</strong> الموجود على يمين شريط البحث أعلى الصفحة لإنشاء Cloud Shell جديد في بوابة Azure، وتحديد بيئة <em><strong>PowerShell</strong></em> بدون مساحة تخزين في اشتراكك.</p>
<p dir="auto">يوفّر Cloud Shell واجهة سطر الأوامر في الجزء الموجود في أسفل بوابة Azure. يمكنك تغيير حجم هذا الجزء أو تكبيره لتسهيل العمل فيه.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة <em>معالج Bash</em>، فبدّل إلى <em><strong>PowerShell</strong></em>.</p>
</blockquote>
</li>
<li>
<p dir="auto">في شريط أدوات Cloud Shell، في قائمة <strong>الإعدادات</strong>، حدد <strong>الانتقال إلى الإصدار الكلاسيكي</strong> (هذا مطلوب لاستخدام محرر التعليمات البرمجية).</p>
<p dir="auto"><strong>تأكد من التبديل إلى الإصدار الكلاسيكي من cloud shell قبل المتابعة.</strong></p>
</li>
<li>
<p dir="auto">في جزء Cloud Shell، أدخل الأوامر التالية لاستنساخ مستودع GitHub الذي يحتوي على ملفات التعليمات البرمجية لهذا التمرين (اكتب الأمر أو انسخه إلى الحافظة ثم انقر بزر الماوس الأيمن في سطر الأوامر وقم بلصقه كنص عادي):</p>
</li>
<div div="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>rm -r mslearn-ai-vision -f
git clone https://github.com/MicrosoftLearning/mslearn-ai-vision
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="rm -r mslearn-ai-vision -f
git clone https://github.com/MicrosoftLearning/mslearn-ai-vision" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: عند لصق الأوامر في CloudShell، قد يشغل الإخراج مساحة كبيرة من ذاكرة التخزين المؤقت للشاشة. يمكنك مسح الشاشة عن طريق إدخال الأمر <code>cls</code> لتسهيل التركيز على كل مهمة.</p>
</blockquote>

<li>
<p dir="auto">بعد استنساخ مخزن بيانات خاصة، انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية لتطبيق الدردشة:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>cd mslearn-ai-vision/Labfiles/08-gen-ai-vision/python
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="cd mslearn-ai-vision/Labfiles/08-gen-ai-vision/python" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>cd mslearn-ai-vision/Labfiles/08-gen-ai-vision/c-sharp
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="cd mslearn-ai-vision/Labfiles/08-gen-ai-vision/c-sharp" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">في جزء سطر أوامر Cloud Shell، أدخل الأمر التالي لتثبيت المكتبات التي ستستخدمها:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python -m venv labenv
./labenv/bin/Activate.ps1
pip install python-dotenv azure-identity azure-ai-projects azure-ai-inference
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python -m venv labenv
./labenv/bin/Activate.ps1
pip install python-dotenv azure-identity azure-ai-projects azure-ai-inference" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Azure.Identity
dotnet add package Azure.AI.Inference --version 1.0.0-beta.3
dotnet add package Azure.AI.Projects --version 1.0.0-beta.3
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Azure.Identity
dotnet add package Azure.AI.Inference --version 1.0.0-beta.3
dotnet add package Azure.AI.Projects --version 1.0.0-beta.3" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">أدخل الأمر التالي لتحرير ملف التكوين الذي تم توفيره:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>code .env
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="code .env" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>code appsettings.json
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="code appsettings.json" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto">يتم فتح الملف في محرر التعليمات البرمجية.</p>

<li>
<p dir="auto">في ملف التعليمات البرمجية، استبدل العنصر النائب <strong>your_project_connection_string</strong> بسلسلة الاتصال الخاصة بمشروعك (المنسوخة من صفحة <strong>نظرة عامة</strong> على المشروع في بوابة Azure AI Foundry)، واستبدل العنصر النائب <strong>your_model_deployment</strong> بالاسم الذي قمت بتعيينه لتوزيع نموذج Phi-4-multimodal-instruct الخاص بك.</p>
</li>
<li>
<p dir="auto">بعد استبدال العناصر النائبة في محرر التعليمات البرمجية، استخدم الأمر <strong>CTRL+S</strong> أو <strong>انقر زر الماوس الأيمن &gt; حفظ</strong> لحفظ التغييرات ثم استخدم الأمر <strong>CTRL+Q</strong> أو <strong>انقر زر الماوس الأيمن &gt; خروج</strong> لإغلاق محرر التعليمات البرمجية مع إبقاء سطر أوامر Cloud Shell مفتوحًا.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">اكتب التعليمة البرمجية للاتصال بمشروعك والحصول على عميل دردشة لنموذجك</h3><a id="user-content-اكتب-التعليمة-البرمجية-للاتصال-بمشروعك-والحصول-على-عميل-دردشة-لنموذجك" class="anchor" aria-label="Permalink: اكتب التعليمة البرمجية للاتصال بمشروعك والحصول على عميل دردشة لنموذجك" href="#اكتب-التعليمة-البرمجية-للاتصال-بمشروعك-والحصول-على-عميل-دردشة-لنموذجك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: عند إضافة التعليمات البرمجية، تأكد من الحفاظ على المسافة البادئة الصحيحة.</p>
</blockquote>
<ol dir="rtl">
<li>
<p dir="auto">أدخل الأمر التالي لتحرير ملف التعليمات البرمجية الذي تم توفيره:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>code chat-app.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="code chat-app.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>code Program.cs
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="code Program.cs" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">في ملف التعليمات البرمجية، لاحظ العبارات الموجودة في أعلى الملف والتي تمت إضافتها لاستيراد مساحات الأسماء (Namespaces) الضرورية لـ (SDK). بعد ذلك، ابحث عن التعليق <strong>إضافة المراجع</strong>، وأضف التعليمة البرمجية التالية للإشارة إلى المساحات الأساسية في المكتبات التي قمت بتثبيتها مسبقًا:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Add references
from dotenv import load_dotenv
from azure.identity import DefaultAzureCredential
from azure.ai.projects import AIProjectClient
from azure.ai.inference.models import (
    SystemMessage,
    UserMessage,
    TextContentItem,
    ImageContentItem,
    ImageUrl,
)</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Add references
using Azure.Identity;
using Azure.AI.Projects;
using Azure.AI.Inference;</code></pre></div>

<li>
<p dir="auto">في الوظيفة <strong>الرئيسية</strong>، تحت التعليق <strong>الحصول على إعدادات التكوين</strong>، لاحظ أن التعليمة البرمجية تقوم بتحميل قيم سلسلة الاتصال بالمشروع واسم نشر النموذج التي قمت بتحديدها في ملف التكوين.</p>
</li>
<li>
<p dir="auto">ابحث عن التعليق <strong>تهيئة عميل المشروع</strong>، وأضف التعليمة البرمجية التالية للاتصال بمشروع Azure AI Foundry الخاص بك باستخدام بيانات اعتماد Azure التي قمت بتسجيل الدخول بها حاليًا:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Initialize the project client
project_client = AIProjectClient.from_connection_string(
    conn_str=project_connection,
    credential=DefaultAzureCredential())</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Initialize the project client
var projectClient = new AIProjectClient(project_connection,
                    new DefaultAzureCredential());</code></pre></div>

<li>
<p dir="auto">ابحث عن التعليق <strong>الحصول على عميل دردشة</strong>، وأضف التعليمة البرمجية التالية لإنشاء عنصر عميل للدردشة مع النموذج الخاص بك:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get a chat client
chat_client = project_client.inference.get_chat_completions_client(model=model_deployment)</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get a chat client
ChatCompletionsClient chat = projectClient.GetChatCompletionsClient();</code></pre></div>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">اكتب تعليمة برمجية لإرسال مطالبة صورة تعتمد على عنوان URL</h3><a id="user-content-اكتب-تعليمة-برمجية-لإرسال-مطالبة-صورة-تعتمد-على-عنوان-url" class="anchor" aria-label="Permalink: اكتب تعليمة برمجية لإرسال مطالبة صورة تعتمد على عنوان URL" href="#اكتب-تعليمة-برمجية-لإرسال-مطالبة-صورة-تعتمد-على-عنوان-url"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="auto">لاحظ أن التعليمات البرمجية تتضمن تكرار حلقي للسماح للمستخدم بإدخال مطالبة حتى يدخل "إنهاء". بعد ذلك في قسم التكرار، ابحث عن التعليق <strong>الحصول على رد لإدخال الصورة</strong>، وأضف التعلية البرمجية التالية لإرسال مطالبة تتضمن الصورة التالية:</p>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/orange.jpeg"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/orange.jpeg" alt="صورة المانجو." style="max-width: 100%;"></a></p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get a response to image input
image_url = "https://github.com/MicrosoftLearning/mslearn-ai-vision/raw/refs/heads/main/Labfiles/08-gen-ai-vision/orange.jpeg"
image_format = "jpeg"
request = Request(image_url, headers={"User-Agent": "Mozilla/5.0"})
image_data = base64.b64encode(urlopen(request).read()).decode("utf-8")
data_url = f"data:image/{image_format};base64,{image_data}"
<br>
response = chat_client.complete(
    messages=[
        SystemMessage(system_message),
        UserMessage(content=[
            TextContentItem(text=prompt),
            ImageContentItem(image_url=ImageUrl(url=data_url))
        ]),
    ]
)
print(response.choices[0].message.content)</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get a response to image input
string imageUrl = "https://github.com/MicrosoftLearning/mslearn-ai-vision/raw/refs/heads/main/Labfiles/08-gen-ai-vision/orange.jpeg";
ChatCompletionsOptions requestOptions = new ChatCompletionsOptions()
{
    Messages = {
       new ChatRequestSystemMessage(system_message),
       new ChatRequestUserMessage([
            new ChatMessageTextContentItem(prompt),
            new ChatMessageImageContentItem(new Uri(imageUrl))
        ]),
    },
    Model = model_deployment
};
var response = chat.Complete(requestOptions);
Console.WriteLine(response.Value.Content);</code></pre></div>

<li>
<p dir="auto">استخدم الأمر <strong>CTRL+S</strong> لحفظ التغييرات في ملف التعليمات البرمجية، لكن لا تغلقه بعد.</p>
</li>
<li>
<p dir="auto">في جزء سطر أوامر Cloud Shell أسفل محرر التعليمات البرمجية، أدخل الأمر التالي لتشغيل التطبيق:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python chat-app.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python chat-app.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet run
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

<li>
<p dir="auto">عند طلب بذلك، أدخل المطالبة التالية:</p>
</li>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>Suggest some recipes that include this fruit
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="Suggest some recipes that include this fruit" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">راجع الاستجابة. ثم أدخل <code>quit</code> للخروج من البرنامج.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">تعديل التعليمة البرمجية لتحميل ملف صورة محلي</h3><a id="user-content-تعديل-التعليمة-البرمجية-لتحميل-ملف-صورة-محلي" class="anchor" aria-label="Permalink: تعديل التعليمة البرمجية لتحميل ملف صورة محلي" href="#تعديل-التعليمة-البرمجية-لتحميل-ملف-صورة-محلي"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="auto">في محرر التعليمات البرمجية الخاص بكود تطبيقك، في قسم التكرار، ابحث عن التعليمة البرمجية الذي أضفتها مسبقًا ضمن التعليق <strong>الحصول على رد لإدخال الصورة</strong>. ثم عدّل التعليمات البرمجية كما يلي، لتحميل ملف الصورة المحلي هذا:</p>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/mystery-fruit.jpeg"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/mystery-fruit.jpeg" alt="صورة لفاكهة التنين." style="max-width: 100%;"></a></p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get a response to image input
script_dir = Path(__file__).parent  # Get the directory of the script
image_path = script_dir / 'mystery-fruit.jpeg'
mime_type = "image/jpeg"
<br>
# Read and encode the image file
with open(image_path, "rb") as image_file:
    base64_encoded_data = base64.b64encode(image_file.read()).decode('utf-8')
<br>
# Include the image file data in the prompt
data_url = f"data:{mime_type};base64,{base64_encoded_data}"
response = chat_client.complete(
    messages=[
        SystemMessage(system_message),
        UserMessage(content=[
            TextContentItem(text=prompt),
            ImageContentItem(image_url=ImageUrl(url=data_url))
        ]),
    ]
)
print(response.choices[0].message.content)</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get a response to image input
string imagePath = "mystery-fruit.jpeg";
string mimeType = "image/jpeg";
<br>
// Read and encode the image file
byte[] imageBytes = File.ReadAllBytes(imagePath);
var binaryImage = new BinaryData(imageBytes);
<br>
// Include the image file data in the prompt
ChatCompletionsOptions requestOptions = new ChatCompletionsOptions()
{
    Messages = {
        new ChatRequestSystemMessage(system_message),
        new ChatRequestUserMessage([
            new ChatMessageTextContentItem(prompt),
            new ChatMessageImageContentItem(bytes: binaryImage, mimeType: mimeType) 
        ]),
    },
    Model = model_deployment
};
var response = chat.Complete(requestOptions);
Console.WriteLine(response.Value.Content);</code></pre></div>

<li>
<p dir="auto">استخدم الأمر <strong>CTRL+S</strong> لحفظ التغييرات في ملف التعليمات البرمجية. يمكنك أيضًا إغلاق محرر التعليمات البرمجية باستخدام (<strong>CTRL+Q</strong>) إذا رغبت في ذلك.</p>
</li>
<li>
<p dir="auto">في جزء سطر أوامر Cloud Shell أسفل محرر التعليمات البرمجية، أدخل الأمر التالي لتشغيل التطبيق:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python chat-app.py
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python chat-app.py" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet run
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

<li>
<p dir="auto">عند طلب بذلك، أدخل المطالبة التالية:</p>
</li>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>What is this fruit? What recipes could I use it in?
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="What is this fruit? What recipes could I use it in?" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">راجع الاستجابة. ثم أدخل <code>quit</code> للخروج من البرنامج.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: في هذا التطبيق البسيط، لم ننفّذ منطق للاحتفاظ بسجل المحادثة؛ لذلك سيعامل النموذج كل مطالبة على أنها طلب جديد دون أي سياق للمطالبة السابقة.</p>
</blockquote>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">استكشف المزيد: (إذا سمح الوقت)</h2><a id="user-content-استكشف-المزيد-إذا-سمح-الوقت" class="anchor" aria-label="Permalink: استكشف المزيد: (إذا سمح الوقت)" href="#استكشف-المزيد-إذا-سمح-الوقت"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لقد تعلمت كيفية استخدام Azure AI Inference SDK ونموذج متعدد الوسائط لتنفيذ تطبيق الذكاء الاصطناعي التوليدي الذي يمكنه الرد على المطالبات القائمة على الصور. إذا كان لديك الوقت، فإليك بعض الأفكار لمزيد من الاستكشاف.</p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">استخدم نموذجًا متعدد الوسائط مختلفًا</h3><a id="user-content-استخدم-نموذجًا-متعدد-الوسائط-مختلفًا" class="anchor" aria-label="Permalink: استخدم نموذجًا متعدد الوسائط مختلفًا" href="#استخدم-نموذجًا-متعدد-الوسائط-مختلفًا"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لقد استخدمت نموذج <em>Phi-4-multimodal-instruct</em> لتوليد رد لمطالبة قائمة على صورة. الآن دعونا نجرب نموذج OpenAI <em>gpt-4o</em>.</p>
<ol dir="rtl">
<li>في Azure AI Foundry، وزّع نموذج <strong>gpt-4o</strong> إلى نقطة نهاية استدلال نموذج الذكاء الاصطناعي في Azure (قد تحتاج إلى إنشاء مورد جديد في منطقة مختلفة).</li>
<li>حدّث ملف تكوين التعلميات البرمجية الخاصة بتطبيقك (<em>.env</em> لـ Python، و<em>appsettings.json</em> لـ #C) لتحديد اسم نموذج gpt-4o الخاص بك.</li>
<li>شغّل التطبيق كما في السابق، باستخدام نفس المطالبات (يمكنك الرجوع إلى التعليمات البرمجية التي تستخدم صورة تعتمد على عنوان URL إذا شئت).</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">استخدام واجهات برمجة تطبيقات OpenAI</h3><a id="user-content-استخدام-واجهات-برمجة-تطبيقات-openai" class="anchor" aria-label="Permalink: استخدام واجهات برمجة تطبيقات OpenAI" href="#استخدام-واجهات-برمجة-تطبيقات-openai"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">تعتمد التعليمات البرمجية التي استخدمتها في هذا التمرين على Azure AI Inference SDK، والذي يعمل مع أي نموذج تم توزيعه على نقطة نهاية استدلال نموذج الذكاء الاصطناعي في Azure. عند استخدام نموذج OpenAI، يمكنك بدلًا من ذلك استخدام OpenAI SDK.</p>
<p dir="auto">تفترض التعليمات التالية أنك أكملت هذا التمرين والمهمة الإضافية أعلاه لتوزيع نموذج <strong>gpt-4o</strong> واختباره.</p>
<ol dir="rtl">
<li>
<p dir="auto">قم بتثبيت (أو تحديث) الحزم الضرورية لتطبيقك:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python -m venv labenv
./labenv/bin/Activate.ps1
pip install python-dotenv azure-identity azure-ai-projects openai
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python -m venv labenv
./labenv/bin/Activate.ps1
pip install python-dotenv azure-identity azure-ai-projects openai" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>#C</strong></p>
<div dir="auto" class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Azure.Identity
dotnet add package Azure.AI.Projects --prerelease
dotnet add package Azure.AI.OpenAI --prerelease
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Azure.Identity
dotnet add package Azure.AI.Projects --prerelease
dotnet add package Azure.AI.OpenAI --prerelease" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>

<li>
<p dir="auto">حدّث مساحات الأسماء في ملف التعليمات البرمجية الخاص بك (إزالة المراجع <em>azure.ai-inference</em>):</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Add references
from dotenv import load_dotenv
from azure.identity import DefaultAzureCredential
from azure.ai.projects import AIProjectClient
import openai</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Add references
using Azure.Identity;
using Azure.AI.Projects;
using OpenAI.Chat;
using Azure.AI.OpenAI;</code></pre></div>

<li>
<p dir="auto">تعديل التعليمات البرمجية للحصول على عميل دردشة:</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get a chat client
chat_client = project_client.inference.get_azure_openai_client(api_version="2024-10-21")</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get a chat client
ChatClient chatClient = projectClient.GetAzureOpenAIChatClient(model_deployment);</code></pre></div>

<li>
<p dir="auto">تعديل التعليمات البرمجية للحصول على إكمال استنادًا إلى ملف صورة محلي</p>
</li>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get a response to image input
script_dir = Path(__file__).parent  # Get the directory of the script
image_path = script_dir / 'mystery-fruit.jpeg'
mime_type = "image/jpeg"
<br>
# Read and encode the image file
with open(image_path, "rb") as image_file:
    base64_encoded_data = base64.b64encode(image_file.read()).decode('utf-8')
<br>
# Include the image file data in the prompt
data_url = f"data:{mime_type};base64,{base64_encoded_data}"
response = chat_client.chat.completions.create(
    model=model_deployment,
    messages=[
        { "role": "system", "content": system_message },
        { "role": "user", "content": [  
            { 
                "type": "text", 
                "text": prompt 
            },
            { 
                "type": "image_url",
                "image_url": {
                    "url": data_url
                }
            }
        ] } 
    ]
)
completion = response.choices[0].message.content
print(completion)</code></pre></div>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get a response to image input
string imagePath = "mystery-fruit.jpeg";
string mimeType = "image/jpeg";
<br>
// Read and encode the image file
byte[] imageBytes = File.ReadAllBytes(imagePath);
var binaryImage = new BinaryData(imageBytes);
<br>
// Include the image file data in the prompt
List<ChatMessage> messages =
[
    new SystemChatMessage(system_message),
    new UserChatMessage(
        ChatMessageContentPart.CreateTextPart(prompt),
        ChatMessageContentPart.CreateImagePart(binaryImage, mimeType)),
];
<br>
ChatCompletion completion = chatClient.CompleteChat(messages);
Console.WriteLine(completion.Content[0].Text);</code></pre></div>

<li>
<p dir="auto">احفظ تغييراتك وشغّل التطبيق لاختباره بنفس المطالبات التي استخدمتها سابقًا.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تنظيف</h2><a id="user-content-تنظيف" class="anchor" aria-label="Permalink: تنظيف" href="#تنظيف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا كنت قد أنهيت استكشاف Azure AI Foundry، يجب عليك حذف الموارد التي أنشأتها في هذا التمرين لتجنب تكاليف Azure غير الضرورية.</p>
<ol dir="rtl">
<li>ارجع إلى علامة تبويب المتصفح التي تحتوي على بوابة Azure (أو أعد فتح <a href="https://portal.azure.com" rel="nofollow">بوابة Azure</a> في <code>https://portal.azure.com</code> في علامة تبويب متصفح جديدة) واعرض محتويات مجموعة الموارد التي نشرت فيها الموارد المستخدمة في هذا التدريب.</li>
<li>على شريط الأدوات، حدد <strong>حذف مجموعة الموارد</strong>.</li>
<li>أدخل اسم مجموعة الموارد وأكّد أنك تريد حذفها.</li>
</ol>
</article></div></div>
