---
categories:
- Java Development
date: '2026-09-05'
description: GroupDocs.Annotation का उपयोग करके Java में URL से PDF कैसे लोड करें
  और FTP, Azure Blob, Amazon S3 और अन्य स्रोतों से PDF पर टिप्पणी कैसे करें, सीखें।
  चरण‑दर‑चरण सर्वोत्तम प्रथाओं का पालन करें।
keywords:
- load pdf from url
- annotate pdf java
- load pdf java
- load pdf from azure
- load pdf from s3
lastmod: '2026-09-05'
linktitle: दस्तावेज़ लोड करने के ट्यूटोरियल
og_description: GroupDocs.Annotation का उपयोग करके Java में URL से PDF कैसे लोड करें
  और FTP, Azure Blob, Amazon S3 और अन्य स्रोतों से PDF पर टिप्पणी कैसे करें, सीखें।
  चरण‑दर‑चरण सर्वोत्तम प्रथाओं का पालन करें।
og_image_alt: Guide to load PDF from URL in Java with GroupDocs.Annotation
og_title: Java में GroupDocs Annotation के साथ URL से PDF लोड करने का तरीका
schemas:
- author: GroupDocs
  dateModified: '2026-09-05'
  description: Learn how to load PDF from URL in Java using GroupDocs.Annotation and
    annotate PDFs from FTP, Azure Blob, Amazon S3, and other sources. Follow step‑by‑step
    best practices.
  headline: How to load PDF from URL in Java with GroupDocs Annotation
  type: TechArticle
- description: Learn how to load PDF from URL in Java using GroupDocs.Annotation and
    annotate PDFs from FTP, Azure Blob, Amazon S3, and other sources. Follow step‑by‑step
    best practices.
  name: How to load PDF from URL in Java with GroupDocs Annotation
  steps:
  - name: '**Pick the loading method** that matches your storage location.'
    text: '**Pick the loading method** that matches your storage location.'
  - name: '**Add required dependencies** (GroupDocs.Annotation JAR + any cloud SDKs).'
    text: '**Add required dependencies** (GroupDocs.Annotation JAR + any cloud SDKs).'
  - name: '**Write a small loading snippet** – start with the simplest approach.'
    text: '**Write a small loading snippet** – start with the simplest approach.'
  - name: '**Add error handling** (timeouts, retries, logging).'
    text: '**Add error handling** (timeouts, retries, logging).'
  - name: '**Apply performance tweaks** from the sections above.'
    text: '**Apply performance tweaks** from the sections above.'
  - name: '**Run tests** with PDFs of varying sizes and network conditions.'
    text: '**Run tests** with PDFs of varying sizes and network conditions.'
  type: HowTo
- questions:
  - answer: Yes. Pass the password to the `AnnotationConfig` when opening the document;
      this works for **password protected pdf java** files.
    question: Can I annotate password‑protected PDFs?
  - answer: Absolutely. Use the **load pdf from url java** approach with `java.net.URL`
      and an `InputStream`.
    question: Does GroupDocs.Annotation support loading from a public URL?
  - answer: Set the region, enable multipart download for large objects, use credential
      providers (e.g., `DefaultAWSCredentialsProviderChain`), and stream the object
      instead of loading it fully into memory.
    question: How do I correctly **configure aws s3 java** for optimal performance?
  - answer: Yes. FTPS adds TLS encryption without a major performance penalty and
      is supported by GroupDocs.Annotation.
    question: Is FTPS recommended over plain FTP?
  - answer: At least 1 GB, but using stream‑based loading can reduce the requirement
      dramatically.
    question: What is the recommended JVM heap size for processing 200 MB PDFs?
  type: FAQPage
tags:
- groupdocs-annotation
- document-loading
- java-pdf
- cloud-storage
title: Java में GroupDocs Annotation के साथ URL से PDF लोड करने का तरीका
type: docs
url: /hi/java/document-loading/
weight: 3
---

# URL से PDF लोड करना Java में GroupDocs Annotation के साथ

