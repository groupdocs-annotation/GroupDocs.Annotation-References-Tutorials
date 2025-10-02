---
"description": "कुशल दस्तावेज़ प्रबंधन और सहयोग के लिए GroupDocs.Annotation का उपयोग करके .NET में टेक्स्ट पर छवि एनोटेशन जोड़ना सीखें।"
"linktitle": "टेक्स्ट पर छवि एनोटेशन डालें"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "टेक्स्ट पर छवि एनोटेशन डालें"
"url": "/hi/net/advanced-usage/put-image-annotation-over-text/"
type: docs
"weight": 21
---

# टेक्स्ट पर छवि एनोटेशन डालें

## परिचय
.NET विकास की दुनिया में, GroupDocs.Annotation दस्तावेज़ों में एनोटेशन जोड़ने, सहयोग और दस्तावेज़ प्रबंधन को और अधिक कुशल बनाने के लिए एक शक्तिशाली समाधान प्रदान करता है। एक सामान्य आवश्यकता पाठ पर छवि एनोटेशन डालना है, जिसे GroupDocs.Annotation for .NET का उपयोग करके सहजता से पूरा किया जा सकता है।
## आवश्यक शर्तें
GroupDocs.Annotation for .NET का उपयोग करके पाठ पर छवि एनोटेशन डालने की प्रक्रिया में आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1. .NET लाइब्रेरी के लिए GroupDocs.Annotation: लाइब्रेरी को डाउनलोड करें और इंस्टॉल करें [यहाँ](https://releases.groupdocs.com/annotation/net/).
2. विकास परिवेश: उपयुक्त विकास परिवेश स्थापित करें, जैसे कि Visual Studio या कोई अन्य .NET IDE.
3. दस्तावेज़ और छवि फ़ाइलें: दस्तावेज़ फ़ाइल (PDF, DOCX, आदि) और छवि फ़ाइल तैयार करें जिसे आप एनोटेशन के लिए उपयोग करना चाहते हैं।
4. C# की बुनियादी समझ: इस ट्यूटोरियल में दिए गए कोड स्निपेट को लागू करने के लिए C# प्रोग्रामिंग भाषा से परिचित होना आवश्यक है।

## नामस्थान आयात करें
एनोटेशन प्रक्रिया के साथ आगे बढ़ने से पहले, सुनिश्चित करें कि आपने अपने C# प्रोजेक्ट में आवश्यक नेमस्पेस आयात कर लिए हैं:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## चरण 1: आउटपुट पथ परिभाषित करें
सबसे पहले, आउटपुट पथ को परिभाषित करें जहां एनोटेट दस्तावेज़ सहेजा जाएगा:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## चरण 2: एनोटेटर आरंभ करें
आरंभ करें `Annotator` इनपुट दस्तावेज़ पथ प्रदान करके ऑब्जेक्ट:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां जाएगा
}
```
## चरण 3: छवि एनोटेशन बनाएँ
एक बनाएं `ImageAnnotation` बॉक्स आयाम, अपारदर्शिता, पृष्ठ संख्या, छवि पथ और z-इंडेक्स जैसे वांछित गुणों वाला ऑब्जेक्ट:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## चरण 4: एनोटेशन जोड़ें
दस्तावेज़ में छवि एनोटेशन जोड़ें `Add` की विधि `Annotator` वस्तु:
```csharp
annotator.Add(image);
```
## चरण 5: एनोटेट दस्तावेज़ सहेजें
एनोटेट किए गए दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें:
```csharp
annotator.Save(outputPath);
```
## चरण 6: सफलता संदेश प्रदर्शित करें
एनोटेट किए गए दस्तावेज़ के पथ के साथ एक सफलता संदेश प्रदर्शित करें:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष
निष्कर्ष में, GroupDocs.Annotation का उपयोग करके .NET अनुप्रयोगों में टेक्स्ट पर छवि एनोटेशन जोड़ना एक सीधी प्रक्रिया है। इस ट्यूटोरियल में दिए गए चरण-दर-चरण गाइड का पालन करके, आप कुशलतापूर्वक दस्तावेज़ों को एनोटेट कर सकते हैं और अपने .NET प्रोजेक्ट में सहयोग और दस्तावेज़ प्रबंधन क्षमताओं को बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं पीडीएफ के अलावा अन्य दस्तावेजों पर भी टिप्पणी कर सकता हूं?
हां, GroupDocs.Annotation विभिन्न दस्तावेज़ स्वरूपों जैसे DOCX, XLSX, PPTX, और अधिक का समर्थन करता है।
### क्या GroupDocs.Annotation के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
हां, आप यहां से निःशुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं [यहाँ](https://releases.groupdocs.com/).
### मैं GroupDocs.Annotation के लिए समर्थन कैसे प्राप्त कर सकता हूं?
आप GroupDocs.Annotation समुदाय फ़ोरम से सहायता प्राप्त कर सकते हैं [यहाँ](https://forum.groupdocs.com/c/annotation/10).
### क्या मुझे परीक्षण प्रयोजनों के लिए अस्थायी लाइसेंस की आवश्यकता है?
हां, आप यहां से अस्थायी लाइसेंस प्राप्त कर सकते हैं [यहाँ](https://purchase.groupdocs.com/temporary-license/) परीक्षण प्रयोजनों के लिए.
### क्या मैं एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
हां, GroupDocs.Annotation एनोटेशन की उपस्थिति जैसे रंग, अस्पष्टता, फ़ॉन्ट आकार आदि को अनुकूलित करने के लिए विभिन्न विकल्प प्रदान करता है।