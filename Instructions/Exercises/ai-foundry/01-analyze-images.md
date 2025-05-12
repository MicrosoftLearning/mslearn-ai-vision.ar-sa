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
  <td><div dir="auto">تحليل الصور باستخدام الذكاء الاصطناعي في Azure Vision</div></td>
  <td><div dir="auto">Module 2 - Develop computer vision solutions with Azure AI Vision</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">تحليل الصور باستخدام الذكاء الاصطناعي في Azure Vision</h1><a id="user-content-تحليل-الصور-باستخدام-الذكاء-الاصطناعي-في-azure-vision" class="anchor" aria-label="Permalink: تحليل الصور باستخدام الذكاء الاصطناعي في Azure Vision" href="#تحليل-الصور-باستخدام-الذكاء-الاصطناعي-في-azure-vision"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الذكاء الاصطناعي في Azure Vision عبارة عن قدرة ذكاء اصطناعي تمكن أنظمة البرامج من تفسير المدخلات المرئية من خلال تحليل الصور. في Microsoft Azure، توفر خدمة الذكاء الاصطناعي في Azure <strong>Vision</strong> نماذج معدة مسبقاً لمهام رؤية الكمبيوتر الشائعة، بما في ذلك تحليل الصور لاقتراح التسميات التوضيحية والعلامات، واكتشاف الأشياء والأشخاص الشائعين.</p>
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
<p dir="auto">انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: إذا جرت مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد <strong>ليس الآن</strong>. إذا جرت مطالبتك برسالة <em>اكتشاف مشروع وظيفة Azure في المجلد</em>، يمكنك إغلاق هذه الرسالة بأمان.</p>
</blockquote>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">توفير مورد خدمات الذكاء الاصطناعي في Azure</h2><a id="user-content-توفير-مورد-خدمات-الذكاء-الاصطناعي-في-azure" class="anchor" aria-label="Permalink: توفير مورد خدمات الذكاء الاصطناعي في Azure" href="#توفير-مورد-خدمات-الذكاء-الاصطناعي-في-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا لم يكن لديك بالفعل مورد في اشتراكك، فسيتعين عليك توفير مورد <strong>خدمات الذكاء الاصطناعي في Azure</strong>.</p>
<ol dir="rtl">
<li>
<p dir="auto">افتح مدخل Azure على <code>https://portal.azure.com</code>، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.</p>
</li>
<li>
<p dir="auto">حدد <strong>Create a resource.</strong></p>
</li>
<li>
<p dir="auto">في شريط البحث ابحث عن<em>خدمات الذكاء الاصطناعي في Azure</em>، وحدد <strong>خدمات الذكاء الاصطناعي في Azure</strong>، وأنشئ مورد حساب متعدد الخدمات لخدمات الذكاء الاصطناعي في Azure بالإعدادات التالية:</p>
<ul dir="rtl">
<li><strong>Subscription</strong>: <em>اشتراكك في Azure</em></li>
<li><strong>مجموعة الموارد</strong>: <em>اختر أو أنشئ مجموعة موارد (إذا كنت تستخدم اشتراكاً مقيداً، فقد لا يكون لديك إذن لإنشاء مجموعة موارد جديدة - استخدم المجموعة المتوفرة)</em></li>
<li><strong>المنطقة</strong>: <em>اختر من بين شرق الولايات المتحدة أو غرب الولايات المتحدة أو وسط فرنسا أو وسط كوريا أو شمال أوروبا أو جنوب شرق آسيا أو غرب أوروبا أو شرق آسيا*</em></li>
<li><strong>الاسم</strong>: <em>أدخل اسماً فريداً</em></li>
<li><strong>مستوى التسعير</strong>: قياسي S0</li>
</ul>
<p dir="auto">*تتوفر ميزات الذكاء الاصطناعي في Azure اصدار 4.0 حالياً في هذه المناطق فقط.</p>
</li>
<li>
<p dir="auto">حدد مربعات الاختيار المطلوبة ثم أنشئ المورد.</p>
</li>
<li>
<p dir="auto">انتظر حتى يكتمل النشر، ثم اعرض تفاصيل النشر.</p>
</li>
<li>
<p dir="auto">عند نشر المورد، انتقل إليه واعرض <strong>صفحة المفاتيح ونقطة النهاية</strong> الخاصة به. ستحتاج إلى نقطة النهاية وأحد المفاتيح من هذه الصفحة في الإجراء التالي.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">الاستعداد لاستخدام Azure AI Vision SDK</h2><a id="user-content-الاستعداد-لاستخدام-azure-ai-vision-sdk" class="anchor" aria-label="Permalink: الاستعداد لاستخدام Azure AI Vision SDK" href="#الاستعداد-لاستخدام-azure-ai-vision-sdk"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">في هذا التمرين، ستكمل تطبيق عميل جرى تنفيذه جزئياً يستخدم Azure AI Vision SDK لتحليل الصور.</p>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: يمكنك اختيار استخدام SDK إما لـ <strong>C#</strong> أو <strong>Python</strong>. في الخطوات الواردة أدناه، نفذ الإجراءات المناسبة للغتك المفضلة.</p>
</blockquote>
<ol dir="rtl">
<li>
<p dir="auto">في تعليمة Visual Studio البرمجية في جزء <strong>Explorer</strong>، استعرض للوصول إلى المجلد <strong>Labfiles/01-analyze-images</strong> ووسع المجلد <strong>C-Sharp</strong> أو <strong>Python</strong> وفقاً لتفضيلات اللغة لديك.</p>
</li>
<li>
<p dir="auto">انقر بزر الماوس الأيمن فوق مجلد <strong>image-analysis</strong> وافتح وحدة طرفية متكاملة. ثم عليك تثبيت حزمة Azure AI Vision SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:</p>
</li>
<p dir="rtl"><strong>#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Azure.AI.Vision.ImageAnalysis -v 1.0.0-beta.3
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Azure.AI.Vision.ImageAnalysis -v 1.0.0-beta.3" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: إذا جرت مطالبتك بتثبيت ملحقات مجموعة أدوات التطوير، يمكنك إغلاق الرسالة بأمان.</p>
</blockquote>
<p dir="rtl"><strong>Python</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>pip install azure-ai-vision-imageanalysis==1.0.0b3
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="pip install azure-ai-vision-imageanalysis==1.0.0b3" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<blockquote>
<p dir="auto"><strong>نصيحة</strong>: إذا كنت تقوم بهذا النشاط العملي على جهازك الخاص، فسوف تحتاج أيضًا إلى تثبيت <code>matplotlib</code> و <code>pillow</code>.</p>
</blockquote>

