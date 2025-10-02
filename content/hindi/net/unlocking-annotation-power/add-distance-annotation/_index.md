---
"description": ".NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ों में दूरी एनोटेशन जोड़ने का तरीका जानें। सहयोग और संचार को सहजता से बढ़ाएँ।"
"linktitle": "दस्तावेज़ में दूरी एनोटेशन जोड़ें"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "दस्तावेज़ में दूरी एनोटेशन जोड़ें"
"url": "/hi/net/unlocking-annotation-power/add-distance-annotation/"
type: docs
"weight": 12
---

# दस्तावेज़ में दूरी एनोटेशन जोड़ें

## परिचय
इस ट्यूटोरियल में, आप सीखेंगे कि GroupDocs.Annotation for .NET का उपयोग करके दस्तावेज़ में दूरी एनोटेशन कैसे जोड़ें। कार्य पूरा करने के लिए इन चरणों का पालन करें:
## आवश्यक शर्तें

आगे बढ़ने से पहले सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:

- .NET लाइब्रेरी के लिए GroupDocs.Annotation: .NET लाइब्रेरी के लिए GroupDocs.Annotation को डाउनलोड और इंस्टॉल करें [इस लिंक](https://releases.groupdocs.com/annotation/net/).
- एनोटेट करने के लिए दस्तावेज़: वह दस्तावेज़ (जैसे, पीडीएफ) तैयार करें जिसमें आप दूरी एनोटेशन जोड़ना चाहते हैं।
- विकास परिवेश: विजुअल स्टूडियो या अपनी पसंद के किसी अन्य IDE के साथ अपना विकास परिवेश सेट करें।

## नामस्थान आयात करें

शुरू करने से पहले, अपने कोड में ज़रूरी नेमस्पेस शामिल करना सुनिश्चित करें। ये नेमस्पेस ज़रूरी क्लास और मेथड तक पहुँचने के लिए ज़रूरी हैं।

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## चरण 1: एनोटेटर आरंभ करें

आरंभ करने से शुरू करें `Annotator` उस दस्तावेज़ का पथ वाला ऑब्जेक्ट चुनें जिसे आप एनोटेट करना चाहते हैं.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां जाएगा
}
```

## चरण 2: दूरी एनोटेशन बनाएँ

अब, एक बनाएं `DistanceAnnotation` ऑब्जेक्ट और इसके गुणों जैसे बॉक्स आयाम, संदेश, अपारदर्शिता, पेन रंग, आदि को कॉन्फ़िगर करें।

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

## चरण 3: एनोटेशन जोड़ें

निर्मित दूरी एनोटेशन को दस्तावेज़ में जोड़ें `Add` एनोटेटर ऑब्जेक्ट की विधि.

```csharp
annotator.Add(distance);
```

## चरण 4: दस्तावेज़ सहेजें

एनोटेट किए गए दस्तावेज़ को अपने सिस्टम पर इच्छित स्थान पर सहेजें।

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## चरण 5: पुष्टि प्रदर्शित करें

अंत में, एनोटेट दस्तावेज़ के सफलतापूर्वक सहेजे जाने की पुष्टि करने वाला संदेश प्रदर्शित करें।

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष

GroupDocs.Annotation for .NET का उपयोग करके दस्तावेज़ों में दूरी एनोटेशन जोड़ना एक सरल प्रक्रिया है। इस ट्यूटोरियल में बताए गए चरणों का पालन करके, आप अपने दस्तावेज़ों को मूल्यवान एनोटेशन के साथ बेहतर बना सकते हैं, जिससे बेहतर सहयोग और संचार की सुविधा मिलती है।

## अक्सर पूछे जाने वाले प्रश्न

### प्रश्न: क्या मैं दूरी एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?

उत्तर: हां, आप अपनी आवश्यकताओं के अनुरूप रंग, अस्पष्टता, रेखा शैली आदि जैसे विभिन्न गुणों को अनुकूलित कर सकते हैं।

### प्रश्न: क्या GroupDocs.Annotation विभिन्न प्रकार के दस्तावेज़ों पर एनोटेशन का समर्थन करता है?

उत्तर: हां, GroupDocs.Annotation पीडीएफ, वर्ड, एक्सेल, पावरपॉइंट और अधिक सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला पर एनोटेशन का समर्थन करता है।

### प्रश्न: क्या GroupDocs.Annotation के लिए कोई निःशुल्क परीक्षण उपलब्ध है?

A: हां, आप GroupDocs.Annotation के निःशुल्क परीक्षण का उपयोग कर सकते हैं [इस लिंक](https://releases.groupdocs.com/).

### प्रश्न: मैं GroupDocs.Annotation for .NET के लिए दस्तावेज़ कहां पा सकता हूं?

उत्तर: आप उपलब्ध विस्तृत दस्तावेज़ देख सकते हैं [यहाँ](https://tutorials.groupdocs.com/annotation/net/).

### प्रश्न: मैं GroupDocs.Annotation के संबंध में समर्थन या सहायता कैसे प्राप्त कर सकता हूं?

उत्तर: आप GroupDocs.Annotation समुदाय फोरम से समर्थन और सहायता प्राप्त कर सकते हैं [यहाँ](https://forum.groupdocs.com/c/annotation/10).