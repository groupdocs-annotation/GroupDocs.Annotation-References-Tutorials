---
categories:
- Document Processing
date: '2026-10-05'
description: GroupDocs.Annotation .NET का उपयोग करके C# में साफ़ दस्तावेज़ प्रीव्यू
  बनाते समय एनोटेशन को छुपाने का तरीका सीखें। कोड उदाहरण, प्रदर्शन सुझाव और समस्या
  निवारण के साथ चरण-दर-चरण मार्गदर्शिका।
keywords:
- how to hide annotations
- preview document without annotations
- remove annotations from preview
- clean document preview .NET
- generate document preview without annotations
lastmod: '2026-10-05'
linktitle: एनोटेशन के बिना दस्तावेज़ प्रीव्यू
og_description: C# में साफ़ दस्तावेज़ प्रीव्यू बनाते समय एनोटेशन को छुपाने का तरीका
  सीखें। यह मार्गदर्शिका सेटअप, कोड, प्रदर्शन सुझाव और समस्या निवारण को कवर करती है।
og_image_alt: Guide showing how to generate document preview without annotations using
  GroupDocs.Annotation for .NET
og_title: C# में दस्तावेज़ प्रीव्यू बनाते समय एनोटेशन को कैसे छुपाएँ
schemas:
- author: GroupDocs
  dateModified: '2026-10-05'
  description: Learn how to hide annotations while generating clean document previews
    in C# using GroupDocs.Annotation .NET. Step-by-step guide with code examples,
    performance tips, and troubleshooting.
  headline: How to hide annotations when generating document preview in C#
  type: TechArticle