<li>
<p dir="auto">اعرض محتويات مجلد <strong>تحليل الصور</strong>، ولاحظ أنه يحتوي على ملف لإعدادات التكوين:</p>
<ul dir="rtl">
<li><strong>C#</strong>: appsettings.json</li>
<li><strong>Python</strong>: .env</li>
</ul>
<p dir="auto">يمكنك فتح ملف التكوين وتحديث قيم التكوين التي يحتوي عليها لتعكس <strong>نقطة النهاية</strong> و<strong>مفتاح</strong> المصادقة لمورد خدمات الذكاء الاصطناعي في Azure. احفظ تغييراتك.</p>
</li>
<li>
<p dir="auto">لاحظ أن مجلد <strong>تحليل الصور</strong> يحتوي على ملف تعليمات برمجية لتطبيق العميل:</p>
<ul dir="rtl">
<li><strong>C#</strong>: Program.cs</li>
<li><strong>Python</strong>: image-analysis.py</li>
</ul>
<p dir="auto">افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق <strong>استيراد مساحات الأسماء</strong>. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Azure AI Vision SDK:</p>
</li>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Import namespaces
using Azure.AI.Vision.ImageAnalysis;</code></pre></div>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># import namespaces
from azure.ai.vision.imageanalysis import ImageAnalysisClient
from azure.ai.vision.imageanalysis.models import VisualFeatures
from azure.core.credentials import AzureKeyCredential</code></pre></div>