यदि आप **GroupDocs.Annotation for Java** के साथ काम कर रहे हैं और आपको **URL से PDF लोड** करना है — या FTP, Azure Blob, Amazon S3, या अन्य क्लाउड सेवाओं में संग्रहीत PDF — तो यह गाइड आपके लिए है। आप सबसे भरोसेमंद तरीकों को जानेंगे जिससे PDF को मेमोरी में लाया जा सके ताकि आप तुरंत उसे एनोटेट करना शुरू कर सकें, साथ ही प्रदर्शन, सुरक्षा और स्केलेबिलिटी को ध्यान में रखते हुए।

**AnnotationConfig** वह कॉन्फ़िगरेशन ऑब्जेक्ट है जो नियंत्रित करता है कि GroupDocs.Annotation जावा में दस्तावेज़ों को कैसे लोड और प्रोसेस करता है।

## त्वरित उत्तर

GroupDocs.Annotation में, `File` स्थानीय फ़ाइल को दर्शाता है और `InputStream` बाइट डेटा पढ़ने के लिए जावा स्ट्रीम है।
- **Java में एनोटेशन के लिए PDF लोड करने का सबसे आसान तरीका क्या है?** तेज़तम प्रदर्शन के लिए स्थानीय `File` या `InputStream` का उपयोग करें।  
- **क्या मैं PDF को सीधे URL से लोड कर सकता हूँ?** हाँ – `load pdf from url java` तरीका `java.net.URL` स्ट्रीम्स के साथ काम करता है।  
- **Java दस्तावेज़ लोड करने के लिए AWS S3 को कैसे कॉन्फ़िगर करें?** AWS SDK सेट अप करें, क्रेडेंशियल्स प्रदान करें, और `S3ObjectInputStream` का उपयोग करें।  
- **क्या सुरक्षित दस्तावेज़ एक्सेस के लिए FTP अभी भी एक वैध विकल्प है?** बिल्कुल, विशेष रूप से FTPS और पैसिव मोड सक्षम होने पर।  
- **यदि बड़ा PDF OutOfMemoryError देता है तो क्या करें?** स्ट्रीम‑आधारित लोडिंग पर स्विच करें और सुनिश्चित करें कि आप स्ट्रीम्स को try‑with‑resources के साथ बंद करें।  

## Java में URL से PDF कैसे लोड करें?

java.net.URL जावा क्लास है जो यूनिफॉर्म रिसोर्स लोकेटर को दर्शाता है, जो वेब पर एक संसाधन की पहचान करता है। AnnotationConfig GroupDocs.Annotation का कॉन्फ़िगरेशन ऑब्जेक्ट है जो दस्तावेज़ स्ट्रीम प्राप्त करता है। एक URL इंस्टेंस बनाएं, उसका InputStream खोलें, और स्ट्रीम को AnnotationConfig को पास करें; इससे अस्थायी फ़ाइलों से बचा जाता है और यह किसी भी सार्वजनिक रूप से पहुँच योग्य URL के साथ काम करता है, बशर्ते आप उचित टाइमआउट सेट करें और HTTP त्रुटियों को संभालें।

## Java में Amazon S3 से PDF कैसे लोड करें?

`S3ObjectInputStream` AWS SDK द्वारा प्रदान की गई एक स्ट्रीम क्लास है जो S3 ऑब्जेक्ट से डेटा पढ़ती है। AWS SDK को रीजन और क्रेडेंशियल्स के साथ कॉन्फ़िगर करें, लक्ष्य ऑब्जेक्ट के लिए S3ObjectInputStream प्राप्त करें, और उसे AnnotationConfig में पास करें; AnnotationConfig GroupDocs.Annotation की कॉन्फ़िगरेशन क्लास है जो इनपुट स्ट्रीम स्वीकार करती है। 50 MB से बड़े ऑब्जेक्ट्स के लिए मेमोरी उपयोग कम रखने और ट्रांसफ़र गति बढ़ाने हेतु मल्टीपार्ट डाउनलोड का उपयोग करें।

## Java में Azure Blob स्टोरेज से PDF कैसे लोड करें?

`BlobClient` Azure Storage SDK की एक क्लास है जो किसी विशिष्ट ब्लॉब के साथ इंटरैक्ट करने के ऑपरेशन प्रदान करती है। एक BlobClient बनाएं, ब्लॉब पर openInputStream() कॉल करें, और प्राप्त स्ट्रीम को AnnotationConfig को दें; AnnotationConfig GroupDocs.Annotation का कॉन्फ़िगरेशन ऑब्जेक्ट है जो ब्लॉब स्ट्रीम प्राप्त करता है। अक्सर पढ़ने के लिए ब्लॉब की एक्सेस टियर को Hot सेट करें और लेटेंसी कम करने के लिए क्लाइंट‑साइड कैशिंग सक्षम करें।

