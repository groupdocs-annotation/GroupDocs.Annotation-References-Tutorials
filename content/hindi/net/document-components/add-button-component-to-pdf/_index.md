---
"description": ".NET के लिए Groupdocs.Annotation का उपयोग करके इंटरैक्टिव बटन घटकों के साथ अपने PDF दस्तावेज़ों को बेहतर बनाएँ। सहज एकीकरण के लिए हमारे चरण-दर-चरण ट्यूटोरियल का पालन करें।"
"linktitle": "पीडीएफ दस्तावेज़ में बटन घटक जोड़ें"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "पीडीएफ दस्तावेज़ में बटन घटक जोड़ें"
"url": "/hi/net/document-components/add-button-component-to-pdf/"
type: docs
"weight": 10
---

# पीडीएफ दस्तावेज़ में बटन घटक जोड़ें

## परिचय
इस ट्यूटोरियल में, हम आपको .NET के लिए Groupdocs.Annotation का उपयोग करके PDF दस्तावेज़ में बटन घटक जोड़ने की प्रक्रिया के बारे में बताएंगे। यह चरण-दर-चरण मार्गदर्शिका सुनिश्चित करेगी कि आप इस सुविधा को आसानी से अपने प्रोजेक्ट में एकीकृत कर सकें।
## आवश्यक शर्तें
आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:
1. .NET के लिए Groupdocs.Annotation: सुनिश्चित करें कि आपने .NET के लिए Groupdocs.Annotation लाइब्रेरी स्थापित की है। आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.groupdocs.com/annotation/net/).
2. विकास वातावरण: .NET फ्रेमवर्क स्थापित करके उपयुक्त विकास वातावरण स्थापित करें।

## नामस्थान आयात करें
आगे बढ़ने से पहले, आवश्यक नामस्थानों को अपनी परियोजना में आयात करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
## चरण 1: आउटपुट पथ आरंभ करें
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: बटन घटक जोड़ें
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100),
        PenColor = 65535,
        Style = BorderStyle.Dashed,
        BorderWidth = 0,
        BorderColor = 0,
        AlternateName = "Name",
        PartialName = "Patial Name",
        NormalCaption = "Caption",
        ButtonColor = 16761035,
        Replies = new List<Reply>
        {
            new Reply
            {
                Comment = "First comment",
                RepliedOn = DateTime.Now
            },
            new Reply
            {
                Comment = "Second comment",
                RepliedOn = DateTime.Now
            }
        }
    };
    annotator.Add(button);
    annotator.Save("result.pdf");
}
```
## चरण 3: आउटपुट पथ प्रदर्शित करें
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
बधाई हो! आपने .NET के लिए Groupdocs.Annotation का उपयोग करके PDF दस्तावेज़ में बटन घटक सफलतापूर्वक जोड़ लिया है।

## निष्कर्ष
इस ट्यूटोरियल में, हमने दिखाया है कि .NET के लिए Groupdocs.Annotation का उपयोग करके PDF दस्तावेज़ों में बटन घटकों को कैसे शामिल किया जाए। इन चरणों का पालन करके, आप अपने PDF दस्तावेज़ों को इंटरैक्टिव सुविधाओं के साथ बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं बटन के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुसार बटन घटक के आकार, रंग और शैली जैसे विभिन्न गुणों को अनुकूलित कर सकते हैं।
### क्या Groupdocs.Annotation for .NET सभी PDF संस्करणों के साथ संगत है?
.NET के लिए Groupdocs.Annotation पीडीएफ संस्करणों की एक विस्तृत श्रृंखला का समर्थन करता है, जो अधिकांश दस्तावेजों के साथ संगतता सुनिश्चित करता है।
### क्या मैं एक एकल PDF दस्तावेज़ में एकाधिक बटन घटक जोड़ सकता हूँ?
बिल्कुल, आप Groupdocs.Annotation for .NET का उपयोग करके एक पीडीएफ दस्तावेज़ में जितने आवश्यक हो उतने बटन घटक जोड़ सकते हैं।
### क्या Groupdocs.Annotation for .NET अन्य फ़ाइल स्वरूपों के लिए समर्थन प्रदान करता है?
हां, पीडीएफ के अलावा, Groupdocs.Annotation for .NET DOCX, PPTX और XLSX सहित विभिन्न अन्य दस्तावेज़ स्वरूपों का समर्थन करता है।
### क्या परीक्षण के उद्देश्य से कोई परीक्षण संस्करण उपलब्ध है?
हां, आप यहां से Groupdocs.Annotation for .NET का निःशुल्क परीक्षण प्राप्त कर सकते हैं [यहाँ](https://releases.groupdocs.com/).