---
categories:
- Java Development
date: '2026-01-05'
description: GroupDocs.Annotation Java API का उपयोग करके PDF को एनोटेशन के बिना कैसे
  सहेजें और PDF स्टिकी नोट्स को कैसे हटाएँ, सीखें। कोड उदाहरणों, लाइसेंसिंग टिप्स
  और ट्रबलशूटिंग के साथ चरण‑दर‑चरण ट्यूटोरियल।
keywords: save pdf without annotations, remove pdf sticky notes, PDF annotation removal
  API, GroupDocs annotation tutorial, Java PDF processing, delete annotations from
  PDF programmatically
lastmod: '2026-01-05'
linktitle: Save PDF Without Annotations Java
tags:
- pdf-processing
- groupdocs
- annotation-management
- java-api
title: जावा में एनोटेशन के बिना PDF कैसे सहेजें
type: docs
url: /hi/java/annotation-management/groupdocs-annotation-java-remove-pdf-annotations/
weight: 1
---

# जावा में एनोटेशन के बिना PDF कैसे सेव करें - पूर्ण डेवलपर गाइड

यदि आपको **PDF को एनोटेशन के बिना सेव करें** जल्दी और भरोसेमंद तरीके से करना है, तो आप सही जगह पर हैं। इस गाइड में हम जावा और GroupDocs.Annotation लाइब्रेरी का उपयोग करके PDF से स्टिकी नोट्स, हाइलाइट्स और कमेंट्स को हटाने के बारे में सब कुछ बताएँगे।

## त्वरित उत्तर
- **“PDF को एनोटेशन के बिना सेव करना” क्या मतलब है?** यह एक नई PDF कॉपी बनाता है जिसमें सभी एनोटेशन ऑब्जेक्ट्स नहीं होते।  
- **कौन सी लाइब्रेरी इसे संभालती है?** जावा के लिए GroupDocs.Annotation।  
- **क्या मुझे लाइसेंस चाहिए?** मूल्यांकन के लिए एक फ्री ट्रायल काम करता है; व्यावसायिक उपयोग के लिए प्रोडक्शन लाइसेंस आवश्यक है।  
- **क्या मैं कुछ एनोटेशन रख सकता हूँ?** हाँ – चयनात्मक हटाने के विकल्प उपयोग करें (देखें “Selective Annotation Removal”)।  
- **क्या यह बड़े PDF के लिए सुरक्षित है?** उचित JVM सेटिंग्स और बैच प्रोसेसिंग के साथ, यह अच्छी तरह स्केल करता है।

## PDF एनोटेशन हटाने का महत्व (और सही तरीका)

क्या आपने कभी ऐसा PDF खोला है जिसमें स्टिकी नोट्स, हाइलाइट्स और कमेंट्स की भरमार हो और आपको उन्हें हटाना पड़े? यदि आप जावा एप्लिकेशन में PDF के साथ काम कर रहे हैं, तो आपने संभवतः इस स्थिति का सामना किया होगा। चाहे आप डॉक्यूमेंट मैनेजमेंट सिस्टम बना रहे हों, या क्लाइंट को भेजने से पहले PDF को साफ़ करना चाहते हों।

हाथ से एनोटेशन हटाना थकाऊ और त्रुटिप्रवण होता है। लेकिन GroupDocs.Annotation जावा API के साथ, आप कुछ ही कोड लाइनों में सभी एनोटेशन प्रोग्रामेटिकली हटा सकते हैं। अब प्रत्येक टिप्पणी को मैन्युअली क्लिक करने की जरूरत नहीं!

इस गाइड में, हम जावा का उपयोग करके PDF एनोटेशन हटाने के बारे में सब कुछ बताएँगे। आप न केवल “कैसे” बल्कि “कब” और “क्यों” भी सीखेंगे – साथ ही कुछ ऐसी बातों को भी कवर करेंगे जो आपको रास्ते में अटक सकती हैं।