- description: Learn how to hide annotations while generating clean document previews
    in C# using GroupDocs.Annotation .NET. Step-by-step guide with code examples,
    performance tips, and troubleshooting.
  name: How to hide annotations when generating document preview in C#
  steps:
  - name: initialize your annotator (the foundation)
    text: The `Annotator` class loads a document and provides methods for rendering
      and annotation manipulation. csharp using (Annotator annotator = new Annotator("path/to/your/document"))
      { // All your preview generation happens within this scope }
  - name: configure your preview options (this is where the magic happens)
    text: The `PreviewOptions` class defines rendering parameters such as format,
      resolution, and whether annotations are included. csharp // Define how each
      page should be handled during preview generation PreviewOptions previewOptions
      = new PreviewOptions(pageNumber => { var pagePath = $"output_directory\\r
  - name: generate the preview (the payoff)
    text: The `GeneratePreview` method processes the document according to the supplied
      options and returns file paths for the created images. csharp annotator.Document.GeneratePreview(previewOptions);
  type: HowTo
- questions:
  - answer: Absolutely! GroupDocs.Annotation supports over 50 formats—including PDF,
      PPTX, XLSX, and common image types. See the [documentation](https://docs.groupdocs.com/annotation/net/)
      for the full list.
    question: Can I preview documents other than DOCX files?
  - answer: Initialise the `Annotator` with a `LoadOptions` object that includes the
      password. The `LoadOptions` class lets you specify the document password and
      other loading parameters.
    question: How do I handle password‑protected documents?
  - answer: Yes. The same code works in ASP.NET, but store generated images in a temporary
      folder and clean them up after the response to avoid disk bloat.
    question: Can I generate previews in a web application?
  - answer: PNG offers the highest quality, JPEG loads faster, and WebP provides the
      best compression if your target browsers support it. PNG is the safest default.
    question: What’s the best output format for web display?
  - answer: Process pages in batches of 5‑10, monitor memory usage, and optionally
      show a progress bar to improve the user experience.
    question: How do I handle very large documents efficiently?
  type: FAQPage
tags:
- groupdocs
- document-preview
- annotations
- dotnet
- csharp
title: C# में दस्तावेज़ प्रीव्यू बनाते समय एनोटेशन को कैसे छुपाएँ
type: docs
url: /hi/net/document-preview/create-document-preview-without-annotations-groupdocs-dotnet/
weight: 1
---

# C# में दस्तावेज़ पूर्वावलोकन बनाते समय एनोटेशन को कैसे छुपाएँ

यदि आपको दस्तावेज़ का पूर्वावलोकन साझा करना है लेकिन **एनोटेशन छुपाएँ** चाहते हैं, तो आप सही जगह पर हैं। यह ट्यूटोरियल आपको C# में GroupDocs.Annotation for .NET के साथ साफ़, एनोटेशन‑मुक्त पूर्वावलोकन बनाने का तरीका दिखाता है, जिसमें स्थापना से लेकर प्रदर्शन अनुकूलन तक सब कुछ शामिल है।

## त्वरित उत्तर
- **प्राथमिक क्लास जो पूर्वावलोकन बनाती है?** The `Annotator` class.
- **कौन सा विकल्प एनोटेशन को अक्षम करता है?** Set `RenderAnnotations = false` in `PreviewOptions`.
- **न्यूनतम .NET संस्करण?** .NET 6 की सिफारिश की जाती है; .NET Core 3.1 भी काम करता है।
- **क्या मैं PDFs और Word फ़ाइलों का पूर्वावलोकन कर सकता हूँ?** Yes – over 50 formats are supported.
- **परीक्षण के लिए लाइसेंस चाहिए?** A temporary license is available for free trials.

## एनोटेशन को छुपाने का क्या अर्थ है?

*एनोटेशन को छुपाना* वह प्रक्रिया है जिसमें दस्तावेज़ पूर्वावलोकन छवियों को उत्पन्न किया जाता है जबकि स्रोत फ़ाइल में मौजूद किसी भी टिप्पणी, हाइलाइट या मार्कअप को दबाया जाता है। यह तकनीक सुनिश्चित करती है कि दृश्य आउटपुट में केवल मूल सामग्री ही रहे, जिससे यह सार्वजनिक वितरण, क्लाइंट प्रस्तुतियों, या किसी भी स्थिति में उपयुक्त बनता है जहाँ आंतरिक नोट्स छुपे रहने चाहिए।

## आपको साफ़ दस्तावेज़ पूर्वावलोकन क्यों चाहिए (और उन्हें कैसे प्राप्त करें)

जब आप क्लाइंट्स, पार्टनर्स या सार्वजनिक के साथ पूर्वावलोकन साझा करते हैं, तो आंतरिक टिप्पणियाँ अनप्रोफेशनल लग सकती हैं या गोपनीय रणनीति को उजागर कर सकती हैं। साफ़ पूर्वावलोकन सामग्री पर ध्यान केंद्रित रखते हैं और आपके कार्यप्रवाह की सुरक्षा करते हैं। GroupDocs.Annotation आपको एनोटेशन रेंडरिंग को टॉगल करने की सुविधा देता है, जिससे आप एक ही स्रोत फ़ाइल से एनोटेटेड और साफ़ दोनों संस्करण बना सकते हैं।

## शुरू करने से पहले आपको क्या चाहिए

### आवश्यकताएँ क्या हैं?
शुरू करने के लिए आपको अपने विकास मशीन पर निम्नलिखित घटकों को स्थापित करना होगा। इन वस्तुओं को तैयार रखने से कोड रनटाइम त्रुटियों के बिना चलता है और आप स्थानीय रूप से पूर्ण पूर्वावलोकन पाइपलाइन का परीक्षण कर सकते हैं।

- GroupDocs.Annotation for .NET 25.4.0 या बाद का (नवीनतम रिलीज़ मेमोरी‑ऑप्टिमाइज़्ड पूर्वावलोकन जनरेशन जोड़ता है)।
- Visual Studio 2022 या कोई भी .NET‑संगत IDE।
- एक वैध GroupDocs लाइसेंस (अस्थायी लाइसेंस मूल्यांकन के लिए मुफ्त हैं)।

## त्वरित सेटअप: अपने प्रोजेक्ट में GroupDocs.Annotation जोड़ना

### विकल्प 1: NuGet पैकेज मैनेजर कंसोल
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

### विकल्प 2: .NET CLI (मेरी व्यक्तिगत पसंद)
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

**प्रो टिप:** पैकेज संस्करण को सभी टीम सदस्यों में समान रखें ताकि सूक्ष्म रेंडरिंग अंतर से बचा जा सके।

स्थापना को एक छोटे sanity‑check से सत्यापित करें:
```csharp
using System.IO;
using GroupDocs.Annotation;

// This should compile without errors
using (Annotator annotator = new Annotator("path/to/document"))
{
    // You're good to go!
}
```

## आप एनोटेशन के बिना पूर्वावलोकन कैसे जनरेट कर सकते हैं?

`Annotator` से दस्तावेज़ लोड करें, `PreviewOptions` को कॉन्फ़िगर करें, और `GeneratePreview` को कॉल करें। `RenderAnnotations = false` सेट करने से इंजन आउटपुट छवियों से हर टिप्पणी, हाइलाइट और स्टैम्प को हटा देता है।

### चरण 1: अपने annotator को इनिशियलाइज़ करें (बुनियाद)
`Annotator` क्लास एक दस्तावेज़ लोड करता है और रेंडरिंग तथा एनोटेशन मैनिपुलेशन के लिए मेथड्स प्रदान करता है।  
```csharp
```csharp
using (Annotator annotator = new Annotator("path/to/your/document"))
{
    // All your preview generation happens within this scope
}
```
```

### चरण 2: अपने preview options को कॉन्फ़िगर करें (यहीं जादू होता है)
`PreviewOptions` क्लास रेंडरिंग पैरामीटर जैसे फ़ॉर्मेट, रिज़ॉल्यूशन, और क्या एनोटेशन शामिल हैं, को परिभाषित करता है।  
```csharp
```csharp
// Define how each page should be handled during preview generation
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = $"output_directory\\result{pageNumber}.png";
    return File.Create(pagePath);
});

// Set the output format for the preview as PNG
previewOptions.PreviewFormat = PreviewFormats.PNG;

// Specify which pages to include in the preview generation
previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};

// The key setting: disable rendering of annotations
previewOptions.RenderAnnotations = false;
```
```

### चरण 3: पूर्वावलोकन जनरेट करें (परिणाम)
`GeneratePreview` मेथड प्रदान किए गए विकल्पों के अनुसार दस्तावेज़ को प्रोसेस करता है और बनाई गई छवियों के फ़ाइल पाथ लौटाता है।  
```csharp
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
```

## सामान्य समस्याएँ (और उन्हें कैसे ठीक करें)

### समस्या 1: “फ़ाइल नहीं मिली” त्रुटियाँ
**लक्षण:** जब `Annotator` बनाया जाता है तो एक अपवाद फेंका जाता है।  
**समाधान:** पूर्ण पाथ का उपयोग करें या सुनिश्चित करें कि आपके रिलेटिव पाथ सही हैं। एक त्वरित sanity‑check इस प्रकार दिखता है:
```csharp
string fullPath = Path.GetFullPath("your-document.pdf");
using (Annotator annotator = new Annotator(fullPath))
```

### समस्या 2: खराब पूर्वावलोकन गुणवत्ता
**लक्षण:** आउटपुट छवियां धुंधली या पिक्सेलेटेड दिखती हैं।  
**समाधान:** स्पष्टता बढ़ाने के लिए `PreviewOptions` में DPI सेटिंग बढ़ाएँ:
```csharp
previewOptions.Width = 1920;  // Higher resolution
previewOptions.Height = 1080;
```

### समस्या 3: बड़े दस्तावेज़ों में मेमोरी समस्याएँ
**लक्षण:** `OutOfMemoryException` या स्पष्ट रूप से धीमी प्रोसेसिंग।  
**समाधान:** पूरे फ़ाइल को एक बार लोड करने के बजाय पेजों को बैच में प्रोसेस करें:
```csharp
// Process 5 pages at a time instead of all at once
previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5};
```

## वास्तविक उपयोग केस (जहाँ यह वास्तव में महत्वपूर्ण है)

### कानूनी दस्तावेज़ साझा करना
कानूनी फर्में अनुबंध पूर्वावलोकन वितरित कर सकती हैं जो आंतरिक बातचीत नोट्स को छुपाते हैं, जिससे क्लाइंट संचार पेशेवर रहता है।

### शैक्षणिक प्रकाशन
शोधकर्ता पीयर रिव्यू के बाद साफ़ पांडुलिपि ड्राफ्ट साझा कर सकते हैं, जिससे जर्नल सबमिशन से पहले समीक्षक टिप्पणियों को हटाया जा सके।

### व्यापार रिपोर्टिंग
स्टेकहोल्डर्स को परिष्कृत रिपोर्ट मिलती हैं जिसमें “इस संख्या की जाँच करें” या “बोर्ड मीटिंग से पहले अपडेट करें” जैसे नोट्स नहीं होते, जो अन्यथा विश्वास को कम कर सकते हैं।

### दस्तावेज़ अभिलेख
अनुपालन टीमें नियामक मानकों को पूरा करने के लिए एनोटेशन‑मुक्त प्रतियां संग्रहीत करती हैं, जबकि आंतरिक संदर्भ के लिए मूल एनोटेटेड संस्करण को संरक्षित रखती हैं।

## प्रदर्शन सर्वोत्तम प्रथाएँ

### बड़े फ़ाइलों के लिए मेमोरी को कैसे प्रबंधित करें?
पेजों को छोटे बैचों में प्रोसेस करें और `Annotator` को तुरंत डिस्पोज़ करें। यह तरीका 200 पेज से बड़े दस्तावेज़ों में अधिकतम 60 % तक मेमोरी उपयोग को कम करता है।
```csharp
// Good: Dispose properly
using (Annotator annotator = new Annotator(documentPath))
{
    // Generate preview
} // Automatically disposed here

// Avoid: Manual disposal (easy to forget)
Annotator annotator = new Annotator(documentPath);
// ... use annotator
annotator.Dispose(); // Easy to forget or skip due to exceptions
```

### बैच प्रोसेसिंग को कैसे तेज़ करें?
100‑पेज के दस्तावेज़ को 10 पेज के समूहों में विभाजित करें, प्रत्येक समूह को क्रमिक रूप से जनरेट करें, और परिणाम को एक अस्थायी फ़ोल्डर में लिखें। यह तकनीक सामान्य सर्वर हार्डवेयर पर कुल प्रोसेसिंग समय को लगभग 30 % तक कम करती है।
```csharp
// Process in batches of 10 pages
for (int startPage = 1; startPage <= totalPages; startPage += 10)
{
    int endPage = Math.Min(startPage + 9, totalPages);
    var pageRange = Enumerable.Range(startPage, endPage - startPage + 1).ToArray();
    
    previewOptions.PageNumbers = pageRange;
    annotator.Document.GeneratePreview(previewOptions);
}
```

### इष्टतम आउटपुट फ़ॉर्मेट कैसे चुनें?
- **PNG:** सर्वोत्तम दृश्य गुणवत्ता; विस्तृत स्कीमैटिक्स के लिए आदर्श।  
- **JPEG:** छोटा फ़ाइल आकार; टेक्स्ट‑भारी दस्तावेज़ों के लिए उपयुक्त जहाँ हल्की कम्प्रेशन आर्टिफैक्ट्स स्वीकार्य हों।  
- **WebP:** आधुनिक फ़ॉर्मेट जिसमें उत्कृष्ट कम्प्रेशन है; अपनाने से पहले ब्राउज़र समर्थन जांचें।

## उन्नत कॉन्फ़िगरेशन विकल्प

### फ़ाइल नामकरण को कैसे कस्टमाइज़ करें?
`PreviewOptions` लैम्ब्डा आपको प्रत्येक फ़ाइल नाम में पेज नंबर, टाइमस्टैम्प, या कस्टम पहचानकर्ता डालने की अनुमति देता है।
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    string timestamp = DateTime.Now.ToString("yyyyMMdd_HHmmss");
    var pagePath = $"previews\\{timestamp}_page_{pageNumber:D3}.png";
    return File.Create(pagePath);
});
```

### इमेज क्वालिटी को कैसे नियंत्रित करें?
`PreviewOptions` में `Width`, `Height`, और `Resolution` प्रॉपर्टीज़ को समायोजित करें। बड़े आयाम उच्च गुणवत्ता देते हैं लेकिन फ़ाइल आकार बढ़ता है।
```csharp
previewOptions.Width = 2400;   // Higher resolution
previewOptions.Height = 3200;  // Maintains aspect ratio
previewOptions.PreviewFormat = PreviewFormats.PNG; // Best quality
```

### केवल विशिष्ट पेजों को कैसे प्रोसेस करें?
`PageNumbers` कलेक्शन को उन सटीक पेजों पर सेट करें जिनकी आपको आवश्यकता है, जिससे I/O कम होता है और सैकड़ों पेज वाले दस्तावेज़ों के लिए जनरेशन तेज़ हो जाता है।
```csharp
// Only process odd pages (useful for double-sided documents)
var oddPages = Enumerable.Range(1, totalPages)
                        .Where(p => p % 2 == 1)
                        .ToArray();
