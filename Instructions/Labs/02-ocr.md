---
lab:
  title: قراءة النص في الصور
  description: استخدم التعرف البصري على الحروف (OCR) في خدمة Azure AI Vision Image Analysis لتحديد موقع النصوص داخل الصور واستخراجها.
---

# قراءة النص في الصور

التعرّف البصري على الحروف (OCR) هو مجموعة فرعية من رؤية الكمبيوتر التي تتعامل مع قراءة النص في الصور والمستندات. توفر خدمة ‏Image Analysis ‏**‏Azure AI Vision** واجهة برمجة تطبيقات (API) لقراءة النصوص، وستستكشفها في هذا التمرين.

> **ملاحظة**: يستند هذا التدريب إلى برامج SDK قبل الإصدار، والتي قد تخضع للتغيير. عند الضرورة، استخدمنا إصدارات محددة من الحزم؛ والتي قد لا تعكس أحدث الإصدارات المتوفرة. قد تواجه بعض السلوك أو التحذيرات أو الأخطاء غير المتوقعة.

يستند هذا التمرين إلى عدة تطوير البرامج (SDK) الخاصة بـ Azure Vision Analysis للغة Python، لكن يمكنك تطوير تطبيقات الرؤية الحاسوبية باستخدام عِدد تطوير برامج (SDK) خاصة بلغات متعددة، منها:

