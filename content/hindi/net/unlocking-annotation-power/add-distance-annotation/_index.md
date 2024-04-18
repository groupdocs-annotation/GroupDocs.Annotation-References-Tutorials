---
title: दस्तावेज़ में दूरी एनोटेशन जोड़ें
linktitle: दस्तावेज़ में दूरी एनोटेशन जोड़ें
second_title: GroupDocs.Annotation .NET API
description: .NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ों में दूरी एनोटेशन जोड़ने का तरीका जानें। सहजता से सहयोग और संचार बढ़ाएँ।
type: docs
weight: 12
url: /hi/net/unlocking-annotation-power/add-distance-annotation/
---
## परिचय
इस ट्यूटोरियल में, आप सीखेंगे कि .NET के लिए GroupDocs.Annotation का उपयोग करके किसी दस्तावेज़ में दूरी एनोटेशन कैसे जोड़ा जाए। कार्य पूरा करने के लिए इन चरणों का पालन करें:
## आवश्यक शर्तें

सुनिश्चित करें कि आगे बढ़ने से पहले आपके पास निम्नलिखित शर्तें हों:

-  .NET लाइब्रेरी के लिए GroupDocs.Annotation: .NET लाइब्रेरी के लिए GroupDocs.Annotation को यहां से डाउनलोड और इंस्टॉल करें।[इस लिंक](https://releases.groupdocs.com/annotation/net/).
- एनोटेट करने के लिए दस्तावेज़: वह दस्तावेज़ तैयार करें (उदाहरण के लिए, पीडीएफ) जिसमें आप दूरी एनोटेशन जोड़ना चाहते हैं।
- विकास वातावरण: विजुअल स्टूडियो या अपनी पसंद के किसी अन्य आईडीई के साथ अपना विकास वातावरण स्थापित करें।

## नामस्थान आयात करें

शुरू करने से पहले, अपने कोड में आवश्यक नामस्थान शामिल करना सुनिश्चित करें। ये नामस्थान आवश्यक कक्षाओं और विधियों तक पहुँचने के लिए आवश्यक हैं।

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## चरण 1: एनोटेटर प्रारंभ करें

 को इनिशियलाइज़ करके प्रारंभ करें`Annotator` जिस दस्तावेज़ को आप एनोटेट करना चाहते हैं उसके पथ के साथ ऑब्जेक्ट करें।

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां जाएगा
}
```

## चरण 2: दूरी एनोटेशन बनाएं

 अब, एक बनाएं`DistanceAnnotation` ऑब्जेक्ट बनाएं और उसके गुणों जैसे बॉक्स आयाम, संदेश, अपारदर्शिता, पेन रंग आदि को कॉन्फ़िगर करें।

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

 का उपयोग करके दस्तावेज़ में बनाई गई दूरी एनोटेशन जोड़ें`Add` एनोटेटर ऑब्जेक्ट की विधि।

```csharp
annotator.Add(distance);
```

## चरण 4: दस्तावेज़ सहेजें

एनोटेटेड दस्तावेज़ को अपने सिस्टम पर वांछित स्थान पर सहेजें।

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## चरण 5: पुष्टिकरण प्रदर्शित करें

अंत में, एनोटेटेड दस्तावेज़ की सफल बचत की पुष्टि करने वाला एक संदेश प्रदर्शित करें।

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष

.NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ों में दूरी एनोटेशन जोड़ना एक सीधी प्रक्रिया है। इस ट्यूटोरियल में उल्लिखित चरणों का पालन करके, आप अपने दस्तावेज़ों को मूल्यवान टिप्पणियों के साथ बेहतर सहयोग और संचार की सुविधा प्रदान कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### प्रश्न: क्या मैं दूरी एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?

उत्तर: हां, आप अपनी आवश्यकताओं के अनुरूप विभिन्न गुणों जैसे रंग, अस्पष्टता, रेखा शैली आदि को अनुकूलित कर सकते हैं।

### प्रश्न: क्या GroupDocs.Annotation विभिन्न प्रकार के दस्तावेज़ों पर एनोटेशन का समर्थन करता है?

उ: हां, GroupDocs.Annotation पीडीएफ, वर्ड, एक्सेल, पॉवरपॉइंट और अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला पर एनोटेशन का समर्थन करता है।

### प्रश्न: क्या GroupDocs.Annotation के लिए कोई निःशुल्क परीक्षण उपलब्ध है?

 उ: हां, आप GroupDocs.Annotation के निःशुल्क परीक्षण तक पहुंच सकते हैं[इस लिंक](https://releases.groupdocs.com/).

### प्रश्न: मुझे .NET के लिए GroupDocs.Annotation के लिए दस्तावेज़ कहां मिल सकते हैं?

 उ: आप उपलब्ध विस्तृत दस्तावेज़ का संदर्भ ले सकते हैं[यहाँ](https://reference.groupdocs.com/annotation/net/).

### प्रश्न: मैं GroupDocs.Annotation से समर्थन या सहायता कैसे प्राप्त कर सकता हूं?

 उ: आप GroupDocs.Annotation समुदाय मंच से समर्थन और सहायता प्राप्त कर सकते हैं[यहाँ](https://forum.groupdocs.com/c/annotation/10).