## Java में पासवर्ड‑सुरक्षित PDF कैसे लोड करें?

`AnnotationConfig` GroupDocs.Annotation की एक क्लास है जो दस्तावेज़ लोड करने और प्रोसेस करने के कॉन्फ़िगरेशन सेटिंग्स रखती है। `setPassword("yourPassword")` के माध्यम से PDF पासवर्ड के साथ AnnotationConfig का इंस्टेंस बनाएं, फिर फ़ाइल या स्ट्रीम को सामान्य रूप से लोड करें; लाइब्रेरी दस्तावेज़ को रन‑टाइम पर डिक्रिप्ट करती है, जिससे डिस्क पर क्लियर‑टेक्स्ट फ़ाइल को उजागर किए बिना एनोटेशन संभव हो जाता है।

## Java में FTP सर्वर से PDF कैसे लोड करें?

`FTPClient` Apache Commons Net की एक क्लास है जो फ़ाइल ट्रांसफ़र के लिए FTP प्रोटोकॉल को लागू करती है। AnnotationConfig GroupDocs.Annotation की कॉन्फ़िगरेशन क्लास है जो इनपुट स्ट्रीम प्राप्त करती है। FTPS के साथ कनेक्ट करने के लिए FTPClient का उपयोग करें, पैसिव मोड में स्विच करें, फ़ाइल को InputStream के रूप में प्राप्त करें, और उस स्ट्रीम को AnnotationConfig को पास करें; लीक से बचने के लिए हमेशा FTP कनेक्शन को finally ब्लॉक या try‑with‑resources के साथ बंद करें।

## GroupDocs Annotation के साथ PDF लोड करना Java में

सही लोडिंग रणनीति चुनना एक सुगम **annotate pdf java** अनुभव की पहली कदम है। नीचे हम प्रत्येक विधि को विभाजित करते हैं, कब उपयोग करना है इसे उजागर करते हैं, और प्रदर्शन तथा सुरक्षा प्रभावों को दर्शाते हैं।

### स्थानीय फ़ाइल सिस्टम लोडिंग
**Best for**: विकास, परीक्षण, या छोटे‑स्तर के ऐप्स जहाँ फ़ाइलें पहले से सर्वर पर मौजूद हैं।  
**Performance**: न्यूनतम लेटेंसी के साथ सबसे तेज़।

### स्ट्रीम‑आधारित लोडिंग
**Best for**: बड़े PDFs, मेमोरी‑सीमित वातावरण, या जब आपको I/O पर सूक्ष्म नियंत्रण चाहिए।  
**Performance**: डेटा को चंक्स में प्रोसेस करके `OutOfMemoryError` को रोकता है।

### URL‑आधारित लोडिंग
**Best for**: सार्वजनिक रूप से उपलब्ध PDFs या वेब सेवाओं के साथ एकीकरण।  
**Performance**: नेटवर्क गुणवत्ता पर निर्भर करता है; हमेशा रीट्राइज़ और टाइमआउट लागू करें।

### क्लाउड स्टोरेज इंटीग्रेशन (S3, Azure, आदि)
**Best for**: एंटरप्राइज़‑ग्रेड समाधान जो वैश्विक पहुँच और उच्च उपलब्धता की आवश्यकता रखते हैं।  
**Performance**: स्केलेबल, लेकिन आपको **configure aws s3 java** को सही ढंग से सेट करना होगा (रीजन, क्रेडेंशियल्स, स्ट्रीमिंग)।

### FTP सर्वर लोडिंग
**Best for**: लेगेसी सिस्टम या सुरक्षित फ़ाइल‑ट्रांसफ़र वर्कफ़्लो।  
**Performance**: विश्वसनीय, हालांकि आमतौर पर आधुनिक क्लाउड API की तुलना में धीमा।

## पासवर्ड‑सुरक्षित PDF Java फ़ाइलों को लोड करना

