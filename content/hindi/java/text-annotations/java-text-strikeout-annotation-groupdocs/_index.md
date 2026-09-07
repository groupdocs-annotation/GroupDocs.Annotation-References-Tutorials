---
categories:
- Java Development
date: '2026-03-30'
description: GroupDocs.Annotation का उपयोग करके जावा में स्ट्राइकआउट एनोटेशन कैसे
  जोड़ें, सीखें। कोड उदाहरणों, समस्या निवारण टिप्स और दस्तावेज़ मार्कअप के लिए सर्वोत्तम
  प्रथाओं के साथ चरण‑दर‑चरण मार्गदर्शिका।
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: GroupDocs के साथ स्ट्राइकआउट एनोटेशन जोड़ने का जावा ट्यूटोरियल
type: docs
url: /hi/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# स्ट्राइकआउट एनोटेशन जावा जोड़ें - पूर्ण GroupDocs गाइड

क्या आपने कभी दस्तावेज़ को देखते हुए सोचा है, “मुझे इस टेक्स्ट को स्ट्राइकआउट करना है, लेकिन मेरे पास लाल पेन नहीं है”? आप अकेले नहीं हैं। चाहे आप दस्तावेज़ समीक्षा प्रणाली बना रहे हों, संपादन वर्कफ़्लो बना रहे हों, या सिर्फ अपने जावा एप्लिकेशन में टेक्स्ट को हटाने के लिए मार्क करना चाहते हों, **add strikeout annotation java** एक आवश्यक कौशल है। इस ट्यूटोरियल में हम सब कुछ समझाएंगे जो आपको प्रोडक्शन में काम करने वाली टेक्स्ट स्ट्राइकआउट फ़ंक्शनैलिटी को लागू करने के लिए चाहिए।

## त्वरित उत्तर
- **Java में स्ट्राइकआउट एनोटेशन को सपोर्ट करने वाली लाइब्रेरी कौन सी है?** GroupDocs.Annotation for Java  
- **SEO के लिए मुझे कौन सा मुख्य कीवर्ड टार्गेट करना चाहिए?** add strikeout annotation java  
- **क्या सैंपल कोड चलाने के लिए मुझे लाइसेंस चाहिए?** विकास के लिए एक फ्री ट्रायल या टेम्पररी लाइसेंस काम करता है; प्रोडक्शन के लिए पूर्ण लाइसेंस आवश्यक है।  
- **क्या मैं इसे PDF, DOCX, और PPTX फ़ाइलों के साथ उपयोग कर सकता हूँ?** हाँ – GroupDocs.Annotation सभी प्रमुख दस्तावेज़ फ़ॉर्मैट्स को सपोर्ट करता है।  
- **कौन सा जावा संस्करण आवश्यक है?** JDK 8 या उससे ऊपर (JDK 11+ की सिफारिश)।

## add strikeout annotation java क्या है?
स्ट्राइकआउट एनोटेशन चयनित टेक्स्ट के ऊपर एक रेखा खींचता है, जिससे दृश्य रूप से संकेत मिलता है कि सामग्री को हटाया या अनदेखा किया जाना चाहिए। यह हटाने का सुझाव देने का एक गैर‑विनाशकारी तरीका है, जबकि मूल टेक्स्ट को ऑडिट ट्रेल या सहयोगी समीक्षाओं के लिए अपरिवर्तित रखा जाता है।

## जावा एप्लिकेशन्स में स्ट्राइकआउट एनोटेशन क्यों उपयोग करें?
- **दस्तावेज़ समीक्षा वर्कफ़्लो** – समीक्षक स्रोत को बदले बिना अनचाहे टेक्स्ट को फ़्लैग कर सकते हैं।  
- **सहयोगी संपादन** – टीम सदस्य तुरंत सुझाए गए हटाव देख सकते हैं।  
- **क़ानूनी और अनुपालन** – परिवर्तनों का स्पष्ट ऑडिट ट्रेल रखें।  
- **सामग्री माइग्रेशन** – सिस्टमों के बीच सामग्री स्थानांतरित करने से पहले पुरानी सेक्शन को मार्क करें।  

## पूर्वापेक्षाएँ और पर्यावरण सेटअप
कोड में डुबकी लगाने से पहले आपको निम्नलिखित की आवश्यकता होगी:

- **Java Development Kit (JDK)** 8+ (JDK 11+ की सिफारिश)  
- **Maven या Gradle** निर्भरता प्रबंधन के लिए  
- **IDE** – IntelliJ IDEA, Eclipse, या Java एक्सटेंशन के साथ VS Code  
- **GroupDocs.Annotation लाइब्रेरी** – हम उदाहरणों में संस्करण 25.2 का उपयोग करेंगे  

*उपयोगी:* जावा एनोटेशन और PDF हैंडलिंग का बुनियादी ज्ञान।

## जावा के लिए GroupDocs.Annotation सेटअप

### वास्तव में काम करने वाली Maven कॉन्फ़िगरेशन
अपने `pom.xml` में नीचे दिखाए अनुसार रिपॉजिटरी और डिपेंडेंसी जोड़ें:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/annotation/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-annotation</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

### अपना लाइसेंस व्यवस्थित करना
GroupDocs कई लाइसेंस विकल्प प्रदान करता है:

- **Free trial** – परीक्षण के लिए उत्तम (कोई क्रेडिट कार्ड आवश्यक नहीं)  
- **Temporary license** – विकास और स्टेजिंग के लिए आदर्श  
- **Full license** – प्रोडक्शन उपयोग के लिए आवश्यक; देखें [purchase page](https://purchase.groupdocs.com/buy)

> **Pro tip:** API का पता लगाने के लिए पहले फ्री ट्रायल से शुरू करें, फिर जब आप वास्तविक फीचर बनाने के लिए तैयार हों तो टेम्पररी लाइसेंस पर स्विच करें।

### त्वरित सत्यापन सेटअप
लाइब्रेरी सही ढंग से लोड होती है यह सत्यापित करने के लिए यह न्यूनतम प्रोग्राम चलाएँ:

```java
import com.groupdocs.annotation.Annotator;

public class DocumentSetup {
    public static void main(String[] args) {
        try {
            Annotator annotator = new Annotator("path/to/your/document.pdf");
            System.out.println("GroupDocs.Annotation is ready to use!");
            annotator.dispose();
        } catch (Exception e) {
            System.out.println("Setup issue: " + e.getMessage());
        }
    }
}
```

यदि कंसोल बिना त्रुटियों के सफलता संदेश प्रिंट करता है, तो आप स्ट्राइकआउट एनोटेशन जोड़ने के लिए तैयार हैं।

## स्ट्राइकआउट एनोटेशन जावा कैसे जोड़ें

नीचे एक पूर्ण, प्रोडक्शन‑तैयार इम्प्लीमेंटेशन स्पष्ट चरणों में विभाजित है।

### चरण 1 – Annotator को इनिशियलाइज़ करें
एक `Annotator` इंस्टेंस बनाएँ जो स्रोत दस्तावेज़ की ओर इशारा करता हो:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **क्यों महत्वपूर्ण है:** एक absolute या सही ढंग से रिजॉल्व्ड relative पाथ का उपयोग करने से “file not found” अपवादों से बचा जा सकता है।

### चरण 2 – (वैकल्पिक) टिप्पणी उत्तर तैयार करें
जवाब जोड़ने से एनोटेशन सहयोगी बनता है:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

जब उपयोगकर्ता स्ट्राइकआउट पर होवर करता है तो ये टिप्पणियाँ दिखाई देती हैं।

### चरण 3 – स्ट्राइकआउट क्षेत्र निर्धारित करें
उस आयत को निर्दिष्ट करें जो उस टेक्स्ट को घेरता है जिसे आप स्ट्राइकआउट करना चाहते हैं:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **कोऑर्डिनेट टिप:** मूल बिंदु (0,0) पेज का शीर्ष‑बायाँ कोना है; X दाएँ बढ़ता है, Y नीचे। इन मानों को फाइन‑ट्यून करने के लिए कोऑर्डिनेट दिखाने वाला PDF व्यूअर उपयोग करें।

### चरण 4 – स्ट्राइकआउट एनोटेशन कॉन्फ़िगर करें
दिखावट, पेज नंबर सेट करें, और टिप्पणियों को संलग्न करें:

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535);  // Yellow color
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0);
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

*रंग नोट:* `65535` पूर्णांक RGB फ़ॉर्मेट में पीला दर्शाता है। अन्य रंगों के लिए मान बदलें।