previewOptions.PageNumbers = oddPages;
```

## समस्या निवारण गाइड

### पूर्वावलोकन जनरेशन चुपचाप क्यों फेल हो जाता है?
सामान्य कारणों में शामिल हैं:
1. आउटपुट डायरेक्टरी अनुपलब्ध या लिखने की अनुमति नहीं है।  
2. पासवर्ड‑सुरक्षित स्रोत दस्तावेज़।  
3. असमर्थित फ़ाइल फ़ॉर्मेट।  
4. अपर्याप्त सिस्टम मेमोरी।

### एनोटेशन अभी भी क्यों दिख रहे हैं?
सुनिश्चित करें कि `GeneratePreview` कॉल करने से पहले `PreviewOptions` इंस्टेंस पर `RenderAnnotations = false` सेट किया गया है। `RenderAnnotations` प्रॉपर्टी यह नियंत्रित करती है कि पूर्वावलोकन रेंडरिंग के दौरान एनोटेशन लेयर ड्रॉ की जाएँ या नहीं।
```csharp
previewOptions.RenderAnnotations = false;  // Must be explicitly false
previewOptions.RenderComments = false;     // Also disable comments if needed
```

### प्रदर्शन धीमा क्यों है?
- परीक्षण के दौरान रिज़ॉल्यूशन कम करें।  
- प्रति बैच कम पेज प्रोसेस करें।  
- सुनिश्चित करें कि आप नवीनतम GroupDocs.Annotation संस्करण (25.4.0 या नया) का उपयोग कर रहे हैं जिसमें प्रदर्शन सुधार शामिल हैं।

## कब इस दृष्टिकोण का उपयोग नहीं करना चाहिए
- **रीयल‑टाइम पूर्वावलोकन:** त्वरित, ऑन‑द‑फ़्लाई पूर्वावलोकन के लिए क्लाइंट‑साइड रेंडरिंग तेज़ हो सकती है।  
- **इंटरैक्टिव दस्तावेज़:** फ़ॉर्म या एम्बेडेड स्क्रिप्ट्स स्थैतिक छवियों के रूप में रेंडर होने पर कार्यक्षमता खो सकते हैं।  
- **स्केलेबल ग्राफ़िक्स:** यदि आपको वेक्टर‑आधारित आउटपुट (जैसे SVG) चाहिए, तो रास्टर छवियों के बजाय PDF पेज जनरेट करने पर विचार करें।

## निष्कर्ष

GroupDocs.Annotation for .NET के साथ एनोटेशन के बिना साफ़ दस्तावेज़ पूर्वावलोकन बनाना सरल है। याद रखें:

1. `Annotator` को सही ढंग से डिस्पोज़ करें।  
2. `PreviewOptions` में `RenderAnnotations = false` सेट करें।  
3. बड़े फ़ाइलों को बैच‑प्रोसेस करें ताकि मेमोरी उपयोग कम रहे।  
4. वास्तविक दस्तावेज़ों के साथ परीक्षण करें ताकि DPI और फ़ॉर्मेट विकल्पों को ठीक‑ठाक किया जा सके।

एक सरल टेस्ट फ़ाइल से शुरू करें, ऊपर दिए गए विकल्पों के साथ प्रयोग करें, और आपके पास पेशेवर‑ग्रेड, एनोटेशन‑मुक्त पूर्वावलोकन तैयार होंगे जो किसी भी दर्शकों के लिए उपयुक्त हैं।

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं DOCX फ़ाइलों के अलावा अन्य दस्तावेज़ों का पूर्वावलोकन कर सकता हूँ?**  
A: बिल्कुल! GroupDocs.Annotation 50 से अधिक फ़ॉर्मेट्स का समर्थन करता है—जिसमें PDF, PPTX, XLSX, और सामान्य इमेज टाइप्स शामिल हैं। पूर्ण सूची के लिए [दस्तावेज़ीकरण](https://docs.groupdocs.com/annotation/net/) देखें।

**Q: पासवर्ड‑सुरक्षित दस्तावेज़ों को कैसे हैंडल करूँ?**  
A: `Annotator` को एक `LoadOptions` ऑब्जेक्ट के साथ इनिशियलाइज़ करें जिसमें पासवर्ड शामिल हो। `LoadOptions` क्लास आपको दस्तावेज़ पासवर्ड और अन्य लोडिंग पैरामीटर निर्दिष्ट करने की अनुमति देती है।  
```csharp
LoadOptions loadOptions = new LoadOptions { Password = "your-password" };
using (Annotator annotator = new Annotator("protected-doc.pdf", loadOptions))
```

**Q: क्या मैं वेब एप्लिकेशन में पूर्वावलोकन जनरेट कर सकता हूँ?**  
A: हाँ। वही कोड ASP.NET में काम करता है, लेकिन उत्पन्न छवियों को एक अस्थायी फ़ोल्डर में रखें और प्रतिक्रिया के बाद उन्हें साफ़ करें ताकि डिस्क बloat न हो।

**Q: वेब डिस्प्ले के लिए सबसे अच्छा आउटपुट फ़ॉर्मेट क्या है?**  
A: PNG सबसे उच्च गुणवत्ता देता है, JPEG तेज़ लोड होता है, और WebP सबसे अच्छा कम्प्रेशन देता है यदि आपके लक्ष्य ब्राउज़र इसका समर्थन करते हैं। PNG सबसे सुरक्षित डिफ़ॉल्ट है।

**Q: बहुत बड़े दस्तावेज़ों को कुशलता से कैसे हैंडल करूँ?**  
A: पेजों को 5‑10 के बैच में प्रोसेस करें, मेमोरी उपयोग की निगरानी करें, और वैकल्पिक रूप से प्रोग्रेस बार दिखाएँ ताकि उपयोगकर्ता अनुभव बेहतर हो।

**Q: क्या मैं आउटपुट इमेज क्वालिटी को कस्टमाइज़ कर सकता हूँ?**  
A: हाँ—`PreviewOptions` में `Width`, `Height`, और `Resolution` को समायोजित करें। बड़े मान क्वालिटी बढ़ाते हैं लेकिन फ़ाइल आकार भी बढ़ता है।

**Q: यदि मुझे दोनों एनोटेटेड और साफ़ संस्करण चाहिए तो?**  
A: पूर्वावलोकन को दो बार चलाएँ—एक बार `RenderAnnotations = true` के साथ और एक बार `false` के साथ। प्रत्येक सेट को अलग-अलग डायरेक्टरी में संग्रहीत करें ताकि आसान रीट्रीवल हो सके।

## संसाधन

- [GroupDocs.Annotation .NET दस्तावेज़ीकरण](https://docs.groupdocs.com/annotation/net/)  
- [GroupDocs Annotation API रेफ़रेंस](https://reference.groupdocs.com/annotation/net/)  
- [GroupDocs रिलीज़ .NET के लिए](https://releases.groupdocs.com/annotation/net/)  
- [GroupDocs लाइसेंस खरीदें](https://purchase.groupdocs.com/buy)  
- [GroupDocs फ्री ट्रायल्स](https://releases.groupdocs.com/annotation/net/)  
- [अस्थायी लाइसेंस अनुरोध करें](https://purchase.groupdocs.com/temporary-license/)  
- [GroupDocs फ़ोरम](https://forum.groupdocs.com/c/annotation/)  

**अंतिम अपडेट:** 2026-10-05  
**परीक्षण किया गया:** GroupDocs.Annotation 25.4.0 for .NET  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल

- [PDF एनोटेशन हटाने का तरीका C# – GroupDocs.Annotation गाइड](/annotation/net/annotation-management/remove-annotations-groupdocs-annotation-dotnet/)
- [.NET में टिप्पणी के बिना दस्तावेज़ पूर्वावलोकन जनरेट करें](/annotation/net/document-preview/groupdocs-annotation-net-document-preview-no-comments/)
- [कस्टम फ़ॉन्ट लोड करें .NET - GroupDocs.Annotation इंटीग्रेशन गाइड](/annotation/net/advanced-usage/loading-custom-fonts/)