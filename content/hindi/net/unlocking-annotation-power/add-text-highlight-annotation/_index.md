---
"description": "GroupDocs.Annotation for .NET का उपयोग करके दस्तावेज़ों में टेक्स्ट हाइलाइट एनोटेशन जोड़ने का तरीका जानें। इस व्यापक के साथ सहयोग और उत्पादकता बढ़ाएँ।"
"linktitle": "दस्तावेज़ में टेक्स्ट हाइलाइट एनोटेशन जोड़ें"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "दस्तावेज़ में टेक्स्ट हाइलाइट एनोटेशन जोड़ें"
"url": "/hi/net/unlocking-annotation-power/add-text-highlight-annotation/"
type: docs
"weight": 22
---

# दस्तावेज़ में टेक्स्ट हाइलाइट एनोटेशन जोड़ें

## परिचय
दस्तावेज़ प्रबंधन और सहयोग के क्षेत्र में, GroupDocs.Annotation for .NET एक मज़बूत समाधान के रूप में उभरता है, जो डेवलपर्स को उनके अनुप्रयोगों में टेक्स्ट हाइलाइट एनोटेशन को सहजता से एकीकृत करने में सक्षम बनाता है। यह ट्यूटोरियल GroupDocs.Annotation for .NET का उपयोग करके दस्तावेज़ों में टेक्स्ट हाइलाइट एनोटेशन जोड़ने के लिए एक व्यापक मार्गदर्शिका के रूप में कार्य करता है। चरण-दर-चरण निर्देशों और विस्तृत स्पष्टीकरणों के माध्यम से, आप इस शक्तिशाली लाइब्रेरी की क्षमताओं का दोहन करने में दक्षता प्राप्त करेंगे।
## आवश्यक शर्तें
टेक्स्ट हाइलाइट एनोटेशन के कार्यान्वयन में आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:
1. पर्यावरण सेटअप: .NET विकास के लिए उपयुक्त विकास पर्यावरण कॉन्फ़िगर करें।
2. .NET के लिए GroupDocs.Annotation की स्थापना: दिए गए से .NET के लिए GroupDocs.Annotation डाउनलोड करें और इंस्टॉल करें [लिंक को डाउनलोड करें](https://releases.groupdocs.com/annotation/net/).
3. C# से परिचित होना: C# प्रोग्रामिंग भाषा की बुनियादी समझ।
4. एनोटेट करने के लिए दस्तावेज़: एक दस्तावेज़ (जैसे, पीडीएफ) तैयार करें जिस पर आप एनोटेट करना चाहते हैं।

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
#अब, आइए टेक्स्ट हाइलाइट एनोटेशन जोड़ने की प्रक्रिया को कई चरणों में विभाजित करें:
## चरण 1: आउटपुट पथ परिभाषित करें
आउटपुट पथ निर्दिष्ट करें जहां एनोटेट दस्तावेज़ सहेजा जाएगा:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एनोटेटर आरंभ करें
इसका एक उदाहरण बनाएं `Annotator` क्लास, दस्तावेज़ फ़ाइल नाम को पैरामीटर के रूप में पास करना:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## चरण 3: हाइलाइट एनोटेशन बनाएँ
एक उदाहरण बनाना `HighlightAnnotation` ऑब्जेक्ट और उसके गुणों को कॉन्फ़िगर करें:
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
बनाए गए हाइलाइट एनोटेशन को दस्तावेज़ में जोड़ें:
```csharp
annotator.Add(highlight);
```
## चरण 5: एनोटेट दस्तावेज़ सहेजें
एनोटेट किए गए दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें:
```csharp
annotator.Save(outputPath);
```

## निष्कर्ष
निष्कर्ष में, .NET के लिए GroupDocs.Annotation दस्तावेज़ों में टेक्स्ट हाइलाइट एनोटेशन को शामिल करने के लिए एक सुव्यवस्थित दृष्टिकोण प्रदान करता है। इस ट्यूटोरियल में बताए गए चरणों का पालन करके, डेवलपर्स अपने अनुप्रयोगों के भीतर दस्तावेज़ सहयोग और उत्पादकता को सहजता से बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Annotation for .NET सभी दस्तावेज़ प्रारूपों के साथ संगत है?
.NET के लिए GroupDocs.Annotation पीडीएफ, वर्ड, एक्सेल और अधिक सहित विभिन्न दस्तावेज़ स्वरूपों का समर्थन करता है। पूरी सूची के लिए दस्तावेज़ देखें।
### क्या एनोटेशन को विशिष्ट आवश्यकताओं के अनुसार अनुकूलित किया जा सकता है?
हां, डेवलपर्स के पास एनोटेशन के गुणों और स्वरूप पर पूर्ण नियंत्रण होता है, जिससे विविध आवश्यकताओं को पूरा करने के लिए अनुकूलन की सुविधा मिलती है।
### क्या GroupDocs.Annotation for .NET के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
हां, आप प्रदान किए गए नि:शुल्क परीक्षण का उपयोग करके .NET के लिए GroupDocs.Annotation की सुविधाओं का पता लगा सकते हैं [जोड़ना](https://releases.groupdocs.com/).
### मैं GroupDocs.Annotation for .NET से संबंधित किसी भी समस्या या प्रश्न के लिए समर्थन कैसे प्राप्त कर सकता हूं?
समर्थन और सहायता के लिए, आप GroupDocs.Annotation फ़ोरम पर जा सकते हैं [यहाँ](https://forum.groupdocs.com/c/annotation/10).
### GroupDocs.Annotation for .NET के लिए कौन से लाइसेंसिंग विकल्प उपलब्ध हैं?
.NET के लिए GroupDocs.Annotation विभिन्न लाइसेंसिंग विकल्प प्रदान करता है, जिसमें परीक्षण उद्देश्यों के लिए अस्थायी लाइसेंस और उत्पादन वातावरण के लिए वाणिज्यिक लाइसेंस शामिल हैं। खरीद पृष्ठ पर जाएँ [यहाँ](https://purchase.groupdocs.com/buy) अधिक जानकारी के लिए.