</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">عرض الصور التي ستحللها</h2><a id="user-content-عرض-الصور-التي-ستحللها" class="anchor" aria-label="Permalink: عرض الصور التي ستحللها" href="#عرض-الصور-التي-ستحللها"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">في هذا التمرين، ستستخدم خدمة الذكاء الاصطناعي في Azure Vision لتحليل صور متعددة.</p>
<ol dir="rtl">
<li>في تعليمة Visual Studio البرمجية، وسع مجلد <strong>تحليل الصور</strong> ومجلد <strong>الصور</strong> الذي يحتوي عليه.</li>
<li>حدد كل ملفات الصور تباعاً لعرضها في Visual Studio Code.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تحليل صورة لاقتراح تسمية توضيحية</h2><a id="user-content-تحليل-صورة-لاقتراح-تسمية-توضيحية" class="anchor" aria-label="Permalink: تحليل صورة لاقتراح تسمية توضيحية" href="#تحليل-صورة-لاقتراح-تسمية-توضيحية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">أنت الآن جاهز لاستخدام SDK للاتصال بخدمة Vision وتحليل الصورة.</p>
<ol dir="rtl">
<li>في ملف التعليمات البرمجية لتطبيق العميل الخاص بك (<strong>Program.cs</strong> أو <strong>image-ana Analysis.py</strong>)، في الدالة <strong>الرئيسية</strong>، لاحظ أنه جرى توفير التعليمات البرمجية لتحميل إعدادات التكوين. ثم ابحث عن التعليق <strong>مصادقة عميل الذكاء الاصطناعي في Azure Vision</strong>. ثم، ضمن هذا التعليق، أضف التعليمات البرمجية الخاصة باللغة التالية لإنشاء كائن عميل الذكاء الاصطناعي في Azure Vision ومصادقته:</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Authenticate Azure AI Vision client
ImageAnalysisClient client = new ImageAnalysisClient(
    new Uri(aiSvcEndpoint),
    new AzureKeyCredential(aiSvcKey));</code></pre></div>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Authenticate Azure AI Vision client
cv_client = ImageAnalysisClient(
    endpoint=ai_endpoint,
    credential=AzureKeyCredential(ai_key)
)</code></pre></div>
<ol start="2" dir="rtl">
<li>
<p dir="auto">في الدالة <strong>الرئيسية</strong>، ضمن الرمز الذي أضفته للتو، لاحظ أن الرمز يحدد المسار إلى ملف صورة ثم يمرر مسار الصورة إلى دالتين أخريتين (<strong>AnalyzeImage</strong> <strong>وBackgroundForeground</strong>). هذه الوظائف لم تُنفذ بالكامل بعد.</p>
</li>
<li>
<p dir="auto">في الدالة <strong>AnalyzeImage</strong>، ضمن التعليق <strong>الحصول على نتيجة مع تحديد الميزات المراد استردادها</strong>، أضف الرمز التالي:</p>
</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get result with specified features to be retrieved
ImageAnalysisResult result = client.Analyze(
    BinaryData.FromStream(stream),
    VisualFeatures.Caption | 
    VisualFeatures.DenseCaptions |
    VisualFeatures.Objects |
    VisualFeatures.Tags |
    VisualFeatures.People);</code></pre></div>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get result with specified features to be retrieved
result = cv_client.analyze(
    image_data=image_data,
    visual_features=[
        VisualFeatures.CAPTION,
        VisualFeatures.DENSE_CAPTIONS,
        VisualFeatures.TAGS,
        VisualFeatures.OBJECTS,
        VisualFeatures.PEOPLE],
)</code></pre></div>
<ol start="4" dir="auto">
<li>في الدالة <strong>AnalyzeImage</strong>، ضمن التعليق <strong>عرض نتائج التحليلات</strong>، أضف التعليمات البرمجية التالية (بما في ذلك التعليقات التي تشير إلى المكان الذي ستضيف فيه المزيد من التعليمات البرمجية لاحقاً.):</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Display analysis results
// Get image captions
if (result.Caption.Text != null)
{
    Console.WriteLine(" Caption:");
    Console.WriteLine($"   \"{result.Caption.Text}\", Confidence {result.Caption.Confidence:0.00}\n");
}
<br>
// Get image dense captions
Console.WriteLine(" Dense Captions:");
foreach (DenseCaption denseCaption in result.DenseCaptions.Values)
{
    Console.WriteLine($"   Caption: '{denseCaption.Text}', Confidence: {denseCaption.Confidence:0.00}");
}
<br>
// Get image tags
<br>
<br>
// Get objects in the image
<br>
<br>
// Get people in the image</code></pre></div>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Display analysis results
# Get image captions
if result.caption is not None:
    print("\nCaption:")
    print(" Caption: '{}' (confidence: {:.2f}%)".format(result.caption.text, result.caption.confidence * 100))
<br>
# Get image dense captions
if result.dense_captions is not None:
    print("\nDense Captions:")
    for caption in result.dense_captions.list:
        print(" Caption: '{}' (confidence: {:.2f}%)".format(caption.text, caption.confidence * 100))