**आप अंत तक क्या सीखेंगे:**
- अपने जावा प्रोजेक्ट के लिए GroupDocs.Annotation सेटअप करना  
- PDF से सभी एनोटेशन को साफ़ तरीके से हटाने वाला कोड लिखना  
- विभिन्न एनोटेशन प्रकारों और एज केसों को संभालना  
- बड़े डॉक्यूमेंट्स के लिए प्रदर्शन को अनुकूलित करना  
- सामान्य समस्याओं का ट्रबलशूटिंग करना  

आइए शुरू करें और उन PDF को साफ़ करें!

## पूर्वापेक्षाएँ - शुरू करने से पहले आपको क्या चाहिए

कोड में कूदने से पहले, सुनिश्चित करें कि आपका वातावरण सही ढंग से सेट है:

**डेवलपमेंट एनवायरनमेंट:**
- जावा डेवलपमेंट किट (JDK) 8 या उससे ऊपर (बेहतर प्रदर्शन के लिए JDK 11+ की सलाह दी जाती है)  
- आपका पसंदीदा IDE – IntelliJ IDEA, Eclipse, या VS Code बहुत अच्छे काम करते हैं  
- डिपेंडेंसी मैनेजमेंट के लिए Maven या Gradle (हम Maven उदाहरणों का उपयोग करेंगे)

**ज्ञान की पूर्वापेक्षाएँ:**
- बेसिक जावा प्रोग्रामिंग स्किल्स (क्लास और मेथड्स के साथ सहज होना चाहिए)  
- जावा में फ़ाइल हैंडलिंग की परिचितता  
- PDF एनोटेशन क्या होते हैं (कमेंट्स, हाइलाइट्स, शैप्स आदि) की समझ

**GroupDocs.Annotation सेटअप:**
हम नीचे इंस्टॉलेशन विस्तार से कवर करेंगे, लेकिन सभी फीचर्स उपयोग करने के लिए आपको फ्री ट्रायल या वैध लाइसेंस चाहिए होगा।

यदि आप PDF के विशेषज्ञ नहीं हैं तो चिंता न करें – हम सब कुछ चरण‑दर‑चरण समझाएँगे!

## जावा के लिए GroupDocs.Annotation सेटअप करना

### Maven इंस्टॉलेशन (आसान तरीका)

Maven के साथ GroupDocs.Annotation को अपने प्रोजेक्ट में जोड़ना बहुत सरल है। अपने `pom.xml` में यह जोड़ें:

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

