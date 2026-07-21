---
categories:
- Java Development
date: '2026-03-14'
description: GroupDocs.Annotation के साथ एनोटेटेड दस्तावेज़ों से विशिष्ट पृष्ठों को
  सहेजने के लिए जावा में try‑with‑resources का उपयोग करना सीखें। इसमें Spring Boot
  दस्तावेज़ सेवा का उदाहरण शामिल है।
keywords: save specific pages Java annotation, GroupDocs annotation page range, Java
  document annotation tutorial, selective PDF page saving Java, extract annotated
  pages
lastmod: '2026-03-14'
linktitle: Save Specific Pages Java Annotation
tags:
- groupdocs
- java-annotation
- document-processing
- pdf-manipulation
title: रिसोर्सेज़ जावा के साथ प्रयास – एनोटेटेड दस्तावेज़ों से विशिष्ट पृष्ठ सहेजें
type: docs
url: /hi/java/document-saving/groupdocs-annotation-java-save-specific-page-range/
weight: 1
---

# जावा में एनोटेटेड दस्तावेज़ों से विशिष्ट पृष्ठ कैसे सहेजें

## परिचय

क्या आप कभी बड़े एनोटेटेड दस्तावेज़ों में डूबते हुए महसूस करते हैं जबकि आपको केवल कुछ विशिष्ट पृष्ठों की जरूरत होती है? **try with resources java** के साथ, आप GroupDocs.Annotation का उपयोग करके केवल आवश्यक पृष्ठों को कुशलतापूर्वक निकाल सकते हैं। चाहे आप कानूनी अनुबंध, तकनीकी मैनुअल या शोध पत्रों को संभाल रहे हों, केवल प्रासंगिक पृष्ठों को निकालने से स्टोरेज बचता है, प्रोसेसिंग तेज़ होती है, और आपका कार्यप्रवाह व्यवस्थित रहता है।

इस गाइड में, हम आपको वह सब बताएँगे जो आपको जानना आवश्यक है – लाइब्रेरी सेटअप से लेकर उन्नत प्रदर्शन ट्रिक्स तक, जो आपके जावा एप्लिकेशन को सुचारू रूप से चलाते रहेंगे।

**अंत तक आप यह सीखेंगे:**
- अपने जावा प्रोजेक्ट में GroupDocs.Annotation को सही तरीके से सेटअप करना
- साफ़ और रखरखाव योग्य कोड के साथ चयनात्मक पृष्ठ सहेजना लागू करना
- अधिकांश डेवलपर्स को फँसाने वाले सामान्य जालों से बचना
- बड़े दस्तावेज़ प्रोसेसिंग के लिए प्रदर्शन को अनुकूलित करना
- समस्याओं को सिरदर्द बनने से पहले ही हल करना

## त्वरित उत्तर
- **“try with resources java” क्या करता है?** यह Annotator को स्वचालित रूप से बंद कर देता है, जिससे फ़ाइल लॉक और मेमोरी लीक नहीं होते।  
- **कौन सी लाइब्रेरी पृष्ठ‑रेंज सहेजने को संभालती है?** `GroupDocs.Annotation` `SaveOptions` के साथ `setFirstPage`/`setLastPage` प्रदान करती है।  
- **क्या मैं इसे Spring Boot सेवा में उपयोग कर सकता हूँ?** हाँ – “Spring Boot Document Service Integration” सेक्शन देखें।  
- **क्या मुझे लाइसेंस चाहिए?** विकास के लिए फ्री ट्रायल काम करता है; उत्पादन के लिए पूर्ण लाइसेंस आवश्यक है।  
- **क्या यह बड़े PDFs (1000+ पृष्ठ) के लिए सुरक्षित है?** मेमोरी उपयोग कम रखने के लिए `load‑only‑annotated‑pages` और बैच प्रोसेसिंग का उपयोग करें।

## विशिष्ट पृष्ठ क्यों सहेजें? (वास्तविक दुनिया का संदर्भ)

तकनीकी विवरण में कूदने से पहले, चलिए देखते हैं कि यह फीचर क्यों गेम‑चेंजर है:

**Storage Efficiency**: 500‑पृष्ठों की मैनुअल जिसमें केवल 20 पृष्ठों पर एनोटेशन हैं? सभी 500 पृष्ठों को सहेजने की बजाय आप केवल 20 प्रासंगिक पृष्ठ निकाल सकते हैं और फ़ाइल आकार को 96 % तक घटा सकते हैं।

**Faster Processing**: छोटी फ़ाइलें तेज़ अपलोड, डाउनलोड और प्रोसेसिंग देती हैं। आपके उपयोगकर्ता (और आपके सर्वर) आपका धन्यवाद करेंगे।

**Better User Experience**: सैकड़ों पृष्ठों को स्क्रॉल करके एनोटेटेड सेक्शन खोजने की ज़रूरत नहीं। उन्हें ठीक वही दें जिसकी उन्हें जरूरत है।

**Compliance and Security**: नियामक उद्योगों में आपको दस्तावेज़ के केवल विशिष्ट सेक्शन ही साझा करने की अनुमति हो सकती है। चयनात्मक सहेजना अनुपालन को आसान बनाता है।

## पूर्वापेक्षाएँ और सेटअप

### आपको क्या चाहिए

- **Java Development Kit (JDK)**: संस्करण 8 या उससे ऊपर (JDK 11+ अनुशंसित)  
- **Maven or Gradle**: निर्भरता प्रबंधन के लिए  
- **GroupDocs.Annotation for Java**: संस्करण 25.2 या बाद का  
- **Basic Java knowledge**: फ़ाइल I/O और OOP की समझ  

### GroupDocs.Annotation for Java सेटअप करना

#### Maven कॉन्फ़िगरेशन

`pom.xml` में यह जोड़ें (विश्वास करें, कॉपी‑पेस्ट आपका दोस्त है):

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

#### Gradle सेटअप (यदि आप Gradle टीम हैं)

```gradle
repositories {
    maven {
        url "https://releases.groupdocs.com/annotation/java/"
    }
}

dependencies {
    implementation 'com.groupdocs:groupdocs-annotation:25.2'
}
```

### लाइसेंस प्राप्त करना

यहाँ वह बात है जो अधिकांश ट्यूटोरियल नहीं बताते: **फ्री ट्रायल से शुरू करें**। सच में। चीज़ों को जटिल न बनाएं।