<br>
# Get image tags
<br>
<br>
# Get objects in the image
<br>
<br>
# Get people in the image</code></pre></div>
<ol start="5" dir="auto">
<li>احفظ تغييراتك وارجع إلى الوحدة الطرفية المتكاملة لمجلد <strong>تحليل الصور</strong>، وأدخل الأمر التالي لتشغيل البرنامج باستخدام الوسيطة <strong>image/street.jpg</strong>:</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet run images/street.jpg
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet run images/street.jpg" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl"><strong>Python</strong></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>python image-analysis.py images/street.jpg
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="python image-analysis.py images/street.jpg" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<ol start="6" dir="auto">
<li>لاحظ الإخراج الذي يجب أن يتضمن تسمية توضيحية مقترحة للصورة <strong>street.jpg</strong>.</li>
<li>يمكنك تشغيل البرنامج مرة أخرى، هذه المرة باستخدام الوسيطة <strong>image/building.jpg</strong> لرؤية التسمية التوضيحية التي يجري إنشاؤها لصورة <strong>Building.jpg</strong>.</li>
<li>كرر الخطوة السابقة لإنشاء تسمية توضيحية لملف <strong>images/person.jpg</strong>.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">الحصول على العلامات المقترحة لصورة</h2><a id="user-content-الحصول-على-العلامات-المقترحة-لصورة" class="anchor" aria-label="Permalink: الحصول على العلامات المقترحة لصورة" href="#الحصول-على-العلامات-المقترحة-لصورة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">قد يكون من المفيد في بعض الأحيان تحديد <em>العلامات</em> ذات الصلة التي توفر أدلة حول محتويات الصورة.</p>
<ol dir="rtl">
<li>في الدالة <strong>AnalyzeImage</strong>، ضمن التعليق <strong>الحصول على علامات الصور</strong>، أضف التعليمات البرمجية التالية:</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get image tags
if (result.Tags.Values.Count > 0)
{
    Console.WriteLine($"\n Tags:");
    foreach (DetectedTag tag in result.Tags.Values)
    {
        Console.WriteLine($"   '{tag.Name}', Confidence: {tag.Confidence:F2}");
    }
}</code></pre></div>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get image tags
if result.tags is not None:
    print("\nTags:")
    for tag in result.tags.list:
        print(" Tag: '{}' (confidence: {:.2f}%)".format(tag.name, tag.confidence * 100))</code></pre></div>
<ol start="2" dir="rtl">
<li>احفظ التغييرات وشغل البرنامج مرة واحدة لكل ملف من ملفات الصور في <strong>مجلد الصور</strong>، مع ملاحظة أنه بالإضافة إلى التسمية التوضيحية للصورة، يجري عرض قائمة بالعلامات المقترحة.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">الكشف عن العناصر وتحديد موقعها في صورة</h2><a id="user-content-الكشف-عن-العناصر-وتحديد-موقعها-في-صورة" class="anchor" aria-label="Permalink: الكشف عن العناصر وتحديد موقعها في صورة" href="#الكشف-عن-العناصر-وتحديد-موقعها-في-صورة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><em>اكتشاف الكائنات</em> هو شكل محدد من أشكال رؤية الكمبيوتر حيث يجري تحديد الكائنات الفردية داخل الصورة والإشارة إلى موقعها بواسطة مربع محيط.</p>
<ol dir="rtl">
<li>في الدالة <strong>AnalyzeImage</strong>، ضمن التعليق <strong>الحصول على عناصر في الصورة</strong>، أضف التعليمة البرمجية التالية:</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get objects in the image
if (result.Objects.Values.Count > 0)
{
    Console.WriteLine(" Objects:");
<br>
    // Prepare image for drawing
    stream.Close();
    System.Drawing.Image image = System.Drawing.Image.FromFile(imageFile);
    Graphics graphics = Graphics.FromImage(image);
    Pen pen = new Pen(Color.Cyan, 3);
    Font font = new Font("Arial", 16);
    SolidBrush brush = new SolidBrush(Color.WhiteSmoke);
<br>
    foreach (DetectedObject detectedObject in result.Objects.Values)
    {
        Console.WriteLine($"   \"{detectedObject.Tags[0].Name}\"");
<br>
        // Draw object bounding box
        var r = detectedObject.BoundingBox;
        Rectangle rect = new Rectangle(r.X, r.Y, r.Width, r.Height);
        graphics.DrawRectangle(pen, rect);
        graphics.DrawString(detectedObject.Tags[0].Name,font,brush,(float)r.X, (float)r.Y);
    }
<br>
    // Save annotated image
    String output_file = "objects.jpg";
    image.Save(output_file);
    Console.WriteLine("  Results saved in " + output_file + "\n");
}</code></pre></div>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get objects in the image
if result.objects is not None:
    print("\nObjects in image:")