**Pro tip:** नया प्रोजेक्ट शुरू करते समय हमेशा नवीनतम संस्करण उपयोग करें। नवीनतम संस्करण संख्या के लिए [GroupDocs releases page](https://releases.groupdocs.com/annotation/java/) देखें।

### लाइसेंस को व्यवस्थित करना

बहुत से डेवलपर्स यहाँ अटक जाते हैं – लेकिन यह वास्तव में बहुत आसान है:

**Option 1: Free Trial** (टेस्टिंग के लिए परफेक्ट)  
- [GroupDocs Releases](https://releases.groupdocs.com/annotation/java/) से डाउनलोड करें  
- कोई क्रेडिट कार्ड आवश्यक नहीं  
- मूल्यांकन के लिए पूरी कार्यक्षमता  

**Option 2: Temporary License** (डेवलपमेंट के लिए)  
- [GroupDocs Purchase](https://purchase.groupdocs.com/temporary-license/) से प्राप्त करें  
- आमतौर पर कुछ ही मिनटों में जारी हो जाता है  
- प्रूफ़‑ऑफ़‑कॉन्सेप्ट प्रोजेक्ट्स के लिए बढ़िया  

**Option 3: Full License** (प्रोडक्शन के लिए)  
- [GroupDocs Purchase](https://purchase.groupdocs.com/buy) पर खरीदें  
- विभिन्न प्राइसिंग टियर्स उपलब्ध  
- सपोर्ट और अपडेट्स शामिल  

### बेसिक सेटअप और इनिशियलाइज़ेशन

डिपेंडेंसी सेट हो जाने के बाद, इनिशियलाइज़ेशन बहुत आसान है:

```java
import com.groupdocs.annotation.Annotator;

Annotator annotator = new Annotator("path/to/your/document.pdf");
```

बस इतना ही! आप एनोटेशन हटाने के लिए तैयार हैं। लेकिन मुख्य भाग में जाने से पहले, चलिए देखते हैं कि आप किन‑किन प्रकार के एनोटेशन का सामना कर सकते हैं।

## जावा में PDF स्टिकी नोट्स कैसे हटाएँ

सभी एनोटेशन समान नहीं होते। एक सामान्य PDF में आप ये पा सकते हैं:

- **Text annotations:** कमेंट्स, स्टिकी नोट्स, टेक्स्ट कॉलआउट्स  
- **Drawing annotations:** शैप्स, एरोज़, फ्रीहैंड ड्रॉइंग्स  
- **Highlight annotations:** टेक्स्ट हाइलाइटिंग, स्ट्राइकथ्रू, अंडरलाइन  
- **Stamp annotations:** “Approved”, “Confidential”, कस्टम स्टैम्प्स  
- **Link annotations:** डॉक्यूमेंट के भीतर हाइपरलिंक्स  

अच्छी खबर? GroupDocs.Annotation इन सभी को उसी सरल एप्रोच से संभाल सकता है जिसे हम अब दिखाने वाले हैं।

## चरण‑दर‑चरण गाइड: सभी PDF एनोटेशन हटाएँ

अब मुख्य भाग! जावा का उपयोग करके **PDF को एनोटेशन के बिना सेव करें** कैसे करें:

### चरण 1: अपने आउटपुट पाथ को सेट करें

सबसे पहले – तय करें कि साफ़ किया हुआ PDF कहाँ जाना चाहिए:

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/RemoveAnnotationFromDocument.pdf"; // Update with your path
```

**Best practice:** ऐसे फ़ाइलनाम उपयोग करें जो दर्शाते हों कि डॉक्यूमेंट साफ़ किया गया है। जैसे `document_clean.pdf` या `document_no_annotations.pdf` अच्छा रहेगा।

### चरण 2: Annotator को इनिशियलाइज़ करें

अपने एनोटेटेड PDF की ओर इशारा करने वाला `Annotator` ऑब्जेक्ट बनाएँ:

```java
final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/AnnotatedAreaReplies5.pdf");
```

**Common gotcha:** फ़ाइल पाथ सही है और फ़ाइल मौजूद है, यह सुनिश्चित करें। अगर फ़ाइल नहीं मिलेगी तो API एक्सेप्शन फेंकेगा।

### चरण 3: क्लीन आउटपुट के लिए SaveOptions कॉन्फ़िगर करें

यहीं पर जादू होता है। सभी एनोटेशन हटाने के लिए `SaveOptions` सेट करें:

```java
import com.groupdocs.annotation.options.export.SaveOptions;
import com.groupdocs.annotation.options.export.AnnotationType;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**What's happening here:** एनोटेशन टाइप को `NONE` सेट करके आप API को बता रहे हैं कि डॉक्यूमेंट को सेव करते समय सभी एनोटेशन को बाहर रखें। यह “सभी को छोड़कर सब कुछ सेव करो” जैसा है।

### चरण 4: अपना क्लीन डॉक्यूमेंट सेव करें

सब कुछ कॉन्फ़िगर हो जाने के बाद, एनोटेशन‑फ्री PDF को सेव करें:

```java
annotator.save(outputPath, saveOptions);
```

### चरण 5: रिसोर्सेज़ को क्लीन‑अप करें (महत्वपूर्ण!)

इस स्टेप को मत भूलें – यह मेमोरी लीक्स को रोकता है:

```java
annotator.dispose();
```

**Why this matters:** Annotator मेमोरी में रिसोर्सेज़ रखता है। यदि आप कई डॉक्यूमेंट प्रोसेस कर रहे हैं, तो सही ढंग से डिस्पोज़ न करने से मेमोरी इश्यू हो सकते हैं।

### पूरा कोड उदाहरण

आप नीचे दिया गया पूरा कोड ब्लॉक कॉपी‑पेस्ट कर सकते हैं:

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.options.export.SaveOptions;
import com.groupdocs.annotation.options.export.AnnotationType;

public class RemovePDFAnnotations {
    public static void main(String[] args) {
        String outputPath = "output/cleaned_document.pdf";
        
        final Annotator annotator = new Annotator("input/annotated_document.pdf");
        
        SaveOptions saveOptions = new SaveOptions();
        saveOptions.setAnnotationTypes(AnnotationType.NONE);
        
        annotator.save(outputPath, saveOptions);
        annotator.dispose();
        
        System.out.println("Annotations removed successfully! Clean document saved to: " + outputPath);
    }
}
```

## उन्नत कॉन्फ़िगरेशन विकल्प

### चयनात्मक एनोटेशन हटाना

यदि आप कुछ एनोटेशन रखना चाहते हैं और बाकी हटाना चाहते हैं, तो आप बाहर रखने वाले टाइप्स को निर्दिष्ट कर सकते हैं:

```java
SaveOptions saveOptions = new SaveOptions();
// Remove only text and highlight annotations, keep shapes and stamps
saveOptions.setAnnotationTypes(AnnotationType.TEXT | AnnotationType.HIGHLIGHT);
```

### कई डॉक्यूमेंट प्रोसेस करना

यदि आप कई PDF के साथ काम कर रहे हैं, तो यह पैटर्न अच्छी तरह काम करता है:

```java
String[] inputFiles = {"doc1.pdf", "doc2.pdf", "doc3.pdf"};

for (String inputFile : inputFiles) {
    String outputFile = inputFile.replace(".pdf", "_clean.pdf");
    
    try (Annotator annotator = new Annotator(inputFile)) {
        SaveOptions saveOptions = new SaveOptions();
        saveOptions.setAnnotationTypes(AnnotationType.NONE);
        annotator.save(outputFile, saveOptions);
    }
}
```

**Note:** `try‑with‑resources` स्टेटमेंट स्वचालित रूप से डिस्पोज़ को संभालता है।

## इस समाधान का उपयोग कब करें

PDF एनोटेशन हटाना हमेशा सही विकल्प नहीं होता। नीचे ऐसे परिदृश्य हैं जहाँ यह बिल्कुल उपयुक्त है:

**उत्कृष्ट उपयोग केस:**
- **Client deliverables:** क्लाइंट को डॉक्यूमेंट भेजने से पहले आंतरिक कमेंट्स हटाएँ  
- **Document archiving:** दीर्घकालिक स्टोरेज के लिए डॉक्यूमेंट्स को साफ़ करें  
- **Automated workflows:** डॉक्यूमेंट प्रोसेसिंग पाइपलाइन का हिस्सा बनाकर एनोटेशन हटाएँ  
- **Print preparation:** प्रिंट करने से पहले स्क्रीन‑केवल एनोटेशन हटाएँ  
- **Version control:** रिव्यू किए गए डॉक्यूमेंट्स के साफ़ “final” वर्ज़न बनाएँ  

**इन मामलों में दोबारा सोचें:**
- एनोटेशन में महत्वपूर्ण अप्रूवल जानकारी हो  
- आपको कानूनी रूप से ऑडिट ट्रेल बनाए रखने की आवश्यकता हो  
- एनोटेशन डॉक्यूमेंट की मूल सामग्री का हिस्सा हों  

## सामान्य समस्याओं का ट्रबलशूटिंग

### "File Not Found" एक्सेप्शन

**Problem:** आपका कोड `FileNotFoundException` फेंक रहा है  
**Solution:**  
- फ़ाइल पाथ दोबारा चेक करें (संदेह होने पर एब्सोल्यूट पाथ उपयोग करें)  
- सुनिश्चित करें कि फ़ाइल किसी अन्य एप्लिकेशन में खुली नहीं है  
- फ़ाइल परमिशन की जाँच करें  

### बड़े PDF में मेमोरी इश्यू

**Problem:** बड़े डॉक्यूमेंट प्रोसेस करते समय एप्लिकेशन मेमोरी खत्म हो जाता है  
**Solution:**  
```java
// Increase JVM heap size when starting your application
// java -Xmx2g YourApplication
```

### लाइसेंस‑संबंधी एरर्स

**Problem:** इवैल्यूएशन वाटरमार्क या लाइसेंस एरर मिल रहे हैं  
**Solution:**  
- लाइसेंस फ़ाइल सही लोकेशन पर है, यह सत्यापित करें  
- लाइसेंस की समाप्ति तिथि देखें  
- सही लाइसेंस टाइप (डेवलपमेंट बनाम प्रोडक्शन) उपयोग कर रहे हैं, यह सुनिश्चित करें  

### खाली आउटपुट फ़ाइलें

**Problem:** आउटपुट PDF बनता है लेकिन खाली या करप्ट दिखता है  
**Solution:**  
- जांचें कि इनपुट PDF पासवर्ड‑प्रोटेक्टेड तो नहीं है  
- इनपुट फ़ाइल करप्ट नहीं है, यह पुष्टि करें  
- समस्या को अलग करने के लिए किसी अन्य PDF के साथ टेस्ट करें  

## प्रदर्शन अनुकूलन टिप्स

### मेमोरी मैनेजमेंट बेस्ट प्रैक्टिसेज

बड़े डॉक्यूमेंट या कई फ़ाइलों को प्रोसेस करते समय:

```java
// Set appropriate JVM parameters
// -Xms512m -Xmx2g -XX:+UseG1GC

// Use try‑with‑resources for automatic cleanup
try (Annotator annotator = new Annotator(inputPath)) {
    // Your processing code here
}
```

### बैच प्रोसेसिंग ऑप्टिमाइज़ेशन

कई डॉक्यूमेंट के लिए, उन्हें बैच में प्रोसेस करें:

```java
private static void processDocumentBatch(List<String> filePaths, int batchSize) {
    for (int i = 0; i < filePaths.size(); i += batchSize) {
        int endIndex = Math.min(i + batchSize, filePaths.size());
        List<String> batch = filePaths.subList(i, endIndex);
        
        // Process this batch
        for (String filePath : batch) {
            processDocument(filePath);
        }
        
        // Optional: Force garbage collection between batches
        System.gc();
    }
}
```

### प्रदर्शन मॉनिटरिंग

सरल लॉगिंग के साथ प्रदर्शन पर नज़र रखें:

```java
long startTime = System.currentTimeMillis();

// Your annotation removal code here

long endTime = System.currentTimeMillis();
System.out.println("Processing completed in " + (endTime - startTime) + "ms");
```

## वास्तविक दुनिया के इंटीग्रेशन उदाहरण

### Spring Boot सर्विस

Spring Boot एप्लिकेशन में इसे कैसे इंटीग्रेट किया जा सकता है:

```java
@Service
public class PDFCleaningService {
    
    public String removeAnnotations(MultipartFile inputFile) throws IOException {
        String tempInputPath = saveTempFile(inputFile);
        String outputPath = generateOutputPath(inputFile.getOriginalFilename());
        
        try (Annotator annotator = new Annotator(tempInputPath)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setAnnotationTypes(AnnotationType.NONE);
            annotator.save(outputPath, saveOptions);
        }
        
        // Clean up temp file
        Files.deleteIfExists(Paths.get(tempInputPath));
        
        return outputPath;
    }
}
```

### RESTful API एंडपॉइंट

```java
@RestController
@RequestMapping("/api/pdf")
public class PDFProcessingController {
    
    @PostMapping("/remove-annotations")
    public ResponseEntity<byte[]> removeAnnotations(@RequestParam("file") MultipartFile file) {
        // Implementation using the code patterns shown above
        // Return cleaned PDF as byte array
    }
}
```

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं ID या author के आधार पर विशिष्ट एनोटेशन हटा सकता हूँ?**  
A: GroupDocs.Annotation API मुख्यतः टाइप के आधार पर एनोटेशन हटाने पर फोकस करता है, न कि व्यक्तिगत IDs पर। अधिक ग्रैन्युलर कंट्रोल के लिए आपको एनोटेशन कलेक्शन को सीधे हैंडल करना पड़ेगा।

**Q: एनोटेशन हटाने पर फॉर्म फ़ील्ड्स का क्या होता है?**  
A: फॉर्म फ़ील्ड्स आमतौर पर संरक्षित रहते हैं क्योंकि उन्हें पारंपरिक अर्थ में एनोटेशन नहीं माना जाता। हालांकि, यदि आपके पास एनोटेशन‑आधारित फॉर्म फ़ील्ड्स हैं, तो वे प्रभावित हो सकते हैं।

**Q: क्या हटाए जाने वाले एनोटेशन की प्रीव्यू देखना संभव है?**  
A: हाँ! आप `get()` मेथड का उपयोग करके पहले सभी एनोटेशन प्राप्त कर सकते हैं, फिर तय कर सकते हैं कि हटाना है या नहीं।

**Q: क्या यह पासवर्ड‑प्रोटेक्टेड PDF के साथ काम कर सकता है?**  
A: आपको Annotator इनिशियलाइज़ करते समय पासवर्ड प्रदान करना होगा:  
```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("your-password");
Annotator annotator = new Annotator("document.pdf", loadOptions);
```

**Q: मिश्रित एनोटेशन टाइप वाले PDF को कैसे हैंडल करें?**  
A: `AnnotationType.NONE` सेटिंग सभी टाइप्स को हटाता है। यदि आप चयनात्मक हटाना चाहते हैं, तो बिटवाइज़ ऑपरेशन्स का उपयोग करके उन टाइप्स को संयोजित करें जिन्हें आप बाहर रखना चाहते हैं।

**Q: प्रोसेसिंग के लिए फ़ाइल आकार की सीमा क्या है?**  
A: कोई हार्ड लिमिट नहीं है, लेकिन प्रदर्शन उपलब्ध मेमोरी पर निर्भर करता है। बहुत बड़े फ़ाइलों (100 MB+) के लिए JVM हीप साइज बढ़ाने औरच प्रोसेसिंग पर विचार करें।

## निष्कर्ष

जावा के साथ PDF एनोटेशन हटाना जटिल नहीं होना चाहिए। GroupDocs.Annotation के साथ आप कुछ ही कोड लाइनों में अपने डॉक्यूमेंट्स को साफ़ कर सकते हैं। याद रखने योग्य मुख्य बिंदु:

- मेमोरी लीक्स से बचने के लिए हमेशा Annotator ऑब्जेक्ट्स को डिस्पोज़ करें  
- बड़े डॉक्यूमेंट्स के लिए उचित JVM सेटिंग्स उपयोग करें  
- विभिन्न PDF प्रकारों के साथ टेस्ट करके कम्पैटिबिलिटी सुनिश्चित करें  
- अपने उपयोग केस को ध्यान में रखें – कभी‑कभी एनोटेशन को संरक्षित रखना बेहतर होता है!  

क्या आप इसे अपने प्रोजेक्ट में लागू करने के लिए तैयार हैं? फ्री ट्रायल से शुरू करें और विभिन्न डॉक्यूमेंट टाइप्स के साथ प्रयोग करें। GroupDocs.Annotation API शक्तिशाली और लचीला है – PDF प्रोसेसिंग वर्कफ़्लो को ऑटोमेट करने के लिए एकदम उपयुक्त।

**अगले कदम:**
- नवीनतम संस्करण डाउनलोड करें और अपने स्वयं के PDF के साथ आज़माएँ  
- उन्नत फीचर्स के लिए [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) देखें  
- यदि मदद चाहिए तो [GroupDocs community forum](https://forum.groupdocs.com/c/annotation/) में जुड़ें  

---

**Last Updated:** 2026-01-05  
**Tested With:** GroupDocs.Annotation 25.2  
**Author:** GroupDocs  

--- 

## अतिरिक्त संसाधन

- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/)  
- [Complete API Reference](https://reference.groupdocs.com/annotation/java/)  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/)  
- [Purchase License](https://purchase.groupdocs.com/buy)  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/)  
- [Get Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [Community Support Forum](https://forum.groupdocs.com/c/annotation/)