GroupDocs.Annotation **password protected pdf java** दस्तावेज़ों को लोड करने का समर्थन भी करता है। फ़ाइल खोलते समय बस पासवर्ड को `AnnotationConfig` को पास करें, और लाइब्रेरी इसे रन‑टाइम पर डिक्रिप्ट कर देगी। यह क्षमता आपको संवेदनशील PDFs को सुरक्षित रखने देती है जबकि पूर्ण एनोटेशन सुविधाएँ प्रदान करती है।

## Java में URL से PDF लोड करना

यदि आपको **load pdf from url java** की आवश्यकता है, तो आप `java.net.URL` का उपयोग करके `InputStream` खोल सकते हैं और उसे सीधे `AnnotationConfig` को पास कर सकते हैं। यह विधि सार्वजनिक रूप से होस्ट किए गए PDFs या जब आपका एप्लिकेशन REST एन्डपॉइंट से PDFs खपत करता है, के लिए अच्छी तरह काम करती है।

## दस्तावेज़ लोडिंग रणनीति क्यों महत्वपूर्ण है

विशिष्ट ट्यूटोरियल में जाने से पहले, चलिए देखते हैं कि दस्तावेज़ लोड करने का तरीका **annotate pdf java** प्रोजेक्ट्स को सीधे कैसे प्रभावित करता है:
- **Performance impact** – स्थानीय स्ट्रीम्स बहुत तेज़ होते हैं; रिमोट स्रोतों (FTP, क्लाउड) को टाइमआउट हैंडलिंग और कनेक्शन पूलिंग की आवश्यकता होती है।
- **Security considerations** – क्रेडेंशियल प्रबंधन, एन्क्रिप्टेड कनेक्शन, और उचित परमिशन स्कोप संवेदनशील PDFs की सुरक्षा करते हैं।
- **Scalability requirements** – कुशल लोडिंग (जैसे, स्ट्रीमिंग) आपके ऐप को दर्जनों या हजारों समवर्ती एनोटेशन सत्रों को संभालने देती है।

## सामान्य चुनौतियाँ और समाधान

| चुनौती | आम लक्षण | प्रमाणित समाधान |
|-----------|----------------|-----------------|
| कनेक्शन टाइमआउट | रिमोट लोड पर ऐप फ्रीज़ हो जाता है | स्पष्ट टाइमआउट सेट करें, कनेक्शन पूलिंग उपयोग करें, FTP के लिए पैसिव मोड सक्षम करें |
| मेमोरी प्रबंधन | बड़े PDFs पर `OutOfMemoryError` | स्ट्रीम‑आधारित लोडिंग पर स्विच करें, आवश्यक होने पर JVM हीप बढ़ाएँ, स्ट्रीम्स को try‑with‑resources से बंद करें |
| प्रमाणीकरण समस्याएँ | अंतरालिक “access denied” त्रुटियाँ | मजबूत क्रेडेंशियल स्टोरेज उपयोग करें, टोकन स्वचालित रूप से रिफ्रेश करें, S3 के लिए IAM नीतियों की जाँच करें |
| फ़ॉर्मेट समर्थन में भ्रम | कौन से फ़ाइल प्रकार काम करते हैं, स्पष्ट नहीं | GroupDocs.Annotation सभी लोडिंग विधियों में 50+ फ़ॉर्मेट (PDF, DOCX, XLSX, PPTX, इमेज) का समर्थन करता है |

## प्रदर्शन अनुकूलन सर्वोत्तम प्रथाएँ

### क्लाउड स्टोरेज के लिए
- बकेट का रीजन आपके सर्वर के सबसे निकट चुनें।
- बड़े ऑब्जेक्ट्स को समानांतर चंक्स में डाउनलोड करें।
- बार‑बार एक्सेस किए जाने वाले PDFs को स्थानीय रूप से कैश करें ताकि पुनः एनोटेशन तेज़ हो।

### FTP ऑपरेशन्स के लिए
- कनेक्शन पूल के साथ FTP कनेक्शन को पुन: उपयोग करें।
- फ़ाइलों को बाइनरी मोड में ट्रांसफ़र करें।
- बिना बड़े प्रदर्शन हानि के एन्क्रिप्शन के लिए FTPS को प्राथमिकता दें।

### स्ट्रीम प्रोसेसिंग के लिए
- तेज़ I/O के लिए कच्ची स्ट्रीम्स को `BufferedInputStream` में रैप करें।
- स्ट्रीम्स को तुरंत try‑with‑resources से डिस्पोज़ करें।
- UI‑रेस्पॉन्सिव एप्लिकेशन्स के लिए async प्रोसेसिंग पर विचार करें।

