---
title: एफ़टीपी से दस्तावेज़ लोड करें
linktitle: एफ़टीपी से दस्तावेज़ लोड करें
second_title: GroupDocs.Annotation .NET API
description: निर्बाध दस्तावेज़ एनोटेशन के लिए GroupDocs.Annotation के साथ अपने .NET अनुप्रयोगों को बेहतर बनाएं। चरण-दर-चरण ट्यूटोरियल शामिल है।
type: docs
weight: 12
url: /hi/net/document-loading-essentials/load-document-from-ftp/
---
## परिचय
.NET के लिए GroupDocs.Annotation एक बहुमुखी लाइब्रेरी है जिसे .NET अनुप्रयोगों के भीतर दस्तावेज़ एनोटेशन क्षमताओं को सहजता से सुविधाजनक बनाने के लिए डिज़ाइन किया गया है। चाहे आप पीडीएफ, माइक्रोसॉफ्ट ऑफिस दस्तावेजों, छवियों, या अन्य प्रारूपों के साथ काम कर रहे हों, यह लाइब्रेरी सहयोग और दस्तावेज़ प्रबंधन को बढ़ाने के लिए टिप्पणियाँ, हाइलाइट्स और आकार जैसे एनोटेशन जोड़ने के लिए एक एकीकृत समाधान प्रदान करती है।
## आवश्यक शर्तें
ट्यूटोरियल में जाने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यक शर्तें हैं:
1. C# का ज्ञान: इस ट्यूटोरियल में दिए गए कोड उदाहरणों को समझने और लागू करने के लिए C# प्रोग्रामिंग भाषा में दक्षता आवश्यक है।
2.  .NET के लिए GroupDocs.Annotation: .NET के लिए GroupDocs.Annotation को डाउनलोड और इंस्टॉल करना सुनिश्चित करें।[लिंक को डाउनलोड करें](https://releases.groupdocs.com/annotation/net/). लाइब्रेरी को अपने .NET प्रोजेक्ट में सफलतापूर्वक एकीकृत करने के लिए इंस्टॉलेशन निर्देशों का पालन करें।
## नामस्थान आयात करें
.NET कार्यात्मकताओं के लिए GroupDocs.Annotation का उपयोग करने के लिए, आपको अपने C# प्रोजेक्ट में आवश्यक नामस्थान आयात करने की आवश्यकता है। इन चरणों का पालन करें:

अपने C# प्रोजेक्ट में, अपनी कोड फ़ाइल की शुरुआत में आवश्यक नामस्थान शामिल करें:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

अब, आइए FTP से दस्तावेज़ लोड करने और .NET के लिए GroupDocs.Annotation का उपयोग करके उसमें एनोटेशन जोड़ने की प्रक्रिया के बारे में गहराई से जानें।
## चरण 1: आउटपुट पथ को परिभाषित करें
आउटपुट पथ निर्दिष्ट करें जहां एनोटेटेड दस्तावेज़ सहेजा जाएगा।
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एफ़टीपी से दस्तावेज़ लोड करें
दिए गए फ़ाइल पथ का उपयोग करके FTP सर्वर से दस्तावेज़ पुनर्प्राप्त करें।
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // एनोटेशन कोड यहां जोड़ा जाएगा
}
```
## चरण 3: एनोटेशन जोड़ें
दस्तावेज़ में वांछित एनोटेशन, जैसे क्षेत्र एनोटेशन, को परिभाषित करें और जोड़ें।
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## चरण 4: एनोटेटेड दस्तावेज़ सहेजें
एनोटेटेड दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें।
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## चरण 5: एफ़टीपी से फ़ाइल पुनर्प्राप्त करें
एफ़टीपी सर्वर से फ़ाइल लाने की विधि लागू करें।
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## चरण 6: एफ़टीपी अनुरोध बनाएं
फ़ाइल डाउनलोड करने के लिए एक FTP अनुरोध जनरेट करें।
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## चरण 7: फ़ाइल स्ट्रीम प्राप्त करें
एफ़टीपी प्रतिक्रिया से फ़ाइल स्ट्रीम पुनर्प्राप्त करें।
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## निष्कर्ष
अंत में, .NET के लिए GroupDocs.Annotation डेवलपर्स को दस्तावेज़ एनोटेशन कार्यात्मकताओं को उनके .NET अनुप्रयोगों में निर्बाध रूप से एकीकृत करने का अधिकार देता है। इस ट्यूटोरियल में उल्लिखित चरण-दर-चरण मार्गदर्शिका का पालन करके, आप एफ़टीपी से दस्तावेज़ों को कुशलतापूर्वक लोड कर सकते हैं और आसानी से एनोटेशन जोड़ सकते हैं, अपने अनुप्रयोगों के भीतर सहयोग और दस्तावेज़ प्रबंधन को बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या .NET के लिए GroupDocs.Annotation सभी दस्तावेज़ प्रारूपों के साथ संगत है?
हाँ, .NET के लिए GroupDocs.Annotation PDF, Microsoft Office दस्तावेज़, चित्र और बहुत कुछ सहित दस्तावेज़ स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं .NET के लिए GroupDocs.Annotation का उपयोग करके जोड़े गए एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
बिल्कुल, .NET के लिए GroupDocs.Annotation रंग, शैली और आकार सहित एनोटेशन उपस्थिति के लिए व्यापक अनुकूलन विकल्प प्रदान करता है।
### क्या .NET के लिए GroupDocs.Annotation क्लाउड स्टोरेज सेवाओं के लिए समर्थन प्रदान करता है?
हां, .NET के लिए GroupDocs.Annotation लोकप्रिय क्लाउड स्टोरेज सेवाओं के साथ सहजता से एकीकृत होता है, जिससे आप ड्रॉपबॉक्स, गूगल ड्राइव और वनड्राइव जैसी सेवाओं से दस्तावेज़ों को लोड और सहेज सकते हैं।
### क्या .NET के लिए GroupDocs.Annotation के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हाँ, आप नि:शुल्क परीक्षण संस्करण डाउनलोड करके .NET के लिए GroupDocs.Annotation की सुविधाओं का पता लगा सकते हैं।[रिलीज पेज](https://releases.groupdocs.com/).
### मैं .NET के लिए GroupDocs.Annotation के लिए तकनीकी सहायता या समर्थन कैसे प्राप्त कर सकता हूँ?
 तकनीकी सहायता, समस्या निवारण, या सामान्य पूछताछ के लिए, आप .NET के लिए GroupDocs.Annotation पर जा सकते हैं[सहयता मंच](https://forum.groupdocs.com/c/annotation/10).