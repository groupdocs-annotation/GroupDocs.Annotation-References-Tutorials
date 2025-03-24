---
title: تحميل المستند من بروتوكول نقل الملفات
linktitle: تحميل المستند من بروتوكول نقل الملفات
second_title: GroupDocs.Annotation .NET API
description: قم بتحسين تطبيقات .NET الخاصة بك باستخدام GroupDocs.Annotation للحصول على تعليقات توضيحية سلسة للمستندات. وشملت البرنامج التعليمي خطوة بخطوة.
weight: 12
url: /ar/net/document-loading-essentials/load-document-from-ftp/
---
## مقدمة
تعد GroupDocs.Annotation for .NET مكتبة متعددة الاستخدامات مصممة لتسهيل إمكانات التعليقات التوضيحية للمستندات داخل تطبيقات .NET دون عناء. سواء كنت تتعامل مع ملفات PDF أو مستندات Microsoft Office أو الصور أو التنسيقات الأخرى، توفر هذه المكتبة حلاً موحدًا لإضافة التعليقات التوضيحية، مثل التعليقات والإبرازات والأشكال، لتعزيز التعاون وإدارة المستندات.
## المتطلبات الأساسية
قبل الغوص في البرنامج التعليمي، تأكد من توفر المتطلبات الأساسية التالية:
1. معرفة لغة C#: يعد إتقان لغة البرمجة C# أمرًا ضروريًا لفهم وتنفيذ أمثلة التعليمات البرمجية الواردة في هذا البرنامج التعليمي.
2.  GroupDocs.Annotation لـ .NET: تأكد من تنزيل وتثبيت GroupDocs.Annotation لـ .NET من[رابط التحميل](https://releases.groupdocs.com/annotation/net/). اتبع تعليمات التثبيت لدمج المكتبة في مشروع .NET الخاص بك بنجاح.
## استيراد مساحات الأسماء
من أجل الاستفادة من GroupDocs.Annotation لوظائف .NET، تحتاج إلى استيراد مساحات الأسماء المطلوبة إلى مشروع C# الخاص بك. اتبع الخطوات التالية:

ضمن مشروع C# الخاص بك، قم بتضمين مساحات الأسماء الضرورية في بداية ملف التعليمات البرمجية الخاص بك:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

الآن، دعونا نتعمق في عملية تحميل مستند من FTP وإضافة التعليقات التوضيحية إليه باستخدام GroupDocs.Annotation for .NET.
## الخطوة 1: تحديد مسار الإخراج
حدد مسار الإخراج حيث سيتم حفظ المستند المشروح.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تحميل المستند من FTP
قم باسترجاع المستند من خادم FTP باستخدام مسار الملف المقدم.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // سيتم إضافة رمز التعليق التوضيحي هنا
}
```
## الخطوة 3: إضافة تعليق توضيحي
قم بتعريف وإضافة التعليق التوضيحي المطلوب، مثل التعليق التوضيحي للمنطقة، إلى المستند.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## الخطوة 4: حفظ المستند المشروح
احفظ المستند المشروح في مسار الإخراج المحدد.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## الخطوة 5: استرداد الملف من FTP
قم بتنفيذ طريقة جلب الملف من خادم FTP.
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
قم بإنشاء طلب FTP لتنزيل الملف.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## الخطوة 7: الحصول على تدفق الملفات
استرداد دفق الملف من استجابة FTP.
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
في الختام، يعمل GroupDocs.Annotation for .NET على تمكين المطورين من دمج وظائف التعليقات التوضيحية للمستندات بسلاسة في تطبيقات .NET الخاصة بهم. باتباع الدليل التفصيلي الموضح في هذا البرنامج التعليمي، يمكنك تحميل المستندات بكفاءة من FTP وإضافة التعليقات التوضيحية بسهولة، مما يعزز التعاون وإدارة المستندات داخل تطبيقاتك.
## الأسئلة الشائعة
### هل GroupDocs.Annotation لـ .NET متوافق مع كافة تنسيقات المستندات؟
نعم، يدعم GroupDocs.Annotation for .NET نطاقًا واسعًا من تنسيقات المستندات، بما في ذلك PDF ومستندات Microsoft Office والصور والمزيد.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية المضافة باستخدام GroupDocs.Annotation لـ .NET؟
بالتأكيد، يوفر GroupDocs.Annotation for .NET خيارات تخصيص واسعة النطاق لمظهر التعليقات التوضيحية، بما في ذلك الألوان والأنماط والأشكال.
### هل يوفر GroupDocs.Annotation for .NET الدعم لخدمات التخزين السحابية؟
نعم، يتكامل GroupDocs.Annotation for .NET بسلاسة مع خدمات التخزين السحابية الشائعة، مما يسمح لك بتحميل المستندات وحفظها من خدمات مثل Dropbox وGoogle Drive وOneDrive.
### هل هناك إصدار تجريبي متاح لـ GroupDocs.Annotation لـ .NET؟
 نعم، يمكنك استكشاف ميزات GroupDocs.Annotation for .NET عن طريق تنزيل الإصدار التجريبي المجاني من[صفحة الإصدار](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على مساعدة فنية أو دعم بخصوص GroupDocs.Annotation لـ .NET؟
 للحصول على المساعدة الفنية أو استكشاف الأخطاء وإصلاحها أو الاستفسارات العامة، يمكنك زيارة GroupDocs.Annotation for .NET[منتدى الدعم](https://forum.groupdocs.com/c/annotation/10).