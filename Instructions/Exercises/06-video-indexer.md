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
  <td><div dir="auto">تحليل الفيديو باستخدام فهرس الفيديو</div></td>
  <td><div dir="auto">Module 8 - Getting Started with Azure AI Vision</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">تحليل الفيديو باستخدام فهرس الفيديو</h1><a id="user-content-تحليل-الفيديو-باستخدام-فهرس-الفيديو" class="anchor" aria-label="Permalink: تحليل الفيديو باستخدام فهرس الفيديو" href="#تحليل-الفيديو-باستخدام-فهرس-الفيديو"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">توجد نسبة كبيرة من البيانات التي جرى إنشاؤها واستهلاكها اليوم بتنسيق الفيديو. <strong>فهرس فيديو الذكاء الاصطناعي في Azure</strong> هي خدمة تعمل الذكاء الاصطناعي يمكنك استخدامها لفهرسة مقاطع الفيديو واستخراج نتائج التحليلات منها.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: بداية من 21 يونيو 2022، تقتصر قدرات خدمات الذكاء الاصطناعي في Azure التي ترجع معلومات التعريف الشخصية المقيدة على العملاء الذين حصلوا على <a href="https://docs.microsoft.com/azure/cognitive-services/cognitive-services-limited-access" rel="nofollow">حق وصول محدود</a>. دون الحصول على موافقة وصول محدودة، لا يتوفر التعرّف على الأشخاص والمشاهير باستخدام فهرس الفيديو لهذا المختبر. لمزيد من التفاصيل حول التغييرات التي أجرتها Microsoft، ولماذا - راجع <a href="https://azure.microsoft.com/blog/responsible-ai-investments-and-safeguards-for-facial-recognition/" rel="nofollow">استثمارات الذكاء الاصطناعي المسؤول وضماناته للتعرّف على الوجوه</a>.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">استنساخ المستودع لهذه الدورة التدريبية</h2><a id="user-content-استنساخ-المستودع-لهذه-الدورة-التدريبية" class="anchor" aria-label="Permalink: استنساخ المستودع لهذه الدورة التدريبية" href="#استنساخ-المستودع-لهذه-الدورة-التدريبية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا استنسخت مؤخراً مستودع التعليمات البرمجية <strong>mslearn-ai-vision</strong> إلى البيئة التي تعمل فيها في هذا التمرين المعملي، فافتحه في تعليمة Visual Studio البرمجية؛ بخلاف ذلك، اتبع هذه الخطوات لاستنساخها الآن.</p>
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
<p dir="auto">انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: في حالة مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد <strong>ليس الآن</strong>.</p>
</blockquote>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تحميل فيديو إلى فهرس الفيديو</h2><a id="user-content-تحميل-فيديو-إلى-فهرس-الفيديو" class="anchor" aria-label="Permalink: تحميل فيديو إلى فهرس الفيديو" href="#تحميل-فيديو-إلى-فهرس-الفيديو"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">أولا، ستحتاج إلى تسجيل الدخول إلى مدخل فهرس فيديو وتحميل فيديو.</p>
<blockquote>
<p dir="auto"><strong>تلميح</strong>: ذا كانت صفحة فهرس الفيديو بطيئة التحميل في بيئة المختبر المستضافة، فاستخدم المستعرض المثبت محلياً. يمكنك التبديل مرة أخرى إلى الجهاز الظاهري المستضاف للمهام اللاحقة.</p>
</blockquote>
<ol dir="rtl">
<li>في مستعرضك، افتح مدخل فهرس الفيديو على <code>https://www.videoindexer.ai</code>.</li>
<li>إذا كان لديك حساب فهرس فيديو موجود، فسجل الدخول. وإلا، فسجل للحصول على حساب مجاني وسجل الدخول باستخدام حساب Microsoft الخاص بك (أو أي نوع حساب صالح آخر). إذا واجهت صعوبة في تسجيل الدخول، فحاول فتح جلسة مستعرض خاصة.</li>
<li>في علامة تبويب جديدة، يمكنك تنزيل فيديو الذكاء الاصطناعي المسؤول عن طريق زيارة <code>https://aka.ms/responsible-ai-video</code>. حفظ الملف.</li>
<li>في فهرس الفيديو، حدد خيار <strong>تحميل</strong>. ثم حدد خيار <strong>استعراض بحثاً عن الملفات</strong>، وحدد الفيديو الذي جرى تنزيله، وانقر فوق <strong>إضافة</strong>. غير الاسم الافتراضي إلى <strong>الذكاء الاصطناعي المسؤول</strong>، راجع الإعدادات الافتراضية، وحدد خانة الاختيار للتحقق من التوافق مع نهج Microsoft للتعرّف على الوجه، وتحميل الملف.</li>
<li>بعد تحميل الملف، انتظر بضع دقائق بينما يفهرسه فهرس الفيديو تلقائياً.</li>
</ol>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: في هذا التمرين، نستخدم هذا الفيديو لاستكشاف وظيفة فهرس الفيديو لكن يجب أن تكرس وقتاً لمشاهدته بالكامل عند الانتهاء من التمرين لأنه يحتوي على معلومات وإرشادات مفيدة لتطوير التطبيقات الممكنة الذكاء الاصطناعي بشكل مسؤول!</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">مراجعة نتائج تحليلات الفيديو</h2><a id="user-content-مراجعة-نتائج-تحليلات-الفيديو" class="anchor" aria-label="Permalink: مراجعة نتائج تحليلات الفيديو" href="#مراجعة-نتائج-تحليلات-الفيديو"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">تستخرج عملية الفهرسة نتائج تحليلات من الفيديو يمكنك عرضها في المدخل.</p>
<ol dir="rtl">
<li>
<p dir="auto">في مدخل فهرس الفيديو، عند فهرسة الفيديو، حدده لعرضه. سترى مشغل الفيديو جنباً إلى جنب مع جزء يعرض نتائج التحليلات المستخرجة من الفيديو.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: نظراً لنهج الوصول المحدود لحماية هويات الأفراد، قد لا ترى الأسماء عند فهرس الفيديو.</p>
</blockquote>
</li>
</ol>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/video-indexer-insights.png"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/video-indexer-insights.png" alt="فهرس الفيديو مع مشغل فيديو وجزء Insights" style="max-width: 100%;"></a></p>
<ol start="2" dir="auto">
<li>خلال تشغيل الفيديو، حدد علامة تبويب <strong>المخطط الزمني</strong> لعرض نسخة من صوت الفيديو.</li>
</ol>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/video-indexer-transcript.png"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/video-indexer-transcript.png" alt="فهرس الفيديو مع مشغل فيديو وجزء المخطط الزمني يعرض نص الفيديو." style="max-width: 100%;"></a></p>
<ol start="3" dir="auto">
<li>في الجزء العلوي الأيسر من البوابة الإلكترونية، حدد رمز <strong>العرض</strong> (الذي يشبه 🗇)، وفي قائمة نتائج التحليلات، بالإضافة إلى <strong>النص</strong>، حدد <strong>OCR</strong> <strong>ومكبرات الصوت</strong>.</li>
</ol>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/video-indexer-view-menu.png"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/video-indexer-view-menu.png" alt="قائمة عرض فهرس الفيديو مع تحديد النسخة المكتوبة وOCR والسماعات" style="max-width: 100%;"></a></p>
<ol start="4" dir="rtl">
<li>
<p dir="auto">لاحظ أن جزء <strong>المخطط الزمني</strong> يتضمن الآن:</p>
<ul dir="rtl">
<li>نسخة مكتوبة من السرد الصوتي.</li>
<li>النص المرئي في الفيديو.</li>
<li>مؤشرات السماعات التي تظهر في الفيديو. يجري التعرّف على بعض الأشخاص المشهورين تلقائياً بالاسم، بينما تجري الإشارة إلى البعض الآخر بالرقم (على سبيل المثال <em>المتحدث رقم 1</em>).</li>
</ul>
</li>
<li>
<p dir="auto">بدل مرة أخرى إلى <strong>جزء Insights</strong> واعرض نتائج التحليلات التي تظهر هناك. يشمل ذلك ما يلي:</p>
<ul dir="rtl">
<li>الأفراد الذين يظهرون في الفيديو.</li>
<li>المواضيع التي جرت مناقشتها في الفيديو.</li>
<li>تسميات العناصر التي تظهر في الفيديو.</li>
<li>الكيانات المسماة، مثل الأشخاص والعلامات التجارية التي تظهر في الفيديو.</li>
<li>المشاهد الرئيسية.</li>
</ul>
</li>
<li>
<p dir="auto">مع ظهور جزء <strong>Insights</strong>، حدد رمز <strong>العرض</strong> مرة أخرى، وفي قائمة نتائج التحليلات أضف <strong>الكلمات الأساسية</strong> <strong>والتوجهات</strong> إلى الجزء.</p>
<p dir="auto">يمكن أن تساعدك نتائج التحليلات التي جرى العثور عليها في تحديد النُسق الرئيسية في الفيديو. على سبيل المثال، توضح <strong>موضوعات</strong> هذا الفيديو أنه يتعلق بوضوح بالتكنولوجيا والمسؤولية الاجتماعية والأخلاق.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">البحث عن نتائج التحليلات</h2><a id="user-content-البحث-عن-نتائج-التحليلات" class="anchor" aria-label="Permalink: البحث عن نتائج التحليلات" href="#البحث-عن-نتائج-التحليلات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">يمكنك استخدام فهرس الفيديو للبحث في الفيديو عن نتائج التحليلات.</p>
<ol dir="rtl">
<li>في جزء <strong>Insights</strong>، في مربع <strong>البحث</strong>، أدخل <em>نحلة</em>. قد تحتاج إلى التمرير لأسفل في جزء Insights لمشاهدة النتائج لجميع أنواع نتائج التحليلات.</li>
<li>لاحظ أنه جرى العثور على <em>علامة</em> مطابقة واحدة، مع الإشارة إلى موقعها في الفيديو أدناه.</li>
<li>حدد بداية القسم الذي يُشار فيه إلى وجود نحلة، وشاهد الفيديو عند هذه النقطة (قد تحتاج إلى إيقاف الفيديو مؤقتاً والاختيار بعناية - تظهر النحلة لفترة وجيزة فقط!)</li>
<li>يمكنك إلغاء تحديد مربع <strong>البحث</strong> لإظهار كافة نتائج التحليلات الخاصة بالفيديو.</li>
</ol>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/video-indexer-search.png"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/video-indexer-search.png" alt="نتائج بحث فهرس الفيديو عن نحلة" style="max-width: 100%;"></a></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">استخدام عناصر واجهة مستخدم فهرس الفيديو</h2><a id="user-content-استخدام-عناصر-واجهة-مستخدم-فهرس-الفيديو" class="anchor" aria-label="Permalink: استخدام عناصر واجهة مستخدم فهرس الفيديو" href="#استخدام-عناصر-واجهة-مستخدم-فهرس-الفيديو"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">مدخل فهرس الفيديو هو واجهة مفيدة لإدارة مشاريع فهرسة الفيديو. مع ذلك، قد تكون هناك مناسبات تريد فيها إتاحة الفيديو ونتائج تحليلاته للأشخاص الذين ليس لديهم حق الوصول إلى حساب فهرس الفيديو الخاص بك. يوفر فهرس الفيديو عناصر واجهة المستخدم التي يمكنك تضمينها في صفحة ويب لهذا الغرض.</p>
<ol dir="rtl">
<li>في تعليمة Visual Studio البرمجية في المجلد <strong>06-video-indexer</strong> افتح <strong>Analysis-video.html</strong>. هذه صفحة HTML أساسية ستضيف إليها أدوات <strong>مشغل</strong> فهرس الفيديو <strong>وInsights</strong>. لاحظ الإشارة إلى البرنامج النصي <strong>vb.widgets.mediator.js</strong> في الرأس - يتيح هذا البرنامج النصي لعناصر واجهة مستخدم فهرس الفيديو المتعددة الموجودة على الصفحة التفاعل مع بعضها البعض.</li>
<li>في مدخل فهرس الفيديو، ارجع إلى صفحة <strong>ملفات الوسائط</strong> وافتح فيديو <strong>الذكاء الاصطناعي المسؤول</strong>.</li>
<li>ضمن مشغل الفيديو، حدد <strong>&lt;/&gt; تضمين</strong> لعرض التعليمات البرمجية HTML iframe لتضمين عناصر واجهة المستخدم.</li>
<li>في مربع الحوار <strong>مشاركة وتضمين</strong>، حدد عنصر واجهة المستخدم <strong>Player</strong>، واضبط حجم الفيديو على 560 × 315، ثم انسخ رمز التضمين إلى الحافظة.</li>
<li>في تعليمة Visual Studio البرمجية في ملف <strong>Analysis-video.html</strong>، الصق الكود المنسوخ أسفل التعليق <strong>&lt; -- تظهر أداة المشغل هنا -- &gt;</strong>.</li>
<li>بالعودة إلى مربع حوار <strong>المشاركة والتضمين</strong>، حدد أداة <strong>Insights</strong> ثم انسخ التعليمة البرمجية المراد تضمينها إلى الحافظة. بعد ذلك، أغلق مربع الحوار <strong>مشاركة وتضمين</strong> وبدل مرة أخرى إلى تعليمة Visual Studio البرمجية والصق الكود المنسوخ أسفل التعليق <strong>&lt; -- تظهر أداة Insights هنا -- &gt;</strong>.</li>
<li>حفظ الملف. ثم في جزء <strong>Explorer</strong>، انقر بزر الماوس الأيمن فوق <strong>analyze-video.html</strong> وحدد <strong>الكشف في مستكشف الملفات</strong>.</li>
<li>في مستكشف الملفات، افتح <strong>analyze-video.html</strong> في مستعرضك لرؤية صفحة الويب.</li>
<li>يمكنك تجربة عناصر واجهة المستخدم باستخدام أداة <strong>Insights</strong> للبحث عن نتائج التحليلات والانتقال إليها في الفيديو.</li>
</ol>
<p dir="auto"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/video-indexer-widgets.png"><img src="https://github.com/MicrosoftLearning/mslearn-ai-vision.ar-sa/blob/OLPRODLOC/Instructions/media/video-indexer-widgets.png" alt="عناصر واجهة مستخدم فهرس الفيديو في صفحة ويب" style="max-width: 100%;"></a></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">استخدام واجهة برمجة تطبيقات REST لفهرس الفيديو</h2><a id="user-content-استخدام-واجهة-برمجة-تطبيقات-rest-لفهرس-الفيديو" class="anchor" aria-label="Permalink: استخدام واجهة برمجة تطبيقات REST لفهرس الفيديو" href="#استخدام-واجهة-برمجة-تطبيقات-rest-لفهرس-الفيديو"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">يوفر فهرس الفيديو واجهة برمجة تطبيقات REST التي يمكنك استخدامها لتحميل مقاطع الفيديو وإدارتها في حسابك.</p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">الحصول على تفاصيل واجهة برمجة التطبيقات</h3><a id="user-content-الحصول-على-تفاصيل-واجهة-برمجة-التطبيقات" class="anchor" aria-label="Permalink: الحصول على تفاصيل واجهة برمجة التطبيقات" href="#الحصول-على-تفاصيل-واجهة-برمجة-التطبيقات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لاستخدام واجهة برمجة تطبيقات فهرس الفيديو، تحتاج إلى بعض المعلومات لمصادقة الطلبات:</p>
<ol dir="rtl">
<li>في مدخل فهرس الفيديو، عليك توسيع الجزء الأيمن وحدد صفحة <strong>إعدادات الحساب</strong>.</li>
<li>لاحظ <strong>معرّف</strong> الحساب على هذه الصفحة - ستحتاج إليه لاحقاً.</li>
<li>افتح علامة تبويب مستعرض جديدة وانتقل إلى مدخل مطور فهرس الفيديو في <code>https://api-portal.videoindexer.ai</code>، وسجل الدخول باستخدام بيانات الاعتماد لحساب فهرس الفيديو الخاص بك.</li>
<li>في صفحة <strong>ملف التعريف</strong>، اعرض <strong>الاشتراكات</strong> المقترنة بملف التعريف الخاص بك.</li>
<li>في الصفحة التي تحتوي على اشتراكك (اشتراكاتك)، لاحظ أنه جرى تعيين مفتاحين (أساسي وثانوي) لكل اشتراك. ثم حدد <strong>إظهار</strong> لأي من المفاتيح لمشاهدته. ستحتاج إلى هذا المفتاح قريباً.</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">استخدام واجهة برمجة تطبيقات REST</h3><a id="user-content-استخدام-واجهة-برمجة-تطبيقات-rest" class="anchor" aria-label="Permalink: استخدام واجهة برمجة تطبيقات REST" href="#استخدام-واجهة-برمجة-تطبيقات-rest"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن أصبح لديك معرّف الحساب ومفتاح API، يمكنك استخدام واجهة برمجة تطبيقات REST للعمل مع مقاطع الفيديو في حسابك. في هذا الإجراء، ستستخدم برنامج PowerShell النصي لإجراء مكالمات REST؛ ولكن تنطبق نفس المبادئ مع أدوات HTTP المساعدة مثل cURL أو Postman، أو أي لغة برمجة قادرة على إرسال واستقبال JSON عبر HTTP.</p>
<p dir="auto">تتبع جميع التفاعلات مع Video Indexer REST API النمط نفسه:</p>
<ul dir="rtl">
<li>يجري استخدام طلب أولي لأسلوب <strong>AccessToken</strong> باستخدام مفتاح API في الرأس للحصول على رمز وصول.</li>
<li>تستخدم الطلبات اللاحقة رمز الوصول للمصادقة عند استدعاء أساليب REST للعمل مع مقاطع الفيديو.</li>
</ul>
<ol dir="rtl">
<li>في تعليمة Visual Studio البرمجية في المجلد <strong>06-video-indexer</strong> افتح <strong>get-videos.ps1</strong>.</li>
<li>في البرنامج النصي PowerShell، استبدل العناصر النائبة <strong>YOUR_ACCOUNT_ID</strong>** YOUR_API_KEY **بمعرّف الحساب وقيم مفتاح واجهة برمجة التطبيقات التي حددتها مسبقاً.</li>
<li>لاحظ أن <em>موقع</em> الحساب المجاني "تجريبي". إذا أنشئت حساب فهرس فيديو غير مقيد (مع مورد Azure مرتبط)، فيمكنك تغيير هذا إلى الموقع الذي يجري فيه توفير مورد Azure الخاص بك (على سبيل المثال "eastus").</li>
<li>راجع التعليمة البرمجية الموجودة في البرنامج النصي، مع ملاحظة أنه يستدعي طريقتين REST: واحدة للحصول على رمز وصول، وأخرى لسرد مقاطع الفيديو في حسابك.</li>
<li>احفظ التغييرات، ثم في الجزء العلوي الأيسر من جزء البرنامج النصي، استخدم زر <strong>&amp;#9655؛</strong> لتشغيل البرنامج النصي.</li>
<li>اعرض استجابة JSON من خدمة REST التي يجب أن تحتوي على تفاصيل <strong>فيديو الذكاء الاصطناعي المسؤول</strong> الذي فهرسته مسبقاً.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">مزيد من المعلومات</h2><a id="user-content-مزيد-من-المعلومات" class="anchor" aria-label="Permalink: مزيد من المعلومات" href="#مزيد-من-المعلومات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لا يزال التعرّف على الأشخاص والمشاهير متاحاً، ولكن وفقاً <a href="https://aka.ms/aah91ff" rel="nofollow">لمعيار الذكاء الاصطناعي المسؤول</a>، يجري تقييد هؤلاء الأشخاص بموجب نهج الوصول المحدود. وتشمل هذه الميزات التعرّف على الوجه والتعرّف على المشاهير. لمعرفة المزيد والتقدم للحصول على الوصول، راجع <a href="https://docs.microsoft.com/azure/cognitive-services/cognitive-services-limited-access" rel="nofollow">الوصول المحدود لخدمات الذكاء الاصطناعي في Azure</a>.</p>
<p dir="auto">لمزيد من المعلومات حول <strong>فهرس الفيديو</strong>، راجع وثائق <a href="https://learn.microsoft.com/azure/azure-video-indexer/" rel="nofollow">فهرس الفيديو</a>.</p>
</article></div></div>