## त्वरित प्रारंभ गाइड

1. **अपने स्टोरेज लोकेशन के अनुरूप लोडिंग मेथड चुनें।**
2. **आवश्यक डिपेंडेंसीज़ जोड़ें** (GroupDocs.Annotation JAR + कोई भी क्लाउड SDK)।
3. **एक छोटा लोडिंग स्निपेट लिखें** – सबसे सरल दृष्टिकोण से शुरू करें।
4. **एरर हैंडलिंग जोड़ें** (टाइमआउट, रीट्राइज़, लॉगिंग)।
5. **ऊपर के सेक्शन से प्रदर्शन ट्यूनिंग लागू करें**।
6. **विभिन्न आकार और नेटवर्क स्थितियों वाले PDFs के साथ टेस्ट चलाएँ**।

## उपलब्ध ट्यूटोरियल

हमारे विस्तृत GroupDocs.Annotation Java ट्यूटोरियल्स के साथ दस्तावेज़ लोडिंग क्षमताओं में महारत हासिल करें। ये चरण‑दर‑चरण गाइड दिखाते हैं कि स्थानीय डिस्क, स्ट्रीम्स, URLs, Amazon S3 और Azure जैसे क्लाउड स्टोरेज, FTP सर्वर, और पासवर्ड‑सुरक्षित फ़ाइलों से दस्तावेज़ कैसे लोड करें। प्रत्येक ट्यूटोरियल में कार्यशील जावा कोड उदाहरण, इम्प्लीमेंटेशन नोट्स, और सर्वोत्तम प्रथाएँ शामिल हैं।

### [FTP से PDFs को Annotate करना GroupDocs.Annotation for Java का उपयोग करके: एक पूर्ण गाइड](./annotate-pdf-ftp-groupdocs-java/)
GroupDocs.Annotation for Java का उपयोग करके FTP सर्वर से सीधे PDF दस्तावेज़ों को एनोटेट करना सीखें। यह ट्यूटोरियल FTP कनेक्शन सेटअप, सुरक्षित प्रमाणीकरण, एरर हैंडलिंग, और प्रदर्शन अनुकूलन को कवर करता है। लेगेसी सिस्टम या सुरक्षित फ़ाइल ट्रांसफ़र वर्कफ़्लो के साथ एकीकरण के लिए उपयुक्त।

### [GroupDocs.Annotation Java का उपयोग करके Azure Blob फ़ाइलें डाउनलोड और एनोटेट कैसे करें](./download-annotate-azure-blob-groupdocs-java/)
Azure Blob स्टोरेज से फ़ाइलें सहजता से डाउनलोड करके उन्हें GroupDocs.Annotation for Java के साथ एनोटेट करना सीखें। यह व्यापक गाइड Azure प्रमाणीकरण, ब्लॉब एक्सेस पैटर्न, और कुशल दस्तावेज़ प्रोसेसिंग वर्कफ़्लो को कवर करता है।

### [Java का उपयोग करके Amazon S3 से दस्तावेज़ लोड और एनोटेट करें: GroupDocs.Annotation इंटीग्रेशन के लिए गाइड](./annotate-documents-amazon-s3-java-groupdocs/)
Java में GroupDocs.Annotation के साथ Amazon S3 पर संग्रहीत दस्तावेज़ों को कुशलता से लोड और एनोटेट करना सीखें। यह गाइड AWS SDK इंटीग्रेशन, IAM कॉन्फ़िगरेशन, प्रदर्शन अनुकूलन, और लागत‑प्रभावी एक्सेस पैटर्न को कवर करता है।

## सामान्य समस्याओं का निवारण

### दस्तावेज़ लोडिंग चुपचाप विफल हो जाता है
**Symptoms**: कोई त्रुटि नहीं आती, लेकिन दस्तावेज़ कभी नहीं दिखता।  
**Solution**: फ़ाइल अनुमतियों की जाँच करें, पुष्टि करें कि फ़ॉर्मेट समर्थित है, और GroupDocs.Annotation में डिबग लॉगिंग सक्षम करें।

