---
lab:
  title: قراءة النص في الصور
  module: Module 11 - Reading Text in Images and Documents
---

# قراءة النص في الصور

التعرّف البصري على الحروف (OCR) هو مجموعة فرعية من رؤية الكمبيوتر التي تتعامل مع قراءة النص في الصور والمستندات. توفر خدمة **الذكاء الاصطناعي في Azure Vision** واجهة برمجة التطبيقات (API) لقراءة النص، والتي ستستكشفها في هذا التمرين.

## توفير مورد لرؤية الكمبيوتر

إذا لم يكن لديك مورد **Computer Vision** في اشتراكك بالفعل، فستحتاج إلى إنشائه.

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.
1. حدد **Create a resource.**
1. في شريط البحث، ابحث عن *Computer Vision*، ثم حدد **Computer Vision**، وأنشئ المورد باستخدام الإعدادات التالية:
    - **Subscription**: *اشتراكك في Azure*
    - **مجموعة الموارد**: *اختر أو أنشئ مجموعة موارد (إذا كنت تستخدم اشتراكاً مقيداً، فقد لا يكون لديك إذن لإنشاء مجموعة موارد جديدة - استخدم المجموعة المتوفرة)*
    - **المنطقة**: *اختر من بين شرق الولايات المتحدة أو غرب الولايات المتحدة أو وسط فرنسا أو وسط كوريا أو شمال أوروبا أو جنوب شرق آسيا أو غرب أوروبا أو شرق آسيا\**
    - **الاسم**: *أدخل اسماً فريداً*
    - **مستوى التسعير**: مجاني (F0)

    \*تتوفر ميزات الذكاء الاصطناعي في Azure اصدار 4.0 حالياً في هذه المناطق فقط.

1. حدد مربعات الاختيار المطلوبة ثم أنشئ المورد.
1. انتظر حتى يكتمل النشر، ثم اعرض تفاصيل النشر.
1. عند نشر المورد، انتقل إليه واعرض **صفحة المفاتيح ونقطة النهاية** الخاصة به. ستحتاج إلى نقطة النهاية وأحد المفاتيح من هذه الصفحة في الإجراء التالي.

## استنساخ المستودع لهذه الدورة التدريبية

ستقوم بتطوير التعليمات البرمجية الخاصة بك باستخدام Cloud Shell من بوابة Azure. تم توفير ملفات التعليمات البرمجية لتطبيقك في GitHub repo.

> **تلميح**: إذا كنت قد نسخت المستودع **mslearn-ai-vision** مؤخرًا بالفعل، فيمكنك تخطي هذه المهمة. وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة تطويرك.

1. في بوابة Azure، استخدم الزر **[\>_]** على يمين شريط البحث أعلى الصفحة لإنشاء Cloud Shell جديد في بوابة Azure، وتحديد بيئة ***PowerShell***. يوفّر Cloud Shell واجهة سطر أوامر في جزء أسفل بوابة Azure.

    > **ملاحظة**: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة *معالج Bash*، فبدّل إلى ***PowerShell***.

1. في شريط أدوات Cloud Shell، في قائمة **الإعدادات**، حدد **الانتقال إلى الإصدار الكلاسيكي** (هذا مطلوب لاستخدام محرر التعليمات البرمجية).

    > **تلميح**: عند لصق الأوامر في CloudShell، قد يشغل الإخراج مساحة كبيرة من ذاكرة التخزين المؤقت للشاشة. يمكنك مسح الشاشة عن طريق إدخال الأمر `cls` لتسهيل التركيز على كل مهمة.

1. في جزء PowerShell، أدخل الأوامر التالية لاستنساخ مستودع GitHub لهذا التمرين:

    ```
    rm -r mslearn-ai-vision -f
    git clone https://github.com/microsoftlearning/mslearn-ai-vision mslearn-ai-vision
    ```

1. بعد استنساخ مخزن بيانات خاصة، انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية لتطبيق الدردشة:  

    ```
   cd mslearn-ai-vision/Labfiles/05-ocr
    ```

## الاستعداد لاستخدام Azure AI Vision SDK

في هذا التمرين، ستكمل تطبيق عميل جرى تنفيذه جزئياً يستخدم Azure AI Vision SDK لقراءة النص.

> **ملاحظة**: يمكنك اختيار استخدام SDK إما لـ **C#** أو **Python**. في الخطوات الواردة أدناه، نفذ الإجراءات المناسبة للغتك المفضلة.

1. انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية للتطبيق بلغتك المفضلة:  

    **C#**

    ```
   cd C-Sharp/read-text
    ```
    
    **Python**

    ```
   cd Python/read-text
    ```

1. ثبِّت حزمة عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Vision والتبعيات المطلوبة عن طريق تشغيل الأوامر المناسبة لتفضيل اللغة:

    **C#**
    
    ```
    dotnet add package Azure.AI.Vision.ImageAnalysis -v 1.0.0
    dotnet add package SkiaSharp --version 3.116.1
    dotnet add package SkiaSharp.NativeAssets.Linux --version 3.116.1
    ``` 

    **Python**
    
    ```
    pip install azure-ai-vision-imageanalysis==1.0.0
    pip install dotenv
    pip install matplotlib
    ```

1. باستخدام الأمر "`ls`"، يمكنك عرض محتويات المجلد **computer-vision**. لاحظ أنه يحتوي على ملف لإعدادات التكوين:

    - **C#**: appsettings.json
    - **Python**: .env

1. أدخل الأمر التالي لتحرير ملف التكوين الذي تم توفيره:

    **C#**

    ```
   code appsettings.json
    ```

    **Python**

    ```
   code .env
    ```

    يتم فتح الملف في محرر التعليمات البرمجية.

1. في ملف التعليمات البرمجية، حدّث قيم التكوين في الملف لتعكس **نقطة النهاية** **ومفتاح** مصادقة لمورد Computer Vision.
1. بعد استبدال العناصر النائبة، استخدم الأمر **CTRL+S** أو **Right-click > Save** لحفظ التغييرات ثم استخدم الأمر **CTRL+Q** أو **Right-click > Quit** لإغلاق محرر التعليمات البرمجية مع إبقاء سطر أوامر Cloud Shell مفتوحًا.

## استخدم Azure AI Vision SDK لقراءة النص من الصورة

إحدى ميزات **الذكاء الاصطناعي في Azure Vision SDK** هي قراءة النص من صورة. في هذا التمرين، ستكمل تطبيق عميل جرى تنفيذه جزئياً يستخدم Azure AI Vision SDK لقراءة النص من صورة.

1. لاحظ أن مجلد **read-text** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: read-text.py

    افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Azure AI Vision SDK:

    **C#**
    
    ```C#
    // Import namespaces
    using Azure.AI.Vision.ImageAnalysis;
    using SkiaSharp;
    ```
    
    **Python**
    
    ```Python
    # import namespaces
    from azure.ai.vision.imageanalysis import ImageAnalysisClient
    from azure.ai.vision.imageanalysis.models import VisualFeatures
    from azure.core.credentials import AzureKeyCredential
    ```

1. في ملف التعليمات البرمجية لتطبيق العميل الخاص بك، في الدالة **الرئيسية**، جرى توفير التعليمات البرمجية لتحميل إعدادات التكوين. ثم ابحث عن التعليق **مصادقة عميل الذكاء الاصطناعي في Azure Vision**. ثم، ضمن هذا التعليق، أضف التعليمات البرمجية الخاصة باللغة التالية لإنشاء عنصر عميل الذكاء الاصطناعي في Azure Vision ومصادقته:

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

1. في الدالة **الرئيسية**، ضمن التعليمات البرمجية التي أضفتها للتو، لاحظ أن التعليمات البرمجية تحدد المسار إلى ملف صورة ثم تمرر مسار الصورة إلى دالة **GetTextRead**. لم تُنفذ هذه الدالة بالكامل بعد.

1. لنضيف بعض التعليمات البرمجية إلى نص دالة **GetTextRead**. ابحث عن التعليق **استخدم دالة تحليل الصورة لقراءة النص في الصورة**. ثم، ضمن هذا التعليق، أضف التعليمات البرمجية الخاصة باللغة التالية، مع ملاحظة تحديد الميزات المرئية عند استدعاء الدالة `Analyze`:

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
    
        // Load the image using SkiaSharp
        using SKBitmap bitmap = SKBitmap.Decode(imageFile);
        // Create canvas to draw on the bitmap
        using SKCanvas canvas = new SKCanvas(bitmap);

        // Create paint for drawing polygons (bounding boxes)
        SKPaint paint = new SKPaint
        {
            Color = SKColors.Cyan,
            StrokeWidth = 3,
            Style = SKPaintStyle.Stroke,
            IsAntialias = true
        };

        foreach (var line in result.Read.Blocks.SelectMany(block => block.Lines))
        {
            // Return the text detected in the image
    
    
        }
            
        // Save the annotated image using SkiaSharp
        using (SKFileWStream output = new SKFileWStream("text.jpg"))
        {
            // Encode the bitmap into JPEG format with full quality (100)
            bitmap.Encode(output, SKEncodedImageFormat.Jpeg, 100);
        }

        Console.WriteLine("\nResults saved in text.jpg\n");
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

