---
lab:
  title: تحليل الصور باستخدام الذكاء الاصطناعي في Azure Vision
  module: Module 2 - Develop computer vision solutions with Azure AI Vision
---

# تحليل الصور باستخدام الذكاء الاصطناعي في Azure Vision

الذكاء الاصطناعي في Azure Vision عبارة عن قدرة ذكاء اصطناعي تمكن أنظمة البرامج من تفسير المدخلات المرئية من خلال تحليل الصور. في Microsoft Azure، توفر خدمة الذكاء الاصطناعي في Azure **Vision** نماذج معدة مسبقاً لمهام رؤية الكمبيوتر الشائعة، بما في ذلك تحليل الصور لاقتراح التسميات التوضيحية والعلامات، واكتشاف الأشياء والأشخاص الشائعين. يمكنك أيضا استخدام خدمة الذكاء الاصطناعي في Azure Vision لإزالة الخلفية أو إنشاء احتواء أمامي للصور.

## استنساخ المستودع لهذه الدورة التدريبية

إذا لم تكن قد استنسخت بالفعل مستودع التعليمات البرمجية **الذكاء الاصطناعي في Azure Vision** في البيئة التي تعمل فيها في هذا التمرين المعملي، فاتبع هذه الخطوات لتنفيذ ذلك. بخلاف ذلك، افتح المجلد المستنسخ في تعليمة Visual Studio البرمجية.

