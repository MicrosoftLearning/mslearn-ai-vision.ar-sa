---
lab:
  title: تطوير تطبيق دردشة يدعم الرؤية
  description: تعرّف على كيفية استخدام Azure AI Foundry لبناء تطبيق ذكاء اصطناعي توليدي يدعم إدخال الصور.
---

# تطوير تطبيق دردشة يدعم الرؤية

في هذا التمرين، يمكنك استخدام نموذج الذكاء الاصطناعي التوليدي *Phi-4-multimodal-instruct* لتوليد ردود للمطالبات التي تتضمن صورًا. ستطوّر تطبيقًا يقدّم مساعدات ذكاء اصطناعي تتعلق بالمنتجات الطازجة في متجر بقالة باستخدام Azure AI Foundry وخدمة استدلال نماذج Azure AI.

سيستغرق هذا التدريب حوالي **30** دقيقة.

## إنشاء مشروع في مصنع الذكاء الاصطناعي في Azure

دعنا نبدأ بإنشاء مشروع في مصنع الذكاء الاصطناعي في Azure.

1. في متصفح الويب، افتح [مدخل Azure AI Foundry](https://ai.azure.com) على `https://ai.azure.com` وسجّل الدخول باستخدام بيانات اعتماد Azure الخاصة بك. أغلق أية تلميحات أو أجزاء تشغيل سريع يتم فتحها عندما تقوم بتسجيل الدخول، وإذا لزم الأمر، استخدم شعار **مصنع الذكاء الاصطناعي في Azure** في أعلى اليسار للانتقال إلى الصفحة الرئيسية، والتي تبدو مشابهة للصورة التالية:

    ![لقطة شاشة لمدخل Azure AI Foundry.](../media/ai-foundry-home.png)

2. في الصفحة الرئيسية، حدد **+ إنشاء مشروع**.
3. في معالج** إنشاء مشروع**، أدخل اسمًا مناسبًا لمشروعك وإذا تم اقتراح مركز موجود، فحدد خيار إنشاء مركز جديد. ثم راجع موارد Azure التي سيتم إنشاؤها تلقائيًا لدعم مركزك ومشروعك.
4. حدد **تخصيص** وحدد الإعدادات التالية لمركزك:
    - **اسم المركز**: *اسم صالح لمركزك*
    - **Subscription**: *اشتراكك في Azure*
    - **Resource group**: *إنشاء مجموعة موارد أو تحديدها*
    - **الموقع**: حدد أيًا من المناطق التالية\*:
        - شرق الولايات المتحدة
        - East US 2
        - وسط شمال الولايات المتحدة
        - South Central US
        - منطقة السويد الوسطى
        - غرب الولايات المتحدة
        - غرب الولايات المتحدة الأمريكية 3
    - **توصيل خدمات Azure AI أو Azure OpenAI**: *إنشاء مورد جديد لخدمات الذكاء الاصطناعي*
    - **الاتصال بـ Azure AI Search**: تخطي الاتصال

    > \* في وقت كتابة هذا الدليل، يتوفر نموذج Microsoft *Phi-4-multimodal-instruct* الذي سنستخدمه في هذا التمرين في هذه المناطق. يمكنك التحقق من أحدث توفر إقليمي لنماذج معينة في [وثائق Azure AI Foundry](https://learn.microsoft.com/azure/ai-foundry/how-to/deploy-models-serverless-availability#region-availability). في حال تم الوصول إلى الحد الأقصى للحصة الإقليمية لاحقًا في التمرين، قد تحتاج إلى إنشاء مورد آخر في منطقة مختلفة.

5. حدد **التالي** لمراجعة التكوين الخاص بك. ثم حدد **إنشاء** وانتظر حتى تكتمل العملية.
6. عند إنشاء مشروعك، أغلق أي تلميحات يتم عرضها وراجع صفحة المشروع في مدخل مصنع الذكاء الاصطناعي في Azure، والذي يجب أن يبدو مشابهة للصورة التالية:

    ![لقطة شاشة توضح تفاصيل مشروع ذكاء اصطناعي في Azure في مدخل مصنع الذكاء الاصطناعي في Azure.](../media/ai-foundry-project.png)

## توزيع نموذج متعدد الوسائط

أنت الآن جاهز لتوزيع نموذج متعدد الوسائط يمكنه دعم الإدخال المستند إلى الصور. هناك العديد من النماذج التي يمكنك الاختيار من بينها، بما في ذلك نموذج OpenAI *gpt-4o*. في هذا التمرين، سنستخدم نموذج *Phi-4-multimodal-instruct* الذي يدعم المطالبات التي تتضمن صورًا.

1. في شريط الأدوات الموجود في أعلى يمين من صفحة مشروع مصنع الذكاء الاصطناعي في Azure، استخدم أيقونة** ميزات المعاينة**(**&#9215;**) للتأكد من تمكين ميزة **نشر النماذج في خدمة استنتاج نموذج Azure AI**. تضمن هذه الميزة توفّر توزيع النموذج الخاص بك لخدمة الاستدلال بالذكاء الاصطناعي في Azure، والتي ستستخدمها في كود التطبيق الخاص بك.
2. في الجزء الموجود على يسار مشروعك، في قسم **أصولي**، حدد صفحة **النماذج + نقاط النهاية**.
3. في صفحة **النماذج + نقاط النهاية**، في علامة التبويب **عمليات توزيع النماذج**، في القائمة **+ نشر النموذج**، حدّد **توزيع النموذج الأساسي**.
4. ابحث عن نموذج **Phi-4-multimodal-instruct** في القائمة، ثم حدده وأكّده.
5. وافق على اتفاقية الترخيص إذا طلب منك ذلك، ثم وزّع النموذج بالإعدادات التالية عن طريق تحديد **تخصيص** في تفاصيل التوزيع:
    - **اسم التوزيع**: *اسم صالح توزيع نموذجك*
    - **نوع النشر**: معيار عالمي
    - **تفاصيل التوزيع**: *استخدام الإعدادات الافتراضية*
6. انتظر حتى تصبح حالة التزويد للتوزيع **مكتملة**.

## اختبر النموذج في مساحة التجربة

الآن بعد أن أصبح لديك توزيع نموذج متعدد الوسائط، يمكنك اختباره باستخدام مطالبة قائمة على الصورة في بيئة الدردشة.

1. في جزء التنقل على اليسار، حدد صفحة **مساحات التجربة** وافتح مساحة تجربة **الدردشة**
1. 1. في علامة تبويب المتصفح الجديدة، نزّل الملف [mango.jpeg](https://github.com/MicrosoftLearning/mslearn-ai-vision/raw/refs/heads/main/Labfiles/08-gen-ai-vision/mango.jpeg) من `https://github.com/MicrosoftLearning/mslearn-ai-vision/raw/refs/heads/main/Labfiles/08-gen-ai-vision/mango.jpeg` واحفظه في مجلد على نظام الملفات المحلي لديك.
1. في صفحة بيئة الدردشة، في جزء **الإعداد**، تأكد من تحديد توزيع نموذج **Phi-4-multimodal-instruct** الخاص بك.
1. في لوحة جلسة الدردشة الرئيسية، أسفل مربع إدخال الدردشة، استخدم زر الإرفاق (**&#128206;**) لتحميل ملف الصورة *mango.jpeg*، ثم أضف النص `What desserts could I make with this fruit?` وأرسل المطالبة.

    ![لقطة شاشة لبيئة الدردشة مع مطالبة قائمة على صورة.](../media/chat-playground-image.png)

1. راجع الرد، والذي من المفترض أن يوفر لك إرشادات ذات صلة بالحلويات التي يمكنك صنعها باستخدام المانجو.

## أنشئ تطبيق عميل

الآن بعد أن نشرت النموذج، يمكنك استخدام النشر في تطبيق عميل.

> **تلميح**: يمكنك اختيار تطوير الحل باستخدام لغة Python أو Microsoft C# *(قريبًا)*. اتبع الإرشادات في القسم المناسب للغة التي اخترتها.

### إعداد تكوين التطبيق

1. في مدخل مصنع الذكاء الاصطناعي في Azure، اعرض صفحة **النظرة العامة** لمشروعك.
2. في منطقة **تفاصيل المشروع**، لاحظ **سلسلة الاتصال للمشروع**. ستستخدم سلسلة الاتصال هذه للاتصال بمشروعك في تطبيق العميل.
3. افتح علامة تبويب جديدة للمتصفح (مع إبقاء مدخل مصنع الذكاء الاصطناعي في Azure مفتوحًا في علامة التبويب الموجودة). بعد ذلك في علامة التبويب الجديدة، انتقل إلى [بوابة Azure](https://portal.azure.com) على `https://portal.azure.com`؛ وسجّل الدخول باستخدام بيانات اعتماد Azure الخاصة بك إذا طُلب منك ذلك.

    أغلق أي إشعارات ترحيبية لرؤية الصفحة الرئيسية لبوابة Azure.

1. استخدم الزر **[\>_]** الموجود على يمين شريط البحث أعلى الصفحة لإنشاء Cloud Shell جديد في بوابة Azure، وتحديد بيئة ***PowerShell*** بدون مساحة تخزين في اشتراكك.

    يوفّر Cloud Shell واجهة سطر الأوامر في الجزء الموجود في أسفل بوابة Azure. يمكنك تغيير حجم هذا الجزء أو تكبيره لتسهيل العمل فيه.

    > **ملاحظة**: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة *معالج Bash*، فبدّل إلى ***PowerShell***.

5. في شريط أدوات Cloud Shell، في قائمة **الإعدادات**، حدد **الانتقال إلى الإصدار الكلاسيكي** (هذا مطلوب لاستخدام محرر التعليمات البرمجية).

    **<font color="red">تأكد من التبديل إلى الإصدار الكلاسيكي من cloud shell قبل المتابعة.</font>**

1. في جزء Cloud Shell، أدخل الأوامر التالية لاستنساخ مستودع GitHub الذي يحتوي على ملفات التعليمات البرمجية لهذا التمرين (اكتب الأمر أو انسخه إلى الحافظة ثم انقر بزر الماوس الأيمن في سطر الأوامر وقم بلصقه كنص عادي):


    ```
    rm -r mslearn-ai-vision -f
    git clone https://github.com/MicrosoftLearning/mslearn-ai-vision
    ```

    > **تلميح**: عند لصق الأوامر في CloudShell، قد يشغل الإخراج مساحة كبيرة من ذاكرة التخزين المؤقت للشاشة. يمكنك مسح الشاشة عن طريق إدخال الأمر `cls` لتسهيل التركيز على كل مهمة.

7. بعد استنساخ مخزن بيانات خاصة، انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية لتطبيق الدردشة:  

    **Python**

    ```
   cd mslearn-ai-vision/Labfiles/08-gen-ai-vision/python
    ```

    **C#**

    ```
   cd mslearn-ai-vision/Labfiles/08-gen-ai-vision/c-sharp
    ```

8. في جزء سطر أوامر Cloud Shell، أدخل الأمر التالي لتثبيت المكتبات التي ستستخدمها:

    **Python**

    ```
   python -m venv labenv
   ./labenv/bin/Activate.ps1
   pip install python-dotenv azure-identity azure-ai-projects azure-ai-inference
    ```

    **C#**

    ```
   dotnet add package Azure.Identity
   dotnet add package Azure.AI.Inference --version 1.0.0-beta.3
   dotnet add package Azure.AI.Projects --version 1.0.0-beta.3
    ```

9. أدخل الأمر التالي لتحرير ملف التكوين الذي تم توفيره:

    **Python**

    ```
   code .env
    ```

    **C#**

    ```
   code appsettings.json
    ```

    يتم فتح الملف في محرر التعليمات البرمجية.

10. في ملف التعليمات البرمجية، استبدل العنصر النائب **your_project_connection_string** بسلسلة الاتصال الخاصة بمشروعك (المنسوخة من صفحة **نظرة عامة** على المشروع في بوابة Azure AI Foundry)، واستبدل العنصر النائب **your_model_deployment** بالاسم الذي قمت بتعيينه لتوزيع نموذج Phi-4-multimodal-instruct الخاص بك.
11. بعد استبدال العناصر النائبة في محرر التعليمات البرمجية، استخدم الأمر **CTRL+S** أو **انقر زر الماوس الأيمن > حفظ** لحفظ التغييرات ثم استخدم الأمر **CTRL+Q** أو **انقر زر الماوس الأيمن > خروج** لإغلاق محرر التعليمات البرمجية مع إبقاء سطر أوامر Cloud Shell مفتوحًا.

### اكتب التعليمة البرمجية للاتصال بمشروعك والحصول على عميل دردشة لنموذجك

> **تلميح**: عند إضافة التعليمات البرمجية، تأكد من الحفاظ على المسافة البادئة الصحيحة.

1. أدخل الأمر التالي لتحرير ملف التعليمات البرمجية الذي تم توفيره:

    **Python**

    ```
   code chat-app.py
    ```

    **C#**

    ```
   code Program.cs
    ```

2. في ملف التعليمات البرمجية، لاحظ العبارات الموجودة في أعلى الملف والتي تمت إضافتها لاستيراد مساحات الأسماء (Namespaces) الضرورية لـ (SDK). بعد ذلك، ابحث عن التعليق **إضافة المراجع**، وأضف التعليمة البرمجية التالية للإشارة إلى المساحات الأساسية في المكتبات التي قمت بتثبيتها مسبقًا:

    **Python**

    ```python
   # Add references
   from dotenv import load_dotenv
   from azure.identity import DefaultAzureCredential
   from azure.ai.projects import AIProjectClient
   from azure.ai.inference.models import (
        SystemMessage,
        UserMessage,
        TextContentItem,
        ImageContentItem,
        ImageUrl,
   )
    ```

    **C#**

    ```csharp
   // Add references
   using Azure.Identity;
   using Azure.AI.Projects;
   using Azure.AI.Inference;
    ```

3. في الوظيفة **الرئيسية**، تحت التعليق **الحصول على إعدادات التكوين**، لاحظ أن التعليمة البرمجية تقوم بتحميل قيم سلسلة الاتصال بالمشروع واسم نشر النموذج التي قمت بتحديدها في ملف التكوين.
4. ابحث عن التعليق **تهيئة عميل المشروع**، وأضف التعليمة البرمجية التالية للاتصال بمشروع Azure AI Foundry الخاص بك باستخدام بيانات اعتماد Azure التي قمت بتسجيل الدخول بها حاليًا:

    **Python**

    ```python
   # Initialize the project client
   project_client = AIProjectClient.from_connection_string(
        conn_str=project_connection,
        credential=DefaultAzureCredential())
    ```

    **C#**

    ```csharp
   // Initialize the project client
   var projectClient = new AIProjectClient(project_connection,
                        new DefaultAzureCredential());
    ```

5. ابحث عن التعليق **الحصول على عميل دردشة**، وأضف التعليمة البرمجية التالية لإنشاء عنصر عميل للدردشة مع النموذج الخاص بك:

    **Python**

    ```python
   # Get a chat client
   chat_client = project_client.inference.get_chat_completions_client(model=model_deployment)
    ```

    **C#**

    ```csharp
   // Get a chat client
   ChatCompletionsClient chat = projectClient.GetChatCompletionsClient();
    ```

### اكتب تعليمة برمجية لإرسال مطالبة صورة تعتمد على عنوان URL

1. لاحظ أن التعليمات البرمجية تتضمن تكرار حلقي للسماح للمستخدم بإدخال مطالبة حتى يدخل "إنهاء". بعد ذلك في قسم التكرار، ابحث عن التعليق **الحصول على رد لإدخال الصورة**، وأضف التعلية البرمجية التالية لإرسال مطالبة تتضمن الصورة التالية:

    ![صورة المانجو.](../media/orange.jpeg)

    **Python**

    ```python
   # Get a response to image input
   image_url = "https://github.com/MicrosoftLearning/mslearn-ai-vision/raw/refs/heads/main/Labfiles/08-gen-ai-vision/orange.jpeg"
   image_format = "jpeg"
   request = Request(image_url, headers={"User-Agent": "Mozilla/5.0"})
   image_data = base64.b64encode(urlopen(request).read()).decode("utf-8")
   data_url = f"data:image/{image_format};base64,{image_data}"

   response = chat_client.complete(
        messages=[
            SystemMessage(system_message),
            UserMessage(content=[
                TextContentItem(text=prompt),
                ImageContentItem(image_url=ImageUrl(url=data_url))
            ]),
        ]
   )
   print(response.choices[0].message.content)
    ```

    **C#**

    ```csharp
   // Get a response to image input
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
   Console.WriteLine(response.Value.Content);
    ```

2. استخدم الأمر **CTRL+S** لحفظ التغييرات في ملف التعليمات البرمجية، لكن لا تغلقه بعد.

3. في جزء سطر أوامر Cloud Shell أسفل محرر التعليمات البرمجية، أدخل الأمر التالي لتشغيل التطبيق:

    **Python**

    ```
   python chat-app.py
    ```

    **C#**

    ```
   dotnet run
    ```

4. عند طلب بذلك، أدخل المطالبة التالية:

    ```
   Suggest some recipes that include this fruit
    ```

5. راجع الاستجابة. ثم أدخل `quit` للخروج من البرنامج.

### تعديل التعليمة البرمجية لتحميل ملف صورة محلي

1. في محرر التعليمات البرمجية الخاص بكود تطبيقك، في قسم التكرار، ابحث عن التعليمة البرمجية الذي أضفتها مسبقًا ضمن التعليق **الحصول على رد لإدخال الصورة**. ثم عدّل التعليمات البرمجية كما يلي، لتحميل ملف الصورة المحلي هذا:

    ![صورة لفاكهة التنين.](../media/mystery-fruit.jpeg)

    **Python**

    ```python
   # Get a response to image input
   script_dir = Path(__file__).parent  # Get the directory of the script
   image_path = script_dir / 'mystery-fruit.jpeg'
   mime_type = "image/jpeg"

    # Read and encode the image file
    with open(image_path, "rb") as image_file:
        base64_encoded_data = base64.b64encode(image_file.read()).decode('utf-8')

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
    print(response.choices[0].message.content)
    ```

    **C#**

    ```csharp
   // Get a response to image input
   string imagePath = "mystery-fruit.jpeg";
   string mimeType = "image/jpeg";
    
   // Read and encode the image file
   byte[] imageBytes = File.ReadAllBytes(imagePath);
   var binaryImage = new BinaryData(imageBytes);
    
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
   Console.WriteLine(response.Value.Content);
    ```

2. استخدم الأمر **CTRL+S** لحفظ التغييرات في ملف التعليمات البرمجية. يمكنك أيضًا إغلاق محرر التعليمات البرمجية باستخدام (**CTRL+Q**) إذا رغبت في ذلك.

3. في جزء سطر أوامر Cloud Shell أسفل محرر التعليمات البرمجية، أدخل الأمر التالي لتشغيل التطبيق:

    **Python**

    ```
   python chat-app.py
    ```

    **C#**

    ```
   dotnet run
    ```

4. عند طلب بذلك، أدخل المطالبة التالية:

    ```
   What is this fruit? What recipes could I use it in?
    ```

5. راجع الاستجابة. ثم أدخل `quit` للخروج من البرنامج.

    > **ملاحظة**: في هذا التطبيق البسيط، لم ننفّذ منطق للاحتفاظ بسجل المحادثة؛ لذلك سيعامل النموذج كل مطالبة على أنها طلب جديد دون أي سياق للمطالبة السابقة.

## استكشف المزيد: (إذا سمح الوقت)

لقد تعلمت كيفية استخدام Azure AI Inference SDK ونموذج متعدد الوسائط لتنفيذ تطبيق الذكاء الاصطناعي التوليدي الذي يمكنه الرد على المطالبات القائمة على الصور. إذا كان لديك الوقت، فإليك بعض الأفكار لمزيد من الاستكشاف.

### استخدم نموذجًا متعدد الوسائط مختلفًا

لقد استخدمت نموذج *Phi-4-multimodal-instruct* لتوليد رد لمطالبة قائمة على صورة. الآن دعونا نجرب نموذج OpenAI *gpt-4o*.

1. في Azure AI Foundry، وزّع نموذج **gpt-4o** إلى نقطة نهاية استدلال نموذج الذكاء الاصطناعي في Azure (قد تحتاج إلى إنشاء مورد جديد في منطقة مختلفة).
1. حدّث ملف تكوين التعلميات البرمجية الخاصة بتطبيقك (*.env* لـ Python، و*appsettings.json* لـ C#) لتحديد اسم نموذج gpt-4o الخاص بك.
1. شغّل التطبيق كما في السابق، باستخدام نفس المطالبات (يمكنك الرجوع إلى التعليمات البرمجية التي تستخدم صورة تعتمد على عنوان URL إذا شئت).

### استخدام واجهات برمجة تطبيقات OpenAI

تعتمد التعليمات البرمجية التي استخدمتها في هذا التمرين على Azure AI Inference SDK، والذي يعمل مع أي نموذج تم توزيعه على نقطة نهاية استدلال نموذج الذكاء الاصطناعي في Azure. عند استخدام نموذج OpenAI، يمكنك بدلًا من ذلك استخدام OpenAI SDK.

تفترض التعليمات التالية أنك أكملت هذا التمرين والمهمة الإضافية أعلاه لتوزيع نموذج **gpt-4o** واختباره.

1. قم بتثبيت (أو تحديث) الحزم الضرورية لتطبيقك:

    **Python**

    ```
   python -m venv labenv
   ./labenv/bin/Activate.ps1
   pip install python-dotenv azure-identity azure-ai-projects openai
    ```
    
    **C#**

    ```
   dotnet add package Azure.Identity
   dotnet add package Azure.AI.Projects --prerelease
   dotnet add package Azure.AI.OpenAI --prerelease
    ```

1. حدّث مساحات الأسماء في ملف التعليمات البرمجية الخاص بك (إزالة المراجع *azure.ai-inference*):

    **Python**

    ```python
   # Add references
   from dotenv import load_dotenv
   from azure.identity import DefaultAzureCredential
   from azure.ai.projects import AIProjectClient
   import openai
    ```

    **C#**

    ```csharp
   // Add references
   using Azure.Identity;
   using Azure.AI.Projects;
   using OpenAI.Chat;
   using Azure.AI.OpenAI;
    ```

1. تعديل التعليمات البرمجية للحصول على عميل دردشة:

    **Python**

    ```python
   # Get a chat client
   chat_client = project_client.inference.get_azure_openai_client(api_version="2024-10-21")
    ```

    **C#**

    ```csharp
   // Get a chat client
   ChatClient chatClient = projectClient.GetAzureOpenAIChatClient(model_deployment);
    ```

1. تعديل التعليمات البرمجية للحصول على إكمال استنادًا إلى ملف صورة محلي

    **Python**

    ```python
   # Get a response to image input
   script_dir = Path(__file__).parent  # Get the directory of the script
   image_path = script_dir / 'mystery-fruit.jpeg'
   mime_type = "image/jpeg"

   # Read and encode the image file
   with open(image_path, "rb") as image_file:
        base64_encoded_data = base64.b64encode(image_file.read()).decode('utf-8')

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
   print(completion)
    ```

    **C#**

    ```csharp
   // Get a response to image input
   string imagePath = "mystery-fruit.jpeg";
   string mimeType = "image/jpeg";
    
   // Read and encode the image file
   byte[] imageBytes = File.ReadAllBytes(imagePath);
   var binaryImage = new BinaryData(imageBytes);

   // Include the image file data in the prompt
   List<ChatMessage> messages =
   [
        new SystemChatMessage(system_message),
        new UserChatMessage(
            ChatMessageContentPart.CreateTextPart(prompt),
            ChatMessageContentPart.CreateImagePart(binaryImage, mimeType)),
   ];

   ChatCompletion completion = chatClient.CompleteChat(messages);
   Console.WriteLine(completion.Content[0].Text);
    ```

1. احفظ تغييراتك وشغّل التطبيق لاختباره بنفس المطالبات التي استخدمتها سابقًا.

## تنظيف

إذا كنت قد أنهيت استكشاف Azure AI Foundry، يجب عليك حذف الموارد التي أنشأتها في هذا التمرين لتجنب تكاليف Azure غير الضرورية.

1. ارجع إلى علامة تبويب المتصفح التي تحتوي على بوابة Azure (أو أعد فتح [بوابة Azure](https://portal.azure.com) في `https://portal.azure.com` في علامة تبويب متصفح جديدة) واعرض محتويات مجموعة الموارد التي نشرت فيها الموارد المستخدمة في هذا التدريب.
1. على شريط الأدوات، حدد **حذف مجموعة الموارد**.
1. أدخل اسم مجموعة الموارد وأكّد أنك تريد حذفها.
