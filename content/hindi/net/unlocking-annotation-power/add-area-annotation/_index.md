---
title: दस्तावेज़ में क्षेत्र एनोटेशन जोड़ें
linktitle: दस्तावेज़ में क्षेत्र एनोटेशन जोड़ें
second_title: GroupDocs.Annotation .NET API
description: .NET के लिए Groupdocs.Annotation के साथ अपने दस्तावेज़ सहयोग को बढ़ाएं। चरण-दर-चरण क्षेत्र एनोटेशन जोड़ने का तरीका जानें।
type: docs
weight: 10
url: /hi/net/unlocking-annotation-power/add-area-annotation/
---
## परिचय
इस ट्यूटोरियल में, हम .NET के लिए Groupdocs.Annotation का उपयोग करके दस्तावेज़ों में क्षेत्र एनोटेशन जोड़ने की प्रक्रिया में आपका मार्गदर्शन करेंगे। क्षेत्र एनोटेशन एक मूल्यवान सुविधा है जो उपयोगकर्ताओं को किसी दस्तावेज़ के विशिष्ट क्षेत्रों को उजागर करने, सामग्री को स्पष्टता और संदर्भ प्रदान करने की अनुमति देती है।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यकताएँ हैं:
1.  .NET के लिए Groupdocs.Annotation: सुनिश्चित करें कि आपके पास आवश्यक लाइब्रेरी और निर्भरताएँ स्थापित हैं। आप इन्हें यहां से डाउनलोड कर सकते हैं[वेबसाइट](https://releases.groupdocs.com/annotation/net/).
2. विकास वातावरण: .NET विकास के लिए एक उपयुक्त विकास वातावरण स्थापित करें।

## नामस्थान आयात करें
आरंभ करने के लिए, अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करें। इन नामस्थानों में एनोटेशन के साथ काम करने के लिए आवश्यक कक्षाएं और विधियां शामिल हैं।
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

## चरण 1: आउटपुट पथ आरंभ करें
आउटपुट पथ को परिभाषित करें जहां एनोटेटेड दस्तावेज़ सहेजा जाएगा।
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एनोटेटर प्रारंभ करें
 का एक उदाहरण बनाएं`Annotator` दस्तावेज़ के पथ को एक पैरामीटर के रूप में पारित करके कक्षा।
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां जाएगा
}
```
## चरण 3: क्षेत्र एनोटेशन बनाएं
क्षेत्र एनोटेशन के गुणों को परिभाषित करें, जैसे पृष्ठभूमि रंग, स्थिति, संदेश, अस्पष्टता, आदि।
```csharp
AreaAnnotation area = new AreaAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is area annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
 का उपयोग करके दस्तावेज़ में क्षेत्र एनोटेशन जोड़ें`Add` की विधि`Annotator` उदाहरण।
```csharp
annotator.Add(area);
```
## चरण 5: दस्तावेज़ सहेजें
एनोटेटेड दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें।
```csharp
annotator.Save(outputPath);
```
## चरण 6: सफलता संदेश प्रदर्शित करें
उपयोगकर्ता को सूचित करें कि दस्तावेज़ को सफलतापूर्वक एनोटेट और सहेजा गया है।
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि .NET के लिए Groupdocs.Annotation का उपयोग करके दस्तावेज़ों में क्षेत्र एनोटेशन कैसे जोड़ें। चरण-दर-चरण मार्गदर्शिका का पालन करके, आप आसानी से अपने दस्तावेज़ों को मूल्यवान टिप्पणियों के साथ बढ़ा सकते हैं, सहयोग और समझ में सुधार कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं क्षेत्र एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी प्राथमिकताओं के अनुरूप विभिन्न पहलुओं जैसे पृष्ठभूमि रंग, अस्पष्टता, कलम शैली इत्यादि को अनुकूलित कर सकते हैं।
### क्या Groupdocs.Annotation अन्य दस्तावेज़ प्रारूपों के साथ संगत है?
हाँ, Groupdocs.Annotation PDF, DOCX, PPTX और अन्य सहित विभिन्न दस्तावेज़ प्रारूपों का समर्थन करता है।
### क्या मैं एक ही दस्तावेज़ में एकाधिक एनोटेशन जोड़ सकता हूँ?
बिल्कुल, आप आवश्यकतानुसार एक ही दस्तावेज़ में विभिन्न प्रकार के कई एनोटेशन जोड़ सकते हैं।
### क्या Groupdocs.Annotation क्रॉस-प्लेटफ़ॉर्म संगतता प्रदान करता है?
हाँ, Groupdocs.Annotation .NET फ्रेमवर्क के साथ संगत है, जो इसे Windows, Linux और macOS विकास परिवेशों के लिए उपयुक्त बनाता है।
### क्या परीक्षण प्रयोजनों के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप नि:शुल्क परीक्षण संस्करण तक पहुंच सकते हैं[वेबसाइट](https://releases.groupdocs.com/).