<br>
    # Prepare image for drawing
    image = Image.open(image_filename)
    fig = plt.figure(figsize=(image.width/100, image.height/100))
    plt.axis('off')
    draw = ImageDraw.Draw(image)
    color = 'cyan'
<br>
    for detected_object in result.objects.list:
        # Print object name
        print(" {} (confidence: {:.2f}%)".format(detected_object.tags[0].name, detected_object.tags[0].confidence * 100))
<br>        
        # Draw object bounding box
        r = detected_object.bounding_box
        bounding_box = ((r.x, r.y), (r.x + r.width, r.y + r.height)) 
        draw.rectangle(bounding_box, outline=color, width=3)
        plt.annotate(detected_object.tags[0].name,(r.x, r.y), backgroundcolor=color)
<br>
    # Save annotated image
    plt.imshow(image)
    plt.tight_layout(pad=0)
    outputfile = 'objects.jpg'
    fig.savefig(outputfile)
    print('  Results saved in', outputfile)</code></pre></div>
<ol start="2" dir="auto">
<li>احفظ التغييرات وشغل البرنامج مرة واحدة لكل ملف من ملفات <strong>الصور</strong> الموجودة في مجلد الصور، مع ملاحظة أي كائنات يجري اكتشافها. بعد كل تشغيل، اعرض ملف <strong>Objects.jpg</strong> الذي جرى إنشاؤه في نفس المجلد مثل ملف التعليمات البرمجية الخاص بك لرؤية الكائنات ذات التعليقات التوضيحية.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">كشف الأشخاص وتحديدهم في الصورة</h2><a id="user-content-كشف-الأشخاص-وتحديدهم-في-الصورة" class="anchor" aria-label="Permalink: كشف الأشخاص وتحديدهم في الصورة" href="#كشف-الأشخاص-وتحديدهم-في-الصورة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><em>اكتشاف الأشخاص</em> هو شكل محدد من أشكال الرؤية الحاسوبية يجري من خلاله التعرّف على الأفراد داخل الصورة والإشارة إلى موقعهم بواسطة مربع محيط.</p>
<ol dir="rtl">
<li>في الدالة <strong>AnalyzeImage</strong>، ضمن التعليق <strong>الحصول على أشخاص في الصورة</strong>، أضف التعليمة البرمجية التالية:</li>
</ol>
<p dir="rtl"><strong>#C</strong></p>
<div class="highlight highlight-source-cs notranslate position-relative overflow-auto" dir="auto"><pre><code>// Get people in the image
if (result.People.Values.Count > 0)
{
    Console.WriteLine($" People:");
<br>
    // Prepare image for drawing
    System.Drawing.Image image = System.Drawing.Image.FromFile(imageFile);
    Graphics graphics = Graphics.FromImage(image);
    Pen pen = new Pen(Color.Cyan, 3);
    Font font = new Font("Arial", 16);
    SolidBrush brush = new SolidBrush(Color.WhiteSmoke);
<br>
    foreach (DetectedPerson person in result.People.Values)
    {
        // Draw object bounding box
        var r = person.BoundingBox;
        Rectangle rect = new Rectangle(r.X, r.Y, r.Width, r.Height);
        graphics.DrawRectangle(pen, rect);
        
        // Return the confidence of the person detected
        //Console.WriteLine($"   Bounding box {person.BoundingBox.ToString()}, Confidence: {person.Confidence:F2}");
    }
<br>
    // Save annotated image
    String output_file = "persons.jpg";
    image.Save(output_file);
    Console.WriteLine("  Results saved in " + output_file + "\n");
}</code></pre></div>
<p dir="rtl"><strong>Python</strong></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><code># Get people in the image
if result.people is not None:
    print("\nPeople in image:")
<br>
    # Prepare image for drawing
    image = Image.open(image_filename)
    fig = plt.figure(figsize=(image.width/100, image.height/100))
    plt.axis('off')
    draw = ImageDraw.Draw(image)
    color = 'cyan'
<br>
    for detected_people in result.people.list:
        # Draw object bounding box
        r = detected_people.bounding_box
        bounding_box = ((r.x, r.y), (r.x + r.width, r.y + r.height))
        draw.rectangle(bounding_box, outline=color, width=3)
