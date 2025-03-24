---
title: दस्तावेज़ में टेक्स्ट स्क्विग्ली एनोटेशन जोड़ें
linktitle: दस्तावेज़ में टेक्स्ट स्क्विग्ली एनोटेशन जोड़ें
second_title: GroupDocs.Annotation .NET API
description: .NET के लिए Groupdocs.Annotation का उपयोग करके दस्तावेज़ों में आसानी से टेक्स्ट स्क्विग्ली एनोटेशन जोड़ने का तरीका जानें। सहयोग और दस्तावेज़ समीक्षा प्रक्रियाओं को बढ़ाएँ।
weight: 25
url: /hi/net/unlocking-annotation-power/add-text-squiggly-annotation/
---

# दस्तावेज़ में टेक्स्ट स्क्विग्ली एनोटेशन जोड़ें

## परिचय

.NET के लिए Groupdocs.Annotation एक बहुमुखी लाइब्रेरी है जो डेवलपर्स को अपने .NET अनुप्रयोगों में मजबूत एनोटेशन क्षमताओं को सहजता से एकीकृत करने में सक्षम बनाती है। चाहे आप PDF, Word दस्तावेज़, या अन्य लोकप्रिय फ़ाइल स्वरूपों के साथ काम कर रहे हों, Groupdocs.Annotation दस्तावेज़ सहयोग को एनोटेट करने और बढ़ाने के लिए एक सहज समाधान प्रदान करता है।

## आवश्यक शर्तें

ट्यूटोरियल में जाने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यक शर्तें हैं:

## नामस्थान आयात करें

.NET के लिए Groupdocs.Annotation द्वारा प्रदान की गई कार्यक्षमताओं तक पहुंचने के लिए आवश्यक नामस्थान आयात करना सुनिश्चित करें।

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

अब जब हमने आवश्यक शर्तें पूरी कर ली हैं, तो आइए टेक्स्ट स्क्विग्ली एनोटेशन को कई चरणों में जोड़ने की प्रक्रिया को तोड़ दें।

## चरण 1: आउटपुट पथ को परिभाषित करें

उस पथ को परिभाषित करें जहां एनोटेटेड दस्तावेज़ सहेजा जाएगा।

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## चरण 2: एनोटेटर प्रारंभ करें

इनपुट दस्तावेज़ पथ प्रदान करके एनोटेटर ऑब्जेक्ट को प्रारंभ करें।

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां जाता है
}
```

## चरण 3: स्क्विग्ली एनोटेशन बनाएं

एक SquigglyAnnotation ऑब्जेक्ट बनाएं और उसके गुण निर्दिष्ट करें।

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

दस्तावेज़ में निर्मित स्क्विग्ली एनोटेशन जोड़ें।

```csharp
annotator.Add(squiggly);
```

## चरण 5: दस्तावेज़ सहेजें

एनोटेटेड दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें।

```csharp
annotator.Save(outputPath);
```

## चरण 6: पुष्टिकरण प्रदर्शित करें

एनोटेटेड दस्तावेज़ की सफल बचत की पुष्टि करने वाला एक संदेश प्रदर्शित करें।

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष

अंत में, .NET के लिए Groupdocs.Annotation डेवलपर्स को दस्तावेज़ एनोटेशन कार्यात्मकताओं को उनके .NET अनुप्रयोगों में निर्बाध रूप से एकीकृत करने के लिए उपकरणों का एक मजबूत सेट प्रदान करता है। इस चरण-दर-चरण मार्गदर्शिका का पालन करके, आप आसानी से अपने दस्तावेज़ों में टेक्स्ट स्क्विग्ली एनोटेशन जोड़ सकते हैं, सहयोग और दस्तावेज़ समीक्षा प्रक्रियाओं को बढ़ा सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### प्रश्न: क्या Groupdocs.Annotation विभिन्न फ़ाइल स्वरूपों पर एनोटेशन का समर्थन कर सकता है?

उत्तर: हां, Groupdocs.Annotation पीडीएफ, वर्ड दस्तावेज़, एक्सेल शीट और अन्य सहित फ़ाइल स्वरूपों की एक विस्तृत श्रृंखला पर एनोटेशन का समर्थन करता है।

### प्रश्न: क्या Groupdocs.Annotation डेस्कटॉप और वेब एप्लिकेशन दोनों के साथ संगत है?

उत्तर: बिल्कुल! Groupdocs.Annotation को लचीलेपन और बहुमुखी प्रतिभा की पेशकश करते हुए डेस्कटॉप और वेब अनुप्रयोगों दोनों में सहजता से एकीकृत किया जा सकता है।

### प्रश्न: क्या Groupdocs.Annotation के लिए कोई लाइसेंसिंग विकल्प उपलब्ध हैं?

उत्तर: हां, Groupdocs.Annotation व्यक्तिगत या उद्यम की जरूरतों के अनुरूप लचीले लाइसेंसिंग विकल्प प्रदान करता है, जिसमें परीक्षण उद्देश्यों के लिए अस्थायी लाइसेंस भी शामिल हैं।

### प्रश्न: क्या Groupdocs.Annotation का उपयोग करके बनाए गए एनोटेशन को अनुकूलित किया जा सकता है?

उत्तर: निश्चित रूप से! Groupdocs.Annotation एनोटेशन के लिए व्यापक अनुकूलन विकल्प प्रदान करता है, जिससे डेवलपर्स को उनकी विशिष्ट आवश्यकताओं के अनुसार एनोटेशन तैयार करने की अनुमति मिलती है।

### प्रश्न: क्या Groupdocs.Annotation डेवलपर्स के लिए समर्थन और दस्तावेज़ीकरण प्रदान करता है?

उत्तर: सचमुच! Groupdocs.Annotation डेवलपर्स को अपनी सुविधाओं का प्रभावी ढंग से उपयोग करने में सहायता करने के लिए व्यापक दस्तावेज़ीकरण और समर्पित सहायता फ़ोरम प्रदान करता है।