---
"description": ".NET के लिए GroupDocs.Annotation का उपयोग करके अपने दस्तावेज़ों में तीर एनोटेशन जोड़ने का तरीका जानें। दस्तावेज़ की स्पष्टता और अन्तरक्रियाशीलता को सहजता से बढ़ाएँ।"
"linktitle": "दस्तावेज़ में तीर एनोटेशन जोड़ें"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "दस्तावेज़ में तीर एनोटेशन जोड़ें"
"url": "/hi/net/unlocking-annotation-power/add-arrow-annotation/"
"weight": 11
---

# दस्तावेज़ में तीर एनोटेशन जोड़ें

## परिचय
इस ट्यूटोरियल में, हम आपको GroupDocs.Annotation for .NET का उपयोग करके अपने दस्तावेज़ों में तीर एनोटेशन जोड़ने की प्रक्रिया के माध्यम से मार्गदर्शन करेंगे। तीर एनोटेशन किसी दस्तावेज़ के भीतर दिशा को इंगित करने या विशिष्ट तत्वों को इंगित करने के लिए उपयोगी होते हैं।
## आवश्यक शर्तें
आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1. .NET के लिए GroupDocs.Annotation: .NET के लिए GroupDocs.Annotation लाइब्रेरी स्थापित करें। आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.groupdocs.com/annotation/net/).
2. विकास परिवेश: सुनिश्चित करें कि आपके पास .NET विकास के लिए एक विकास परिवेश स्थापित है, जिसमें Visual Studio या कोई अन्य पसंदीदा IDE शामिल है।

## नामस्थान आयात करें
सबसे पहले, आपको एनोटेशन के लिए आवश्यक क्लासेस और विधियों तक पहुंचने के लिए आवश्यक नेमस्पेस को आयात करना होगा।
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## चरण 1: एनोटेटर आरंभ करें
इनपुट दस्तावेज़ फ़ाइल पथ प्रदान करके एनोटेटर को आरंभ करें।
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## चरण 2: एरो एनोटेशन बनाएं
ArrowAnnotation वर्ग का एक उदाहरण बनाएं और इसके गुणधर्मों को परिभाषित करें, जैसे स्थिति, संदेश, अपारदर्शिता, पेन रंग, शैली, चौड़ाई, आदि।
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
दस्तावेज़ में तीर एनोटेशन जोड़ें `Add` व्याख्याकार की विधि.
```csharp
	annotator.Add(arrow);
```
## चरण 4: दस्तावेज़ सहेजें
एनोटेट किए गए दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें.
```csharp
	annotator.Save(outputPath);
}
```
## चरण 5: पुष्टि प्रदर्शित करें
दस्तावेज़ के सफलतापूर्वक सहेजे जाने का संकेत देने वाला एक पुष्टिकरण संदेश प्रदर्शित करें.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
अब आपने GroupDocs.Annotation for .NET का उपयोग करके अपने दस्तावेज़ में सफलतापूर्वक एक तीर एनोटेशन जोड़ दिया है।

## निष्कर्ष
इस ट्यूटोरियल में, हमने GroupDocs.Annotation for .NET का उपयोग करके दस्तावेज़ों में तीर एनोटेशन जोड़ने की प्रक्रिया को कवर किया है। इन चरणों का पालन करके, आप अपने दस्तावेज़ों को स्पष्ट दिशात्मक संकेतकों के साथ बढ़ा सकते हैं, जिससे वे अधिक जानकारीपूर्ण और आकर्षक बन सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं तीर एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपने ट्यूटोरियल और दस्तावेज़ आवश्यकताओं के अनुरूप रंग, शैली, चौड़ाई और अपारदर्शिता जैसे विभिन्न गुणों को अनुकूलित कर सकते हैं।
### क्या GroupDocs.Annotation सभी दस्तावेज़ प्रारूपों के साथ संगत है?
GroupDocs.Annotation पीडीएफ, DOCX, PPTX, XLSX, और अधिक सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं GroupDocs.Annotation का उपयोग करके प्रोग्रामेटिक रूप से एनोटेशन जोड़ सकता हूँ?
हां, GroupDocs.Annotation API प्रदान करता है जो आपको प्रोग्रामेटिक रूप से दस्तावेज़ों से एनोटेशन जोड़ने, संपादित करने और हटाने की अनुमति देता है।
### क्या GroupDocs.Annotation निःशुल्क परीक्षण प्रदान करता है?
हां, आप इसे यहां से डाउनलोड करके GroupDocs.Annotation को मुफ्त में आज़मा सकते हैं [यहाँ](https://releases.groupdocs.com/).
### मैं GroupDocs.Annotation के लिए तकनीकी सहायता कहां से प्राप्त कर सकता हूं?
तकनीकी सहायता और सहायता के लिए, आप GroupDocs.Annotation फ़ोरम पर जा सकते हैं [यहाँ](https://forum.groupdocs.com/c/annotation/10).