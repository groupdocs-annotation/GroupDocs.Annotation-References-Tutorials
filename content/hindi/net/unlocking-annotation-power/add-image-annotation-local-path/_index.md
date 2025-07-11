---
"description": ".NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ों में छवि एनोटेशन जोड़ना सीखें। दस्तावेज़ प्रसंस्करण क्षमताओं को आसानी से बढ़ाएँ।"
"linktitle": "दस्तावेज़ में छवि एनोटेशन जोड़ें (स्थानीय पथ)"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "दस्तावेज़ में छवि एनोटेशन जोड़ें (स्थानीय पथ)"
"url": "/hi/net/unlocking-annotation-power/add-image-annotation-local-path/"
"weight": 14
---

# दस्तावेज़ में छवि एनोटेशन जोड़ें (स्थानीय पथ)

## परिचय
GroupDocs.Annotation for .NET एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को प्रोग्रामेटिक रूप से दस्तावेज़ों में विभिन्न प्रकार के एनोटेशन जोड़ने की अनुमति देती है। इस ट्यूटोरियल में, हम सीखेंगे कि स्थानीय पथ का उपयोग करके दस्तावेज़ में छवि एनोटेशन कैसे जोड़ें।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
1. C# प्रोग्रामिंग भाषा का बुनियादी ज्ञान।
2. आपके सिस्टम पर Visual Studio स्थापित है.
3. GroupDocs.Annotation .NET पुस्तकालय स्थापित या अपनी परियोजना में tutorialsd के लिए।
4. एक इनपुट दस्तावेज़ (जैसे, पीडीएफ) और एनोटेशन के लिए एक छवि फ़ाइल।
## नामस्थान आयात करें
सबसे पहले, आपको अपनी C# फ़ाइल में आवश्यक नामस्थान आयात करने होंगे। ये नामस्थान GroupDocs.Annotation के साथ काम करने के लिए आवश्यक कक्षाओं और विधियों तक पहुँच प्रदान करते हैं।
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## चरण 1: आउटपुट पथ परिभाषित करें
आउटपुट पथ को परिभाषित करें जहां एनोटेट दस्तावेज़ सहेजा जाएगा।
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एनोटेटर आरंभ करें
इनपुट दस्तावेज़ का पथ प्रदान करके एनोटेटर को आरंभ करें।
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां दिया गया है
}
```
## चरण 3: छवि एनोटेशन बनाएँ
इसका एक उदाहरण बनाएं `ImageAnnotation` क्लास चुनें और उसकी स्थिति, अपारदर्शिता, पृष्ठ संख्या और छवि पथ जैसे गुण निर्दिष्ट करें।
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## चरण 4: एनोटेशन जोड़ें
दस्तावेज़ में निर्मित छवि एनोटेशन को जोड़ने के लिए निम्न का उपयोग करें: `Add` व्याख्याकार की विधि.
```csharp
annotator.Add(image);
```
## चरण 5: दस्तावेज़ सहेजें
एनोटेट किए गए दस्तावेज़ को आउटपुट पथ पर सहेजें.
```csharp
annotator.Save(outputPath);
```
## चरण 6: आउटपुट पथ प्रदर्शित करें
दस्तावेज़ के सफलतापूर्वक सहेजे जाने और आउटपुट फ़ाइल के स्थान को इंगित करने वाला संदेश प्रदर्शित करें।
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा है कि GroupDocs.Annotation for .NET का उपयोग करके दस्तावेज़ में छवि एनोटेशन कैसे जोड़ें। इन सरल चरणों का पालन करके, आप शक्तिशाली एनोटेशन सुविधाओं के साथ अपने दस्तावेज़ प्रसंस्करण क्षमताओं को बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं पीडीएफ के अलावा अन्य दस्तावेजों पर भी टिप्पणी कर सकता हूं?
हां, GroupDocs.Annotation वर्ड, एक्सेल, पावरपॉइंट और अन्य सहित विभिन्न दस्तावेज़ प्रारूपों का समर्थन करता है।
### क्या GroupDocs.Annotation .NET कोर के साथ संगत है?
हां, GroupDocs.Annotation .NET फ्रेमवर्क और .NET कोर दोनों के साथ संगत है।
### क्या मैं एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
बिल्कुल, आप अपनी आवश्यकताओं के अनुसार एनोटेशन के स्वरूप, आकार, रंग और अन्य गुणों को अनुकूलित कर सकते हैं।
### क्या GroupDocs.Annotation सहयोगात्मक एनोटेशन के लिए समर्थन प्रदान करता है?
हां, GroupDocs.Annotation सहयोगात्मक एनोटेशन सुविधाएं प्रदान करता है जो कई उपयोगकर्ताओं को एक साथ दस्तावेज़ों को एनोटेट करने में सक्षम बनाता है।
### मुझे अतिरिक्त सहायता या समर्थन कहां मिल सकता है?
आप समुदाय से सहायता और समर्थन के लिए GroupDocs.Annotation फ़ोरम पर जा सकते हैं।