* [Azure AI Vision Analysis للغة JavaScript](https://www.npmjs.com/package/@azure-rest/ai-vision-image-analysis)
* [Azure AI Vision Analysis للغة Microsoft .NET](https://www.nuget.org/packages/Azure.AI.Vision.ImageAnalysis)
* [Azure AI Vision Analysis للغة Java](https://mvnrepository.com/artifact/com.azure/azure-ai-vision-imageanalysis)

سيستغرق هذا التدريب حوالي **30** دقيقة.

## إنشاء مورد Azure AI Vision

إذا لم يكن لديك مورد Azure AI Vision في اشتراكك بالفعل، فستحتاج إلى إنشائه.

> **ملاحظة**: في هذا التمرين، ستستخدم مورد **Computer Vision** مستقلًا. يمكنك أيضًا استخدام خدمات Azure AI Vision ضمن مورد متعدد الخدمات من *Azure AI Services*، إما مباشرةً أو في مشروع *Azure AI Foundry*.

1. افتح [مدخل Microsoft Azure](https://portal.azure.com) عبر `https://portal.azure.com`، وسجِّل الدخول باستخدام بيانات اعتماد Azure الخاصة بك. أغلِق أي رسائل ترحيب أو تلميحات قد تظهر.
1. حدد **Create a resource.**
1. في شريط البحث، ابحث عن `Computer Vision`، وحدد **Computer Vision**، وأنشئ المورد باستخدام الإعدادات التالية:
    - **Subscription**: *اشتراكك في Azure*
    - **Resource group**: *إنشاء مجموعة موارد أو تحديدها*
    - **المنطقة**: *اختَر من بين **شرق الولايات المتحدة** أو **غرب الولايات المتحدة** أو **وسط فرنسا** أو **وسط كوريا** أو **شمال أوروبا** أو **جنوب شرق آسيا** أو **غرب أوروبا** أو **شرق آسيا**\**
    - **الاسم**: *اسم صالح لمورد Computer Vision*
    - **مستوى التسعير**: مجاني (F0)

    \*تتوفر ميزات الذكاء الاصطناعي في Azure اصدار 4.0 حالياً في هذه المناطق فقط.

1. حدد مربعات الاختيار المطلوبة ثم أنشئ المورد.
1. انتظر حتى يكتمل النشر، ثم اعرض تفاصيل النشر.
1. بعد توزيع المورد، انتقل إليه وضمن عقدة **إدارة الموارد** في جزء التنقل، اعرض صفحة **المفاتيح ونقطة النهاية** الخاصة به. ستحتاج إلى نقطة النهاية وأحد المفاتيح من هذه الصفحة في الإجراء التالي.

## تطوير تطبيق لاستخراج النصوص باستخدام عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Vision

في هذا التمرين، ستكمل تطبيق عميل تم تنفيذه جزئيًا يستخدم عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Vision لاستخراج النصوص من الصور.

### إعداد تكوين التطبيق

1. في مدخل Microsoft Azure، استخدم الزر **[\>_]** الموجود على يمين شريط البحث في أعلى الصفحة لإنشاء جلسة جديدة من Cloud Shell في مدخل Microsoft Azure، وحدد بيئة ***PowerShell*** دون مساحة تخزين في اشتراكك.

    يوفّر Cloud Shell واجهة سطر الأوامر في الجزء الموجود في أسفل بوابة Azure.

    > **ملاحظة**: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة *معالج Bash*، فبدّل إلى ***PowerShell***.

    > **ملاحظة**: إذا طلب منك المدخل تحديد مساحة تخزين للاحتفاظ بملفاتك بشكل دائم، فاختَر **لا يلزم حساب تخزين**، وحدّد الاشتراك الذي تستخدمه ثم اضغط على **تطبيق**.

1. في شريط أدوات Cloud Shell، في قائمة **الإعدادات**، حدد **الانتقال إلى الإصدار الكلاسيكي** (هذا مطلوب لاستخدام محرر التعليمات البرمجية).

    **<font color="red">تأكد من التبديل إلى الإصدار الكلاسيكي من cloud shell قبل المتابعة.</font>**

1. غيِّر حجم جزء cloud shell بحيث تظل قادرًا على رؤية صفحة **المفاتيح ونقطة النهاية** لمورد Computer Vision.

    > **تلميح**" يمكنك تغيير حجم الجزء عن طريق سحب الحد العلوي. يمكنك أيضًا استخدام زرَّي التصغير والتكبير للتبديل بين cloud shell والواجهة الرئيسية للمدخل.

1. في جزء Cloud Shell، أدخل الأوامر التالية لنسخ مخزن بيانات GitHub الخاص الذي يحتوي على ملفات التعليمات البرمجية لهذا التدريب (اكتب الأمر أو انسخه إلى الحافظة ثم انقر بزر الماوس الأيمن في سطر الأوامر والصقه كنص عادي):

    ```
    rm -r mslearn-ai-vision -f
    git clone https://github.com/MicrosoftLearning/mslearn-ai-vision
    ```

    > **تلميح**: أثناء لصق الأوامر في CloudShell، قد تشغل النتيجة كمية كبيرة من مساحة المخزن المؤقت للشاشة. يمكنك مسح الشاشة عن طريق إدخال الأمر `cls` لتسهيل التركيز على كل مهمة.

1. بعد نسخ المستودع، استخدم الأمر التالي للانتقال إلى ملفات التعليمات البرمجية للتطبيق:

    ```
   cd mslearn-ai-vision/Labfiles/ocr/python/read-text
   ls -a -l
    ```

    يحتوي المجلد على تكوين التطبيق وملفات التعليمات البرمجية له. كما يحتوي على المجلد الفرعي **images/**، والذي يحتوي على بعض ملفات الصور لتحليلها في تطبيقك.

1. ثبِّت حزمة عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Vision والحزم الأخرى المطلوبة بتشغيل الأوامر التالية:

    ```
   python -m venv labenv
   ./labenv/bin/Activate.ps1
   pip install -r requirements.txt azure-ai-vision-imageanalysis==1.0.0
    ```

1. أدخِل الأمر التالي لتحرير ملف التكوين الخاص بتطبيقك:

    ```
   code .env
    ```

    يتم فتح الملف في محرر التعليمات البرمجية.

1. في ملف التعليمات البرمجية، حدِّث قيم التكوين التي يحتوي عليها الملف لتعكس **نقطة النهاية** و**مفتاح** مصادقة لمورد Computer Vision (المنسوخ من صفحة **المفاتيح ونقطة النهاية** الخاصة به في مدخل Microsoft Azure).
1. بعد استبدال العناصر النائبة، استخدم الأمر **CTRL+S** لحفظ التغييرات ثم استخدم الأمر **CTRL+Q** لإغلاق محرر التعليمات البرمجية مع إبقاء سطر أوامر Cloud Shell مفتوحWا.

### إضافة التعليمات البرمجية لقراءة النص في الصور

1. في سطر أوامر cloud shell، أدخِل الأمر التالي لفتح ملف التعليمات البرمجية لتطبيق العميل:

    ```
   code read-text.py
    ```

    > **تلميح**: قد تحتاج إلى تكبير جزء cloud shell ونقل شريط التقسيم بين وحدة تحكم سطر الأوامر ومحرر التعليمات البرمجية لعرض التعليمات البرمجية بسهولة أكبر.

1. في ملف التعليمات البرمجية، ابحث عن التعليق **Import namespaces**، وأضِف التعليمات البرمجية التالية لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Vision:

    ```python
   # import namespaces
   from azure.ai.vision.imageanalysis import ImageAnalysisClient
   from azure.ai.vision.imageanalysis.models import VisualFeatures
   from azure.core.credentials import AzureKeyCredential
    ```

1. في الدالة **Main**، تم تضمين التعليمات البرمجية لتحميل إعدادات التكوين وتحديد الملف الذي سيتم تحليله. بعد ذلك، ابحث عن التعليق **Authenticate Azure AI Vision client** وأضِف التعليمات البرمجية التالية الخاصة باللغة لإنشاء كائن عميل Azure AI Vision Image Analysis ومصادقته:

    ```python
   # Authenticate Azure AI Vision client
   cv_client = ImageAnalysisClient(
        endpoint=ai_endpoint,
        credential=AzureKeyCredential(ai_key))
    ```

1. في الدالة **Main**، وضمن التعليمات البرمجية التي أضفتها للتو، ابحث عن التعليق **Read text in image** وأضِف التعليمات البرمجية التالية لاستخدام عميل Image Analysis لقراءة النص في الصورة:

    ```python
   # Read text in image
   with open(image_file, "rb") as f:
        image_data = f.read()
   print (f"\nReading text in {image_file}")

   result = cv_client.analyze(
        image_data=image_data,
        visual_features=[VisualFeatures.READ])
    ```

1. ابحث عن التعليق **Print the text** وأضِف التعليمات البرمجية التالية (بما في ذلك التعليق النهائي) لطباعة أسطر النص المكتشفة، واستدعاء دالة لإضافة تعليقات توضيحية إليها داخل الصورة (باستخدام **bounding_polygon** الذي تم إرجاعه لكل سطر من النص):

    ```python
   # Print the text
   if result.read is not None:
        print("\nText:")
    
        for line in result.read.blocks[0].lines:
            print(f" {line.text}")        
        # Annotate the text in the image
        annotate_lines(image_file, result.read)

        # Find individual words in each line
        
    ```

1. احفظ التغييرات (*CTRL+S*) مع إبقاء محرر التعليمات البرمجية مفتوحًا في حال احتجت إلى إصلاح أي خطأ مطبعي.

1. غيِّر حجم الأجزاء لعرض مساحة أكبر من وحدة التحكم، ثم أدخِل الأمر التالي لتشغيل البرنامج:

    ```
   python read-text.py images/Lincoln.jpg
    ```

1. يقرأ البرنامج النص في ملف الصورة المحدد (*images/Lincoln.jpg*)، كما يظهر أدناه:

    ![صورة لتمثال أبراهام لينكولن.](../media/Lincoln.jpg)

1. في المجلد **read-text**، **تم إنشاء صورة lines.jpg**. استخدم أمر **تنزيل** (المخصص لـ Azure cloud shell) لتنزيلها:

    ```
   download lines.jpg
    ```

    ينشئ أمر التنزيل رابطًا منبثقًا في أسفل يمين متصفحك، والذي يمكنك تحديده لتنزيل الملف وفتحه. يجب أن تبدو الصورة مشابهة لما يلي:

    ![صورة يُميَّز فيها النص.](../media/text.jpg)

1. شغِّل البرنامج مرة أخرى، وهذه المرة حدد المَعلَمة *images/Business-card.jpg* لاستخراج النص من الصورة التالية:

    ![صورة لبطاقة عمل ممسوحة ضوئيًا.](../media/Business-card.jpg)

    ```
   python read-text.py images/Business-card.jpg
    ```

1. نزِّل الملف **lines.jpg** الناتج واعرضه:

    ```
   download lines.jpg
    ```

1. شغِّل البرنامج مرة أخرى، وهذه المرة حدد المَعلَمة *images/Note.jpg* لاستخراج النص من هذه الصورة:

    ![صورة لقائمة تسوق مكتوبة بخط اليد.](../media/Note.jpg)

    ```
   python read-text.py images/Note.jpg
    ```

1. نزِّل الملف **lines.jpg** الناتج واعرضه:

    ```
   download lines.jpg
    ```

### إضافة التعليمات البرمجية لإرجاع موضع الكلمات الفردية

1. غيِّر حجم الأجزاء لعرض مساحة أكبر من ملف التعليمات البرمجية. بعد ذلك، ابحث عن التعليق **Find individual words in each line** وأضِف التعليمات البرمجية التالية (احرص على الحفاظ على مستوى المسافة البادئة الصحيح):

    ```python
   # Find individual words in each line
   print ("\nIndividual words:")
   for line in result.read.blocks[0].lines:
        for word in line.words:
            print(f"  {word.text} (Confidence: {word.confidence:.2f}%)")
   # Annotate the words in the image
   annotate_words(image_file, result.read)
    ```

1. احفظ التغييرات (*CTRL+S*). بعد ذلك، في جزء سطر الأوامر، أعِد تشغيل البرنامج لاستخراج النص من *images/Lincoln.jpg*.
1. لاحظ الناتج، الذي يجب أن يتضمن كل كلمة فردية في الصورة، بالإضافة إلى درجة الثقة المرتبطة بالتنبؤ بها.
1. في المجلد **read-text**، تم إنشاء صورة **words.jpg**. استخدم أمر **تنزيل** (المخصص لـ Azure cloud shell) لتنزيلها وعرضها:

    ```
   download words.jpg
    ```

1. أعِد تشغيل البرنامج باستخدام الملفين *images/Business-card.jpg* و*images/Note.jpg*، ثم اعرض الملف **words.jpg** الذي تم إنشاؤه لكل صورة.

## تنظيف الموارد

إذا انتهيت من استكشاف Azure AI Vision، فيُستحسن حذف الموارد التي أنشأتها في هذا التمرين لتفادي تحمّل تكاليف غير ضرورية على Azure:

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.

1. في شريط البحث العلوي، ابحث عن *Computer Vision*، وحدد مورد Computer Vision الذي أنشأته في هذا الواجب.

1. في صفحة المورد، حدد **حذف** واتبع الإرشادات لحذف المورد.