### चरण 5 – एनोटेशन लागू करें और सहेजें
एनोटेशन को दस्तावेज़ में जोड़ें और आउटपुट फ़ाइल लिखें:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### चरण 6 – संसाधनों को साफ़ करें (महत्वपूर्ण!)
नेटीव संसाधनों को मुक्त करने के लिए हमेशा annotator को डिस्पोज़ करें:

```java
if (annotator != null) {
    annotator.dispose();
}
```

प्रोडक्शन में, उपयोग को try‑with‑resources ब्लॉक या `try/finally` कंस्ट्रक्ट में रैप करें।

## सामान्य समस्याएँ और उनके समाधान

| समस्या | लक्षण | समाधान |
|---------|---------|-----|
| **फ़ाइल नहीं मिली** | `Annotator` एक अपवाद फेंकता है | एब्सोल्यूट पाथ का उपयोग करें, पढ़ने की अनुमति सत्यापित करें, सुनिश्चित करें कि कोई अन्य प्रक्रिया फ़ाइल को लॉक नहीं कर रही है |
| **गलत कोऑर्डिनेट्स** | स्ट्राइकआउट इच्छित टेक्स्ट से दूर दिखाई देता है | PDF व्यूअर के कोऑर्डिनेट सिस्टम को दोबारा जांचें; बिंदुओं को तदनुसार समायोजित करें |
| **एनोटेशन अदृश्य** | सहेजने के बाद कोई दृश्य स्ट्राइकआउट नहीं दिखता | `opacity` बढ़ाएँ (जैसे, `0.9`), `pageNumber` (0‑आधारित) सत्यापित करें, सुनिश्चित करें कि बिंदु एक सही आयत बनाते हैं |
| **OutOfMemoryError** | बड़ी PDFs पर एप्लिकेशन क्रैश हो जाता है | JVM हीप बढ़ाएँ (`-Xmx2048m`), दस्तावेज़ों को बैच में प्रोसेस करें, हमेशा `dispose()` कॉल करें |

## प्रोडक्शन के लिए प्रदर्शन सर्वोत्तम प्रथाएँ

