---
"description": ".NET के लिए Groupdocs.Annotation का उपयोग करके PDF दस्तावेज़ों को आसानी से घुमाना सीखें। दस्तावेज़ प्रबंधन दक्षता में सुधार करें।"
"linktitle": "पीडीएफ दस्तावेज़ों को घुमाना"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "पीडीएफ दस्तावेज़ों को घुमाना"
"url": "/hi/net/advanced-usage/rotating-pdf-documents/"
"weight": 22
---

# पीडीएफ दस्तावेज़ों को घुमाना

## परिचय
पीडीएफ दस्तावेजों को घुमाना एक महत्वपूर्ण कार्य हो सकता है जब उन फ़ाइलों से निपटना हो जिन्हें अलग तरीके से देखा या संसाधित किया जाना चाहिए। इस ट्यूटोरियल में, हम .NET के लिए Groupdocs.Annotation का उपयोग करके चरण दर चरण पीडीएफ दस्तावेजों को घुमाने का तरीका जानेंगे।
## आवश्यक शर्तें
ट्यूटोरियल में शामिल होने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
1. Groupdocs.Annotation for .NET लाइब्रेरी: सुनिश्चित करें कि आपने Groupdocs.Annotation for .NET लाइब्रेरी डाउनलोड और इंस्टॉल कर ली है। आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.groupdocs.com/annotation/net/).
2. C# प्रोग्रामिंग का बुनियादी ज्ञान: यह ट्यूटोरियल मानता है कि आपको C# प्रोग्रामिंग भाषा और .NET लाइब्रेरीज़ के साथ काम करने की बुनियादी समझ है।

## नामस्थान आयात करें
सबसे पहले, आपको Groupdocs.Annotation लाइब्रेरी द्वारा प्रदान की गई कार्यक्षमता तक पहुंचने के लिए अपने C# प्रोजेक्ट में आवश्यक नेमस्पेस को आयात करना होगा।
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## चरण 1: पीडीएफ दस्तावेज़ लोड करें
उस पीडीएफ दस्तावेज़ को लोड करके शुरू करें जिसे आप घुमाना चाहते हैं `Annotator` कक्षा।
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## चरण 2: रोटेशन और प्रक्रिया पृष्ठ सेट करें
रोटेशन एंगल और वे पेज निर्दिष्ट करें जिन्हें आप घुमाना चाहते हैं। इस उदाहरण में, हम पहले पेज को 90 डिग्री दक्षिणावर्त घुमाएँगे।
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## चरण 3: घुमाए गए दस्तावेज़ को सहेजें
निर्दिष्ट परिवर्तनों के साथ घुमाए गए PDF दस्तावेज़ को सहेजें।
```csharp
annotator.Save("result.pdf");
```
## चरण 4: पुष्टि प्रदर्शित करें
उपयोगकर्ता को सूचित करें कि दस्तावेज़ सफलतापूर्वक घुमाया गया है।
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## निष्कर्ष
पीडीएफ दस्तावेजों को घुमाना एक बुनियादी काम है, और .NET के लिए Groupdocs.Annotation के साथ, यह सरल और कुशल हो जाता है। इस ट्यूटोरियल में बताए गए चरणों का पालन करके, आप आसानी से अपनी आवश्यकताओं के अनुसार पीडीएफ फाइलों को घुमा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं .NET के लिए Groupdocs.Annotation का उपयोग करके PDF दस्तावेज़ में एकाधिक पृष्ठों को घुमा सकता हूँ?
हां, आप सेटिंग समायोजित करके एकाधिक पृष्ठों को घुमाने के लिए निर्दिष्ट कर सकते हैं। `ProcessPages` संपत्ति तदनुसार.
### क्या Groupdocs.Annotation for .NET .NET फ्रेमवर्क के सभी संस्करणों के साथ संगत है?
.NET के लिए Groupdocs.Annotation .NET फ्रेमवर्क संस्करणों की एक विस्तृत श्रृंखला का समर्थन करता है, जो अधिकांश विकास वातावरणों के लिए अनुकूलता सुनिश्चित करता है।
### क्या Groupdocs.Annotation for .NET पीडीएफ दस्तावेजों को अलग-अलग दिशाओं में घुमाने के लिए विकल्प प्रदान करता है?
हां, आप अपनी आवश्यकताओं के आधार पर पीडीएफ दस्तावेजों को दक्षिणावर्त, वामावर्त या कस्टम कोणों पर घुमा सकते हैं।
### क्या मैं अपने मौजूदा दस्तावेज़ प्रबंधन सिस्टम में Groupdocs.Annotation for .NET को एकीकृत कर सकता हूँ?
बिल्कुल, Groupdocs.Annotation for .NET सहज एकीकरण विकल्प प्रदान करता है, जिससे आप दस्तावेज़ प्रबंधन क्षमताओं को आसानी से बढ़ा सकते हैं।
### क्या Groupdocs.Annotation for .NET के लिए कोई परीक्षण संस्करण उपलब्ध है?
हां, आप यहां से निःशुल्क परीक्षण संस्करण प्राप्त कर सकते हैं [यहाँ](https://releases.groupdocs.com/).