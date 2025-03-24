---
title: दस्तावेज़ में टेक्स्ट रिडक्शन एनोटेशन जोड़ें
linktitle: दस्तावेज़ में टेक्स्ट रिडक्शन एनोटेशन जोड़ें
second_title: GroupDocs.Annotation .NET API
description: जानें कि .NET के लिए GroupDocs.Annotation का उपयोग करके PDF दस्तावेज़ों में टेक्स्ट रिडक्शन एनोटेशन कैसे जोड़ें। संवेदनशील जानकारी को सहजता से सुरक्षित रखें।
weight: 23
url: /hi/net/unlocking-annotation-power/add-text-redaction-annotation/
---

# दस्तावेज़ में टेक्स्ट रिडक्शन एनोटेशन जोड़ें

## परिचय
किसी दस्तावेज़ में टेक्स्ट रिडक्शन एनोटेशन जोड़ना संवेदनशील जानकारी को सुरक्षित रूप से प्रबंधित करने में एक महत्वपूर्ण कदम हो सकता है। .NET के लिए GroupDocs.Annotation इसे निर्बाध रूप से प्राप्त करने के लिए एक मजबूत समाधान प्रदान करता है। इस ट्यूटोरियल में, हम चरण दर चरण आपके दस्तावेज़ में टेक्स्ट रिडक्शन एनोटेशन जोड़ने की प्रक्रिया में आपका मार्गदर्शन करेंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यक शर्तें हैं:
1.  .NET के लिए GroupDocs.Annotation: सुनिश्चित करें कि आपने .NET लाइब्रेरी के लिए GroupDocs.Annotation स्थापित कर लिया है। आप इसे यहां से डाउनलोड कर सकते हैं[वेबसाइट](https://releases.groupdocs.com/annotation/net/).
2. विकास परिवेश: विज़ुअल स्टूडियो जैसे .NET संगत IDE के साथ एक विकास परिवेश स्थापित करें।

## नामस्थान आयात करना
सबसे पहले, आइए अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## चरण 1: आउटपुट पथ को परिभाषित करें
उस आउटपुट पथ को परिभाषित करें जहां आप एनोटेटेड दस्तावेज़ को सहेजना चाहते हैं। सुनिश्चित करें कि यह सुलभ और लिखने योग्य है।
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एनोटेटर प्रारंभ करें
 इनपुट दस्तावेज़ पथ के साथ एनोटेटर को प्रारंभ करें। प्रतिस्थापित करें`"input.pdf"` आपके दस्तावेज़ के पथ के साथ।
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां जाएगा
}
```
## चरण 3: टेक्स्ट रिडक्शन एनोटेशन बनाएं
 एक बनाने के`TextRedactionAnnotation`आवश्यक गुणों वाली वस्तु जैसे`PageNumber`, `FontColor` , और`Points`. एनोटेशन को अपनी आवश्यकताओं के अनुसार अनुकूलित करें।
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## चरण 4: एनोटेशन जोड़ें और सहेजें
एनोटेटर का उपयोग करके दस्तावेज़ में बनाए गए एनोटेशन को जोड़ें और एनोटेटेड दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें।
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## चरण 5: आउटपुट जांचें
अंत में, पुष्टि करें कि दस्तावेज़ निर्दिष्ट आउटपुट पथ पर सफलतापूर्वक सहेजा गया है।
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Annotation का उपयोग करके किसी दस्तावेज़ में टेक्स्ट रिडक्शन एनोटेशन जोड़ने की प्रक्रिया को देखा है। इन चरणों के साथ, अब आप अपने दस्तावेज़ों में संवेदनशील जानकारी को सुरक्षित रूप से प्रबंधित कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं टेक्स्ट रिडक्शन एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुरूप विभिन्न गुणों जैसे फ़ॉन्ट रंग, भरण रंग और अस्पष्टता को अनुकूलित कर सकते हैं।
### क्या खरीदने से पहले कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप नि:शुल्क परीक्षण संस्करण तक पहुंच सकते हैं[वेबसाइट](https://releases.groupdocs.com/).
### यदि मुझे कोई समस्या आती है तो मुझे सहायता कैसे मिल सकती है?
 आप GroupDocs.Annotation समुदाय मंच से समर्थन प्राप्त कर सकते हैं[यहाँ](https://forum.groupdocs.com/c/annotation/10).
### क्या मुझे परीक्षण उद्देश्यों के लिए अस्थायी लाइसेंस की आवश्यकता है?
 हां, आप यहां से अस्थायी लाइसेंस प्राप्त कर सकते हैं[खरीद पृष्ठ](https://purchase.groupdocs.com/temporary-license/)परीक्षण के लिए।
### क्या मैं एक ही दस्तावेज़ में एकाधिक एनोटेशन जोड़ सकता हूँ?
बिल्कुल, GroupDocs.Annotation आपको एक ही दस्तावेज़ में विभिन्न प्रकार के एनोटेशन और कई उदाहरण जोड़ने की अनुमति देता है।