### मेमोरी प्रबंधन
```java
// Good: try‑with‑resources (Java 7+)
try (Annotator annotator = new Annotator(documentPath)) {
    // annotation logic here
} // annotator automatically disposed

// Alternative: explicit disposal
Annotator annotator = null;
try {
    annotator = new Annotator(documentPath);
    // annotation logic here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### बैच प्रोसेसिंग रणनीति
जब आपको दर्जनों या सैकड़ों फ़ाइलों पर एनोटेशन करना हो:

- प्रति बैच 10‑20 दस्तावेज़ प्रोसेस करें।  
- प्रत्येक फ़ाइल के लिए सफलता/विफलता लॉग करें।  
- मेमोरी लीक से बचने के लिए प्रत्येक दस्तावेज़ के लिए `Annotator` को पुनः इनिशियलाइज़ करें।  

### कैशिंग टिप्स
- बार-बार उपयोग किए जाने वाले दस्तावेज़ टेम्पलेट्स को कैश करें।  
- मानक लेआउट्स के लिए पूर्व‑गणना किए गए कोऑर्डिनेट मैप्स संग्रहीत करें।  

## वास्तविक‑दुनिया उपयोग केस

1. **दस्तावेज़ समीक्षा सिस्टम** – संपादक मूल अनुबंध को बदले बिना हटाने का सुझाव देते हैं।  
2. **क़ानूनी संशोधन** – वकील ऑडिट के लिए मूल शब्दावली को संरक्षित रखते हुए क्लॉज़ हटाव को ट्रैक करते हैं।  
3. **शैक्षणिक पीयर रिव्यू** – समीक्षक हटाने के लिए सेक्शन मार्क करते हैं और इनलाइन टिप्पणी जोड़ते हैं।  
4. **सामग्री माइग्रेशन** – CMS माइग्रेशन के दौरान, स्ट्राइकआउट पुराने कॉपी को हाइलाइट करता है जिसे बदलने की आवश्यकता है।  

## उन्नत कस्टमाइज़ेशन

### कस्टम स्टाइलिंग
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### मेटाडाटा जोड़ना
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## ट्रबलशूटिंग चेकलिस्ट
- ✅ क्या आप स्रोत फ़ाइल मैन्युअली खोल सकते हैं?  
- ✅ क्या सभी GroupDocs डिपेंडेंसीज़ क्लासपाथ में मौजूद हैं?  
- ✅ क्या बिंदु एक वैध आयत बनाते हैं?  
- ✅ क्या पेज नंबर सही है (0‑आधारित)?  
- ✅ क्या पर्याप्त हीप मेमोरी है?  
- ✅ क्या आपके पास आउटपुट फ़ोल्डर के लिए लिखने की अनुमति है?  
- ✅ क्या दस्तावेज़ फ़ॉर्मैट समर्थित है (PDF, DOCX, PPTX, आदि)?  

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: क्या मैं Spring Boot सर्विस के अंदर GroupDocs.Annotation का उपयोग कर सकता हूँ?**  
**उत्तर:** हाँ। Maven डिपेंडेंसी जोड़ें, एक सर्विस क्लास इंजेक्ट करें जो `Annotator` बनाता है, और Spring के बीन स्कोप्स के साथ उसके लाइफ़साइकल को मैनेज करें।

**प्रश्न: कौन से दस्तावेज़ फ़ॉर्मैट स्ट्राइकआउट एनोटेशन को सपोर्ट करते हैं?**  
**उत्तर:** PDF, DOCX, PPTX, और कई अन्य फ़ॉर्मैट्स जो GroupDocs.Annotation सपोर्ट करता है। PDF सबसे सटीक कोऑर्डिनेट हैंडलिंग प्रदान करता है।

**प्रश्न: विभिन्न पेज साइज वाले दस्तावेज़ों को कैसे हैंडल करूँ?**  
**उत्तर:** `annotator.getPageInfo(pageNumber)` के माध्यम से पेज डाइमेंशन प्राप्त करें और अपने कोऑर्डिनेट्स को तदनुसार स्केल करें।

**प्रश्न: क्या मौजूदा स्ट्राइकआउट एनोटेशन को एडिट या डिलीट करना संभव है?**  
**उत्तर:** बिल्कुल। `annotator.getAnnotations(pageNumber)` से प्राप्त करें, फिर `annotator.update(updatedAnnotation)` या `annotator.delete(annotationId)` का उपयोग करें।

**प्रश्न: कई एनोटेशन जोड़ने का प्रदर्शन पर क्या प्रभाव पड़ता है?**  
**उत्तर:** सैकड़ों एनोटेशन जोड़ना सामान्यतः ठीक है, लेकिन मेमोरी उपयोग पर नजर रखें। बहुत बड़े एनोटेशन सेट्स के लिए, व्यू को पेजिनेट करने या आवश्यकता पर लेज़ी‑लोडिंग एनोटेशन पर विचार करें।

## निष्कर्ष
अब आपके पास GroupDocs.Annotation का उपयोग करके **add strikeout annotation java** के लिए एक पूर्ण, प्रोडक्शन‑तैयार गाइड है। सरल सत्यापन उदाहरण से शुरू करें, फिर बैच प्रोसेसिंग, कस्टम स्टाइलिंग, और मेटाडाटा एन्हांसमेंट तक स्केल करें। कोऑर्डिनेट्स को सावधानी से टेस्ट करना, संसाधनों का जिम्मेदारी से प्रबंधन करना, और अपने पर्यावरण के लिए सही लाइसेंस मॉडल चुनना याद रखें।

और अधिक खोजने के लिए तैयार हैं? अन्य एनोटेशन प्रकार—हाइलाइट, नोट, इमेज, एरो, और वॉटरमार्क—को देखें और एक पूर्ण‑फ़ीचर दस्तावेज़ सहयोग सूट बनाएं।

---

**Last Updated:** 2026-03-30  
**Tested With:** GroupDocs.Annotation 25.2 for Java  
**Author:** GroupDocs  

**अतिरिक्त संसाधन**

- [GroupDocs Annotation दस्तावेज़ीकरण](https://docs.groupdocs.com/annotation/java/)
- [API रेफ़रेंस गाइड](https://reference.groupdocs.com/annotation/java/)
- [नवीनतम संस्करण डाउनलोड करें](https://releases.groupdocs.com/annotation/java/)
- [पूर्ण लाइसेंस खरीदें](https://purchase.groupdocs.com/buy)
- [फ्री ट्रायल शुरू करें](https://releases.groupdocs.com/annotation/java/)
- [टेम्पररी लाइसेंस प्राप्त करें](https://purchase.groupdocs.com/temporary-license/)
- [कम्युनिटी सपोर्ट फ़ोरम](https://forum.groupdocs.com/c/annotation/)