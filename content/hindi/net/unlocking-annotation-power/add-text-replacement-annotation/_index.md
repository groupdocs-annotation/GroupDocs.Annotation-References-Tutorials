---
title: दस्तावेज़ में टेक्स्ट रिप्लेसमेंट एनोटेशन जोड़ें
linktitle: दस्तावेज़ में टेक्स्ट रिप्लेसमेंट एनोटेशन जोड़ें
second_title: GroupDocs.Annotation .NET API
description: जानें कि .NET के लिए GroupDocs.Annotation का उपयोग करके आसानी से अपने .NET दस्तावेज़ों में टेक्स्ट रिप्लेसमेंट एनोटेशन कैसे जोड़ें। अपनी दस्तावेज़ हेरफेर क्षमताओं को बढ़ाएँ।
type: docs
weight: 24
url: /hi/net/unlocking-annotation-power/add-text-replacement-annotation/
---
## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Annotation का उपयोग करके आपके दस्तावेज़ों में टेक्स्ट रिप्लेसमेंट एनोटेशन जोड़ने की प्रक्रिया में आपका मार्गदर्शन करेंगे। यह शक्तिशाली लाइब्रेरी डेवलपर्स को विभिन्न प्रकार के दस्तावेज़ों को प्रोग्रामेटिक रूप से हेरफेर और एनोटेट करने की अनुमति देती है। इस ट्यूटोरियल के अंत तक, आप अपने .NET अनुप्रयोगों में टेक्स्ट रिप्लेसमेंट एनोटेशन को सहजता से एकीकृत करने के ज्ञान से लैस हो जाएंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यकताएँ स्थापित हैं:
### 1. .NET फ्रेमवर्क स्थापित
सुनिश्चित करें कि आपकी विकास मशीन पर .NET फ्रेमवर्क स्थापित है। आप इसे माइक्रोसॉफ्ट वेबसाइट से डाउनलोड कर सकते हैं।
### 2. .NET लाइब्रेरी के लिए GroupDocs.Annotation
 .NET लाइब्रेरी के लिए GroupDocs.Annotation को डाउनलोड और इंस्टॉल करें[वेबसाइट](https://releases.groupdocs.com/annotation/net/). यह लाइब्रेरी विभिन्न दस्तावेज़ प्रारूपों में एनोटेशन के साथ काम करने के लिए आवश्यक उपकरण और कार्यक्षमता प्रदान करती है।
### 3. विकास पर्यावरण सेटअप
.NET एप्लिकेशन बनाने और चलाने के लिए अपना पसंदीदा विकास वातावरण, जैसे विज़ुअल स्टूडियो, सेट करें।

## नामस्थान आयात करें
कोडिंग भाग में गोता लगाने से पहले, आइए .NET के लिए GroupDocs.Annotation के साथ काम करने के लिए आवश्यक आवश्यक नामस्थान आयात करें:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## चरण 1: आउटपुट पथ को परिभाषित करें
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
यहां, हम आउटपुट पथ को परिभाषित करते हैं जहां एनोटेटेड दस्तावेज़ सहेजा जाएगा।
## चरण 2: एनोटेटर प्रारंभ करें
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां रखा जाएगा
}
```
हम संसाधनों के उचित निपटान को सुनिश्चित करने के लिए उपयोग ब्लॉक के भीतर इनपुट दस्तावेज़ ("input.pdf") को निर्दिष्ट करके एनोटेटर ऑब्जेक्ट को प्रारंभ करते हैं।
## चरण 3: प्रतिस्थापन एनोटेशन बनाएं
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
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
    TextToReplace = "replaced text"
};
```
यहां, हम निर्माण तिथि, फ़ॉन्ट रंग, संदेश, अस्पष्टता, पृष्ठ संख्या, पृष्ठभूमि रंग, बिंदु (निर्देशांक), उत्तर (टिप्पणियां), और प्रतिस्थापित करने के लिए पाठ जैसे विभिन्न गुणों के साथ एक रिप्लेसमेंटएनोटेशन ऑब्जेक्ट बनाते हैं।
## चरण 4: एनोटेशन जोड़ें
```csharp
annotator.Add(replacement);
```
हम बनाए गए प्रतिस्थापन एनोटेशन को एनोटेटर में जोड़ते हैं।
## चरण 5: दस्तावेज़ सहेजें
```csharp
annotator.Save(outputPath);
```
अंत में, हम एनोटेटेड दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजते हैं।
## चरण 6: सफलता संदेश प्रदर्शित करें
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
एक सफलता संदेश प्रदर्शित होता है जो दर्शाता है कि दस्तावेज़ सफलतापूर्वक सहेजा गया है।

## निष्कर्ष
इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ों में टेक्स्ट प्रतिस्थापन एनोटेशन जोड़ने की प्रक्रिया को कवर किया है। चरण-दर-चरण मार्गदर्शिका का पालन करके और आवश्यक शर्तों को समझकर, आप इस कार्यक्षमता को अपने .NET अनुप्रयोगों में आसानी से एकीकृत कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं .NET के लिए GroupDocs.Annotation का उपयोग करके विभिन्न प्रारूपों के दस्तावेज़ों को एनोटेट कर सकता हूँ?
हां, .NET के लिए GroupDocs.Annotation PDF, DOCX, PPTX, XLSX और अन्य जैसे विभिन्न दस्तावेज़ प्रारूपों को एनोटेट करने का समर्थन करता है।
### क्या .NET के लिए GroupDocs.Annotation डेस्कटॉप और वेब अनुप्रयोगों दोनों के लिए उपयुक्त है?
हां, .NET के लिए GroupDocs.Annotation का उपयोग डेस्कटॉप और वेब एप्लिकेशन दोनों में किया जा सकता है, जो डेवलपर्स के लिए लचीलापन प्रदान करता है।
### क्या मैं .NET के लिए GroupDocs.Annotation का उपयोग करके जोड़े गए एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
बिल्कुल, आप रंग, अस्पष्टता, फ़ॉन्ट इत्यादि जैसे गुणों को संशोधित करके एनोटेशन की उपस्थिति को अनुकूलित कर सकते हैं।
### क्या .NET के लिए GroupDocs.Annotation सहयोगी एनोटेशन सुविधाओं के लिए समर्थन प्रदान करता है?
हाँ, .NET के लिए GroupDocs.Annotation सहयोगी एनोटेशन के लिए सुविधाएँ प्रदान करता है, जिससे कई उपयोगकर्ताओं को एक साथ दस्तावेज़ों को एनोटेट करने की अनुमति मिलती है।
### क्या .NET के लिए GroupDocs.Annotation के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
हाँ, आप .NET के लिए GroupDocs.Annotation के निःशुल्क परीक्षण का लाभ उठा सकते हैं[वेबसाइट](https://releases.groupdocs.com/).