<br>
        # Return the confidence of the person detected
        #print(" {} (confidence: {:.2f}%)".format(detected_people.bounding_box, detected_people.confidence * 100))
<br>       
    # Save annotated image
    plt.imshow(image)
    plt.tight_layout(pad=0)
    outputfile = 'people.jpg'
    fig.savefig(outputfile)
    print('  Results saved in', outputfile)</code></pre></div>
<ol start="2" dir="rtl">
<li>
<p dir="auto">(اختياري) يمكن إلغاء التعليق على أمر <strong>Console.Writeline</strong> ضمن قسم <strong>إرجاع ثقة الشخص الذي جرى اكتشافه</strong> لمراجعة مستوى الثقة الذي نجح إرجاعه إلى أنه جرى اكتشاف شخص في موضع معين من الصورة.</p>
</li>
<li>
<p dir="auto">احفظ التغييرات وشغل البرنامج مرة واحدة لكل ملف من ملفات <strong>الصور</strong> الموجودة في مجلد الصور، مع ملاحظة أي كائنات يجري اكتشافها. بعد كل تشغيل، اعرض ملف <strong>Objects.jpg</strong> الذي جرى إنشاؤه في نفس المجلد مثل ملف التعليمات البرمجية الخاص بك لرؤية الكائنات ذات التعليقات التوضيحية.</p>
</li>
</ol>
<blockquote>
<p dir="auto"><strong>ملاحظة</strong>: في المهام السابقة، استخدمت أسلوباً واحداً لتحليل الصورة، ثم أضفت التعليمات البرمجية بشكل متزايد لتحليل النتائج وعرضها. توفر SDK أيضاً أساليب فردية لاقتراح التسميات التوضيحية، وتحديد العلامات، والكشف عن العناصر، وما إلى ذلك - ما يعني أنه يمكنك استخدام الطريقة الأكثر ملاءمة لإرجاع المعلومات التي تحتاج إليها فقط، ما يقلل من حجم حمولة البيانات التي تحتاج إلى إرجاعها. راجع وثائق <a href="https://learn.microsoft.com/dotnet/api/overview/azure/cognitiveservices/computervision?view=azure-dotnet" rel="nofollow">.NET SDK</a> أو <a href="https://learn.microsoft.com/python/api/azure-cognitiveservices-vision-computervision/azure.cognitiveservices.vision.computervision" rel="nofollow">وثائق Python SDK</a> لمزيد من التفاصيل.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تنظيف الموارد</h2><a id="user-content-تنظيف-الموارد" class="anchor" aria-label="Permalink: تنظيف الموارد" href="#تنظيف-الموارد"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا كنت لا تستخدم موارد Azure التي أنشأتها في هذا المختبر لوحدات التدريب الأخرى، فيمكنك حذفها لتجنب تكبد المزيد من الرسوم. وإليك الطريقة:</p>
<ol dir="rtl">
<li>
<p dir="auto">افتح مدخل Azure على <code>https://portal.azure.com</code>، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.</p>
</li>
<li>
<p dir="auto">في شريط البحث العلوي، ابحث عن <em>حساب متعدد الخدمات لخدمات الذكاء الاصطناعي في Azure</em> وحدد مورد الحساب متعدد الخدمات لخدمات الذكاء الاصطناعي في Azure الذي أنشأته في هذا التمرين المعملي.</p>
</li>
<li>
<p dir="auto">في صفحة المورد، حدد <strong>حذف</strong> واتبع الإرشادات لحذف المورد.</p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">مزيد من المعلومات</h2><a id="user-content-مزيد-من-المعلومات" class="anchor" aria-label="Permalink: مزيد من المعلومات" href="#مزيد-من-المعلومات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">في هذا التمرين، استكشفت بعض إمكانيات تحليل الصور ومعالجتها لخدمة الذكاء الاصطناعي في Azure Vision. تتضمن الخدمة أيضاً إمكانيات اكتشاف الأشياء والأشخاص ومهام رؤية الكمبيوتر الأخرى.</p>
<p dir="auto">لمزيد من المعلومات حول استخدام خدمة <strong>الذكاء الاصطناعي في Azure Vision</strong>، راجع <a href="https://learn.microsoft.com/azure/ai-services/computer-vision/" rel="nofollow">وثائق الذكاء الاصطناعي في Azure Vision</a>.</p>
</article></div></div>
