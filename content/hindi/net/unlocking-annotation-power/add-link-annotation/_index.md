---
"description": ".NET के लिए Groupdocs.Annotation का उपयोग करके दस्तावेज़ों में लिंक एनोटेशन जोड़ने का तरीका जानें। सहयोग और अन्तरक्रियाशीलता को सहजता से बढ़ाएँ।"
"linktitle": "दस्तावेज़ में लिंक एनोटेशन जोड़ें"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "दस्तावेज़ में लिंक एनोटेशन जोड़ें"
"url": "/hi/net/unlocking-annotation-power/add-link-annotation/"
"weight": 16
---

# दस्तावेज़ में लिंक एनोटेशन जोड़ें

## परिचय
.NET के लिए Groupdocs.Annotation एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को उनके .NET अनुप्रयोगों में व्यापक एनोटेशन कार्यक्षमताओं को आसानी से एकीकृत करने में सक्षम बनाती है। इसकी एक प्रमुख विशेषता यह है कि यह दस्तावेज़ों में लिंक एनोटेशन जोड़ने की क्षमता प्रदान करता है, जिससे सहयोग और अन्तरक्रियाशीलता बढ़ती है।
## आवश्यक शर्तें
लिंक एनोटेशन जोड़ने की प्रक्रिया में आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
- C# प्रोग्रामिंग भाषा की बुनियादी समझ।
- .NET लाइब्रेरी के लिए Groupdocs.Annotation स्थापित किया गया।
- उस दस्तावेज़ तक पहुंच जिस पर आप टिप्पणी करना चाहते हैं.

## नामस्थान आयात करें
सबसे पहले, आपको .NET कार्यक्षमताओं के लिए Groupdocs.Annotation का उपयोग करने के लिए आवश्यक नामस्थानों को आयात करना होगा। यह आपके एप्लिकेशन को दस्तावेज़ों को एनोटेट करने के लिए आवश्यक कक्षाओं और विधियों तक पहुँचने की अनुमति देता है।
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## चरण 1: आउटपुट पथ सेट करें
वह पथ निर्धारित करें जहाँ आप एनोटेट दस्तावेज़ को सहेजना चाहते हैं।
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एनोटेटर आरंभ करें
इसका एक उदाहरण बनाएं `Annotator` उस दस्तावेज़ का पथ प्रदान करके क्लास में जाएँ जिस पर आप टिप्पणी करना चाहते हैं।
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // एनोटेशन कोड यहां जाएगा
}
```
## चरण 3: लिंक एनोटेशन बनाएँ
परिभाषित करें `LinkAnnotation` ऑब्जेक्ट चुनें और उसके गुण निर्दिष्ट करें जैसे संदेश, अपारदर्शिता, पृष्ठ संख्या, पृष्ठभूमि रंग, बिंदु, उत्तर और URL.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
    },
    Url = "https://www.google.com"
};
```
## चरण 4: एनोटेशन जोड़ें
बनाए गए लिंक एनोटेशन को दस्तावेज़ में जोड़ें `Add` एनोटेटर इंस्टैंस की विधि.
```csharp
annotator.Add(link);
```
## चरण 5: दस्तावेज़ सहेजें
एनोटेट किए गए दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें.
```csharp
annotator.Save(outputPath);
```
## चरण 6: सफलता संदेश प्रदर्शित करें
एनोटेट दस्तावेज़ के सफलतापूर्वक सहेजे जाने के बारे में उपयोगकर्ता को सूचित करें।
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष
निष्कर्ष में, उपरोक्त चरणों का पालन करके, आप Groupdocs.Annotation for .NET का उपयोग करके दस्तावेज़ों में लिंक एनोटेशन को सहजता से जोड़ सकते हैं। यह दस्तावेज़ सहयोग को बढ़ाता है और उपयोगकर्ताओं को इंटरैक्टिव सुविधाएँ प्रदान करता है।
## अक्सर पूछे जाने वाले प्रश्न
### क्या Groupdocs.Annotation for .NET सभी प्रकार के दस्तावेज़ों के साथ संगत है?
.NET के लिए Groupdocs.Annotation पीडीएफ, वर्ड, एक्सेल और अधिक सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुरूप एनोटेशन के विभिन्न गुणों जैसे रंग, अपारदर्शिता और आकार को अनुकूलित कर सकते हैं।
### क्या Groupdocs.Annotation for .NET वास्तविक समय सहयोग सुविधाएं प्रदान करता है?
हां, Groupdocs.Annotation for .NET वास्तविक समय सहयोग सुविधाएं प्रदान करता है जिससे कई उपयोगकर्ता एक साथ दस्तावेज़ों पर टिप्पणी कर सकते हैं।
### क्या ग्रुपडॉक्स उत्पादों के लिए तकनीकी सहायता उपलब्ध है?
हां, ग्रुपडॉक्स उत्पादों के लिए तकनीकी सहायता फोरम और समर्थन के माध्यम से उपलब्ध है [यहाँ](https://forum.groupdocs.com/c/annotation/10).
### क्या मैं खरीदने से पहले Groupdocs.Annotation for .NET आज़मा सकता हूँ?
हां, आप खरीदारी करने से पहले इसकी विशेषताओं का पता लगाने के लिए Groupdocs.Annotation for .NET का निःशुल्क परीक्षण का लाभ उठा सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).