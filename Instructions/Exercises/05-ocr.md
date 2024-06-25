---
lab:
  title: قراءة النص في الصور
  module: Module 11 - Reading Text in Images and Documents
---

# قراءة النص في الصور

التعرّف البصري على الحروف (OCR) هو مجموعة فرعية من رؤية الكمبيوتر التي تتعامل مع قراءة النص في الصور والمستندات. توفر خدمة **الذكاء الاصطناعي في Azure Vision** واجهة برمجة التطبيقات (API) لقراءة النص، والتي ستستكشفها في هذا التمرين.

## استنساخ المستودع لهذه الدورة التدريبية

إذا لم تستنسخ بالفعل، يجب عليك استنساخ مستودع التعليمات البرمجية لهذه الدورة التدريبية:

1. ابدأ تشغيل Visual Studio Code.
2. افتح لوحة (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع `https://github.com/MicrosoftLearning/mslearn-ai-vision` إلى مجلد محلي (لا يُهم أي مجلد).
3. عند استنساخ المستودع، افتح المجلد في تعليمة Visual Studio البرمجية.
4. انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.

    > **ملاحظة**: إذا جرت مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد **ليس الآن**. إذا جرت مطالبتك برسالة *اكتشاف مشروع وظيفة Azure في المجلد*، يمكنك إغلاق هذه الرسالة بأمان.

## توفير مورد خدمات الذكاء الاصطناعي في Azure

إذا لم يكن لديك بالفعل مورد في اشتراكك، فسيتعين عليك توفير مورد **خدمات الذكاء الاصطناعي في Azure**.

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.
2. في شريط البحث العلوي، ابحث عن *خدمات الذكاء الاصطناعي في Azure*، وحدد **خدمات الذكاء الاصطناعي في Azure**، وأنشئ مورد حساب متعدد الخدمات لخدمات الذكاء الاصطناعي في Azure بالإعدادات التالية:
    - **Subscription**: *اشتراكك في Azure*
    - **مجموعة الموارد**: *اختر أو أنشئ مجموعة موارد (إذا كنت تستخدم اشتراكاً مقيداً، فقد لا يكون لديك إذن لإنشاء مجموعة موارد جديدة - استخدم المجموعة المتوفرة)*
    - **المنطقة**: *اختر من شرق الولايات المتحدة أو فرنسا الوسطى أو كوريا الوسطى أو شمال أوروبا أو جنوب شرق آسيا أو غرب أوروبا أو غرب الولايات المتحدة أو شرق آسيا\**
    - **الاسم**: *أدخل اسماً فريداً*
    - **مستوى التسعير**: قياسي S0

    \*تتوفر ميزات Azure AI Vision 4.0 حالياً في هذه المناطق فقط.

3. حدد مربعات الاختيار المطلوبة ثم أنشئ المورد.
4. انتظر حتى يكتمل النشر، ثم اعرض تفاصيل النشر.
5. عند نشر المورد، انتقل إليه واعرض **صفحة المفاتيح ونقطة النهاية** الخاصة به. ستحتاج إلى نقطة النهاية وأحد المفاتيح من هذه الصفحة في الإجراء التالي.

## الاستعداد لاستخدام Azure AI Vision SDK

في هذا التمرين، ستكمل تطبيق عميل جرى تنفيذه جزئياً يستخدم Azure AI Vision SDK لقراءة النص.

> **ملاحظة**: يمكنك اختيار استخدام SDK إما لـ **C#** أو **Python**. في الخطوات التالية، نفذ الإجراءات المناسبة للغتك المفضلة.

1. في تعليمة Visual Studio البرمجية في جزء **Explorer**، استعرض للوصول إلى المجلد **Labfiles\05-ocr** ووسع المجلد **C-Sharp** أو **Python** وفقاً لتفضيلات اللغة لديك.
2. انقر بزر الماوس الأيمن فوق مجلد **read-text** وافتح محطة طرفية متكاملة. ثم عليك تثبيت حزمة Azure AI Vision SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:

    **C#**
    
    ```
    dotnet add package Azure.AI.Vision.ImageAnalysis -v 1.0.0-beta.1
    ```

    > **ملاحظة**: إذا جرت مطالبتك بتثبيت ملحقات مجموعة أدوات التطوير، يمكنك إغلاق الرسالة بأمان.

    **Python**
    
    ```
    pip install azure-ai-vision-imageanalysis==1.0.0b1
    ```

3. اعرض محتويات مجلد **read-text**، ولاحظ أنه يحتوي على ملف لإعدادات التكوين:

    - **C#**: appsettings.json
    - **Python**: .env

    يمكنك فتح ملف التكوين وتحديث قيم التكوين التي يحتوي عليها لتعكس **نقطة النهاية** و**مفتاح** المصادقة لمورد خدمات الذكاء الاصطناعي في Azure. احفظ تغييراتك.


## استخدم Azure AI Vision SDK لقراءة النص من الصورة

إحدى ميزات **Azure AI Vision SDK** هي قراءة النص من الصورة. في هذا التمرين، ستكمل تطبيق عميل جرى تنفيذه جزئياً يستخدم Azure AI Vision SDK لقراءة النص من صورة.

1. لاحظ أن مجلد **read-text** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: read-text.py

    افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Azure AI Vision SDK:

    **C#**
    
    ```C#
    // Import namespaces
    using Azure.AI.Vision.ImageAnalysis;
    ```
    
    **Python**
    
    ```Python
    # import namespaces
    from azure.ai.vision.imageanalysis import ImageAnalysisClient
    from azure.ai.vision.imageanalysis.models import VisualFeatures
    from azure.core.credentials import AzureKeyCredential
    ```

2. في ملف التعليمات البرمجية لتطبيق العميل الخاص بك، في الدالة **الرئيسية**، جرى توفير التعليمات البرمجية لتحميل إعدادات التكوين. ثم ابحث عن التعليق **مصادقة عميل الذكاء الاصطناعي في Azure Vision**. ثم، ضمن هذا التعليق، أضف التعليمات البرمجية الخاصة باللغة التالية لإنشاء عنصر عميل الذكاء الاصطناعي في Azure Vision ومصادقته:

    **C#**
    
    ```C#
    // Authenticate Azure AI Vision client
    ImageAnalysisClient client = new ImageAnalysisClient(
        new Uri(aiSvcEndpoint),
        new AzureKeyCredential(aiSvcKey));
    ```
    
    **Python**
    
    ```Python
    # Authenticate Azure AI Vision client
    cv_client = ImageAnalysisClient(
        endpoint=ai_endpoint,
        credential=AzureKeyCredential(ai_key)
    )
    ```

3. في الدالة **الرئيسية**، ضمن التعليمات البرمجية التي أضفتها للتو، لاحظ أن التعليمات البرمجية تحدد المسار إلى ملف صورة ثم تمرر مسار الصورة إلى دالة **GetTextRead**. لم تُنفذ هذه الدالة بالكامل بعد.

4. لنضيف بعض التعليمات البرمجية إلى نص دالة **GetTextRead**. ابحث عن التعليق **استخدم دالة تحليل الصورة لقراءة النص في الصورة**. ثم، ضمن هذا التعليق، أضف التعليمات البرمجية الخاصة باللغة التالية، مع ملاحظة تحديد الميزات المرئية عند استدعاء الدالة `Analyze`:

    **C#**

    ```C#
    // Use Analyze image function to read text in image
    ImageAnalysisResult result = client.Analyze(
        BinaryData.FromStream(stream),
        // Specify the features to be retrieved
        VisualFeatures.Read);
    
    stream.Close();
    
    // Display analysis results
    if (result.Read != null)
    {
        Console.WriteLine($"Text:");
    
        // Prepare image for drawing
        System.Drawing.Image image = System.Drawing.Image.FromFile(imageFile);
        Graphics graphics = Graphics.FromImage(image);
        Pen pen = new Pen(Color.Cyan, 3);
        
        foreach (var line in result.Read.Blocks.SelectMany(block => block.Lines))
        {
            // Return the text detected in the image
    
    
        }
            
        // Save image
        String output_file = "text.jpg";
        image.Save(output_file);
        Console.WriteLine("\nResults saved in " + output_file + "\n");   
    }
    ```
    
    **Python**
    
    ```Python
    # Use Analyze image function to read text in image
    result = cv_client.analyze(
        image_data=image_data,
        visual_features=[VisualFeatures.READ]
    )

    # Display the image and overlay it with the extracted text
    if result.read is not None:
        print("\nText:")

        # Prepare image for drawing
        image = Image.open(image_file)
        fig = plt.figure(figsize=(image.width/100, image.height/100))
        plt.axis('off')
        draw = ImageDraw.Draw(image)
        color = 'cyan'

        for line in result.read.blocks[0].lines:
            # Return the text detected in the image

            
        # Save image
        plt.imshow(image)
        plt.tight_layout(pad=0)
        outputfile = 'text.jpg'
        fig.savefig(outputfile)
        print('\n  Results saved in', outputfile)
    ```

5. في الرمز الذي أضفته للتو في دالة **GetTextRead**، وضمن **إرجاع النص المكتشف في تعليق الصورة**، أضف الرمز التالي (يطبع هذا الرمز نص الصورة إلى وحدة التحكم وينشئ صورة **text.jpg** التي تسلط الضوء على نص الصورة) :

    **C#**
    
    ```C#
    // Return the text detected in the image
    Console.WriteLine($"   '{line.Text}'");
    
    // Draw bounding box around line
    var drawLinePolygon = true;
    
    // Return the position bounding box around each line
    
    
    
    // Return each word detected in the image and the position bounding box around each word with the confidence level of each word
    
    
    
    // Draw line bounding polygon
    if (drawLinePolygon)
    {
        var r = line.BoundingPolygon;
    
        Point[] polygonPoints = {
            new Point(r[0].X, r[0].Y),
            new Point(r[1].X, r[1].Y),
            new Point(r[2].X, r[2].Y),
            new Point(r[3].X, r[3].Y)
        };
    
        graphics.DrawPolygon(pen, polygonPoints);
    }
    ```
    
    **Python**
    
    ```Python
    # Return the text detected in the image
    print(f"  {line.text}")    
    
    drawLinePolygon = True
    
    r = line.bounding_polygon
    bounding_polygon = ((r[0].x, r[0].y),(r[1].x, r[1].y),(r[2].x, r[2].y),(r[3].x, r[3].y))
    
    # Return the position bounding box around each line
    
    
    # Return each word detected in the image and the position bounding box around each word with the confidence level of each word
    
    
    # Draw line bounding polygon
    if drawLinePolygon:
        draw.polygon(bounding_polygon, outline=color, width=3)
    ```

6. في مجلد **read-text/images**، حدد **Lincoln.jpg** لعرض الملف الذي تعالجه التعليمات البرمجية.

7. في ملف التعليمات البرمجية للتطبيق الخاص بك، في الدالة **الرئيسية**، افحص التعليمات البرمجية التي يجري تشغيلها إذا حدد المستخدم خيار القائمة **1**. تستدعي هذه التعليمة البرمجية الدالة **GetTextRead**، لتمرير المسار إلى ملف الصورة *Lincoln.jpg*.

8. احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد **read-text**، وأدخل الأمر التالي لتشغيل البرنامج:

    **C#**
    
    ```
    dotnet run
    ```
    
    **Python**
    
    ```
    python read-text.py
    ```

9. عند المطالبة، أدخل **1** ولاحظ الإخراج، وهو النص المستخرج من الصورة.

10. في مجلد **read-text**، حدد صورة **text.jpg** ولاحظ وجود مضلع حول كل *سطر* من النص.

11. ارجع إلى ملف التعليمات البرمجية في تعليمة Visual Studio البرمجية وابحث عن التعليق **إرجاع مربع إحاطة الموضع حول كل سطر**. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية التالية:

    **C#**
    
    ```C#
    // Return the position bounding box around each line
    Console.WriteLine($"   Bounding Polygon: [{string.Join(" ", line.BoundingPolygon)}]");  
    ```
    
    **Python**
    
    ```Python
    # Return the position bounding box around each line
    print("   Bounding Polygon: {}".format(bounding_polygon))
    ```

12. احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد **read-text**، وأدخل الأمر التالي لتشغيل البرنامج:

    **C#**
    
    ```
    dotnet run
    ```
    
    **Python**
    
    ```
    python read-text.py
    ```

13. عند المطالبة، أدخل **1** ولاحظ الإخراج الذي يجب أن يكون كل سطر من النص في الصورة مع موضع كل منها في الصورة.


14. ارجع إلى ملف التعليمات البرمجية في تعليمة Visual Studio البرمجية وابحث عن التعليق **إرجاع كل كلمة مكتشفة في الصورة ومربع إحاطة الموضع حول كل كلمة بمستوى الثقة لكل كلمة**. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية التالية:

    **C#**
    
    ```C#
    // Return each word detected in the image and the position bounding box around each word with the confidence level of each word
    foreach (DetectedTextWord word in line.Words)
    {
        Console.WriteLine($"     Word: '{word.Text}', Confidence {word.Confidence:F4}, Bounding Polygon: [{string.Join(" ", word.BoundingPolygon)}]");
        
        // Draw word bounding polygon
        drawLinePolygon = false;
        var r = word.BoundingPolygon;
    
        Point[] polygonPoints = {
            new Point(r[0].X, r[0].Y),
            new Point(r[1].X, r[1].Y),
            new Point(r[2].X, r[2].Y),
            new Point(r[3].X, r[3].Y)
        };
    
        graphics.DrawPolygon(pen, polygonPoints);
    }
    ```
    
    **Python**
    
    ```Python
    # Return each word detected in the image and the position bounding box around each word with the confidence level of each word
    for word in line.words:
        r = word.bounding_polygon
        bounding_polygon = ((r[0].x, r[0].y),(r[1].x, r[1].y),(r[2].x, r[2].y),(r[3].x, r[3].y))
        print(f"    Word: '{word.text}', Bounding Polygon: {bounding_polygon}, Confidence: {word.confidence:.4f}")
    
        # Draw word bounding polygon
        drawLinePolygon = False
        draw.polygon(bounding_polygon, outline=color, width=3)
    ```

15. احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد **read-text**، وأدخل الأمر التالي لتشغيل البرنامج:

    **C#**
    
    ```
    dotnet run
    ```
    
    **Python**
    
    ```
    python read-text.py
    ```

16. عند المطالبة، أدخل **1** ولاحظ الإخراج الذي يجب أن يكون كل كلمة من النص في الصورة مع موضع كل منها في الصورة. لاحظ كيفية إرجاع مستوى الثقة لكل كلمة أيضاً.

17. في مجلد **read-text**، حدد صورة **text.jpg** ولاحظ كيف يوجد مضلع حول كل *كلمة*.

## استخدم Azure AI Vision SDK لقراءة النص من الصورة

في التمرين السابق، تقرأ نصا محدداً جيداً من صورة، ولكن في بعض الأحيان قد ترغب أيضاً في قراءة النص من الملاحظات أو الأوراق المكتوبة بخط اليد. والخبر السار هو أن **Azure AI Vision SDK** يمكنها أيضاً قراءة النص المكتوب بخط اليد بنفس الرمز الدقيق الذي استخدمته لقراءة نص محدد جيداً. سنستخدم التعليمات البرمجية نفسها من التمرين السابق، ولكن هذه المرة سنستخدم صورة مختلفة.

1. في مجلد **read-text/images**، حدد **Note.jpg** لعرض الملف الذي يعالجه الرمز الخاص بك.

2. في ملف التعليمات البرمجية للتطبيق الخاص بك، في الدالة **الرئيسية**، افحص التعليمات البرمجية التي يجري تشغيلها إذا حدد المستخدم خيار القائمة **2**. تستدعي هذه التعليمة البرمجية الدالة **GetTextRead**، لتمرير المسار إلى ملف الصورة *Note.jpg*.

3. من الوحدة الطرفية المدمجة لمجلد **read-text**، أدخل الأمر التالي لتشغيل البرنامج:

    **C#**
    
    ```
    dotnet run
    ```
    
    **Python**
    
    ```
    python read-text.py
    ```

4. عند المطالبة، أدخل **2** ولاحظ الإخراج، وهو النص المستخرج من صورة الملاحظة.

5. في مجلد **read-text**، حدد صورة **text.jpg** ولاحظ كيف يوجد مضلع حول كل *كلمة* في الملاحظة.

## تنظيف الموارد

إذا كنت لا تستخدم موارد Azure التي أنشأتها في هذا المختبر لوحدات التدريب الأخرى، فيمكنك حذفها لتجنب تكبد المزيد من الرسوم. وإليك الطريقة:

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.

2. في شريط البحث العلوي، ابحث عن *حساب متعدد الخدمات لخدمات الذكاء الاصطناعي في Azure* وحدد مورد الحساب متعدد الخدمات لخدمات الذكاء الاصطناعي في Azure الذي أنشأته في هذا التمرين المعملي

3. في صفحة المورد، حدد **حذف** واتبع الإرشادات لحذف المورد.

## مزيد من المعلومات

لمزيد من المعلومات حول استخدام خدمة **الذكاء الاصطناعي في Azure Vision** لقراءة النص، راجع [وثائق الذكاء الاصطناعي في Azure Vision](https://learn.microsoft.com/azure/ai-services/computer-vision/concept-ocr).
