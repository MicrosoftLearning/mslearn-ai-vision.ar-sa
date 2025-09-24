---
lab:
  title: كشف وتحليل الوجوه
  module: Module 4 - Detecting and Analyze Faces
---

# كشف وتحليل الوجوه

القدرة على اكتشاف وتحليل الوجوه البشرية هي القدرة الأساسية للذكاء الاصطناعي. في هذا التمرين، ستستكشف خدمتي الذكاء الاصطناعي في Azure التي يمكنك استخدامها للعمل مع الوجوه في الصور: خدمة **Azure AI Vision** وخدمة **Face** .

> **هام**: يمكن إكمال هذا الواجب دون طلب أي وصول إضافي إلى الميزات المقيدة.

> **ملاحظة**: بدءًا من 21 يونيو 2022، تقتصر قدرات خدمات الذكاء الاصطناعي في Azure التي ترجع معلومات التعريف الشخصية المقيدة على العملاء الذين تم منحهم [حق وصول محدود](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-limited-access). بالإضافة إلى ذلك، لم تعد القدرات التي تستنتج الحالة العاطفية متوفرة. لمزيد من التفاصيل حول التغييرات التي قامت بها Microsoft، ولماذا - راجع [استثمارات الذكاء الاصطناعي المسؤول وضماناته للتعرف على الوجوه](https://azure.microsoft.com/blog/responsible-ai-investments-and-safeguards-for-facial-recognition/).

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
   cd mslearn-ai-vision/Labfiles/04-face
    ```

## الاستعداد لاستخدام Azure AI Vision SDK

في هذا التمرين، ستكمل تطبيق عميل جرى تنفيذه جزئياً يستخدم Azure AI Vision SDK لتحليل الصور.

> **ملاحظة**: يمكنك اختيار استخدام SDK إما لـ **C#** أو **Python**. في الخطوات الواردة أدناه، نفذ الإجراءات المناسبة للغتك المفضلة.

1. انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية للتطبيق بلغتك المفضلة:  

    **C#**

    ```
   cd C-Sharp/computer-vision
    ```
    
    **Python**

    ```
   cd Python/computer-vision
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
1. بعد استبدال العناصر النائبة، استخدم الأمر **CTRL+S** لحفظ التغييرات ثم استخدم الأمر **CTRL+Q** لإغلاق محرر التعليمات البرمجية مع إبقاء سطر أوامر Cloud Shell مفتوحWا.

## عرض الصورة التي ستقوم بتحليلها

في هذا التمرين، ستستخدم خدمة Azure AI Vision لتحليل صورة للأشخاص.

1. في شريط أدوات cloud shell، حدد **تحميل/تنزيل الملفات** ثم **تنزيل**. في مربع الحوار الجديد، أدخِل مسار الملف التالي وحدد **تنزيل**:

    ```
    mslearn-ai-vision/Labfiles/04-face/C-Sharp/computer-vision/images/people.jpg
    ```

1. افتح الصورة **people.jpg** لعرضها.

## اكتشاف الأوجه في صورة

أنت الآن جاهز لاستخدام SDK لاستدعاء خدمة Vision واكتشاف الوجوه في صورة.

1. لاحظ أن مجلد **computer-vision** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: detect-people.py

1. أدخل الأمر التالي لفتح ملف التعليمات البرمجية لتطبيق العميل:

    **C#**

    ```
   code Program.cs
    ```

    **Python**

    ```
   code image-analysis.py
    ```

1. أضِف التعليمات البرمجية التالية الخاصة باللغة تحت التعليق **Import namespaces** لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام حزمة عدة تطوير البرامج (SDK) الخاصة بـ Azure AI Vision:

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
    
1. في الدالة **Main**، لاحظ أنه تم توفير التعليمات البرمجية لتحميل إعدادات التكوين. ثم ابحث عن التعليق **مصادقة عميل الذكاء الاصطناعي في Azure Vision**. ثم، ضمن هذا التعليق، أضف التعليمات البرمجية الخاصة باللغة التالية لإنشاء كائن عميل الذكاء الاصطناعي في Azure Vision ومصادقته:

    **C#**

    ```C#
    // Authenticate Azure AI Vision client
    ImageAnalysisClient cvClient = new ImageAnalysisClient(
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

1. في الدالة **Main**، ضمن التعليمات البرمجية التي أضفتها للتو، لاحظ أن التعليمات البرمجية تحدد المسار إلى ملف صورة ثم تمرر مسار الصورة إلى دالة تسمى **AnalyzeImage**. لم يتم تنفيذ هذه الدالة بالكامل بعد.

1. في الدالة **AnalyzeImage**، ضمن التعليق **الحصول على النتيجة بالميزات المحددة التي سيتم استردادها (الأشخاص)**، أضف التعليمة البرمجية التالية:

    **C#**

    ```C#
    // Get result with specified features to be retrieved (PEOPLE)
    ImageAnalysisResult result = client.Analyze(
        BinaryData.FromStream(stream),
        VisualFeatures.People);
    ```

    **Python**

    ```Python
    # Get result with specified features to be retrieved (PEOPLE)
    result = cv_client.analyze(
        image_data=image_data,
        visual_features=[
            VisualFeatures.PEOPLE],
    )
    ```

1. في الدالة **AnalyzeImage**، ضمن التعليق **رسم مربع إحاطة حول الأشخاص المكتشفين**، أضف التعليمة البرمجية التالية:

    **C#**

    ```C
    // Draw bounding box around detected people
    foreach (DetectedPerson person in result.People.Values)
    {
        if (person.Confidence > 0.5) 
        {
            // Draw object bounding box
            var r = person.BoundingBox;
            SKRect rect = new SKRect(r.X, r.Y, r.X + r.Width, r.Y + r.Height);
            canvas.DrawRect(rect, paint);
        }

        // Return the confidence of the person detected
        //Console.WriteLine($"   Bounding box {person.BoundingBox.ToString()}, Confidence: {person.Confidence:F2}");
    }
    ```

    **Python**
    
    ```Python
    # Draw bounding box around detected people
    for detected_people in result.people.list:
        if(detected_people.confidence > 0.5):
            # Draw object bounding box
            r = detected_people.bounding_box
            bounding_box = ((r.x, r.y), (r.x + r.width, r.y + r.height))
            draw.rectangle(bounding_box, outline=color, width=3)

        # Return the confidence of the person detected
        #print(" {} (confidence: {:.2f}%)".format(detected_people.bounding_box, detected_people.confidence * 100))
    ```

1. احفظ التغييرات، وأغلِق محرر التعليمات البرمجية، ثم أدخِل الأمر التالي لتشغيل البرنامج:

    **C#**

    ```
    dotnet run
    ```

    **Python**

    ```
    python detect-people.py
    ```

6. لاحظ الإخراج، والذي يجب أن يشير إلى عدد الوجوه التي تم اكتشافها.
7. نزِّل الملف **people.jpg** الذي تم إنشاؤه في نفس المجلد كملف التعليمات البرمجية لرؤية الوجوه ذات التعليقات التوضيحية. في هذه الحالة، استخدمت التعليمات البرمجية سمات الوجه لتسمية موقع الجزء العلوي الأيسر من المربع، وينسق المربع المحيط لرسم مستطيل حول كل وجه.

إذا كنت ترغب في رؤية درجة الثقة لجميع الأشخاص الذين اكتشفتهم الخدمة، يمكنك إلغاء التعليق على سطر التعليمات البرمجية ضمن التعليق `Return the confidence of the person detected` وإعادة تشغيل التعليمات البرمجية.

## الاستعداد لاستخدام Face SDK

بينما توفر خدمة **Azure AI Vision** الكشف الأساسي عن الوجه (جنباً إلى جنب مع العديد من قدرات تحليل الصور الأخرى)، توفر خدمة **Face** وظائف أكثر شمولاً لتحليل الوجه والتعرف عليه.

1. انتقل إلى المجلد **face-api** عن طريق تشغيل الأمر `cd ../face-api`. ثم قم بتثبيت حزمة Face SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:

    **C#**

    ```
    dotnet add package Azure.AI.Vision.Face -v 1.0.0-beta.2
    ```

    **Python**

    ```
    pip install azure-ai-vision-face==1.0.0b2
    ```
    
1. اعرض محتويات مجلد **face-api**، ولاحظ أنه يحتوي على ملف لإعدادات التكوين:
    - **C#**: appsettings.json
    - **Python**: .env

1. يمكنك فتح ملف التكوين وتحديث قيم التكوين التي يحتوي عليها لتعكس **نقطة النهاية** و**مفتاح** المصادقة لمورد خدمات الذكاء الاصطناعي في Azure. احفظ تغييراتك.

1. لاحظ أن مجلد **face-api** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: analyze-faces.py

1. افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Vision SDK:

    **C#**

    ```C#
    // Import namespaces
    using Azure;
    using Azure.AI.Vision.Face;
    using SkiaSharp;
    ```

    **Python**

    ```Python
    # Import namespaces
    from azure.ai.vision.face import FaceClient
    from azure.ai.vision.face.models import FaceDetectionModel, FaceRecognitionModel, FaceAttributeTypeDetection03
    from azure.core.credentials import AzureKeyCredential
    ```

1. في الدالة **Main**، لاحظ أنه تم توفير التعليمات البرمجية لتحميل إعدادات التكوين. ثم ابحث عن التعليق **مصادقة عميل Face**. ثم، ضمن هذا التعليق، أضف التعليمات البرمجية الخاصة باللغة التالية لإنشاء كائن **FaceClient** ومصادقته:

    **C#**

    ```C#
    // Authenticate Face client
    faceClient = new FaceClient(
        new Uri(cogSvcEndpoint),
        new AzureKeyCredential(cogSvcKey));
    ```

    **Python**

    ```Python
    # Authenticate Face client
    face_client = FaceClient(
        endpoint=cog_endpoint,
        credential=AzureKeyCredential(cog_key)
    )
    ```

1. في الدالة **Main**، ضمن التعليمات البرمجية التي أضفتها للتو، لاحظ أن التعليمات البرمجية تعرض قائمة تمكّنك من استدعاء الوظائف في التعليمات البرمجية لاستكشاف قدرات خدمة Face. ستقوم بتنفيذ هذه الدالات في باقي هذا التمرين.

## الكشف عن الوجوه وتحليلها

يُعد الكشف عن الوجوه في صورة، وتحديد سماتها، مثل وضع الرأس، والتمويه، ووجود قناع، وما إلى ذلك إحدى القدرات الأساسية لخدمة التحليل الوجهي.

1. في ملف التعليمات البرمجية للتطبيق الخاص بك، في الدالة **Main** ، افحص التعليمات البرمجية التي يتم تشغيلها إذا حدد المستخدم خيار القائمة **1**. تستدعي هذه التعليمة البرمجية دالة **DetectFaces**، لتمرير المسار إلى ملف صورة.
1. ابحث عن الدالة **DetectFaces** في ملف التعليمات البرمجية، وضمن التعليق **حدد ميزات الوجه المراد استردادها**، أضف التعليمات البرمجية التالية:

    **C#**

    ```C#
    // Specify facial features to be retrieved
    FaceAttributeType[] features = new FaceAttributeType[]
    {
        FaceAttributeType.Detection03.HeadPose,
        FaceAttributeType.Detection03.Blur,
        FaceAttributeType.Detection03.Mask
    };
    ```

    **Python**

    ```Python
    # Specify facial features to be retrieved
    features = [FaceAttributeTypeDetection03.HEAD_POSE,
                FaceAttributeTypeDetection03.BLUR,
                FaceAttributeTypeDetection03.MASK]
    ```

1. في الدالة **DetectFaces**، ضمن التعليمات البرمجية التي أضفتها للتو، ابحث عن التعليق **Get faces** وأضف التعليمات البرمجية التالية:

    **C#**

    ```C#
    // Get faces
    using (var imageData = File.OpenRead(imageFile))
    {    
        var response = await faceClient.DetectAsync(
            BinaryData.FromStream(imageData),
            FaceDetectionModel.Detection03,
            FaceRecognitionModel.Recognition04,
            returnFaceId: false,
            returnFaceAttributes: features);
        IReadOnlyList<FaceDetectionResult> detected_faces = response.Value;

        if (detected_faces.Count() > 0)
        {
            Console.WriteLine($"{detected_faces.Count()} faces detected.");

            // Load the image using SkiaSharp
            using SKBitmap bitmap = SKBitmap.Decode(imageFile);
            using SKCanvas canvas = new SKCanvas(bitmap);

            // Set up paint styles for drawing
            SKPaint rectPaint = new SKPaint
            {
                Color = SKColors.LightGreen,
                StrokeWidth = 3,
                Style = SKPaintStyle.Stroke,
                IsAntialias = true
            };

            SKPaint textPaint = new SKPaint
            {
                Color = SKColors.White,
                TextSize = 16,
                IsAntialias = true
            };

            int faceCount=0;

            // Draw and annotate each face
            foreach (var face in detected_faces)
            {
                faceCount++;
                Console.WriteLine($"\nFace number {faceCount}");
            
                // Get face properties
                Console.WriteLine($" - Head Pose (Yaw): {face.FaceAttributes.HeadPose.Yaw}");
                Console.WriteLine($" - Head Pose (Pitch): {face.FaceAttributes.HeadPose.Pitch}");
                Console.WriteLine($" - Head Pose (Roll): {face.FaceAttributes.HeadPose.Roll}");
                Console.WriteLine($" - Blur: {face.FaceAttributes.Blur.BlurLevel}");
                Console.WriteLine($" - Mask: {face.FaceAttributes.Mask.Type}");

                // Draw and annotate face
                var r = face.FaceRectangle;

                // Create an SKRect from the face rectangle data
                SKRect rect = new SKRect(r.Left, r.Top, r.Left + r.Width, r.Top + r.Height);
                canvas.DrawRect(rect, rectPaint);

                string annotation = $"Face number {faceCount}";
                canvas.DrawText(annotation, r.Left, r.Top, textPaint);
            }

            // Save annotated image
            using (SKFileWStream output = new SKFileWStream("detected_faces.jpg"))
            {
                bitmap.Encode(output, SKEncodedImageFormat.Jpeg, 100);
            }

            Console.WriteLine(" Results saved in detected_faces.jpg");   
        }
    }
    ```

    **Python**

    ```Python
    # Get faces
    with open(image_file, mode="rb") as image_data:
        detected_faces = face_client.detect(
            image_content=image_data.read(),
            detection_model=FaceDetectionModel.DETECTION03,
            recognition_model=FaceRecognitionModel.RECOGNITION04,
            return_face_id=False,
            return_face_attributes=features,
        )

        if len(detected_faces) > 0:
            print(len(detected_faces), 'faces detected.')

            # Prepare image for drawing
            fig = plt.figure(figsize=(8, 6))
            plt.axis('off')
            image = Image.open(image_file)
            draw = ImageDraw.Draw(image)
            color = 'lightgreen'
            face_count = 0

            # Draw and annotate each face
            for face in detected_faces:
    
                # Get face properties
                face_count += 1
                print('\nFace number {}'.format(face_count))

                print(' - Head Pose (Yaw): {}'.format(face.face_attributes.head_pose.yaw))
                print(' - Head Pose (Pitch): {}'.format(face.face_attributes.head_pose.pitch))
                print(' - Head Pose (Roll): {}'.format(face.face_attributes.head_pose.roll))
                print(' - Blur: {}'.format(face.face_attributes.blur.blur_level))
                print(' - Mask: {}'.format(face.face_attributes.mask.type))

                # Draw and annotate face
                r = face.face_rectangle
                bounding_box = ((r.left, r.top), (r.left + r.width, r.top + r.height))
                draw = ImageDraw.Draw(image)
                draw.rectangle(bounding_box, outline=color, width=5)
                annotation = 'Face number {}'.format(face_count)
                plt.annotate(annotation,(r.left, r.top), backgroundcolor=color)

            # Save annotated image
            plt.imshow(image)
            outputfile = 'detected_faces.jpg'
            fig.savefig(outputfile)

            print('\nResults saved in', outputfile)
    ```

1. افحص التعليمات البرمجية التي أضفتها إلى الدالة **DetectFaces**. فهي تحلل ملف الصورة وتكشف أي وجوه يحتوي عليها، بما في ذلك السمات مثل وضع الرأس والتمويه ووجود قناع. يتم عرض تفاصيل كل وجه، بما في ذلك معرف وجه فريد يتم تعيينه لكل وجه؛ ويشار إلى موقع الوجوه على الصورة باستخدام مربع إحاطة.
1. احفظ التغييرات وأغلِق محرر التعليمات البرمجية، ثم أدخِل الأمر التالي لتشغيل البرنامج:

    **C#**

    ```
    dotnet run
    ```

    *قد يعرض إخراج C# تحذيرات حول الدوال غير المتزامنة الآن باستخدام عامل التشغيل **await** . يمكنك تجاهل هذه التحذيرات.*

    **Python**

    ```
    python analyze-faces.py
    ```

1. عند المطالبة، أدخل **1** ولاحظ الإخراج، والذي يجب أن يتضمن معرف وسمات كل وجه تم اكتشافه.
1. نزِّل الملف **detected_faces.jpg** الذي تم إنشاؤه في نفس المجلد كملف التعليمات البرمجية لرؤية الوجوه ذات التعليقات التوضيحية.

## تنظيف الموارد

إذا كنت لا تستخدم موارد Azure التي أنشأتها في هذا المختبر لوحدات التدريب الأخرى، فيمكنك حذفها لتجنب تكبد المزيد من الرسوم.

1. افتح مدخل Azure في `https://portal.azure.com`، وفي شريط البحث العلوي، ابحث عن الموارد التي أنشأتها في هذا المختبر.

1. في صفحة المورد، حدد **حذف** واتبع الإرشادات لحذف المورد. بدلاً من ذلك، يمكنك حذف مجموعة الموارد بأكملها لتنظيف جميع الموارد في الوقت نفسه.

## مزيد من المعلومات

هناك العديد من الميزات الإضافية المتوفرة داخل خدمة **Face**، ولكن بعد [معيار الذكاء الاصطناعي المسؤول](https://aka.ms/aah91ff)، يتم تقييد هذه الميزات بما يتجاوز نهج الوصول المحدود. تتضمن هذه الميزات تحديد نماذج التعرف على الوجه والتحقق منها وإنشاءها. لمعرفة المزيد والتقدم للحصول على الوصول، راجع [الوصول المحدود لخدمات الذكاء الاصطناعي في Azure](https://docs.microsoft.com/en-us/azure/cognitive-services/cognitive-services-limited-access).

لمزيد من المعلومات حول استخدام خدمة **Azure AI Vision** للكشف عن الوجه، راجع [وثائق Azure AI Vision](https://docs.microsoft.com/azure/cognitive-services/computer-vision/concept-detecting-faces).

لمعرفة المزيد حول خدمة **Face**، راجع [وثائق Face](https://learn.microsoft.com/azure/ai-services/computer-vision/overview-identity).
