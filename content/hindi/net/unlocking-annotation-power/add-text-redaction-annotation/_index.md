---
"description": ".NET के लिए GroupDocs.Annotation का उपयोग करके PDF दस्तावेज़ों में टेक्स्ट रिडक्शन एनोटेशन जोड़ना सीखें। संवेदनशील जानकारी को सहजता से सुरक्षित रखें।"
"linktitle": "दस्तावेज़ में टेक्स्ट रिडक्शन एनोटेशन जोड़ें"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "दस्तावेज़ में टेक्स्ट रिडक्शन एनोटेशन जोड़ें"
"url": "/hi/net/unlocking-annotation-power/add-text-redaction-annotation/"
"weight": 23
---

# दस्तावेज़ में टेक्स्ट रिडक्शन एनोटेशन जोड़ें

## परिचय
किसी दस्तावेज़ में टेक्स्ट रिडक्शन एनोटेशन जोड़ना संवेदनशील जानकारी को सुरक्षित रूप से प्रबंधित करने में एक महत्वपूर्ण कदम हो सकता है। GroupDocs.Annotation for .NET इसे सहजता से प्राप्त करने के लिए एक मजबूत समाधान प्रदान करता है। इस ट्यूटोरियल में, हम आपको अपने दस्तावेज़ में टेक्स्ट रिडक्शन एनोटेशन जोड़ने की प्रक्रिया के बारे में चरण दर चरण मार्गदर्शन करेंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:
1. .NET के लिए GroupDocs.Annotation: सुनिश्चित करें कि आपने .NET लाइब्रेरी के लिए GroupDocs.Annotation स्थापित किया है। आप इसे यहाँ से डाउनलोड कर सकते हैं [वेबसाइट](https://releases.groupdocs.com/annotation/net/).
2. विकास परिवेश: Visual Studio जैसे .NET संगत IDE के साथ विकास परिवेश सेट अप करें।

## नामस्थान आयात करना
सबसे पहले, आइए अपने प्रोजेक्ट में आवश्यक नेमस्पेस आयात करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## चरण 1: आउटपुट पथ परिभाषित करें
आउटपुट पथ को परिभाषित करें जहाँ आप एनोटेट किए गए दस्तावेज़ को सहेजना चाहते हैं। सुनिश्चित करें कि यह सुलभ और लिखने योग्य है।
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एनोटेटर आरंभ करें
इनपुट दस्तावेज़ पथ के साथ एनोटेटर को आरंभ करें। `"input.pdf"` अपने दस्तावेज़ के पथ के साथ.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां जाएगा
}
```
## चरण 3: टेक्स्ट रिडक्शन एनोटेशन बनाएं
एक बनाने के `TextRedactionAnnotation` आवश्यक गुणों वाली वस्तु जैसे `PageNumber`, `FontColor`, और `Points`अपनी आवश्यकताओं के अनुसार एनोटेशन को अनुकूलित करें।
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
एनोटेटर का उपयोग करके बनाए गए एनोटेशन को दस्तावेज़ में जोड़ें और एनोटेट किए गए दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें।
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
इस ट्यूटोरियल में, हमने GroupDocs.Annotation for .NET का उपयोग करके दस्तावेज़ में टेक्स्ट रिडक्शन एनोटेशन जोड़ने की प्रक्रिया को देखा है। इन चरणों के साथ, अब आप अपने दस्तावेज़ों में संवेदनशील जानकारी को सुरक्षित रूप से प्रबंधित कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं टेक्स्ट रिडक्शन एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुरूप फ़ॉन्ट रंग, भरण रंग और अपारदर्शिता जैसे विभिन्न गुणों को अनुकूलित कर सकते हैं।
### क्या खरीदने से पहले कोई परीक्षण संस्करण उपलब्ध है?
हां, आप यहां से निःशुल्क परीक्षण संस्करण प्राप्त कर सकते हैं। [वेबसाइट](https://releases.groupdocs.com/).
### यदि मुझे कोई समस्या आती है तो मैं सहायता कैसे प्राप्त कर सकता हूँ?
आप GroupDocs.Annotation समुदाय फ़ोरम से सहायता प्राप्त कर सकते हैं [यहाँ](https://forum.groupdocs.com/c/annotation/10).
### क्या मुझे परीक्षण प्रयोजनों के लिए अस्थायी लाइसेंस की आवश्यकता है?
हां, आप अस्थायी लाइसेंस प्राप्त कर सकते हैं [खरीद पृष्ठ](https://purchase.groupdocs.com/temporary-license/) परीक्षण के लिए.
### क्या मैं एक ही दस्तावेज़ में एकाधिक एनोटेशन जोड़ सकता हूँ?
बिल्कुल, GroupDocs.Annotation आपको एक ही दस्तावेज़ में विभिन्न प्रकार के एनोटेशन और कई उदाहरण जोड़ने की अनुमति देता है।