---
"description": "GroupDocs.Annotation for .NET का उपयोग करके आसानी से अपने .NET दस्तावेज़ों में टेक्स्ट प्रतिस्थापन एनोटेशन जोड़ना सीखें। अपने दस्तावेज़ हेरफेर क्षमताओं को बढ़ाएँ।"
"linktitle": "दस्तावेज़ में टेक्स्ट प्रतिस्थापन एनोटेशन जोड़ें"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "दस्तावेज़ में टेक्स्ट प्रतिस्थापन एनोटेशन जोड़ें"
"url": "/hi/net/unlocking-annotation-power/add-text-replacement-annotation/"
type: docs
"weight": 24
---

# दस्तावेज़ में टेक्स्ट प्रतिस्थापन एनोटेशन जोड़ें

## परिचय
इस ट्यूटोरियल में, हम आपको GroupDocs.Annotation for .NET का उपयोग करके अपने दस्तावेज़ों में टेक्स्ट रिप्लेसमेंट एनोटेशन जोड़ने की प्रक्रिया के बारे में बताएंगे। यह शक्तिशाली लाइब्रेरी डेवलपर्स को प्रोग्रामेटिक रूप से विभिन्न प्रकार के दस्तावेज़ों में हेरफेर करने और उन्हें एनोटेट करने की अनुमति देती है। इस ट्यूटोरियल के अंत तक, आप अपने .NET अनुप्रयोगों में टेक्स्ट रिप्लेसमेंट एनोटेशन को सहजता से एकीकृत करने के ज्ञान से लैस हो जाएँगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ स्थापित हैं:
### 1. .NET फ्रेमवर्क स्थापित
सुनिश्चित करें कि आपके डेवलपमेंट मशीन पर .NET फ्रेमवर्क इंस्टॉल है। आप इसे Microsoft वेबसाइट से डाउनलोड कर सकते हैं।
### 2. .NET लाइब्रेरी के लिए GroupDocs.Annotation
.NET लाइब्रेरी के लिए GroupDocs.Annotation डाउनलोड करें और इंस्टॉल करें [वेबसाइट](https://releases.groupdocs.com/annotation/net/)यह लाइब्रेरी विभिन्न दस्तावेज़ प्रारूपों में एनोटेशन के साथ काम करने के लिए आवश्यक उपकरण और कार्यात्मकताएं प्रदान करती है।
### 3. विकास पर्यावरण सेटअप
.NET अनुप्रयोग बनाने और चलाने के लिए अपना पसंदीदा विकास वातावरण, जैसे कि Visual Studio, सेट अप करें।

## नामस्थान आयात करें
कोडिंग भाग में जाने से पहले, आइए .NET के लिए GroupDocs.Annotation के साथ काम करने के लिए आवश्यक नेमस्पेस को आयात करें:
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
## चरण 1: आउटपुट पथ परिभाषित करें
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
यहां, हम आउटपुट पथ को परिभाषित करते हैं जहां एनोटेट दस्तावेज़ सहेजा जाएगा।
## चरण 2: एनोटेटर आरंभ करें
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां रखा जाएगा
}
```
संसाधनों का उचित निपटान सुनिश्चित करने के लिए हम उपयोग ब्लॉक के भीतर इनपुट दस्तावेज़ ("input.pdf") निर्दिष्ट करके एनोटेटर ऑब्जेक्ट को आरंभीकृत करते हैं।
## चरण 3: प्रतिस्थापन एनोटेशन बनाएँ
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
यहां, हम विभिन्न गुणों जैसे निर्माण तिथि, फ़ॉन्ट रंग, संदेश, अपारदर्शिता, पृष्ठ संख्या, पृष्ठभूमि रंग, बिंदु (निर्देशांक), उत्तर (टिप्पणियाँ), और प्रतिस्थापित करने के लिए पाठ के साथ एक ReplacementAnnotation ऑब्जेक्ट बनाते हैं।
## चरण 4: एनोटेशन जोड़ें
```csharp
annotator.Add(replacement);
```
हम बनाए गए प्रतिस्थापन एनोटेशन को एनोटेटर में जोड़ते हैं।
## चरण 5: दस्तावेज़ सहेजें
```csharp
annotator.Save(outputPath);
```
अंत में, हम एनोटेट दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजते हैं।
## चरण 6: सफलता संदेश प्रदर्शित करें
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
एक सफलता संदेश प्रदर्शित होता है जो यह दर्शाता है कि दस्तावेज़ सफलतापूर्वक सहेजा गया है।

## निष्कर्ष
इस ट्यूटोरियल में, हमने GroupDocs.Annotation for .NET का उपयोग करके दस्तावेज़ों में टेक्स्ट प्रतिस्थापन एनोटेशन जोड़ने की प्रक्रिया को कवर किया है। चरण-दर-चरण मार्गदर्शिका का पालन करके और पूर्वापेक्षाओं को समझकर, आप आसानी से इस कार्यक्षमता को अपने .NET अनुप्रयोगों में एकीकृत कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं .NET के लिए GroupDocs.Annotation का उपयोग करके विभिन्न प्रारूपों के दस्तावेज़ों को एनोटेट कर सकता हूँ?
हां, .NET के लिए GroupDocs.Annotation पीडीएफ, DOCX, पीपीटीएक्स, एक्सएलएसएक्स, और अधिक जैसे विभिन्न दस्तावेज़ प्रारूपों को एनोटेट करने का समर्थन करता है।
### क्या GroupDocs.Annotation for .NET डेस्कटॉप और वेब अनुप्रयोगों दोनों के लिए उपयुक्त है?
हां, .NET के लिए GroupDocs.Annotation का उपयोग डेस्कटॉप और वेब अनुप्रयोगों दोनों में किया जा सकता है, जो डेवलपर्स के लिए लचीलापन प्रदान करता है।
### क्या मैं GroupDocs.Annotation for .NET का उपयोग करके जोड़े गए एनोटेशन की उपस्थिति को अनुकूलित कर सकता हूं?
बिल्कुल, आप रंग, अपारदर्शिता, फ़ॉन्ट आदि जैसे गुणों को संशोधित करके एनोटेशन की उपस्थिति को अनुकूलित कर सकते हैं।
### क्या GroupDocs.Annotation for .NET सहयोगी एनोटेशन सुविधाओं के लिए समर्थन प्रदान करता है?
हां, GroupDocs.Annotation for .NET सहयोगी एनोटेशन के लिए सुविधाएं प्रदान करता है, जिससे कई उपयोगकर्ता एक साथ दस्तावेजों को एनोटेट कर सकते हैं।
### क्या GroupDocs.Annotation for .NET के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
हां, आप यहां से GroupDocs.Annotation for .NET का निःशुल्क परीक्षण प्राप्त कर सकते हैं। [वेबसाइट](https://releases.groupdocs.com/).