---
title: दस्तावेज़ में टेक्स्ट हाइलाइट एनोटेशन जोड़ें
linktitle: दस्तावेज़ में टेक्स्ट हाइलाइट एनोटेशन जोड़ें
second_title: GroupDocs.Annotation .NET API
description: .NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ों में टेक्स्ट हाइलाइट एनोटेशन जोड़ने का तरीका जानें। इस व्यापक के साथ सहयोग और उत्पादकता बढ़ाएँ।
weight: 22
url: /hi/net/unlocking-annotation-power/add-text-highlight-annotation/
---

# दस्तावेज़ में टेक्स्ट हाइलाइट एनोटेशन जोड़ें

## परिचय
दस्तावेज़ प्रबंधन और सहयोग के क्षेत्र में, .NET के लिए GroupDocs.Annotation एक मजबूत समाधान के रूप में उभरता है, जो डेवलपर्स को अपने अनुप्रयोगों में टेक्स्ट हाइलाइट एनोटेशन को सहजता से एकीकृत करने के लिए सशक्त बनाता है। यह ट्यूटोरियल .NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ों में टेक्स्ट हाइलाइट एनोटेशन जोड़ने के लिए एक व्यापक मार्गदर्शिका के रूप में कार्य करता है। चरण-दर-चरण निर्देशों और विस्तृत स्पष्टीकरण के माध्यम से, आप इस शक्तिशाली पुस्तकालय की क्षमताओं का उपयोग करने में दक्षता हासिल करेंगे।
## आवश्यक शर्तें
टेक्स्ट हाइलाइट एनोटेशन के कार्यान्वयन में गहराई से जाने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
1. पर्यावरण सेटअप: .NET विकास के लिए एक उपयुक्त विकास वातावरण कॉन्फ़िगर करें।
2.  .NET के लिए GroupDocs.Annotation की स्थापना: दिए गए लिंक से .NET के लिए GroupDocs.Annotation को डाउनलोड और इंस्टॉल करें।[लिंक को डाउनलोड करें](https://releases.groupdocs.com/annotation/net/).
3. C# से परिचित: C# प्रोग्रामिंग भाषा की बुनियादी समझ।
4. एनोटेट करने के लिए दस्तावेज़: एक दस्तावेज़ तैयार करें (उदाहरण के लिए, पीडीएफ) जिसे आप एनोटेट करना चाहते हैं।

## नामस्थान आयात करें
आरंभ करने के लिए, .NET के लिए GroupDocs.Annotation की कार्यक्षमताओं का उपयोग करने के लिए अपने C# कोड में आवश्यक नामस्थान आयात करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#अब, आइए टेक्स्ट हाइलाइट एनोटेशन को कई चरणों में जोड़ने की प्रक्रिया को तोड़ें:
## चरण 1: आउटपुट पथ को परिभाषित करें
आउटपुट पथ निर्दिष्ट करें जहां एनोटेटेड दस्तावेज़ सहेजा जाएगा:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एनोटेटर प्रारंभ करें
 का एक उदाहरण बनाएं`Annotator` क्लास, दस्तावेज़ फ़ाइल नाम को एक पैरामीटर के रूप में पास करना:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## चरण 3: हाइलाइट एनोटेशन बनाएं
 त्वरित करें ए`HighlightAnnotation` ऑब्जेक्ट बनाएं और उसके गुणों को कॉन्फ़िगर करें:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
```
## चरण 4: एनोटेशन जोड़ें
दस्तावेज़ में निर्मित हाइलाइट एनोटेशन जोड़ें:
```csharp
annotator.Add(highlight);
```
## चरण 5: एनोटेटेड दस्तावेज़ सहेजें
एनोटेटेड दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें:
```csharp
annotator.Save(outputPath);
```

## निष्कर्ष
अंत में, .NET के लिए GroupDocs.Annotation दस्तावेज़ों में टेक्स्ट हाइलाइट एनोटेशन को शामिल करने के लिए एक सुव्यवस्थित दृष्टिकोण प्रदान करता है। इस ट्यूटोरियल में उल्लिखित चरणों का पालन करके, डेवलपर्स अपने अनुप्रयोगों के भीतर दस्तावेज़ सहयोग और उत्पादकता को निर्बाध रूप से बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या .NET के लिए GroupDocs.Annotation सभी दस्तावेज़ प्रारूपों के साथ संगत है?
.NET के लिए GroupDocs.Annotation पीडीएफ, वर्ड, एक्सेल और अन्य सहित विभिन्न दस्तावेज़ प्रारूपों का समर्थन करता है। पूरी सूची के लिए दस्तावेज़ देखें।
### क्या एनोटेशन को विशिष्ट आवश्यकताओं के अनुसार अनुकूलित किया जा सकता है?
हां, डेवलपर्स के पास एनोटेशन की संपत्तियों और उपस्थिति पर पूर्ण नियंत्रण होता है, जिससे विभिन्न आवश्यकताओं को पूरा करने के लिए अनुकूलन की अनुमति मिलती है।
### क्या .NET के लिए GroupDocs.Annotation के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
 हां, आप दिए गए निःशुल्क परीक्षण तक पहुंच कर .NET के लिए GroupDocs.Annotation की सुविधाओं का पता लगा सकते हैं[जोड़ना](https://releases.groupdocs.com/).
### मैं .NET के लिए GroupDocs.Annotation से संबंधित किसी भी समस्या या प्रश्न के लिए समर्थन कैसे प्राप्त कर सकता हूं?
 समर्थन और सहायता के लिए, आप GroupDocs.Annotation फोरम पर जा सकते हैं[यहाँ](https://forum.groupdocs.com/c/annotation/10).
### .NET के लिए GroupDocs.Annotation के लिए कौन से लाइसेंसिंग विकल्प उपलब्ध हैं?
 .NET के लिए GroupDocs.Annotation विभिन्न लाइसेंसिंग विकल्प प्रदान करता है, जिसमें परीक्षण उद्देश्यों के लिए अस्थायी लाइसेंस और उत्पादन वातावरण के लिए वाणिज्यिक लाइसेंस शामिल हैं। खरीद पृष्ठ पर जाएँ[यहाँ](https://purchase.groupdocs.com/buy) अधिक जानकारी के लिए।