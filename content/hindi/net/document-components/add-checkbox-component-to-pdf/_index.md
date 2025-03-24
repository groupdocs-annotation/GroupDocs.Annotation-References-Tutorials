---
title: पीडीएफ दस्तावेज़ में चेकबॉक्स घटक जोड़ें
linktitle: पीडीएफ दस्तावेज़ में चेकबॉक्स घटक जोड़ें
second_title: GroupDocs.Annotation .NET API
description: .NET के लिए Groupdocs.Annotation का उपयोग करके PDF दस्तावेज़ों में चेकबॉक्स घटक जोड़ने का तरीका जानें। इंटरैक्टिव तत्वों के साथ अपने पीडीएफ़ को बेहतर बनाएं।
weight: 11
url: /hi/net/document-components/add-checkbox-component-to-pdf/
---
## परिचय
इस ट्यूटोरियल में, हम आपको .NET के लिए Groupdocs.Annotation का उपयोग करके एक पीडीएफ दस्तावेज़ में चेकबॉक्स घटक जोड़ने की प्रक्रिया के बारे में मार्गदर्शन करेंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1.  .NET SDK के लिए Groupdocs.Annotation: आप इसे यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/annotation/net/).
2. विकास परिवेश: सुनिश्चित करें कि आपके पास एक .NET विकास परिवेश स्थापित है।

## नामस्थान आयात करें
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
अब, आइए उदाहरण को कई चरणों में विभाजित करें:
## चरण 1: आउटपुट पथ को परिभाषित करें
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
यहां, हम आउटपुट पथ को परिभाषित करते हैं जहां संशोधित पीडीएफ दस्तावेज़ सहेजा जाएगा।
## चरण 2: एनोटेटर प्रारंभ करें
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 को आरंभ करें`Annotator` इनपुट पीडीएफ दस्तावेज़ पथ पास करके ऑब्जेक्ट।
## चरण 3: चेकबॉक्स घटक बनाएं
```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100),
    PenColor = 65535,
    Style = BoxStyle.Star,
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
 एक बनाने के`CheckBoxComponent` ऑब्जेक्ट बनाएं और उसके गुणों को अनुकूलित करें जैसे`Checked`, `Box` आयाम,`PenColor`, `Style`और कुछ उत्तर जोड़ें।
## चरण 4: चेकबॉक्स घटक जोड़ें
```csharp
annotator.Add(checkBox);
```
बनाए गए चेकबॉक्स घटक को पीडीएफ दस्तावेज़ में जोड़ें।
## चरण 5: दस्तावेज़ सहेजें
```csharp
annotator.Save("result.pdf");
```
संशोधित पीडीएफ दस्तावेज़ को चेकबॉक्स घटक के साथ सहेजें।
## चरण 6: आउटपुट पथ प्रदर्शित करें
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
वह पथ प्रदर्शित करें जहां संशोधित पीडीएफ दस्तावेज़ सहेजा गया है।

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि .NET के लिए Groupdocs.Annotation का उपयोग करके एक पीडीएफ दस्तावेज़ में चेकबॉक्स घटक कैसे जोड़ा जाए। इस ज्ञान के साथ, आप अपने पीडीएफ दस्तावेज़ों को इंटरैक्टिव तत्वों के साथ बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं चेकबॉक्स का स्वरूप अनुकूलित कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुसार विभिन्न गुणों जैसे रंग, शैली और आकार को अनुकूलित कर सकते हैं।
### क्या .NET के लिए Groupdocs.Annotation व्यावसायिक उपयोग के लिए उपयुक्त है?
हाँ, .NET के लिए Groupdocs.Annotation व्यवसायों के लिए वाणिज्यिक लाइसेंस प्रदान करता है।
### क्या मैं खरीदने से पहले .NET के लिए Groupdocs.Annotation आज़मा सकता हूँ?
 हाँ, आप निःशुल्क परीक्षण का लाभ उठा सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मुझे .NET के लिए Groupdocs.Annotation के लिए समर्थन कहां मिल सकता है?
 आप पर समर्थन और संसाधन पा सकते हैं[ग्रुपडॉक्स फोरम](https://forum.groupdocs.com/c/annotation/10).
### क्या मुझे परीक्षण उद्देश्यों के लिए अस्थायी लाइसेंस की आवश्यकता है?
 आप परीक्षण के लिए अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).