---
lab:
  title: كشف وتحليل الوجوه
  module: Module 4 - Detecting and Analyze Faces
---

# كشف وتحليل الوجوه

القدرة على اكتشاف وتحليل الوجوه البشرية هي القدرة الأساسية للذكاء الاصطناعي. في هذا التمرين، ستستكشف خدمتي الذكاء الاصطناعي في Azure التي يمكنك استخدامها للعمل مع الوجوه في الصور: خدمة **Azure AI Vision** وخدمة **Face** .

> **هام**: يمكن إكمال هذا الواجب دون طلب أي وصول إضافي إلى الميزات المقيدة.

> **ملاحظة**: بدءًا من 21 يونيو 2022، تقتصر قدرات خدمات الذكاء الاصطناعي في Azure التي ترجع معلومات التعريف الشخصية المقيدة على العملاء الذين تم منحهم [حق وصول محدود](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-limited-access). بالإضافة إلى ذلك، لم تعد القدرات التي تستنتج الحالة العاطفية متوفرة. لمزيد من التفاصيل حول التغييرات التي قامت بها Microsoft، ولماذا - راجع [استثمارات الذكاء الاصطناعي المسؤول وضماناته للتعرف على الوجوه](https://azure.microsoft.com/blog/responsible-ai-investments-and-safeguards-for-facial-recognition/).

## استنساخ المستودع لهذه الدورة التدريبية

إذا لم تقم بالاستنساخ بالفعل، يجب عليك استنساخ مستودع التعليمات البرمجية لهذه الدورة التدريبية:

1. ابدأ تشغيل Visual Studio Code.
2. افتح لوحة (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع `https://github.com/MicrosoftLearning/mslearn-ai-vision` إلى مجلد محلي (لا يُهم أي مجلد).
3. عند استنساخ المستودع، افتح المجلد في تعليمة Visual Studio البرمجية.
4. انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.

    > **ملاحظة**: إذا تمت مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد **ليس الآن**.

## توفير مورد خدمات الذكاء الاصطناعي في Azure

إذا لم يكن لديك بالفعل مورد في اشتراكك، فسيتعين عليك توفير مورد **خدمات الذكاء الاصطناعي في Azure**.

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.
2. في شريط البحث العلوي، ابحث عن *خدمات الذكاء الاصطناعي في Azure*، وحدد **خدمات الذكاء الاصطناعي في Azure**، وأنشئ مورد حساب متعدد الخدمات لخدمات الذكاء الاصطناعي في Azure بالإعدادات التالية:
    - **Subscription**: *اشتراكك في Azure*
    - **مجموعة الموارد**: *اختر أو أنشئ مجموعة موارد (إذا كنت تستخدم اشتراكًا مقيدًا، فقد لا يكون لديك إذن لإنشاء مجموعة موارد جديدة - استخدم المجموعة المتوفرة)*
    - **المنطقة**: *اختر أي منطقة متوفرة*
    - **الاسم**: *أدخل اسماً فريداً*
    - **مستوى التسعير**: قياسي S0
3. حدد مربعات الاختيار المطلوبة ثم أنشئ المورد.
4. انتظر حتى يكتمل النشر، ثم اعرض تفاصيل النشر.
5. عند نشر المورد، انتقل إليه واعرض **صفحة المفاتيح ونقطة النهاية** الخاصة به. ستحتاج إلى نقطة النهاية وأحد المفاتيح من هذه الصفحة في الإجراء التالي.

## الاستعداد لاستخدام Azure AI Vision SDK

في هذا التمرين، ستكمل تطبيق عميل تم تنفيذه جزئياً يستخدم Azure AI Vision SDK لتحليل الوجوه في صورة.

> **ملاحظة**: يمكنك اختيار استخدام SDK إما لـ **C#** أو **Python**. في الخطوات الواردة أدناه، نفذ الإجراءات المناسبة للغتك المفضلة.

1. في Visual Studio Code، في جزء **Explorer**، انتقِل إلى المجلد **04-face** وقم بتوسيع المجلد **CSharp** أو **Python** حسب تفضيل اللغة لديك.
2. انقر بزر الماوس الأيمن فوق مجلد **computer-vision** وافتح محطة طرفية متكاملة. ثم قم بتثبيت حزمة Azure AI Vision SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:

    **C#**

    ```
    dotnet add package Azure.AI.Vision.ImageAnalysis -v 1.0.0-beta.3
    ```

    **Python**

    ```
    pip install azure-ai-vision-imageanalysis==1.0.0b3
    ```
    
3. اعرض محتويات مجلد **computer-vision**، ولاحظ أنه يحتوي على ملف لإعدادات التكوين:
    - **C#**: appsettings.json
    - **Python**: .env

4. يمكنك فتح ملف التكوين وتحديث قيم التكوين التي يحتوي عليها لتعكس **نقطة النهاية** و**مفتاح** المصادقة لمورد خدمات الذكاء الاصطناعي في Azure. احفظ تغييراتك.

5. لاحظ أن مجلد **computer-vision** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: detect-people.py

6. افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Azure AI Vision SDK:

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

## عرض الصورة التي ستقوم بتحليلها

في هذا التمرين، ستستخدم خدمة Azure AI Vision لتحليل صورة للأشخاص.

1. في Visual Studio Code، قم بتوسيع مجلد **computer-vision** ومجلد **الصور** الذي يحتوي عليه.
2. حدد الصورة **people.jpg** لعرضها.

## اكتشاف الأوجه في صورة

أنت الآن جاهز لاستخدام SDK لاستدعاء خدمة Vision واكتشاف الوجوه في صورة.

1. في ملف التعليمات البرمجية لتطبيق العميل (**Program.cs** أو **detect-people.py**)، في الدالة **Main**، لاحظ أنه تم توفير التعليمات البرمجية لتحميل إعدادات التكوين. ثم ابحث عن التعليق **مصادقة عميل Azure AI Vision**. ثم، ضمن هذا التعليق، أضف التعليمات البرمجية الخاصة باللغة التالية لإنشاء كائن عميل الذكاء الاصطناعي في Azure Vision ومصادقته:

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

2. في الدالة **Main**، ضمن التعليمات البرمجية التي أضفتها للتو، لاحظ أن التعليمات البرمجية تحدد المسار إلى ملف صورة ثم تمرر مسار الصورة إلى دالة تسمى **AnalyzeImage**. لم يتم تنفيذ هذه الدالة بالكامل بعد.

3. في الدالة **AnalyzeImage**، ضمن التعليق **الحصول على النتيجة بالميزات المحددة التي سيتم استردادها (الأشخاص)**، أضف التعليمة البرمجية التالية:

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

4. في الدالة **AnalyzeImage**، ضمن التعليق **رسم مربع إحاطة حول الأشخاص المكتشفين**، أضف التعليمة البرمجية التالية:

    **C#**

    ```C
    // Draw bounding box around detected people
    foreach (DetectedPerson person in result.People.Values)
    {
        if (person.Confidence > 0.5) 
        {
            // Draw object bounding box
            var r = person.BoundingBox;
            Rectangle rect = new Rectangle(r.X, r.Y, r.Width, r.Height);
            graphics.DrawRectangle(pen, rect);
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

5. احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد **computer-vision**، وأدخل الأمر التالي لتشغيل البرنامج:

    **C#**

    ```
    dotnet run
    ```

    **Python**

    ```
    python detect-people.py
    ```

6. لاحظ الإخراج، والذي يجب أن يشير إلى عدد الوجوه التي تم اكتشافها.
7. اعرض الملف **people.jpg** الذي تم إنشاؤه في نفس المجلد الذي يحتوي على ملف التعليمات البرمجية الخاص بك لرؤية الوجوه الموضحة. في هذه الحالة، استخدمت التعليمات البرمجية سمات الوجه لتسمية موقع الجزء العلوي الأيسر من المربع، وينسق المربع المحيط لرسم مستطيل حول كل وجه.

إذا كنت ترغب في رؤية درجة الثقة لجميع الأشخاص الذين اكتشفتهم الخدمة، يمكنك إلغاء التعليق على سطر التعليمات البرمجية ضمن التعليق `Return the confidence of the person detected` وإعادة تشغيل التعليمات البرمجية.

## الاستعداد لاستخدام Face SDK

بينما توفر خدمة **Azure AI Vision** الكشف الأساسي عن الوجه (جنباً إلى جنب مع العديد من قدرات تحليل الصور الأخرى)، توفر خدمة **Face** وظائف أكثر شمولاً لتحليل الوجه والتعرف عليه.

1. في Visual Studio Code، في جزء **Explorer**، انتقِل إلى المجلد **04-face** وقم بتوسيع المجلد **CSharp** أو **Python** حسب تفضيل اللغة لديك.
2. انقر بزر الماوس الأيمن فوق مجلد **face-api** وافتح محطة طرفية متكاملة. ثم قم بتثبيت حزمة Face SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:

    **C#**

    ```
    dotnet add package Azure.AI.Vision.Face -v 1.0.0-beta.2
    ```

    **Python**

    ```
    pip install azure-ai-vision-face==1.0.0b2
    ```
    
3. اعرض محتويات مجلد **face-api**، ولاحظ أنه يحتوي على ملف لإعدادات التكوين:
    - **C#**: appsettings.json
    - **Python**: .env

4. يمكنك فتح ملف التكوين وتحديث قيم التكوين التي يحتوي عليها لتعكس **نقطة النهاية** و**مفتاح** المصادقة لمورد خدمات الذكاء الاصطناعي في Azure. احفظ تغييراتك.

5. لاحظ أن مجلد **face-api** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: analyze-faces.py

6. افتح ملف التعليمات البرمجية وفي الأعلى، ضمن مراجع مساحة الاسم الموجودة، ابحث عن التعليق **استيراد مساحات الأسماء**. بعد ذلك، ضمن هذا التعليق، أضف التعليمات البرمجية التالية الخاصة باللغة لاستيراد مساحات الأسماء التي ستحتاج إليها لاستخدام Vision SDK:

    **C#**

    ```C#
    // Import namespaces
    using Azure;
    using Azure.AI.Vision.Face;
    ```

    **Python**

    ```Python
    # Import namespaces
    from azure.ai.vision.face import FaceClient
    from azure.ai.vision.face.models import FaceDetectionModel, FaceRecognitionModel, FaceAttributeTypeDetection03
    from azure.core.credentials import AzureKeyCredential
    ```

7. في الدالة **Main**، لاحظ أنه تم توفير التعليمات البرمجية لتحميل إعدادات التكوين. ثم ابحث عن التعليق **مصادقة عميل Face**. ثم، ضمن هذا التعليق، أضف التعليمات البرمجية الخاصة باللغة التالية لإنشاء كائن **FaceClient** ومصادقته:

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

8. في الدالة **Main**، ضمن التعليمات البرمجية التي أضفتها للتو، لاحظ أن التعليمات البرمجية تعرض قائمة تمكّنك من استدعاء الوظائف في التعليمات البرمجية لاستكشاف قدرات خدمة Face. ستقوم بتنفيذ هذه الدالات في باقي هذا التمرين.

## الكشف عن الوجوه وتحليلها

يُعد الكشف عن الوجوه في صورة، وتحديد سماتها، مثل وضع الرأس، والتمويه، ووجود قناع، وما إلى ذلك إحدى القدرات الأساسية لخدمة التحليل الوجهي.

1. في ملف التعليمات البرمجية للتطبيق الخاص بك، في الدالة **Main** ، افحص التعليمات البرمجية التي يتم تشغيلها إذا حدد المستخدم خيار القائمة **1**. تستدعي هذه التعليمة البرمجية دالة **DetectFaces**، لتمرير المسار إلى ملف صورة.
2. ابحث عن الدالة **DetectFaces** في ملف التعليمات البرمجية، وضمن التعليق **حدد ميزات الوجه المراد استردادها**، أضف التعليمات البرمجية التالية:

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

3. في الدالة **DetectFaces**، ضمن التعليمات البرمجية التي أضفتها للتو، ابحث عن التعليق **Get faces** وأضف التعليمات البرمجية التالية:

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

        // Prepare image for drawing
        Image image = Image.FromFile(imageFile);
        Graphics graphics = Graphics.FromImage(image);
        Pen pen = new Pen(Color.LightGreen, 3);
        Font font = new Font("Arial", 4);
        SolidBrush brush = new SolidBrush(Color.White);
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
            Rectangle rect = new Rectangle(r.Left, r.Top, r.Width, r.Height);
            graphics.DrawRectangle(pen, rect);
            string annotation = $"Face number {faceCount}";
            graphics.DrawString(annotation,font,brush,r.Left, r.Top);
        }

        // Save annotated image
        String output_file = "detected_faces.jpg";
        image.Save(output_file);
        Console.WriteLine(" Results saved in " + output_file);   
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

4. افحص التعليمات البرمجية التي أضفتها إلى الدالة **DetectFaces**. فهي تحلل ملف الصورة وتكشف أي وجوه يحتوي عليها، بما في ذلك السمات مثل وضع الرأس والتمويه ووجود قناع. يتم عرض تفاصيل كل وجه، بما في ذلك معرف وجه فريد يتم تعيينه لكل وجه؛ ويشار إلى موقع الوجوه على الصورة باستخدام مربع إحاطة.
5. احفظ التغييرات وارجع إلى الوحدة الطرفية المتكاملة لمجلد **face-api**، وأدخل الأمر التالي لتشغيل البرنامج:

    **C#**

    ```
    dotnet run
    ```

    *قد يعرض إخراج C# تحذيرات حول الدوال غير المتزامنة الآن باستخدام عامل التشغيل **await** . يمكنك تجاهل هذه التحذيرات.*

    **Python**

    ```
    python analyze-faces.py
    ```

6. عند المطالبة، أدخل **1** ولاحظ الإخراج، والذي يجب أن يتضمن معرف وسمات كل وجه تم اكتشافه.
7. اعرض ملف **detected_faces.jpg** الذي تم إنشاؤه في نفس المجلد كملف التعليمات البرمجية لرؤية الوجوه ذات التعليقات التوضيحية.

## مزيد من المعلومات

هناك العديد من الميزات الإضافية المتوفرة داخل خدمة **Face**، ولكن بعد [معيار الذكاء الاصطناعي المسؤول](https://aka.ms/aah91ff)، يتم تقييد هذه الميزات بما يتجاوز نهج الوصول المحدود. تتضمن هذه الميزات تحديد نماذج التعرف على الوجه والتحقق منها وإنشاءها. لمعرفة المزيد والتقدم للحصول على الوصول، راجع [الوصول المحدود لخدمات الذكاء الاصطناعي في Azure](https://docs.microsoft.com/en-us/azure/cognitive-services/cognitive-services-limited-access).

لمزيد من المعلومات حول استخدام خدمة **Azure AI Vision** للكشف عن الوجه، راجع [وثائق Azure AI Vision](https://docs.microsoft.com/azure/cognitive-services/computer-vision/concept-detecting-faces).

لمعرفة المزيد حول خدمة **Face**، راجع [وثائق Face](https://learn.microsoft.com/azure/ai-services/computer-vision/overview-identity).
