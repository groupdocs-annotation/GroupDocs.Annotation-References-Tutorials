---
title: दस्तावेज़ में खोज टेक्स्ट फ़्रैगमेंट एनोटेशन जोड़ें
linktitle: दस्तावेज़ में खोज टेक्स्ट फ़्रैगमेंट एनोटेशन जोड़ें
second_title: GroupDocs.Annotation .NET API
description: .NET के लिए GroupDocs.Annotation की शक्ति का अन्वेषण करें और आसानी से अपने अनुप्रयोगों में दस्तावेज़ एनोटेशन क्षमताओं को जोड़ें।
weight: 20
url: /hi/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---
## परिचय
.NET विकास के क्षेत्र में, GroupDocs.Annotation दस्तावेज़ों को निर्बाध रूप से एनोटेट करने के लिए एक शक्तिशाली उपकरण के रूप में सामने आता है। चाहे आप एक अनुभवी डेवलपर हों या बस .NET की दुनिया में कदम रख रहे हों, यह व्यापक ट्यूटोरियल आपको .NET के लिए GroupDocs.Annotation का उपयोग करने की अनिवार्यताओं के बारे में बताएगा, जिसमें नेमस्पेस आयात करने से लेकर खोज टेक्स्ट खंड एनोटेशन जोड़ने की जटिलताओं में महारत हासिल होगी। दस्तावेज़.
## परिचय
.NET के लिए GroupDocs.Annotation डेवलपर्स को अपने अनुप्रयोगों में दस्तावेज़ एनोटेशन क्षमताओं को सहजता से शामिल करने का अधिकार देता है। इसकी सहज एपीआई और मजबूत सुविधाओं के साथ, डेवलपर्स पीडीएफ, माइक्रोसॉफ्ट ऑफिस दस्तावेज़, छवियों और अन्य सहित विभिन्न दस्तावेज़ प्रारूपों को एनोटेट कर सकते हैं।
## आवश्यक शर्तें
.NET के लिए GroupDocs.Annotation में जाने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यक शर्तें मौजूद हैं:

## नामस्थान आयात करें
सबसे पहले, अपने .NET प्रोजेक्ट में GroupDocs.Annotation कक्षाओं और विधियों तक पहुँचने के लिए आवश्यक नामस्थान आयात करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## चरण 1: आउटपुट पथ को परिभाषित करें
आउटपुट पथ को परिभाषित करके प्रारंभ करें जहां एनोटेटेड दस्तावेज़ सहेजा जाएगा:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एनोटेटर प्रारंभ करें
 इसके बाद, का एक उदाहरण प्रारंभ करें`Annotator` जिस दस्तावेज़ को आप एनोटेट करना चाहते हैं, उसके लिए पथ प्रदान करके क्लास करें:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## चरण 3: खोज टेक्स्ट फ़्रैगमेंट एनोटेशन बनाएं
 एक बनाने के`SearchTextFragment` वांछित गुणों वाली वस्तु, जैसे खोजने के लिए पाठ, फ़ॉन्ट आकार, फ़ॉन्ट परिवार, फ़ॉन्ट रंग और पृष्ठभूमि रंग:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## चरण 4: एनोटेशन जोड़ें
 का उपयोग करके दस्तावेज़ में निर्मित खोज पाठ खंड एनोटेशन जोड़ें`Add` एनोटेटर की विधि:
```csharp
annotator.Add(searchText);
```
## चरण 5: एनोटेटेड दस्तावेज़ सहेजें
एनोटेटेड दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें:
```csharp
annotator.Save(outputPath);
```
## चरण 6: सफलता संदेश प्रदर्शित करें
उपयोगकर्ता को सूचित करें कि दस्तावेज़ सफलतापूर्वक सहेजा गया है:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष
अंत में, .NET के लिए GroupDocs.Annotation दस्तावेज़ों में एनोटेशन जोड़ने, सहयोग बढ़ाने और दस्तावेज़ समीक्षा प्रक्रियाओं को सरल बनाता है। इस गाइड में उल्लिखित चरणों का पालन करके, आप दस्तावेज़ एनोटेशन क्षमताओं को अपने .NET अनुप्रयोगों में निर्बाध रूप से एकीकृत कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Annotation सभी दस्तावेज़ प्रारूपों के साथ संगत है?
हाँ, GroupDocs.Annotation PDF, Microsoft Office दस्तावेज़, चित्र और बहुत कुछ सहित दस्तावेज़ स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
बिल्कुल! GroupDocs.Annotation एनोटेशन के लिए व्यापक अनुकूलन विकल्प प्रदान करता है, जिससे आप फ़ॉन्ट आकार, रंग और शैली जैसे गुणों को समायोजित कर सकते हैं।
### क्या GroupDocs.Annotation के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
 हाँ, आप खरीदारी करने से पहले इसकी सुविधाओं और क्षमताओं का पता लगाने के लिए GroupDocs.Annotation के निःशुल्क परीक्षण का उपयोग कर सकते हैं[यहाँ](https://releases.groupdocs.com/)..
### मुझे GroupDocs.Annotation के लिए समर्थन कहां मिल सकता है?
 GroupDocs.Annotation के समर्थन और सहायता के लिए, आप GroupDocs पर जा सकते हैं[मंच](https://forum.groupdocs.com/c/annotation/10) एनोटेशन-संबंधित प्रश्नों और चर्चाओं के लिए समर्पित।
### मैं GroupDocs.Annotation के लिए अस्थायी लाइसेंस कैसे प्राप्त करूं?
 आप GroupDocs के माध्यम से GroupDocs.Annotation के लिए एक अस्थायी लाइसेंस प्राप्त कर सकते हैं[वेबसाइट](https://purchase.groupdocs.com/temporary-license/), आपको उत्पाद का पूरी तरह से मूल्यांकन करने में सक्षम बनाता है।