1. ابدأ تشغيل Visual Studio Code.
2. افتح لوحة (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع `https://github.com/MicrosoftLearning/mslearn-ai-vision` إلى مجلد محلي (لا يُهم أي مجلد).
3. عند استنساخ المستودع، افتح المجلد في تعليمة Visual Studio البرمجية.
4. انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.

    > **ملاحظة**: إذا جرت مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد **ليس الآن**. إذا جرت مطالبتك برسالة *اكتشاف مشروع وظيفة Azure في المجلد*، يمكنك إغلاق هذه الرسالة بأمان.

## توفير مورد خدمات الذكاء الاصطناعي في Azure

إذا لم يكن لديك بالفعل مورد في اشتراكك، فسيتعين عليك توفير مورد **خدمات الذكاء الاصطناعي في Azure**.

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.
2. حدد **Create a resource.**
3. في شريط البحث ابحث عن*خدمات الذكاء الاصطناعي في Azure*، وحدد **خدمات الذكاء الاصطناعي في Azure**، وأنشئ مورد حساب متعدد الخدمات لخدمات الذكاء الاصطناعي في Azure بالإعدادات التالية:
    - **Subscription**: *اشتراكك في Azure*
    - **مجموعة الموارد**: *اختر أو أنشئ مجموعة موارد (إذا كنت تستخدم اشتراكاً مقيداً، فقد لا يكون لديك إذن لإنشاء مجموعة موارد جديدة - استخدم المجموعة المتوفرة)*
    - **المنطقة**: *اختر من بين شرق الولايات المتحدة أو غرب الولايات المتحدة أو وسط فرنسا أو وسط كوريا أو شمال أوروبا أو جنوب شرق آسيا أو غرب أوروبا أو شرق آسيا\**
    - **الاسم**: *أدخل اسماً فريداً*
    - **مستوى التسعير**: قياسي S0

    \*تتوفر ميزات الذكاء الاصطناعي في Azure اصدار 4.0 حالياً في هذه المناطق فقط.

4. حدد مربعات الاختيار المطلوبة ثم أنشئ المورد.
5. انتظر حتى يكتمل النشر، ثم اعرض تفاصيل النشر.
6. عند نشر المورد، انتقل إليه واعرض **صفحة المفاتيح ونقطة النهاية** الخاصة به. ستحتاج إلى نقطة النهاية وأحد المفاتيح من هذه الصفحة في الإجراء التالي.

## الاستعداد لاستخدام Azure AI Vision SDK

في هذا التمرين، ستكمل تطبيق عميل جرى تنفيذه جزئياً يستخدم Azure AI Vision SDK لتحليل الصور.

> **ملاحظة**: يمكنك اختيار استخدام SDK إما لـ **C#** أو **Python**. في الخطوات الواردة أدناه، نفذ الإجراءات المناسبة للغتك المفضلة.

1. في تعليمة Visual Studio البرمجية في جزء **Explorer**، استعرض للوصول إلى المجلد **Labfiles/01-analyze-images** ووسع المجلد **C-Sharp** أو **Python** وفقاً لتفضيلات اللغة لديك.
2. انقر بزر الماوس الأيمن فوق مجلد **image-analysis** وافتح وحدة طرفية متكاملة. ثم عليك تثبيت حزمة Azure AI Vision SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:

    **C#**
    
    ```
    dotnet add package Azure.AI.Vision.ImageAnalysis -v 1.0.0-beta.3
    ```

    > **ملاحظة**: إذا جرت مطالبتك بتثبيت ملحقات مجموعة أدوات التطوير، يمكنك إغلاق الرسالة بأمان.

    **Python**
    
    ```
    pip install azure-ai-vision-imageanalysis==1.0.0b3
    ```

    > **نصيحة**: إذا كنت تقوم بهذا النشاط العملي على جهازك الخاص، فسوف تحتاج أيضًا إلى تثبيت `matplotlib` و `pillow`.
    
3. اعرض محتويات مجلد **تحليل الصور**، ولاحظ أنه يحتوي على ملف لإعدادات التكوين:
    - **C#**: appsettings.json
    - **Python**: .env

    يمكنك فتح ملف التكوين وتحديث قيم التكوين التي يحتوي عليها لتعكس **نقطة النهاية** و**مفتاح** المصادقة لمورد خدمات الذكاء الاصطناعي في Azure. احفظ تغييراتك.
4. لاحظ أن مجلد **تحليل الصور** يحتوي على ملف تعليمات برمجية لتطبيق العميل:

    - **C#**: Program.cs
    - **Python**: image-analysis.py

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
    
## عرض الصور التي ستحللها

في هذا التمرين، ستستخدم خدمة الذكاء الاصطناعي في Azure Vision لتحليل صور متعددة.

1. في تعليمة Visual Studio البرمجية، وسع مجلد **تحليل الصور** ومجلد **الصور** الذي يحتوي عليه.
2. حدد كل ملفات الصور تباعاً لعرضها في Visual Studio Code.

## تحليل صورة لاقتراح تسمية توضيحية

أنت الآن جاهز لاستخدام SDK للاتصال بخدمة Vision وتحليل الصورة.

1. في ملف التعليمات البرمجية لتطبيق العميل الخاص بك (**Program.cs** أو **image-ana Analysis.py**)، في الدالة **الرئيسية**، لاحظ أنه جرى توفير التعليمات البرمجية لتحميل إعدادات التكوين. ثم ابحث عن التعليق **مصادقة عميل الذكاء الاصطناعي في Azure Vision**. ثم، ضمن هذا التعليق، أضف التعليمات البرمجية الخاصة باللغة التالية لإنشاء كائن عميل الذكاء الاصطناعي في Azure Vision ومصادقته:

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

2. في الدالة **الرئيسية**، ضمن الرمز الذي أضفته للتو، لاحظ أن الرمز يحدد المسار إلى ملف صورة ثم يمرر مسار الصورة إلى دالتين أخريتين (**AnalyzeImage** **وBackgroundForeground**). هذه الوظائف لم تُنفذ بالكامل بعد.

3. في الدالة **AnalyzeImage**، ضمن التعليق **الحصول على نتيجة مع تحديد الميزات المراد استردادها**، أضف الرمز التالي:

**C#**

```C#
// Get result with specified features to be retrieved
ImageAnalysisResult result = client.Analyze(
    BinaryData.FromStream(stream),
    VisualFeatures.Caption | 
    VisualFeatures.DenseCaptions |
    VisualFeatures.Objects |
    VisualFeatures.Tags |
    VisualFeatures.People);
```

**Python**

```Python
# Get result with specified features to be retrieved
result = cv_client.analyze(
    image_data=image_data,
    visual_features=[
        VisualFeatures.CAPTION,
        VisualFeatures.DENSE_CAPTIONS,
        VisualFeatures.TAGS,
        VisualFeatures.OBJECTS,
        VisualFeatures.PEOPLE],
)
```
    
4. في الدالة **AnalyzeImage**، ضمن التعليق **عرض نتائج التحليلات**، أضف التعليمات البرمجية التالية (بما في ذلك التعليقات التي تشير إلى المكان الذي ستضيف فيه المزيد من التعليمات البرمجية لاحقاً.):

**C#**

```C#
// Display analysis results
// Get image captions
if (result.Caption.Text != null)
{
    Console.WriteLine(" Caption:");
    Console.WriteLine($"   \"{result.Caption.Text}\", Confidence {result.Caption.Confidence:0.00}\n");
}

// Get image dense captions
Console.WriteLine(" Dense Captions:");
foreach (DenseCaption denseCaption in result.DenseCaptions.Values)
{
    Console.WriteLine($"   Caption: '{denseCaption.Text}', Confidence: {denseCaption.Confidence:0.00}");
}

// Get image tags


// Get objects in the image


// Get people in the image
```

**Python**

```Python
# Display analysis results
# Get image captions
if result.caption is not None:
    print("\nCaption:")
    print(" Caption: '{}' (confidence: {:.2f}%)".format(result.caption.text, result.caption.confidence * 100))

# Get image dense captions
if result.dense_captions is not None:
    print("\nDense Captions:")
    for caption in result.dense_captions.list:
        print(" Caption: '{}' (confidence: {:.2f}%)".format(caption.text, caption.confidence * 100))

# Get image tags


# Get objects in the image


# Get people in the image

```
    
5. احفظ تغييراتك وارجع إلى الوحدة الطرفية المتكاملة لمجلد **تحليل الصور**، وأدخل الأمر التالي لتشغيل البرنامج باستخدام الوسيطة **image/street.jpg**:

**C#**

```
dotnet run images/street.jpg
```

**Python**

```
python image-analysis.py images/street.jpg
```
    
6. لاحظ الإخراج الذي يجب أن يتضمن تسمية توضيحية مقترحة للصورة **street.jpg**.
7. يمكنك تشغيل البرنامج مرة أخرى، هذه المرة باستخدام الوسيطة **image/building.jpg** لرؤية التسمية التوضيحية التي يجري إنشاؤها لصورة **Building.jpg**.
8. كرر الخطوة السابقة لإنشاء تسمية توضيحية لملف **images/person.jpg**.

## الحصول على العلامات المقترحة لصورة

قد يكون من المفيد في بعض الأحيان تحديد *العلامات* ذات الصلة التي توفر أدلة حول محتويات الصورة.

1. في الدالة **AnalyzeImage**، ضمن التعليق **الحصول على علامات الصور**، أضف التعليمات البرمجية التالية:

**C#**

```C#
// Get image tags
if (result.Tags.Values.Count > 0)
{
    Console.WriteLine($"\n Tags:");
    foreach (DetectedTag tag in result.Tags.Values)
    {
        Console.WriteLine($"   '{tag.Name}', Confidence: {tag.Confidence:F2}");
    }
}
```

**Python**

```Python
# Get image tags
if result.tags is not None:
    print("\nTags:")
    for tag in result.tags.list:
        print(" Tag: '{}' (confidence: {:.2f}%)".format(tag.name, tag.confidence * 100))
```

2. احفظ التغييرات وشغل البرنامج مرة واحدة لكل ملف من ملفات الصور في **مجلد الصور**، مع ملاحظة أنه بالإضافة إلى التسمية التوضيحية للصورة، يجري عرض قائمة بالعلامات المقترحة.

## الكشف عن العناصر وتحديد موقعها في صورة

*اكتشاف الكائنات* هو شكل محدد من أشكال رؤية الكمبيوتر حيث يجري تحديد الكائنات الفردية داخل الصورة والإشارة إلى موقعها بواسطة مربع محيط.

1. في الدالة **AnalyzeImage**، ضمن التعليق **الحصول على عناصر في الصورة**، أضف التعليمة البرمجية التالية:

**C#**

```C#
// Get objects in the image
if (result.Objects.Values.Count > 0)
{
    Console.WriteLine(" Objects:");

    // Prepare image for drawing
    stream.Close();
    System.Drawing.Image image = System.Drawing.Image.FromFile(imageFile);
    Graphics graphics = Graphics.FromImage(image);
    Pen pen = new Pen(Color.Cyan, 3);
    Font font = new Font("Arial", 16);
    SolidBrush brush = new SolidBrush(Color.WhiteSmoke);

    foreach (DetectedObject detectedObject in result.Objects.Values)
    {
        Console.WriteLine($"   \"{detectedObject.Tags[0].Name}\"");

        // Draw object bounding box
        var r = detectedObject.BoundingBox;
        Rectangle rect = new Rectangle(r.X, r.Y, r.Width, r.Height);
        graphics.DrawRectangle(pen, rect);
        graphics.DrawString(detectedObject.Tags[0].Name,font,brush,(float)r.X, (float)r.Y);
    }

    // Save annotated image
    String output_file = "objects.jpg";
    image.Save(output_file);
    Console.WriteLine("  Results saved in " + output_file + "\n");
}
```

**Python**

```Python
# Get objects in the image
if result.objects is not None:
    print("\nObjects in image:")

    # Prepare image for drawing
    image = Image.open(image_filename)
    fig = plt.figure(figsize=(image.width/100, image.height/100))
    plt.axis('off')
    draw = ImageDraw.Draw(image)
    color = 'cyan'

    for detected_object in result.objects.list:
        # Print object name
        print(" {} (confidence: {:.2f}%)".format(detected_object.tags[0].name, detected_object.tags[0].confidence * 100))
        
        # Draw object bounding box
        r = detected_object.bounding_box
        bounding_box = ((r.x, r.y), (r.x + r.width, r.y + r.height)) 
        draw.rectangle(bounding_box, outline=color, width=3)
        plt.annotate(detected_object.tags[0].name,(r.x, r.y), backgroundcolor=color)

    # Save annotated image
    plt.imshow(image)
    plt.tight_layout(pad=0)
    outputfile = 'objects.jpg'
    fig.savefig(outputfile)
    print('  Results saved in', outputfile)
```

2. احفظ التغييرات وشغل البرنامج مرة واحدة لكل ملف من ملفات **الصور** الموجودة في مجلد الصور، مع ملاحظة أي كائنات يجري اكتشافها. بعد كل تشغيل، اعرض ملف **Objects.jpg** الذي جرى إنشاؤه في نفس المجلد مثل ملف التعليمات البرمجية الخاص بك لرؤية الكائنات ذات التعليقات التوضيحية.

## كشف الأشخاص وتحديدهم في الصورة

*اكتشاف الأشخاص* هو شكل محدد من أشكال الرؤية الحاسوبية يجري من خلاله التعرّف على الأفراد داخل الصورة والإشارة إلى موقعهم بواسطة مربع محيط.

1. في الدالة **AnalyzeImage**، ضمن التعليق **الحصول على أشخاص في الصورة**، أضف التعليمة البرمجية التالية:

**C#**

```C#
// Get people in the image
if (result.People.Values.Count > 0)
{
    Console.WriteLine($" People:");

    // Prepare image for drawing
    System.Drawing.Image image = System.Drawing.Image.FromFile(imageFile);
    Graphics graphics = Graphics.FromImage(image);
    Pen pen = new Pen(Color.Cyan, 3);
    Font font = new Font("Arial", 16);
    SolidBrush brush = new SolidBrush(Color.WhiteSmoke);

    foreach (DetectedPerson person in result.People.Values)
    {
        // Draw object bounding box
        var r = person.BoundingBox;
        Rectangle rect = new Rectangle(r.X, r.Y, r.Width, r.Height);
        graphics.DrawRectangle(pen, rect);
        
        // Return the confidence of the person detected
        //Console.WriteLine($"   Bounding box {person.BoundingBox.ToString()}, Confidence: {person.Confidence:F2}");
    }

    // Save annotated image
    String output_file = "persons.jpg";
    image.Save(output_file);
    Console.WriteLine("  Results saved in " + output_file + "\n");
}
```

**Python**

```Python
# Get people in the image
if result.people is not None:
    print("\nPeople in image:")

    # Prepare image for drawing
    image = Image.open(image_filename)
    fig = plt.figure(figsize=(image.width/100, image.height/100))
    plt.axis('off')
    draw = ImageDraw.Draw(image)
    color = 'cyan'

    for detected_people in result.people.list:
        # Draw object bounding box
        r = detected_people.bounding_box
        bounding_box = ((r.x, r.y), (r.x + r.width, r.y + r.height))
        draw.rectangle(bounding_box, outline=color, width=3)

        # Return the confidence of the person detected
        #print(" {} (confidence: {:.2f}%)".format(detected_people.bounding_box, detected_people.confidence * 100))
        
    # Save annotated image
    plt.imshow(image)
    plt.tight_layout(pad=0)
    outputfile = 'people.jpg'
    fig.savefig(outputfile)
    print('  Results saved in', outputfile)
```

2. (اختياري) يمكن إلغاء التعليق على أمر **Console.Writeline** ضمن قسم **إرجاع ثقة الشخص الذي جرى اكتشافه** لمراجعة مستوى الثقة الذي نجح إرجاعه إلى أنه جرى اكتشاف شخص في موضع معين من الصورة.

3. احفظ التغييرات وشغل البرنامج مرة واحدة لكل ملف من ملفات **الصور** الموجودة في مجلد الصور، مع ملاحظة أي كائنات يجري اكتشافها. بعد كل تشغيل، اعرض ملف **Objects.jpg** الذي جرى إنشاؤه في نفس المجلد مثل ملف التعليمات البرمجية الخاص بك لرؤية الكائنات ذات التعليقات التوضيحية.

> **ملاحظة**: في المهام السابقة، استخدمت أسلوباً واحداً لتحليل الصورة، ثم أضفت التعليمات البرمجية بشكل متزايد لتحليل النتائج وعرضها. توفر SDK أيضاً أساليب فردية لاقتراح التسميات التوضيحية، وتحديد العلامات، والكشف عن العناصر، وما إلى ذلك - ما يعني أنه يمكنك استخدام الطريقة الأكثر ملاءمة لإرجاع المعلومات التي تحتاج إليها فقط، ما يقلل من حجم حمولة البيانات التي تحتاج إلى إرجاعها. راجع وثائق [.NET SDK](https://learn.microsoft.com/dotnet/api/overview/azure/cognitiveservices/computervision?view=azure-dotnet) أو [وثائق Python SDK](https://learn.microsoft.com/python/api/azure-cognitiveservices-vision-computervision/azure.cognitiveservices.vision.computervision) لمزيد من التفاصيل.

## إزالة الخلفية أو إنشاء لون غير لامع في المقدمة لصورة

في بعض الحالات، قد تحتاج إلى إزالة خلفية الصورة أو قد ترغب في إنشاء لون غير لامع لمقدمة تلك الصورة. لنبدأ بإزالة الخلفية.

1. في ملف التعليمات البرمجية، ابحث عن الدالة **BackgroundForeground**، وضمن التعليق **إزالة الخلفية من الصورة أو إنشاء خلفية غير لامعة**، أضف التعليمات البرمجية التالية:

**C#**

```C#
// Remove the background from the image or generate a foreground matte
Console.WriteLine($" Background removal:");
// Define the API version and mode
string apiVersion = "2023-02-01-preview";
string mode = "backgroundRemoval"; // Can be "foregroundMatting" or "backgroundRemoval"

string url = $"computervision/imageanalysis:segment?api-version={apiVersion}&mode={mode}";

// Make the REST call
using (var client = new HttpClient())
{
    var contentType = new MediaTypeWithQualityHeaderValue("application/json");
    client.BaseAddress = new Uri(endpoint);
    client.DefaultRequestHeaders.Accept.Add(contentType);
    client.DefaultRequestHeaders.Add("Ocp-Apim-Subscription-Key", key);

    var data = new
    {
        url = $"https://github.com/MicrosoftLearning/mslearn-ai-vision/blob/main/Labfiles/01-analyze-images/Python/image-analysis/{imageFile}?raw=true"
    };

    var jsonData = JsonSerializer.Serialize(data);
    var contentData = new StringContent(jsonData, Encoding.UTF8, contentType);
    var response = await client.PostAsync(url, contentData);

    if (response.IsSuccessStatusCode) {
        File.WriteAllBytes("background.png", response.Content.ReadAsByteArrayAsync().Result);
        Console.WriteLine("  Results saved in background.png\n");
    }
    else
    {
        Console.WriteLine($"API error: {response.ReasonPhrase} - Check your body url, key, and endpoint.");
    }
}
```

**Python**

```Python
# Remove the background from the image or generate a foreground matte
print('\nRemoving background from image...')
    
url = "{}computervision/imageanalysis:segment?api-version={}&mode={}".format(endpoint, api_version, mode)

headers= {
    "Ocp-Apim-Subscription-Key": key, 
    "Content-Type": "application/json" 
}

image_url="https://github.com/MicrosoftLearning/mslearn-ai-vision/blob/main/Labfiles/01-analyze-images/Python/image-analysis/{}?raw=true".format(image_file)  

body = {
    "url": image_url,
}
    
response = requests.post(url, headers=headers, json=body)

image=response.content
with open("background.png", "wb") as file:
    file.write(image)
print('  Results saved in background.png \n')
```
    
2. احفظ التغييرات وشغل البرنامج مرة واحدة لكل ملف من ملفات الصور في مجلد **الصور** ما يفتح ملف **background.png** الذي يجري إنشاؤه في المجلد نفسه مثل ملف التعليمات البرمجية لكل صورة.  لاحظ كيفية إزالة الخلفية من كل الصور.

لننشئ الآن لون غير لامع للمقدمة لصورنا.

3. في ملف التعليمات البرمجية الخاص بك، ابحث عن دالة **BackgroundForeground**؛ وتحت التعليق **تحديد إصدار API ووضعه**، يمكن تغيير متغير الوضع ليكون `foregroundMatting`.

4. احفظ التغييرات وشغل البرنامج مرة واحدة لكل ملف من ملفات الصور في مجلد **الصور** ما يفتح ملف **background.png** الذي يجري إنشاؤه في المجلد نفسه مثل ملف التعليمات البرمجية لكل صورة.  لاحظ كيف جرى إنشاء مقدمة غير لامعة لصورك.

## تنظيف الموارد

إذا كنت لا تستخدم موارد Azure التي أنشأتها في هذا المختبر لوحدات التدريب الأخرى، فيمكنك حذفها لتجنب تكبد المزيد من الرسوم. وإليك الطريقة:

1. افتح مدخل Azure على `https://portal.azure.com`، وسجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure.

2. في شريط البحث العلوي، ابحث عن *حساب متعدد الخدمات لخدمات الذكاء الاصطناعي في Azure* وحدد مورد الحساب متعدد الخدمات لخدمات الذكاء الاصطناعي في Azure الذي أنشأته في هذا التمرين المعملي.

3. في صفحة المورد، حدد **حذف** واتبع الإرشادات لحذف المورد.

## مزيد من المعلومات

في هذا التمرين، استكشفت بعض إمكانيات تحليل الصور ومعالجتها لخدمة الذكاء الاصطناعي في Azure Vision. تتضمن الخدمة أيضاً إمكانيات اكتشاف الأشياء والأشخاص ومهام رؤية الكمبيوتر الأخرى.

لمزيد من المعلومات حول استخدام خدمة **الذكاء الاصطناعي في Azure Vision**، راجع [وثائق الذكاء الاصطناعي في Azure Vision](https://learn.microsoft.com/azure/ai-services/computer-vision/).