- **Free Trial**: परीक्षण और विकास के लिए परफेक्ट – इसे यहाँ से प्राप्त करें: [GroupDocs releases](https://releases.groupdocs.com/annotation/java/)  
- **Temporary License**: अधिक समय के मूल्यांकन की जरूरत? एक [temporary license](https://purchase.groupdocs.com/temporary-license/) प्राप्त करें  
- **Full License**: उत्पादन में जाने के लिए तैयार? [Purchase here](https://purchase.groupdocs.com/buy)

Pro tip: ट्रायल संस्करण में कुछ सीमाएँ हैं, लेकिन यह ट्यूटोरियल फॉलो करने और प्रूफ़‑ऑफ़‑कॉन्सेप्ट बनाने के लिए पर्याप्त है।

## चयनात्मक पृष्ठ सहेजने के लिए try with resources java का उपयोग

अब पर्यावरण तैयार है, देखते हैं कि **try with resources java** पृष्ठ‑रेंज ऑपरेशन को कैसे सुरक्षित और संक्षिप्त बनाता है। यह पैटर्न सुनिश्चित करता है कि `Annotator` इंस्टेंस स्वचालित रूप से डिस्पोज़ हो जाए, जिससे फ़ाइल‑लॉक की समस्याएँ समाप्त हो जाती हैं और मेमोरी उपयोग व्यवस्थित रहता है।

## मुख्य कार्यान्वयन: विशिष्ट पृष्ठ रेंज सहेजना

### बुनियादी तरीका (यहाँ से शुरू करें)

आइए सबसे सरल कार्यान्वयन से शुरू करें। यह 90 % उपयोग मामलों के लिए पर्याप्त है:

#### चरण 1: फ़ाइल पाथ प्रबंधन सेटअप करें

पहले, फ़ाइल पाथ को संभालने के लिए एक यूटिलिटी क्लास बनाएं (बाद में डायरेक्टरी बदलनी पड़े तो आपको धन्यवाद मिलेगा):

```java
import org.apache.commons.io.FilenameUtils;

public class FilePathConfiguration {
    public String getOutputFilePath(String inputFile) {
        return "YOUR_OUTPUT_DIRECTORY/SavingSpecificPageRange" + "." + FilenameUtils.getExtension(inputFile);
    }
}
```

**Why this approach?** यह आपके फ़ाइल‑पाथ लॉजिक को केंद्रीकृत रखता है और टेस्टिंग को आसान बनाता है। `FilenameUtils` का उपयोग करने से मूल फ़ाइल एक्सटेंशन स्वचालित रूप से संरक्षित रहता है।

#### चरण 2: पृष्ठ रेंज सहेजना लागू करें

यहाँ जादू होता है:

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.options.export.SaveOptions;

public class SaveSpecificPageRange {
    public void run(String inputFile) {
        String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
        
        try (final Annotator annotator = new Annotator(inputFile)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(2);  // Start from page 2
            saveOptions.setLastPage(4);   // End at page 4
            
            annotator.save(outputPath, saveOptions);
        }
    }
}
```

**What’s happening here:**
- हम एक **try‑with‑resources java** ब्लॉक (`try ( … )`) का उपयोग करते हैं ताकि `Annotator` स्वचालित रूप से बंद हो जाए, फ़ाइल‑लॉक समस्याएँ समाप्त हो जाएँ।  
- `setFirstPage(2)` और `setLastPage(4)` हमारी समावेशी रेंज (पृष्ठ 2‑4) को परिभाषित करते हैं।  
- रेंज दोनों सिरों पर **inclusive** है – यह विवरण कई डेवलपर्स को भ्रमित करता है।

### उन्नत फ़ाइल पाथ कॉन्फ़िगरेशन

उत्पादन एप्लिकेशन के लिए, आपको अधिक लचीला पाथ हैंडलिंग चाहिए होगा:

```java
public class FilePathConfiguration {
    private final String baseOutputDirectory;
    
    public FilePathConfiguration(String baseOutputDirectory) {
        this.baseOutputDirectory = baseOutputDirectory;
    }
    
    public String getInputFilePath(String filename) {
        return "YOUR_DOCUMENT_DIRECTORY/" + filename;
    }
    
    public String getOutputFilePath(String inputFile, String suffix) {
        String baseName = FilenameUtils.getBaseName(inputFile);
        String extension = FilenameUtils.getExtension(inputFile);
        return String.format("%s/%s_%s.%s", baseOutputDirectory, baseName, suffix, extension);
    }
}
```

अब आप `contract_pages_2-4.pdf` जैसे नाम स्वचालित रूप से जेनरेट कर सकते हैं।

## सामान्य जाल और उन्हें कैसे टालें

### जाल #1: पृष्ठ इंडेक्स भ्रम

**The Problem**: पृष्ठ संख्याएँ 0 से शुरू होने का मान लेना (GroupDocs.Annotation में ऐसा नहीं है)।

**The Solution**: पृष्ठ क्रमांक 1 से शुरू होते हैं, जैसे वास्तविक दस्तावेज़ों में। पृष्ठ 1 पहला पृष्ठ है, पृष्ठ 0 नहीं।

```java
// Wrong - this tries to start from page 0 (doesn't exist)
saveOptions.setFirstPage(0);

// Right - this starts from the actual first page
saveOptions.setFirstPage(1);
```

### जाल #2: संसाधन लीक

**The Problem**: Annotator को सही तरीके से बंद न करना, जिससे फ़ाइल लॉक और मेमोरी लीक हो जाती है।

**The Solution**: हमेशा **try‑with‑resources java** या स्पष्ट क्लोज़िंग का उपयोग करें:

```java
// Good - automatic resource management
try (final Annotator annotator = new Annotator(inputFile)) {
    // your code here
} // automatically closes

// Also acceptable - manual closing
Annotator annotator = null;
try {
    annotator = new Annotator(inputFile);
    // your code here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### जाल #3: अमान्य पृष्ठ रेंज

**The Problem**: दस्तावेज़ में मौजूद नहीं होने वाली पृष्ठ रेंज निर्दिष्ट करना।

**The Solution**: पहले अपनी रेंज को वैलिडेट करें:

```java
public void savePageRangeWithValidation(String inputFile, int firstPage, int lastPage) {
    try (final Annotator annotator = new Annotator(inputFile)) {
        // Get document info to check page count
        DocumentInfo documentInfo = annotator.getDocument().getDocumentInfo();
        int totalPages = documentInfo.getPageCount();
        
        // Validate range
        if (firstPage < 1 || firstPage > totalPages) {
            throw new IllegalArgumentException("First page out of range: " + firstPage);
        }
        if (lastPage < firstPage || lastPage > totalPages) {
            throw new IllegalArgumentException("Last page out of range: " + lastPage);
        }
        
        SaveOptions saveOptions = new SaveOptions();
        saveOptions.setFirstPage(firstPage);
        saveOptions.setLastPage(lastPage);
        
        String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
        annotator.save(outputPath, saveOptions);
    }
}
```

## प्रदर्शन अनुकूलन टिप्स

### बड़े दस्तावेज़ों के लिए मेमोरी प्रबंधन

जब बड़े दस्तावेज़ (100 + पृष्ठ) के साथ काम किया जाता है, मेमोरी उपयोग महत्वपूर्ण हो जाता है:

```java
public class OptimizedPageRangeSaver {
    public void saveWithOptimization(String inputFile, int firstPage, int lastPage) {
        // Configure for lower memory usage
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setLoadOnlyAnnotatedPages(true); // Only load pages with annotations
        
        try (final Annotator annotator = new Annotator(inputFile, loadOptions)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(firstPage);
            saveOptions.setLastPage(lastPage);
            
            // Optional: Enable compression for smaller output files
            saveOptions.setAnnotationsOnly(false); // Set to true if you only want annotations
            
            String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
            annotator.save(outputPath, saveOptions);
        }
    }
}
```

**Key optimization strategies**
- `setLoadOnlyAnnotatedPages(true)` मेमोरी फुटप्रिंट को कम करता है।  
- `setAnnotationsOnly(true)` एक हल्की फ़ाइल बनाता है जिसमें केवल एनोटेशन लेयर होती है।  
- यदि आपके पास कई फ़ाइलें हैं तो दस्तावेज़ों को बैच में प्रोसेस करें।

### कई दस्तावेज़ों की बैच प्रोसेसिंग

उत्पादन परिदृश्यों में जहाँ आप कई दस्तावेज़ प्रोसेस कर रहे हैं:

```java
public class BatchPageRangeSaver {
    public void processBatch(List<String> inputFiles, int firstPage, int lastPage) {
        for (String inputFile : inputFiles) {
            try {
                savePageRangeWithValidation(inputFile, firstPage, lastPage);
                System.out.println("Successfully processed: " + inputFile);
            } catch (Exception e) {
                System.err.println("Failed to process " + inputFile + ": " + e.getMessage());
                // Log the error and continue with next file
            }
        }
    }
}
```

## लोकप्रिय फ्रेमवर्क के साथ एकीकरण

### Spring Boot दस्तावेज़ सेवा एकीकरण

पृष्ठ‑रेंज सहेजने के लिए यहाँ एक सरल Spring Boot सेवा है (ध्यान दें **spring boot document service** शब्दावली):

```java
@Service
public class DocumentPageRangeService {
    
    @Value("${app.document.output-directory}")
    private String outputDirectory;
    
    public String savePageRange(String inputFile, int firstPage, int lastPage) {
        try (final Annotator annotator = new Annotator(inputFile)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(firstPage);
            saveOptions.setLastPage(lastPage);
            
            String outputPath = generateOutputPath(inputFile, firstPage, lastPage);
            annotator.save(outputPath, saveOptions);
            
            return outputPath;
        } catch (Exception e) {
            throw new DocumentProcessingException("Failed to save page range", e);
        }
    }
    
    private String generateOutputPath(String inputFile, int firstPage, int lastPage) {
        String baseName = FilenameUtils.getBaseName(inputFile);
        String extension = FilenameUtils.getExtension(inputFile);
        return String.format("%s/%s_pages_%d-%d.%s", 
                            outputDirectory, baseName, firstPage, lastPage, extension);
    }
}
```

## व्यावहारिक अनुप्रयोग और उपयोग केस

### कानूनी दस्तावेज़ प्रोसेसिंग

कानूनी फर्मों को अक्सर अनुबंध या कोर्ट दस्तावेज़ के विशिष्ट सेक्शन निकालने की जरूरत होती है:

```java
public class LegalDocumentProcessor {
    public void extractEvidencePages(String caseFile, List<Integer> evidencePages) {
        // Group consecutive pages for efficient processing
        List<PageRange> ranges = groupConsecutivePages(evidencePages);
        
        for (PageRange range : ranges) {
            String outputFile = String.format("evidence_%d_%d-to-%d.pdf", 
                                            getCaseNumber(caseFile), range.start, range.end);
            savePageRange(caseFile, range.start, range.end, outputFile);
        }
    }
}
```

### शैक्षिक सामग्री प्रबंधन

शिक्षकों को छात्रों के असाइनमेंट के लिए पाठ्यपुस्तकों के विशिष्ट अध्याय निकालने होते हैं:

```java
public class EducationalContentExtractor {
    public void createAssignmentPacket(String textbook, int chapterStart, int chapterEnd) {
        try (final Annotator annotator = new Annotator(textbook)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(chapterStart);
            saveOptions.setLastPage(chapterEnd);
            
            String assignmentFile = generateAssignmentFileName(textbook, chapterStart, chapterEnd);
            annotator.save(assignmentFile, saveOptions);
        }
    }
}
```

### क्वालिटी एश्योरेंस रिव्यूज़

समीक्षा टिप्पणियों वाले केवल पृष्ठों को निकालकर केंद्रित संशोधन किया जाता है:

```java
public class QAReviewExtractor {
    public void extractReviewedPages(String document) {
        try (final Annotator annotator = new Annotator(document)) {
            // Get pages with annotations
            List<Integer> annotatedPages = getAnnotatedPageNumbers(annotator);
            
            if (!annotatedPages.isEmpty()) {
                int firstPage = Collections.min(annotatedPages);
                int lastPage = Collections.max(annotatedPages);
                
                SaveOptions saveOptions = new SaveOptions();
                saveOptions.setFirstPage(firstPage);
                saveOptions.setLastPage(lastPage);
                
                String reviewFile = document.replace(".pdf", "_review_comments.pdf");
                annotator.save(reviewFile, saveOptions);
            }
        }
    }
}
```

## सर्वोत्तम प्रथाओं का सारांश

1. **Always validate input parameters** – प्रोसेसिंग से पहले पृष्ठ रेंज की जाँच करें।  
2. **Use try‑with‑resources java** – संसाधन लीक और फ़ाइल‑लॉक समस्याओं को रोकता है।  
3. **Implement proper error handling** – एक खराब फ़ाइल पूरी बैच को क्रैश न करने दें।  
4. **Consider memory usage** – बड़े दस्तावेज़ों के लिए `setLoadOnlyAnnotatedPages(true)` का उपयोग करें।  
5. **Test with various file types** – PDFs, Word, PowerPoint अलग‑अलग व्यवहार कर सकते हैं।  
6. **Monitor performance** – उत्पादन में प्रोसेसिंग समय और मेमोरी पर नज़र रखें।

## सामान्य समस्याओं का निवारण

### समस्या: “File is locked” त्रुटि

**Symptoms**: सहेजने की कोशिश पर एक्सेप्शन फेंका जाता है, जिसमें फ़ाइल लॉक का उल्लेख होता है।  

**Causes**:  
- पिछले ऑपरेशन से Annotator सही तरीके से बंद नहीं हुआ।  
- फ़ाइल किसी अन्य एप्लिकेशन में अभी भी खुली है।  
- अपर्याप्त अनुमतियाँ।  

**Solutions**:

```java
// Ensure proper cleanup
try (final Annotator annotator = new Annotator(inputFile)) {
    // ... your code ...
} // Automatically releases file handles

// Verify file accessibility before processing
File file = new File(inputFile);
if (!file.canRead()) {
    throw new IllegalArgumentException("Cannot read input file: " + inputFile);
}
if (!file.getParentFile().canWrite()) {
    throw new IllegalArgumentException("Cannot write to output directory");
}
```

### समस्या: मेमोरी समाप्ति त्रुटियाँ

**Symptoms**: बड़े दस्तावेज़ प्रोसेस करते समय `OutOfMemoryError` आता है।  

**Solutions**:  
1. JVM हीप साइज बढ़ाएँ, उदाहरण के लिए `-Xmx2g`।  
2. पहले दिखाए गए ऑप्टिमाइज़्ड लोडिंग विकल्पों का उपयोग करें।  
3. दस्तावेज़ों को छोटे बैच में प्रोसेस करें।

### समस्या: एनोटेशन नहीं बचे

**Symptoms**: आउटपुट फ़ाइल में मूल एनोटेशन नहीं होते।  

**Solution**: सुनिश्चित करें कि आप एनोटेशन को हट नहीं रहे हैं:

```java
SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationsOnly(false); // Keep both content and annotations
saveOptions.setFirstPage(firstPage);
saveOptions.setLastPage(lastPage);
```

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं गैर‑लगातार पृष्ठ (जैसे पृष्ठ 1, 3, 7) सहेज सकता हूँ?**  
A: एक ही ऑपरेशन में सीधे संभव नहीं है। आपको प्रत्येक रेंज के लिए अलग‑अलग सहेजना होगा या बाद में परिणामों को मिलाना पड़ेगा।

**Q: क्या यह पासवर्ड‑प्रोटेक्टेड दस्तावेज़ों के साथ काम करता है?**  
A: हाँ, लेकिन `Annotator` बनाते समय पासवर्ड देना होगा: `new Annotator(inputFile, loadOptions.setPassword("your_password"))`।

**Q: कौन‑से फ़ाइल फ़ॉर्मेट समर्थित हैं?**  
A: PDF, Microsoft Word, Excel, PowerPoint, और कई अन्य। पूरी सूची के लिए [official documentation](https://docs.groupdocs.com/annotation/java/) देखें।

**Q: क्या मैं मूल सामग्री के बिना केवल एनोटेशन सहेज सकता हूँ?**  
A: बिल्कुल – `saveOptions.setAnnotationsOnly(true)` सेट करके केवल एनोटेशन‑फ़ाइल बनाएं।

**Q: बहुत बड़े दस्तावेज़ (1000+ पृष्ठ) को कैसे संभालूँ?**  
A: `setLoadOnlyAnnotatedPages(true)` उपयोग करें, दस्तावेज़ को हिस्सों में प्रोसेस करें, और JVM हीप बढ़ाने पर विचार करें।

**Q: सहेजने से पहले पृष्ठों का प्रीव्यू करने का कोई तरीका है?**  
A: GroupDocs.Annotation मुख्यतः प्रोसेसिंग पर केंद्रित है, लेकिन आप दस्तावेज़ जानकारी (पृष्ठ गिनती, एनोटेशन लोकेशन) प्राप्त कर सकते हैं जिससे रेंज तय करने में मदद मिलती है।

## संसाधन

- **Documentation**: [GroupDocs.Annotation for Java Docs](https://docs.groupdocs.com/annotation/java/)  
- **API Reference**: [Complete API Documentation](https://reference.groupdocs.com/annotation/java/)  
- **Download**: [Latest Releases](https://releases.groupdocs.com/annotation/java/)  
- **Purchase**: [License Options](https://purchase.groupdocs.com/buy)  
- **Free Trial**: [Try It Now](https://releases.groupdocs.com/annotation/java/)  
- **Temporary License**: [Get Evaluation License](https://purchase.groupdocs.com/temporary-license/)  
- **Support**: [Community Forum](https://forum.groupdocs.com/c/annotation/)

---

**अंतिम अपडेट:** 2026-03-14  
**परीक्षित संस्करण:** GroupDocs.Annotation 25.2 (Java)  
**लेखक:** GroupDocs