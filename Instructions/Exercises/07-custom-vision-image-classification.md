---
lab:
  title: تصنيف الصور باستخدام Azure AI Custom Vision
---

# تصنيف الصور باستخدام Azure AI Custom Vision

تمكنك خدمة **Azure AI Custom Vision** من إنشاء نماذج رؤية الكمبيوتر المدربة على صورك الخاصة. يمكنك استخدامه لتدريب *تصنيف الصور* ونماذج *الكشف عن الكائنات*؛ والتي يمكنك بعد ذلك نشرها واستهلاكها من التطبيقات.

في هذا التمرين، ستستخدم خدمة Custom Vision لتدريب نموذج تصنيف الصور الذي يمكنه اكتشاف ثلاث فئات من الفاكهة (التفاح والموز والبرتقال).

## استنساخ المستودع لهذه الدورة التدريبية

إذا لم تكن قد استنسخت بالفعل باستنساخ مستودع التعليمات البرمجية **mslearn-ai-vision** في البيئة التي تعمل فيها في هذا التمرين المعملي، فاتبع هذه الخطوات لتنفيذ بذلك. بخلاف ذلك، افتح المجلد المستنسخ في تعليمة Visual Studio البرمجية.

1. ابدأ تشغيل Visual Studio Code.
2. افتح لوحة (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع `https://github.com/MicrosoftLearning/mslearn-ai-vision` إلى مجلد محلي (لا يُهم أي مجلد).
3. عند استنساخ المستودع، افتح المجلد في تعليمة Visual Studio البرمجية.
4. انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.

    > **ملاحظة**: إذا جرت مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد **ليس الآن**. إذا جرت مطالبتك برسالة *اكتشاف مشروع وظيفة Azure في المجلد*، يمكنك إغلاق هذه الرسالة بأمان.

## إنشاء موارد الرؤية المخصصة

قبل أن تتمكن من تدريب نموذج، ستحتاج إلى موارد Azure *للتدريب* و*التنبؤ*. يمكنك إنشاء موارد **Custom Vision** لكل من هذه المهام، أو يمكنك إنشاء مورد **خدمات Azure AI** واحد واستخدامه إما (أو كليهما).

في هذا التمرين، ستقوم بإنشاء موارد **Custom Vision** للتدريب والتنبؤ بحيث يمكنك إدارة الوصول والتكاليف لأحمال العمل هذه بشكل منفصل.

1. في علامة تبويب جديدة لمستعرض، افتح مدخل Azure في `https://portal.azure.com`، ثم سجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure لديك.
2. اضغط على زر **&#65291، إنشاء مورد**وابحث عن*custom vision*، وأنشئ مورد** Custom Vision** باستخدام الإعدادات التالية:
    - **إنشاء خيارات**: كلاهما
    - **Subscription**: *اشتراكك في Azure*
    - **مجموعة الموارد**: *اختر أو أنشئ مجموعة موارد (إذا كنت تستخدم اشتراكًا مقيدًا، فقد لا يكون لديك إذن لإنشاء مجموعة موارد جديدة - استخدم المجموعة المتوفرة)*
    - **المنطقة**: *اختر أي منطقة متوفرة*
    - **الاسم**: *أدخل اسماً فريداً*
    - **مستوى أسعار التدريب:** F0
    - **مستوى أسعار التنبؤ**: F0

    > **ملاحظة**: إذا كانت لديك خدمة رؤية معدلة F0 في اشتراكك مسبقًا، فاختر **S0** لأجل هذا.

3. انتظر حتى يتم إنشاء الموارد، ثم اعرض تفاصيل التوزيع ولاحظ أنه يتم توفير موردين لـ Custom Vision؛ مورد للتدريب، ومورد آخر للتنبؤ (الذي يتجلى عن طريق لاحقة **-التنبؤ** ). يمكنك عرض هذا من خلال الانتقال إلى مجموعة الموارد حيث قمت بإنشائها.

> **مهم**: لكل مورد * نقطة نهاية *و*مفاتيح*خاصة به، والتي تستخدم لإدارة الوصول من التعليمات البرمجية الخاصة بك. لتدريب نموذج تصنيف الصور، يجب أن تستخدم التعليمات البرمجية لديك مورد * التدريب* (بنقطة النهاية والمفتاح الخاص بها)؛ ولاستخدام النموذج المدرب للتنبؤ بفئات الصور، يجب أن تستخدم التعليمات البرمجية لديك مورد* التنبؤ* (باستخدام نقطة النهاية والمفتاح الخاص بها).

## إنشاء مشروع Custom Vision

لتدريب نموذج تصنيف الصورة، تحتاج إلى إنشاء مشروع رؤية معدلة بناءً على مورد التدريب الخاص بك. للقيام بذلك، ستستخدم مدخل Custom Vision.

1. في تعليمة Visual Studio البرمجية، اعرض صور التدريب في مجلد **Labfiles/07-custom-vision-image-classification/training-images** حيث قمت باستنساخ المستودع. يحتوي هذا المجلد على مجلدات فرعية من صور التفاح والموز والبرتقال.
2. في علامة تبويب متصفح أخرى، افتح مدخل Custom Vision على `https://customvision.ai`. إذا طُلب منك ذلك، قم بتسجيل الدخول باستخدام حساب Microsoft المرتبط باشتراك Azure الخاص بك ووافق على شروط الخدمة.
3. في مدخل Custom Vision، أنشئ مشروعًا جديدًا بالإعدادات التالية:
    - **الاسم**: تصنيف الفاكهة
    - **الوصف**: تصنيف الصورة للفاكهة
    - **المورد**: * مورد Custom Vision الذي أنشأته مسبقًا*
    - **أنواع المشاريع**: التصنيف
    - **أنواع التصنيف**: متعدد الفئات (علامة واحدة لكل صورة)
    - **المَجالات**: الغذاء
4. في المشروع الجديد، انقر فوق **\[+\]إضافة صور**، وحدد جميع الملفات في مجلد **Labfiles/07-custom-vision-image-classification/training-images/apple** الذي قمت بعرضه سابقًا. ثم قم بتحميل ملفات الصور، مع تحديد العلامة *تفاحة*، على النحو التالي:

![تحميل التفاح مع علامة التفاح](../media/upload_apples.jpg)
   
5. كرر الخطوة السابقة لتحميل الصور في مجلد **الموز** مع *الموز*العلامة، والصور في المجلد **البرتقالي** مع علامة *البرتقالي*.
6. استكشف الصور التي قمت بتحميلها في مشروع Custom Vision - يجب أن يكون هناك 15 صورة لكل فصل، على النحو التالي:

![صور مميزة للفاكهة - 15 تفاحة و 15 موزة و 15 برتقالة](../media/fruit.jpg)
    
7. في مشروع Custom Vision، فوق الصور، انقر فوق **"تدريب"** لتدريب نموذج تصنيف باستخدام الصور ذات العلامات. حدد خيار **"تدريب سريع"**، ثم انتظر حتى يكتمل تكرار التدريب (قد يستغرق ذلك دقيقة أو نحو ذلك).
8. عند تدريب تكرار النموذج، راجع مقاييس الأداء *الدقة**والاستدعاء*و*AP* - تقيس هذه دقة التنبؤ لنموذج التصنيف، ويجب أن تكون جميعها عالية.

> **ملاحظة**: تستند مقاييس الأداء إلى حد احتمال 50% لكل تنبؤ (بمعنى آخر، إذا كان النموذج يحسب احتمالاً بنسبة 50% أو أعلى أن تكون الصورة من فئة معينة، فسيتم التنبؤ بهذه الفئة). يمكنك ضبط هذا في أعلى يسار الصفحة.

## اختبار النموذج

الآن بعد أن دربت النموذج، يمكنك اختباره.

1. فوق مقاييس الأداء، انقر فوق **اختبار سريع**.
2. في المربع **URL للصورة،** اكتب `https://aka.ms/apple-image` وانقر فَوق &#10132;
3. اعرض التوقعات التي يعرضها نموذجك - يجب أن تكون درجة احتمالية *تفاحة* أعلى، كما يلي:

![صورة مَع التنبؤ الطبقي بالتفاح](../media/test-apple.jpg)

4. أغلق نافذة **اختبار سريع**.

## عرض إعدادات المشروع

تم تعيين معرف فريد للمشروع الذي قمت بإنشائه، والذي ستحتاج إلى تحديده في أي تعليمة برمجية تتفاعل معه.

1. انقر فوق أيقونة *الإعدادات* (&#9881;) في أعلى يمين صفحة **الأداء** لعرض إعدادات المشروع.
2. ضمن **عام** (على اليسار)، لاحظ **معرف المشروع** لذي يعرف هذا المشروع بشكل فريد.
3. على اليمين، ضمن **الموارد** لاحظ أنه يتم عرض المفتاح ونقطة النهاية. هذه هي تفاصيل مورد * التدريب* (يمكنك أيضًا الحصول على هذه المعلومات عن طريق عرض المورد في مدخل Microsoft Azure).

## استخدام واجهة برمجة تطبيقات *التدريب*

يوفر مدخل Custom Vision واجهة مستخدم ملائمة يمكنك استخدامها لتحميل الصور ووضع علامات عليها وتدريب النماذج. ومع ذلك، في بعض السيناريوهات قد ترغب في أتمتة تدريب النموذج باستخدام واجهة برمجة تطبيقات تدريب Custom Vision.

> **ملاحظة**: في هذا التمرين، يمكنك اختيار استخدام واجهة برمجة التطبيقات إما من **C#** أو **Python** SDK. في الخطوات الواردة أدناه، نفذ الإجراءات المناسبة للغتك المفضلة.

1. في Visual Studio Code، في جزء **Explorer**، انتقِل إلى المجلد **07-custom-vision-image-classification** وقم بتوسيع المجلد **CSharp** أو **Python** حسب تفضيل اللغة لديك.
2. انقر بزر الماوس الأيمن فوق مجلد **train-classifier** وافتح وحدة طرفية متكاملة. ثم قم بتثبيت حزمة تدريب Custom Vision عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:

**C#**

```
dotnet add package Microsoft.Azure.CognitiveServices.Vision.CustomVision.Training --version 2.0.0
```

**Python**

```
pip install azure-cognitiveservices-vision-customvision==3.1.0
```

3. اعرض محتويات مجلد **train-classifier**، ولاحظ أنه يحتوي على ملف لإعدادات التكوين:
    - **C#**: appsettings.json
    - **Python**: .env

    افتح ملف التكوين وقم بتحديث قيم التكوين التي يحتوي عليها لتعكس نقطة النهاية والمفتاح لمورد *تدريب* Custom Vision لديك ومعرّف المشروع لمشروع التصنيف الذي قمت بإنشائه مسبقًا. احفظ تغييراتك.
4. لاحظ أن مجلد **train-classifier** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: train-classifier.py

    افتح ملف التعليمات البرمجية وراجع التعليمات البرمجية التي يحتوي عليها، مع ملاحظة التفاصيل التالية:
    - يتم استيراد مساحات الأسماء من الحزمة التي قمت بتثبيتها
    - تسترد الدالة **Main** إعدادات التكوين، وتستخدم المفتاح ونقطة النهاية لإنشاء **CustomVisionTrainingClient** مصدق عليه، والذي يتم استخدامه بعد ذلك مع معرف المشروع لإنشاء مرجع **مشروع** إلى مشروعك.
    - تسترد الدالة **Upload_Images** العلامات المعرفة في مشروع Custom Vision ثم تقوم بتحميل ملفات الصور من المجلدات المسماة المقابلة إلى المشروع، مع تعيين معرف العلامة المناسب.
    - تنشئ الدالة **Train_Model** تكراراً تدريبياً جديداً للمشروع وتنتظر اكتمال التدريب.
5. أعد الوحدة الطرفية المتكاملة للمجلد **train-classifier**، وأدخل الأمر التالي لتشغيل البرنامج:

**C#**

```
dotnet run
```

**Python**

```
python train-classifier.py
```
    
6. انتظر حتى ينتهي البرنامج. ثم ارجع إلى المستعرض الخاص بك واعرض صفحة **صور التدريب** لمشروعك في مدخل Custom Vision (قم بتحديث المتصفح إذا لزم الأمر).
7. تحقق من إضافة بعض الصور ذات العلامات الجديدة إلى المشروع. ثم اعرض صفحة **الأداء** وتحقق من إنشاء تكرار جديد.

## نَشر نموذج تصنيف الصور

أنت الآن جاهز لنشر نموذجك المدرّب بحيث يمكن استخدامه من تطبيق عميل.

1. في مدخل Custom Vision، في صفحة **الأداء**، انقر فوق **&#128504; نشر** لنشر النموذج المُدرب بالإعدادات التالية:
    - **اسم النموذج**: مصنف الفاكهة
    - **مورد التنبؤ**: *مورد **التنبؤ** الذي أنشأته سابقًا والذي ينتهي بـ "-Prediction" (<u>ليس هو</u> مورد التدريب)*.
2. في الجزء العلوي الأيسر من صفحة **إعدادات المشروع**، انقر فوق أيقونة *معرض المشاريع* (&#128065;) للعودة إلى الصفحة الرئيسية لمدخل Custom Vision، حيث يتم إدراج مشروعك الآن.
3. في الصفحة الرئيسية لمدخل Custom Vision، في أعلى اليمين، انقر فوق أيقونة *الإعدادات * (&#9881;) لعرض إعدادات خدمة Custom Vision الخاصة بك. ثم، ضمن **الموارد**، ابحث عن مورد * التنبؤ *الذي ينتهي بـ "-Prediction" (<u>وليس</u> مورد التدريب) لتحديد قيم ** المفتاح **** ونقطة النهاية الخاصة به **(يمكنك أيضًا الحصول على هذه المعلومات عن طريق عرض المورد في مدخل Microsoft Azure).

## استخدام مصنف الصور من تطبيق عميل

الآن بعد أن قمت بنشر نموذج تصنيف الصور، يمكنك استخدامه من تطبيق عميل. مرة أخرى، يمكنك اختيار استخدام **C#** أو **Python**.

1. في Visual Studio Code، في المجلد **07-custom-vision-image-classification**، في المجلد الفرعي للغة المفضلة لديك (**C-Sharp** أو **Python**)، إلى اليمين- المجلد **test-classifier** وافتح وحدة طرفية متكاملة. ثم أدخل الأمر التالي الخاص بـ SDK لتثبيت حزمة تنبؤ Custom Vision:

**C#**

```
dotnet add package Microsoft.Azure.CognitiveServices.Vision.CustomVision.Prediction --version 2.0.0
```

**Python**

```
pip install azure-cognitiveservices-vision-customvision==3.1.0
```

> **ملاحظة**: تتضمن حزمة Python SDK كلا من حزم التدريب والتنبؤ، وقد تكون مثبتة بالفعل.

2. قم بتوسيع مجلد **test-classifier** لعرض الملفات التي يحتوي عليها، والتي تستخدم لتنفيذ تطبيق عميل اختبار لنموذج تصنيف الصور.
3. افتح ملف التكوين لتطبيق العميل الخاص بك (*appsettings.json* لـ C# أو *.env* لـ Python) وقم بتحديث قيم التكوين التي يحتوي عليها لتعكس نقطة النهاية والمفتاح لمورد *توقع* Custom Vision ومعرف المشروع لمشروع التصنيف واسم النموذج المنشور (الذي يجب أن يكون *fruit-detector*). احفظ تغييراتك.
4. افتح ملف التعليمات البرمجية لتطبيق العميل الخاص بك (*Program.cs* لـ C#، *test-classification.py* لـ Python) وراجع التعليمات البرمجية التي يحتوي عليها، مع ملاحظة التفاصيل التالية:
    - يتم استيراد مساحات الأسماء من الحزمة التي قمت بتثبيتها
    - تسترد الدالة ** Main** إعدادات التكوين، وتستخدم المفتاح ونقطة النهاية لإنشاء **CustomVisionPredictionClient** مصدّق عليه.
    - يتم استخدام كائن عميل التنبؤ للتنبؤ بفئة لكل صورة في مجلد **test-images**، مع تحديد معرف المشروع واسم النموذج لكل طلب. يتضمن كل توقع احتمالاً لكل فئة ممكنة، ويتم عرض العلامات المتوقعة التي تحتوي على احتمال أكبر من 50% فقط.
5. أعد الوحدة الطرفية المتكاملة للمجلد **test-classifier**، وأدخل الأمر الخاص بـ SDK التالي لتشغيل البرنامج:

**C#**

```
dotnet run
```

**Python**

```
python test-classifier.py
```

6. عرض التسمية (العلامة) ودرجات الاحتمال لكل تنبؤ. يمكنك عرض الصور في مجلد **test-images** للتحقق من أن النموذج قد صنفها بشكل صحيح.

## مزيد من المعلومات

لمزيد من المعلومات حول تصنيف الصور باستخدام خدمة Custom Vision، راجع [وثائق Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/).
