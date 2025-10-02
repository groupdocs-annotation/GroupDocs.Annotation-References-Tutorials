---
"description": ".NET के लिए Groupdocs.Annotation का उपयोग करके दस्तावेज़ों में आसानी से टेक्स्ट स्क्विग्ली एनोटेशन जोड़ने का तरीका जानें। सहयोग और दस्तावेज़ समीक्षा प्रक्रियाओं को बेहतर बनाएँ।"
"linktitle": "दस्तावेज़ में टेक्स्ट स्क्विग्ली एनोटेशन जोड़ें"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "दस्तावेज़ में टेक्स्ट स्क्विग्ली एनोटेशन जोड़ें"
"url": "/hi/net/unlocking-annotation-power/add-text-squiggly-annotation/"
type: docs
"weight": 25
---

# दस्तावेज़ में टेक्स्ट स्क्विग्ली एनोटेशन जोड़ें

## परिचय

.NET के लिए Groupdocs.Annotation एक बहुमुखी लाइब्रेरी है जो डेवलपर्स को उनके .NET अनुप्रयोगों में आसानी से मजबूत एनोटेशन क्षमताओं को एकीकृत करने में सक्षम बनाती है। चाहे आप PDF, Word दस्तावेज़ या अन्य लोकप्रिय फ़ाइल स्वरूपों के साथ काम कर रहे हों, Groupdocs.Annotation दस्तावेज़ सहयोग को एनोटेट करने और बढ़ाने के लिए एक सहज समाधान प्रदान करता है।

## आवश्यक शर्तें

ट्यूटोरियल में आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:

## नामस्थान आयात करें

.NET के लिए Groupdocs.Annotation द्वारा प्रदान की गई कार्यक्षमताओं तक पहुँचने के लिए आवश्यक नामस्थानों को आयात करना सुनिश्चित करें।

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

अब जबकि हमने सभी पूर्वापेक्षाओं को पूरा कर लिया है, तो आइए टेक्स्ट स्क्विग्ली एनोटेशन जोड़ने की प्रक्रिया को कई चरणों में विभाजित करें।

## चरण 1: आउटपुट पथ परिभाषित करें

वह पथ निर्धारित करें जहां एनोटेट दस्तावेज़ सहेजा जाएगा.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## चरण 2: एनोटेटर आरंभ करें

इनपुट दस्तावेज़ पथ प्रदान करके एनोटेटर ऑब्जेक्ट को आरंभ करें।

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां दिया गया है
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

निर्मित स्क्विग्ली एनोटेशन को दस्तावेज़ में जोड़ें।

```csharp
annotator.Add(squiggly);
```

## चरण 5: दस्तावेज़ सहेजें

एनोटेट किए गए दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें.

```csharp
annotator.Save(outputPath);
```

## चरण 6: पुष्टि प्रदर्शित करें

एनोटेट किए गए दस्तावेज़ के सफलतापूर्वक सहेजे जाने की पुष्टि करने वाला संदेश प्रदर्शित करें।

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष

निष्कर्ष में, .NET के लिए Groupdocs.Annotation डेवलपर्स को उनके .NET अनुप्रयोगों में दस्तावेज़ एनोटेशन कार्यक्षमताओं को सहजता से एकीकृत करने के लिए उपकरणों का एक मजबूत सेट प्रदान करता है। इस चरण-दर-चरण मार्गदर्शिका का पालन करके, आप आसानी से अपने दस्तावेज़ों में टेक्स्ट स्क्विग्ली एनोटेशन जोड़ सकते हैं, जिससे सहयोग और दस्तावेज़ समीक्षा प्रक्रियाएँ बेहतर हो जाती हैं।

## अक्सर पूछे जाने वाले प्रश्न

### प्रश्न: क्या Groupdocs.Annotation विभिन्न फ़ाइल स्वरूपों पर एनोटेशन का समर्थन कर सकता है?

उत्तर: हां, Groupdocs.Annotation पीडीएफ, वर्ड दस्तावेज़, एक्सेल शीट आदि सहित फ़ाइल स्वरूपों की एक विस्तृत श्रृंखला पर एनोटेशन का समर्थन करता है।

### प्रश्न: क्या Groupdocs.Annotation डेस्कटॉप और वेब दोनों अनुप्रयोगों के साथ संगत है?

उत्तर: बिल्कुल! Groupdocs.Annotation को डेस्कटॉप और वेब दोनों अनुप्रयोगों में सहजता से एकीकृत किया जा सकता है, जो लचीलापन और बहुमुखी प्रतिभा प्रदान करता है।

### प्रश्न: क्या Groupdocs.Annotation के लिए कोई लाइसेंसिंग विकल्प उपलब्ध हैं?

उत्तर: हां, Groupdocs.Annotation व्यक्तिगत या उद्यम आवश्यकताओं के अनुरूप लचीले लाइसेंसिंग विकल्प प्रदान करता है, जिसमें परीक्षण उद्देश्यों के लिए अस्थायी लाइसेंस भी शामिल हैं।

### प्रश्न: क्या Groupdocs.Annotation का उपयोग करके बनाए गए एनोटेशन को अनुकूलित किया जा सकता है?

उत्तर: निश्चित रूप से! Groupdocs.Annotation एनोटेशन के लिए व्यापक अनुकूलन विकल्प प्रदान करता है, जिससे डेवलपर्स अपनी विशिष्ट आवश्यकताओं के अनुसार एनोटेशन को अनुकूलित कर सकते हैं।

### प्रश्न: क्या Groupdocs.Annotation डेवलपर्स के लिए समर्थन और दस्तावेज़ीकरण प्रदान करता है?

उत्तर: सचमुच! Groupdocs.Annotation डेवलपर्स को इसकी सुविधाओं का प्रभावी ढंग से उपयोग करने में सहायता करने के लिए व्यापक दस्तावेज़ीकरण और समर्पित सहायता फ़ोरम प्रदान करता है।