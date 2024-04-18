---
title: दस्तावेज़ में छवि एनोटेशन जोड़ें (दूरस्थ पथ)
linktitle: दस्तावेज़ में छवि एनोटेशन जोड़ें (दूरस्थ पथ)
second_title: GroupDocs.Annotation .NET API
description: जानें कि .NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ों में छवि एनोटेशन कैसे जोड़ें। शक्तिशाली एनोटेशन क्षमताओं के साथ दस्तावेज़ प्रबंधन बढ़ाएँ।
type: docs
weight: 15
url: /hi/net/unlocking-annotation-power/add-image-annotation-remote-path/
---
## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ में छवि एनोटेशन जोड़ने की प्रक्रिया के बारे में जानेंगे। यह लाइब्रेरी विभिन्न प्रकार के दस्तावेज़ों को प्रोग्रामेटिक रूप से एनोटेट करने के लिए शक्तिशाली उपकरण प्रदान करती है।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1.  .NET के लिए GroupDocs.Annotation: यहां से लाइब्रेरी डाउनलोड और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/annotation/net/).
2. विकास परिवेश: सुनिश्चित करें कि आपके पास .NET विकास के लिए एक कार्यशील विकास परिवेश स्थापित है।
3.  दस्तावेज़: वह दस्तावेज़ तैयार करें जिस पर आप टिप्पणी करना चाहते हैं। इस ट्यूटोरियल के लिए, हम मान लेंगे कि आपके पास नाम का एक पीडीएफ दस्तावेज़ है`input.pdf`.
4. एनोटेशन के लिए छवि: वह छवि चुनें जिसे आप एनोटेशन के लिए उपयोग करना चाहते हैं। सुनिश्चित करें कि आपके पास छवि URL या स्थानीय पथ तैयार है।

## नामस्थान आयात करें
इससे पहले कि हम कोडिंग शुरू करें, आइए आवश्यक नामस्थान आयात करें:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## चरण 1: आउटपुट पथ सेट करें
सबसे पहले, आउटपुट पथ को परिभाषित करें जहां एनोटेटेड दस्तावेज़ सहेजा जाएगा।
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एनोटेटर प्रारंभ करें
 का एक उदाहरण बनाएं`Annotator` क्लास बनाएं और इनपुट दस्तावेज़ निर्दिष्ट करें।
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां जाएगा
}
```
## चरण 3: छवि एनोटेशन जोड़ें
अब, दस्तावेज़ में छवि एनोटेशन जोड़ें। हम छवि एनोटेशन के गुण निर्दिष्ट करेंगे जैसे स्थिति, अपारदर्शिता, पृष्ठ संख्या और छवि पथ।
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // एनोटेशन की स्थिति निर्दिष्ट करें
    CreatedOn = DateTime.Now, // निर्माण तिथि निर्धारित करें
    Opacity = 0.7, // अपारदर्शिता सेट करें (0 से 1)
    PageNumber = 0, // पृष्ठ संख्या निर्दिष्ट करें
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // छवि का URL प्रदान करें
};
annotator.Add(image); // छवि एनोटेशन जोड़ें
```
## चरण 4: दस्तावेज़ सहेजें
एनोटेटेड दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें।
```csharp
annotator.Save(outputPath);
```
## चरण 5: आउटपुट पथ प्रदर्शित करें
उपयोगकर्ता को सफल दस्तावेज़ सेव ऑपरेशन के बारे में सूचित करें और आउटपुट पथ प्रदर्शित करें।
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि .NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ में छवि एनोटेशन कैसे जोड़ें। इन चरणों का पालन करके, आप अपने दस्तावेज़ प्रबंधन अनुप्रयोगों को शक्तिशाली एनोटेशन क्षमताओं के साथ बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Annotation का उपयोग पीडीएफ के अलावा अन्य दस्तावेज़ प्रारूपों के साथ किया जा सकता है?
हाँ, GroupDocs.Annotation Word, Excel, PowerPoint और अन्य सहित विभिन्न दस्तावेज़ स्वरूपों का समर्थन करता है।
### क्या GroupDocs.Annotation .NET कोर के साथ संगत है?
हाँ, GroupDocs.Annotation .NET Framework और .NET Core दोनों के साथ संगत है।
### क्या मैं एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
हाँ, आप रंग, अपारदर्शिता और आकार जैसे एनोटेशन के स्वरूप को अनुकूलित कर सकते हैं।
### क्या GroupDocs.Annotation सहयोगी एनोटेशन सुविधाओं का समर्थन करता है?
हाँ, GroupDocs.Annotation दस्तावेज़ों पर वास्तविक समय सहयोग के लिए सहयोगी एनोटेशन सुविधाएँ प्रदान करता है।
### क्या परीक्षण के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हाँ, आप GroupDocs.Annotation का निःशुल्क परीक्षण प्राप्त कर सकते हैं[यहाँ](https://releases.groupdocs.com/).