1. في الرمز الذي أضفته للتو في دالة **GetTextRead**، وضمن **إرجاع النص المكتشف في تعليق الصورة**، أضف الرمز التالي (يطبع هذا الرمز نص الصورة إلى وحدة التحكم وينشئ صورة **text.jpg** التي تسلط الضوء على نص الصورة) :

    **C#**
    
    ```C#
    // Return the text detected in the image
    Console.WriteLine($"   '{line.Text}'");
    
    // Draw bounding box around line
    bool drawLinePolygon = true;
    
    // Return the position bounding box around each line
    
    
    
    // Return each word detected in the image and the position bounding box around each word with the confidence level of each word
    
    
    
    // Draw line bounding polygon
    if (drawLinePolygon)
    {
        var r = line.BoundingPolygon;
        SKPoint[] polygonPoints = new SKPoint[]
        {
            new SKPoint(r[0].X, r[0].Y),
            new SKPoint(r[1].X, r[1].Y),
            new SKPoint(r[2].X, r[2].Y),
            new SKPoint(r[3].X, r[3].Y)
        };

    DrawPolygon(canvas, polygonPoints, paint);
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

1. في ملف برنامج C# فقط، لا يزال يحتاج البرنامج إلى دالة مساعدة لرسم مضلع. أسفل التعليق **Helper method to draw a polygon given an array of SKPoints**، أضِف التعليمات البرمجية التالية:

    **C#**
   
    ```C#
    // Helper method to draw a polygon given an array of SKPoints
    static void DrawPolygon(SKCanvas canvas, SKPoint[] points, SKPaint paint)
    {
        if (points == null || points.Length == 0)
            return;

        using (var path = new SKPath())
        {
            path.MoveTo(points[0]);
            for (int i = 1; i < points.Length; i++)
            {
                path.LineTo(points[i]);
            }
            path.Close();
            canvas.DrawPath(path, paint);
        }
    }
    ```

1. في الدالة **Main**، افحص التعليمات البرمجية التي يتم تنفيذها إذا حدد المستخدم خيار **1** من القائمة. تستدعي هذه التعليمة البرمجية الدالة **GetTextRead**، لتمرير المسار إلى ملف الصورة *Lincoln.jpg*.

1. احفظ التغييرات وأغلِق محرر التعليمات البرمجية.

1. في شريط أدوات cloud shell، حدد **تحميل/تنزيل الملفات** ثم **تنزيل**. في مربع الحوار الجديد، أدخِل مسار الملف التالي وحدد **تنزيل**:

    **C#**
   
    ```
    mslearn-ai-vision/Labfiles/05-ocr/C-Sharp/read-text/images/Lincoln.jpg
    ```

    **Python**

    ```
    mslearn-ai-vision/Labfiles/05-ocr/Python/read-text/images/Lincoln.jpg
    ```
       
1. افتح الصورة **Lincoln.jpg** لعرضها.

1. بعد عرض الصورة التي تعالجها التعليمات البرمجية، أدخِل الأمر التالي لتشغيل البرنامج:

    **C#**
    
    ```
    dotnet run
    ```
    
    **Python**
    
    ```
    python read-text.py
    ```

1. عند المطالبة، أدخل **1** ولاحظ الإخراج، وهو النص المستخرج من الصورة.

1. في المجلد **read-text**، تم إنشاء الصورة **text.jpg**. يمكنك تنزيلها باستخدام مسار الملف `mslearn-ai-vision/Labfiles/05-ocr/***C-Sharp or Python***/read-text/text.jpg` وستلاحظ وجود مضلع حول كل *سطر* من النص.

1. أعِد فتح ملف التعليمات البرمجية وابحث عن التعليق **Return the position bounding box around each line**. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية التالية:

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

1. احفظ التغييرات وأغلِق محرر التعليمات البرمجية، ثم أدخِل الأمر التالي لتشغيل البرنامج:

    **C#**
    
    ```
    dotnet run
    ```
    
    **Python**
    
    ```
    python read-text.py
    ```

1. عند المطالبة، أدخل **1** ولاحظ الإخراج الذي يجب أن يكون كل سطر من النص في الصورة مع موضع كل منها في الصورة.

1. أعِد فتح ملف التعليمات البرمجية وابحث عن التعليق **Return each word detected in the image and the position bounding box around each word with the confidence level of each word**. ثم، ضمن هذا التعليق، أضف التعليمة البرمجية التالية:

    **C#**
    
    ```C#
    // Return each word detected in the image and the position bounding box around each word with the confidence level of each word
    foreach (DetectedTextWord word in line.Words)
    {
        Console.WriteLine($"     Word: '{word.Text}', Confidence {word.Confidence:F4}, Bounding Polygon: [{string.Join(" ", word.BoundingPolygon)}]");
        
        // Draw word bounding polygon
        drawLinePolygon = false;
        var r = word.BoundingPolygon;
    
        // Convert the bounding polygon into an array of SKPoints    
        SKPoint[] polygonPoints = new SKPoint[]
        {
            new SKPoint(r[0].X, r[0].Y),
            new SKPoint(r[1].X, r[1].Y),
            new SKPoint(r[2].X, r[2].Y),
            new SKPoint(r[3].X, r[3].Y)
        };

        // Draw the word polygon on the canvas
        DrawPolygon(canvas, polygonPoints, paint);
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

1. احفظ التغييرات وأغلِق محرر التعليمات البرمجية، ثم أدخِل الأمر التالي لتشغيل البرنامج:

    **C#**
    
    ```
    dotnet run
    ```
    
    **Python**
    
    ```
    python read-text.py
    ```

1. عند المطالبة، أدخل **1** ولاحظ الإخراج الذي يجب أن يكون كل كلمة من النص في الصورة مع موضع كل منها في الصورة. لاحظ كيفية إرجاع مستوى الثقة لكل كلمة أيضاً.

1. نزِّل الصورة **text.jpg** مرة أخرى ولاحظ وجود مضلع حول كل *كلمة*.

## استخدم Azure AI Vision SDK لقراءة النص من الصورة

في التمرين السابق، تقرأ نصا محدداً جيداً من صورة، ولكن في بعض الأحيان قد ترغب أيضاً في قراءة النص من الملاحظات أو الأوراق المكتوبة بخط اليد. والخبر السار هو أن **Azure AI Vision SDK** يمكنها أيضاً قراءة النص المكتوب بخط اليد بنفس الرمز الدقيق الذي استخدمته لقراءة نص محدد جيداً. سنستخدم التعليمات البرمجية نفسها من التمرين السابق، ولكن هذه المرة سنستخدم صورة مختلفة.

1. نزِّل **Note.jpg** باستخدام مسار الملف `mslearn-ai-vision/Labfiles/05-ocr/***C-Sharp or Python***/read-text/images/Note.jpg` لعرض الصورة التالية التي تعالجها التعليمات البرمجية.

1. في ملف التعليمات البرمجية للتطبيق الخاص بك، في الدالة **الرئيسية**، افحص التعليمات البرمجية التي يجري تشغيلها إذا حدد المستخدم خيار القائمة **2**. تستدعي هذه التعليمة البرمجية الدالة **GetTextRead**، لتمرير المسار إلى ملف الصورة *Note.jpg*.

1. من الوحدة الطرفية، أدخِل الأمر التالي لتشغيل البرنامج:

    **C#**
    
    ```
    dotnet run
    ```
    
    **Python**
    
    ```
    python read-text.py
    ```

1. عند المطالبة، أدخل **2** ولاحظ الإخراج، وهو النص المستخرج من صورة الملاحظة.

1. نزِّل الصورة **text.jpg** مرة أخرى ولاحظ وجود مضلع حول كل *كلمة* في الملاحظة.

## تنظيف الموارد

إذا كنت لا تستخدم موارد Azure التي أنشأتها في هذا المختبر لوحدات التدريب الأخرى، فيمكنك حذفها لتجنب تكبد المزيد من الرسوم. وإليك الطريقة:

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.

1. في شريط البحث العلوي، ابحث عن *Computer Vision*، وحدد مورد Computer Vision الذي أنشأته في هذا الواجب.

1. في صفحة المورد، حدد **حذف** واتبع الإرشادات لحذف المورد.

## مزيد من المعلومات

لمزيد من المعلومات حول استخدام خدمة **الذكاء الاصطناعي في Azure Vision** لقراءة النص، راجع [وثائق الذكاء الاصطناعي في Azure Vision](https://learn.microsoft.com/azure/ai-services/computer-vision/concept-ocr).
