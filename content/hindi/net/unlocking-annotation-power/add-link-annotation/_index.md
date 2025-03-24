---
title: दस्तावेज़ में लिंक एनोटेशन जोड़ें
linktitle: दस्तावेज़ में लिंक एनोटेशन जोड़ें
second_title: GroupDocs.Annotation .NET API
description: जानें कि .NET के लिए Groupdocs.Annotation का उपयोग करके दस्तावेज़ों में लिंक एनोटेशन कैसे जोड़ें। सहयोग और अन्तरक्रियाशीलता को सहजता से बढ़ाएँ।
weight: 16
url: /hi/net/unlocking-annotation-power/add-link-annotation/
---

# दस्तावेज़ में लिंक एनोटेशन जोड़ें

## परिचय
.NET के लिए Groupdocs.Annotation एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को व्यापक एनोटेशन कार्यात्मकताओं को उनके .NET अनुप्रयोगों में सहजता से एकीकृत करने में सक्षम बनाती है। इसके द्वारा प्रदान की जाने वाली प्रमुख विशेषताओं में से एक दस्तावेज़ों में लिंक एनोटेशन जोड़ने, सहयोग और अन्तरक्रियाशीलता बढ़ाने की क्षमता है।
## आवश्यक शर्तें
लिंक एनोटेशन जोड़ने की प्रक्रिया में उतरने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित शर्तें हैं:
- C# प्रोग्रामिंग भाषा की बुनियादी समझ।
- .NET लाइब्रेरी के लिए Groupdocs.Annotation स्थापित किया गया।
- उस दस्तावेज़ तक पहुंच जिसे आप एनोटेट करना चाहते हैं।

## नामस्थान आयात करें
सबसे पहले, आपको .NET कार्यात्मकताओं के लिए Groupdocs.Annotation का उपयोग करने के लिए आवश्यक नामस्थान आयात करने की आवश्यकता है। यह आपके एप्लिकेशन को दस्तावेज़ों को एनोटेट करने के लिए आवश्यक कक्षाओं और विधियों तक पहुंचने की अनुमति देता है।
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## चरण 1: आउटपुट पथ सेट करें
उस पथ को परिभाषित करें जहां आप एनोटेटेड दस्तावेज़ को सहेजना चाहते हैं।
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एनोटेटर प्रारंभ करें
 का एक उदाहरण बनाएं`Annotator` जिस दस्तावेज़ को आप एनोटेट करना चाहते हैं उसका पथ प्रदान करके क्लास बनाएं।
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां जाएगा
}
```
## चरण 3: लिंक एनोटेशन बनाएं
 ए को परिभाषित करें`LinkAnnotation` ऑब्जेक्ट बनाएं और उसके गुण जैसे संदेश, अपारदर्शिता, पृष्ठ संख्या, पृष्ठभूमि रंग, बिंदु, उत्तर और URL निर्दिष्ट करें।
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
    },
    Url = "https://www.google.com"
};
```
## चरण 4: एनोटेशन जोड़ें
 का उपयोग करके दस्तावेज़ में निर्मित लिंक एनोटेशन जोड़ें`Add` एनोटेटर उदाहरण की विधि।
```csharp
annotator.Add(link);
```
## चरण 5: दस्तावेज़ सहेजें
एनोटेटेड दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें।
```csharp
annotator.Save(outputPath);
```
## चरण 6: सफलता संदेश प्रदर्शित करें
एनोटेटेड दस्तावेज़ की सफल बचत के बारे में उपयोगकर्ता को सूचित करें।
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष
अंत में, उपरोक्त चरणों का पालन करके, आप .NET के लिए Groupdocs.Annotation का उपयोग करके दस्तावेज़ों में लिंक एनोटेशन को सहजता से जोड़ सकते हैं। यह दस्तावेज़ सहयोग को बढ़ाता है और उपयोगकर्ताओं को इंटरैक्टिव सुविधाएँ प्रदान करता है।
## अक्सर पूछे जाने वाले प्रश्न
### क्या .NET के लिए Groupdocs.Annotation सभी प्रकार के दस्तावेज़ों के साथ संगत है?
.NET के लिए Groupdocs.Annotation पीडीएफ, वर्ड, एक्सेल और अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुरूप एनोटेशन के विभिन्न गुणों जैसे रंग, अस्पष्टता और आकार को अनुकूलित कर सकते हैं।
### क्या .NET के लिए Groupdocs.Annotation वास्तविक समय सहयोग सुविधाएँ प्रदान करता है?
हाँ, .NET के लिए Groupdocs.Annotation वास्तविक समय सहयोग सुविधाएँ प्रदान करता है जो कई उपयोगकर्ताओं को एक साथ दस्तावेज़ों को एनोटेट करने की अनुमति देता है।
### क्या Groupdocs उत्पादों के लिए तकनीकी सहायता उपलब्ध है?
 हाँ, ग्रुपडॉक्स उत्पादों के लिए तकनीकी सहायता फ़ोरम और समर्थन के माध्यम से उपलब्ध है[यहाँ](https://forum.groupdocs.com/c/annotation/10).
### क्या मैं खरीदने से पहले .NET के लिए Groupdocs.Annotation आज़मा सकता हूँ?
हाँ, आप खरीदारी करने से पहले .NET की विशेषताओं का पता लगाने के लिए Groupdocs.Annotation के निःशुल्क परीक्षण का लाभ उठा सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).