### धीमी लोडिंग प्रदर्शन
**Symptoms**: PDFs को खोलने में अत्यधिक समय लगता है।  
**Solution**: कनेक्शन पूलिंग लागू करें, 50 MB से बड़े फ़ाइलों के लिए स्ट्रीमिंग उपयोग करें, और नेटवर्क लेटेंसी जांचें।

### बड़े फ़ाइलों में मेमोरी समस्याएँ
**Symptoms**: `OutOfMemoryError` या UI फ्रीज़ हो जाता है।  
**Solution**: स्ट्रीम‑आधारित लोडिंग पर स्विच करें, आवश्यक होने पर JVM हीप बढ़ाएँ, और हमेशा स्ट्रीम्स को बंद करें।

### प्रमाणीकरण विफलताएँ
**Symptoms**: अंतरालिक “access denied” संदेश।  
**Solution**: क्रेडेंशियल्स को दोबारा जांचें, टोकन रिफ्रेश लॉजिक उपयोग करें, और सुनिश्चित करें कि IAM नीतियां (S3 के लिए) या Azure RBAC सही ढंग से असाइन की गई हैं।

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं पासवर्ड‑सुरक्षित PDFs को एनोटेट कर सकता हूँ?**  
A: हाँ। दस्तावेज़ खोलते समय पासवर्ड को `AnnotationConfig` को पास करें; यह **password protected pdf java** फ़ाइलों के लिए काम करता है।

**Q: क्या GroupDocs.Annotation सार्वजनिक URL से लोडिंग का समर्थन करता है?**  
A: बिल्कुल। `java.net.URL` और `InputStream` के साथ **load pdf from url java** तरीका उपयोग करें।

**Q: इष्टतम प्रदर्शन के लिए **configure aws s3 java** को सही ढंग से कैसे सेट करूँ?**  
A: रीजन सेट करें, बड़े ऑब्जेक्ट्स के लिए मल्टीपार्ट डाउनलोड सक्षम करें, क्रेडेंशियल प्रोवाइडर्स (जैसे `DefaultAWSCredentialsProviderChain`) उपयोग करें, और ऑब्जेक्ट को पूरी मेमोरी में लोड करने के बजाय स्ट्रीम करें।

**Q: क्या FTPS को साधारण FTP पर प्राथमिकता दी जानी चाहिए?**  
A: हाँ। FTPS प्रमुख प्रदर्शन हानि के बिना TLS एन्क्रिप्शन जोड़ता है और GroupDocs.Annotation द्वारा समर्थित है।

**Q: 200 MB PDFs को प्रोसेस करने के लिए अनुशंसित JVM हीप आकार क्या है?**  
A: कम से कम 1 GB, लेकिन स्ट्रीम‑आधारित लोडिंग उपयोग करने से आवश्यकता काफी घट सकती है।

**अंतिम अपडेट:** 2026-09-05  
**परीक्षित संस्करण:** GroupDocs.Annotation for Java 23.12 (latest stable)  
**लेखक:** GroupDocs  

**अतिरिक्त संसाधन**
- [GroupDocs.Annotation for Java दस्तावेज़ीकरण](https://docs.groupdocs.com/annotation/java/)  
- [GroupDocs.Annotation for Java API संदर्भ](https://reference.groupdocs.com/annotation/java/)  
- [GroupDocs.Annotation for Java डाउनलोड](https://releases.groupdocs.com/annotation/java/)  
- [GroupDocs.Annotation फ़ोरम](https://forum.groupdocs.com/c/annotation)  
- [नि:शुल्क समर्थन](https://forum.groupdocs.com/)  
- [अस्थायी लाइसेंस](https://purchase.groupdocs.com/temporary-license/)

## संबंधित ट्यूटोरियल
- [GroupDocs Java & Azure Blob का उपयोग करके एनोटेटेड PDF सहेजें](/annotation/java/document-loading/download-annotate-azure-blob-groupdocs-java/)
- [Java का उपयोग करके Amazon S3 से PDF को एनोटेट करने के लिए aws s3 getobject java कैसे उपयोग करें](/annotation/java/document-loading/annotate-documents-amazon-s3-java-groupdocs/)
- [GroupDocs.Annotation for Java के साथ PDF को कैसे एनोटेट करें](/annotation/java/annotation-management/annotations-groupdocs-annotation-java-tutorial/)