---
title: दस्तावेज़ में एरो एनोटेशन जोड़ें
linktitle: दस्तावेज़ में एरो एनोटेशन जोड़ें
second_title: GroupDocs.Annotation .NET API
description: जानें कि .NET के लिए GroupDocs.Annotation का उपयोग करके अपने दस्तावेज़ों में एरो एनोटेशन कैसे जोड़ें। दस्तावेज़ की स्पष्टता और अन्तरक्रियाशीलता को सहजता से बढ़ाएँ।
type: docs
weight: 11
url: /hi/net/unlocking-annotation-power/add-arrow-annotation/
---
## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Annotation का उपयोग करके आपके दस्तावेज़ों में एरो एनोटेशन जोड़ने की प्रक्रिया में आपका मार्गदर्शन करेंगे। किसी दस्तावेज़ में दिशा बताने या विशिष्ट तत्वों को इंगित करने के लिए एरो एनोटेशन उपयोगी होते हैं।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1.  .NET के लिए GroupDocs.Annotation: .NET के लिए GroupDocs.Annotation लाइब्रेरी स्थापित करें। आप इसे यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/annotation/net/).
2. विकास वातावरण: सुनिश्चित करें कि आपके पास .NET विकास के लिए विजुअल स्टूडियो या किसी अन्य पसंदीदा आईडीई सहित एक विकास वातावरण स्थापित है।

## नामस्थान आयात करें
सबसे पहले, आपको एनोटेशन के लिए आवश्यक कक्षाओं और विधियों तक पहुंचने के लिए आवश्यक नामस्थान आयात करने की आवश्यकता है।
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## चरण 1: एनोटेटर प्रारंभ करें
इनपुट दस्तावेज़ फ़ाइल पथ प्रदान करके एनोटेटर को प्रारंभ करें।
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## चरण 2: एरो एनोटेशन बनाएं
एरोएनोटेशन क्लास का एक उदाहरण बनाएं और इसके गुणों जैसे स्थिति, संदेश, अस्पष्टता, पेन रंग, शैली, चौड़ाई इत्यादि को परिभाषित करें।
```csharp
	ArrowAnnotation arrow = new ArrowAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is arrow annotation",
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
 का उपयोग करके दस्तावेज़ में तीर एनोटेशन जोड़ें`Add` एनोटेटर की विधि.
```csharp
	annotator.Add(arrow);
```
## चरण 4: दस्तावेज़ सहेजें
एनोटेटेड दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें।
```csharp
	annotator.Save(outputPath);
}
```
## चरण 5: पुष्टिकरण प्रदर्शित करें
दस्तावेज़ की सफल बचत का संकेत देने वाला एक पुष्टिकरण संदेश प्रदर्शित करें।
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
अब आपने .NET के लिए GroupDocs.Annotation का उपयोग करके अपने दस्तावेज़ में सफलतापूर्वक एक एरो एनोटेशन जोड़ लिया है।

## निष्कर्ष
इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ों में एरो एनोटेशन जोड़ने की प्रक्रिया को कवर किया है। इन चरणों का पालन करके, आप अपने दस्तावेज़ों को स्पष्ट दिशात्मक संकेतकों के साथ बेहतर बना सकते हैं, जिससे वे अधिक जानकारीपूर्ण और आकर्षक बन जाएंगे।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं तीर एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी प्राथमिकताओं और दस्तावेज़ आवश्यकताओं के अनुरूप विभिन्न गुणों जैसे रंग, शैली, चौड़ाई और अस्पष्टता को अनुकूलित कर सकते हैं।
### क्या GroupDocs.Annotation सभी दस्तावेज़ प्रारूपों के साथ संगत है?
GroupDocs.Annotation PDF, DOCX, PPTX, XLSX और अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं GroupDocs.Annotation का उपयोग करके प्रोग्रामेटिक रूप से एनोटेशन जोड़ सकता हूँ?
हां, GroupDocs.Annotation एपीआई प्रदान करता है जो आपको दस्तावेज़ों से प्रोग्रामेटिक रूप से एनोटेशन जोड़ने, संपादित करने और हटाने की अनुमति देता है।
### क्या GroupDocs.Annotation निःशुल्क परीक्षण की पेशकश करता है?
 हाँ, आप GroupDocs.Annotation को निःशुल्क डाउनलोड करके आज़मा सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मुझे GroupDocs.Annotation के लिए तकनीकी सहायता कहां मिल सकती है?
तकनीकी सहायता और सहायता के लिए, आप GroupDocs.Annotation फोरम पर जा सकते हैं[यहाँ](https://forum.groupdocs.com/c/annotation/10).