---
"description": "حسّن تطبيقات .NET لديك باستخدام GroupDocs.Annotation لشرح مستندات سلس. يتضمن البرنامج التعليمي خطوة بخطوة."
"linktitle": "تحميل المستند من FTP"
"second_title": "GroupDocs.Annotation .NET API"
"title": "تحميل المستند من FTP"
"url": "/ar/net/document-loading-essentials/load-document-from-ftp/"
type: docs
"weight": 12
---

# تحميل المستند من FTP

## مقدمة
GroupDocs.Annotation لـ .NET هي مكتبة متعددة الاستخدامات مصممة لتسهيل إضافة التعليقات التوضيحية للمستندات داخل تطبيقات .NET بسهولة. سواء كنت تتعامل مع ملفات PDF، أو مستندات Microsoft Office، أو صور، أو تنسيقات أخرى، توفر هذه المكتبة حلاً موحدًا لإضافة التعليقات التوضيحية، مثل التعليقات، والتمييزات، والأشكال، لتحسين التعاون وإدارة المستندات.
## المتطلبات الأساسية
قبل الغوص في البرنامج التعليمي، تأكد من أن لديك المتطلبات الأساسية التالية:
1. معرفة لغة البرمجة C#: تعد الكفاءة في لغة البرمجة C# ضرورية لفهم وتنفيذ أمثلة التعليمات البرمجية المقدمة في هذا البرنامج التعليمي.
2. GroupDocs.Annotation لـ .NET: تأكد من تنزيل GroupDocs.Annotation لـ .NET وتثبيته من [رابط التحميل](https://releases.groupdocs.com/annotation/net/)اتبع تعليمات التثبيت لدمج المكتبة في مشروع .NET الخاص بك بنجاح.
## استيراد مساحات الأسماء
للاستفادة من وظائف GroupDocs.Annotation لـ .NET، عليك استيراد مساحات الأسماء المطلوبة إلى مشروع C#. اتبع الخطوات التالية:

في مشروع C# الخاص بك، قم بتضمين المساحات الأساسية اللازمة في بداية ملف التعليمات البرمجية الخاص بك:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

الآن، دعونا نتعمق في عملية تحميل مستند من FTP وإضافة التعليقات التوضيحية إليه باستخدام GroupDocs.Annotation لـ .NET.
## الخطوة 1: تحديد مسار الإخراج
حدد مسار الإخراج الذي سيتم حفظ المستند الموضح فيه.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تحميل المستند من FTP
استرداد المستند من خادم FTP باستخدام مسار الملف المقدم.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // سيتم إضافة رمز الشرح هنا
}
```
## الخطوة 3: إضافة التعليقات التوضيحية
قم بتحديد وإضافة التعليق التوضيحي المطلوب، مثل تعليق توضيحي لمنطقة، إلى المستند.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## الخطوة 4: حفظ المستند الموضح
احفظ المستند الموضح في مسار الإخراج المحدد.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## الخطوة 5: استرداد الملف من FTP
تنفيذ الطريقة لجلب الملف من خادم FTP.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## الخطوة 6: إنشاء طلب FTP
إنشاء طلب FTP لتنزيل الملف.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## الخطوة 7: الحصول على تدفق الملف
استرداد تدفق الملف من استجابة FTP.
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## خاتمة
في الختام، يُمكّن GroupDocs.Annotation for .NET المطورين من دمج وظائف شرح المستندات بسلاسة في تطبيقات .NET الخاصة بهم. باتباع الدليل المفصل الموضح في هذا البرنامج التعليمي، يمكنك تحميل المستندات بكفاءة من FTP وإضافة الشروح بسهولة، مما يُحسّن التعاون وإدارة المستندات داخل تطبيقاتك.
## الأسئلة الشائعة
### هل GroupDocs.Annotation لـ .NET متوافق مع كافة تنسيقات المستندات؟
نعم، يدعم GroupDocs.Annotation لـ .NET مجموعة واسعة من تنسيقات المستندات، بما في ذلك PDF، ومستندات Microsoft Office، والصور، والمزيد.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية المضافة باستخدام GroupDocs.Annotation لـ .NET؟
بالتأكيد، يوفر GroupDocs.Annotation لـ .NET خيارات تخصيص شاملة لمظهر التعليقات التوضيحية، بما في ذلك الألوان والأنماط والأشكال.
### هل يوفر GroupDocs.Annotation لـ .NET الدعم لخدمات التخزين السحابي؟
نعم، يتكامل GroupDocs.Annotation for .NET بسلاسة مع خدمات التخزين السحابي الشهيرة، مما يسمح لك بتحميل المستندات وحفظها من خدمات مثل Dropbox وGoogle Drive وOneDrive.
### هل هناك نسخة تجريبية متاحة لـ GroupDocs.Annotation لـ .NET؟
نعم، يمكنك استكشاف ميزات GroupDocs.Annotation لـ .NET عن طريق تنزيل الإصدار التجريبي المجاني من [صفحة الإصدار](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على المساعدة الفنية أو الدعم لـ GroupDocs.Annotation لـ .NET؟
للحصول على المساعدة الفنية أو استكشاف الأخطاء وإصلاحها أو الاستفسارات العامة، يمكنك زيارة GroupDocs.Annotation لـ .NET [منتدى الدعم](https://forum.groupdocs.com/c/annotation/10).