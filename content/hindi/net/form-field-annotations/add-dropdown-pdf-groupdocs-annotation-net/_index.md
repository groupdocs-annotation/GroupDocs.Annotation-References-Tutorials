---
"date": "2025-05-06"
"description": ".NET के लिए GroupDocs.Annotation का उपयोग करके इंटरैक्टिव ड्रॉपडाउन घटकों को जोड़कर अपने PDF दस्तावेज़ों को बेहतर बनाने का तरीका जानें। उपयोगकर्ता इनपुट को सुव्यवस्थित करने और दस्तावेज़ की कार्यक्षमता में सुधार करने के लिए इस चरण-दर-चरण मार्गदर्शिका का पालन करें।"
"title": "GroupDocs के साथ PDF में ड्रॉपडाउन जोड़ें. .NET के लिए एनोटेशन एक व्यापक गाइड"
"url": "/hi/net/form-field-annotations/add-dropdown-pdf-groupdocs-annotation-net/"
"weight": 1
---

# .NET के लिए GroupDocs.Annotation का उपयोग करके PDF दस्तावेज़ में ड्रॉपडाउन घटक कैसे जोड़ें

## परिचय

ड्रॉपडाउन जैसे इंटरैक्टिव तत्वों को एकीकृत करके अपने PDF दस्तावेज़ों को बेहतर बनाएँ, जिससे उपयोगकर्ता दस्तावेज़ के भीतर सीधे विकल्प चुन सकें। यह ट्यूटोरियल आपको ड्रॉपडाउन घटकों को कुशलतापूर्वक जोड़ने के लिए GroupDocs.Annotation for .NET का उपयोग करने के बारे में मार्गदर्शन करता है।

**आप क्या सीखेंगे:**
- .NET के लिए GroupDocs.Annotation की स्थापना और उपयोग करना
- पीडीएफ दस्तावेजों में ड्रॉपडाउन घटकों को क्रियान्वित करना
- विकल्प, स्थिति और एनोटेशन जैसे गुणों को कॉन्फ़िगर करना

आइये सबसे पहले यह सुनिश्चित करें कि आपका वातावरण तैयार है!

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित सेटअप है:

### आवश्यक लाइब्रेरी और संस्करण:
- **.NET के लिए ग्रुपडॉक्स.एनोटेशन**: पीडीएफ दस्तावेजों में एनोटेशन जोड़ने के लिए आवश्यक।

### पर्यावरण सेटअप आवश्यकताएँ:
- आपके विकास मशीन पर Visual Studio स्थापित है।
- C# प्रोग्रामिंग भाषा का बुनियादी ज्ञान और .NET अनुप्रयोगों से परिचित होना।

## .NET के लिए GroupDocs.Annotation सेट अप करना

आरंभ करने के लिए, GroupDocs.Annotation लाइब्रेरी स्थापित करें। स्थापना निर्देश यहां दिए गए हैं:

**NuGet पैकेज मैनेजर कंसोल**
```bash
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET सीएलआई**
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### लाइसेंस प्राप्ति चरण

GroupDocs.Annotation के लिए लाइसेंस कई तरीकों से प्राप्त करें:
- **मुफ्त परीक्षण**लाइब्रेरी की विशेषताओं का पता लगाने के लिए परीक्षण संस्करण डाउनलोड करें।
- **अस्थायी लाइसेंस**विस्तारित परीक्षण के लिए अस्थायी लाइसेंस प्राप्त करें।
- **खरीदना**: उत्पादन उपयोग के लिए पूर्ण लाइसेंस खरीदें।

### C# के साथ बुनियादी आरंभीकरण और सेटअप

यहां बताया गया है कि आप GroupDocs.Annotation को कैसे आरंभ कर सकते हैं:

```csharp
using GroupDocs.Annotation;

// अपने PDF दस्तावेज़ के पथ के साथ एक एनोटेटर ऑब्जेक्ट को आरंभ करें।
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

## कार्यान्वयन मार्गदर्शिका

### अपने PDF में ड्रॉपडाउन घटक जोड़ना

#### अवलोकन
इस अनुभाग में, हम पूर्वनिर्धारित विकल्पों के साथ एक ड्रॉपडाउन घटक जोड़ेंगे। यह सुविधा उपयोगकर्ताओं को ड्रॉपडाउन मेनू से कोई विकल्प चुनकर बातचीत करने की अनुमति देती है।

#### चरण-दर-चरण कार्यान्वयन

**चरण 1: एनोटेटर आरंभ करें**

सबसे पहले, इसका एक उदाहरण बनाएं `Annotator` अपने इनपुट पीडीएफ दस्तावेज़ पथ का उपयोग करके क्लास:

```csharp
using GroupDocs.Annotation;
using System;

string inputPdfPath = "YOUR_DOCUMENT_DIRECTORY/input.pdf";
string outputPath = Path.Combine("YOUR_OUTPUT_DIRECTORY/result.pdf");
```

**चरण 2: ड्रॉपडाउन घटक बनाएँ**

अब, आइए कस्टम विकल्पों के साथ एक ड्रॉपडाउन घटक बनाएं:

```csharp
// नया ड्रॉपडाउन घटक बनाएं
DropdownComponent dropdown = new DropdownComponent
{
    // ड्रॉपडाउन में दिखाई देने वाले विकल्पों को परिभाषित करें
    Options = new List<string> { "Item1", "Item2", "Item3" },
    
    // चयनित विकल्प को प्रारंभ में शून्य ही रहने दें
    SelectedOption = null,
    
    // प्लेसहोल्डर टेक्स्ट जोड़ें
    Placeholder = "Choose option",
    
    // ड्रॉपडाउन की स्थिति और आकार सेट करें (X, Y, चौड़ाई, ऊंचाई)
    Box = new Rectangle(100, 100, 100, 100),
    
    // निर्माण टाइमस्टैम्प सेट करें
    CreatedOn = DateTime.Now,
    
    // ड्रॉपडाउन के लिए संदेश/टूलटिप जोड़ें
    Message = "This is dropdown component",
    
    // पृष्ठ संख्या निर्धारित करें (0-आधारित अनुक्रमणिका)
    PageNumber = 0,
    
    // पेन का रंग सेट करें (65535 RGB में नीले रंग का प्रतिनिधित्व करता है)
    PenColor = 65535,
    
    // पेन शैली सेट करें
    PenStyle = PenStyle.Dot,
    
    // पेन की चौड़ाई निर्धारित करें
    PenWidth = 3
};
```

**चरण 3: ड्रॉपडाउन में टिप्पणियाँ जोड़ें (वैकल्पिक)**

आप ड्रॉपडाउन घटक में उत्तर या टिप्पणियाँ जोड़ सकते हैं:

```csharp
// ड्रॉपडाउन में उत्तर/टिप्पणियाँ जोड़ें
dropdown.Replies = new List<Reply>
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
};
```

**चरण 4: दस्तावेज़ में ड्रॉपडाउन जोड़ें और सहेजें**

अंत में, ड्रॉपडाउन को दस्तावेज़ में जोड़ें और उसे सहेजें:

```csharp
// दस्तावेज़ में ड्रॉपडाउन घटक जोड़ें
annotator.Add(dropdown);

// जोड़े गए ड्रॉपडाउन के साथ दस्तावेज़ को सहेजें
annotator.Save(outputPath);
```

### पूर्ण कार्यान्वयन उदाहरण

पीडीएफ दस्तावेज़ में ड्रॉपडाउन घटक जोड़ने के लिए पूरा कोड यहां दिया गया है:

```csharp
using System;
using System.IO;
using System.Collections.Generic;
using GroupDocs.Annotation;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;

namespace GroupDocs.Annotation.Examples
{
    class AddDropdownComponentExample
    {
        public static void Run()
        {
            Console.WriteLine("Adding dropdown component to a PDF document...");
            
            // इनपुट और आउटपुट पथ परिभाषित करें
            string inputPath = "YOUR_DOCUMENT_DIRECTORY/input.pdf";
            string outputPath = "YOUR_OUTPUT_DIRECTORY/output-with-dropdown.pdf";
            
            // इनपुट दस्तावेज़ के साथ एनोटेटर को आरंभ करें
            using (Annotator annotator = new Annotator(inputPath))
            {
                // ड्रॉपडाउन घटक बनाएँ
                DropdownComponent dropdown = new DropdownComponent
                {
                    // ड्रॉपडाउन विकल्प परिभाषित करें
                    Options = new List<string> { "Option 1", "Option 2", "Option 3", "Option 4" },
                    SelectedOption = null,
                    Placeholder = "Select an option...",
                    
                    // स्थिति और आकार
                    Box = new Rectangle(100, 100, 150, 30),
                    
                    // मेटाडाटा
                    CreatedOn = DateTime.Now,
                    Message = "Please select one option from the dropdown",
                    PageNumber = 0,
                    
                    // स्टाइल
                    PenColor = 65535,  // नीला रंग
                    PenStyle = PenStyle.Solid,
                    PenWidth = 2,
                    
                    // वैकल्पिक टिप्पणियाँ
                    Replies = new List<Reply>
                    {
                        new Reply
                        {
                            Comment = "This dropdown is for demonstration purposes",
                            RepliedOn = DateTime.Now
                        }
                    }
                };
                
                // दस्तावेज़ में ड्रॉपडाउन जोड़ें
                annotator.Add(dropdown);
                
                // एनोटेट किए गए दस्तावेज़ को सहेजें
                annotator.Save(outputPath);
                
                Console.WriteLine($"Dropdown component added successfully.\nCheck the output file at: {outputPath}");
            }
        }
    }
}
```

## अपने ड्रॉपडाउन घटक को अनुकूलित करना

### स्थिति और आकार

आप ड्रॉपडाउन की स्थिति और आकार को संशोधित करके समायोजित कर सकते हैं `Box` संपत्ति:

```csharp
// निर्देशांक (200, 150) पर स्थिति, चौड़ाई 200 और ऊंचाई 40
dropdown.Box = new Rectangle(200, 150, 200, 40);
```

### स्टाइलिंग विकल्प

इन गुणों के साथ अपने ड्रॉपडाउन के स्वरूप को अनुकूलित करें:

```csharp
// पेन का रंग लाल (RGB मान) में बदलें
dropdown.PenColor = 16711680; // RGB में लाल

// पेन की शैली बदलें
dropdown.PenStyle = PenStyle.Solid; // विकल्प: सॉलिड, डैश, डॉट, डैशडॉट, आदि।

// पेन की चौड़ाई समायोजित करें
dropdown.PenWidth = 2;
```

### गतिशील ड्रॉपडाउन विकल्प

आप डेटा स्रोत से गतिशील रूप से ड्रॉपडाउन विकल्प भर सकते हैं:

```csharp
// उदाहरण: डेटाबेस या API से विकल्प लोड करना
List<string> dynamicOptions = GetOptionsFromDataSource();
dropdown.Options = dynamicOptions;

// उदाहरण सहायक विधि (कार्यान्वयन भिन्न होगा)
private static List<string> GetOptionsFromDataSource()
{
    // वास्तविक अनुप्रयोग में, यह डेटाबेस से आ सकता है
    return new List<string> { "Value 1", "Value 2", "Value 3" };
}
```

## व्यावहारिक अनुप्रयोगों

### फॉर्म स्वचालन

ड्रॉपडाउन घटकों का उपयोग करके इंटरैक्टिव पीडीएफ फॉर्म बनाएं जो उपयोगकर्ताओं से संरचित डेटा एकत्र करते हैं, जो अनुप्रयोगों, सर्वेक्षणों और प्रश्नावली के लिए आदर्श हैं।

### आंकड़ा मान्यीकरण

उपयोगकर्ता इनपुट को पूर्वनिर्धारित विकल्पों तक सीमित करने के लिए ड्रॉपडाउन को लागू करें, जिससे डेटा की एकरूपता सुनिश्चित हो और फॉर्म सबमिशन में त्रुटियां कम हों।

### इंटरैक्टिव दस्तावेज़ीकरण

तकनीकी दस्तावेज़ीकरण को ऐसे इंटरैक्टिव तत्वों को जोड़कर बेहतर बनाएं जो उपयोगकर्ताओं को दस्तावेज़ के भीतर सीधे कॉन्फ़िगरेशन या विकल्प चुनने की अनुमति देते हैं।

### वर्कफ़्लो प्रबंधन

दस्तावेज़ अनुमोदन वर्कफ़्लो बनाएं जहां समीक्षक सीधे पीडीएफ में स्थिति विकल्प (जैसे, "स्वीकृत," "संशोधन की आवश्यकता है," "अस्वीकृत") का चयन कर सकते हैं।

### शिक्षण सामग्री

इंटरैक्टिव शिक्षण सामग्री विकसित करें जहां छात्र दस्तावेज़ में सन्निहित बहुविकल्पीय प्रश्नों के उत्तर दे सकें।

## प्रदर्शन संबंधी विचार

### स्मृति प्रबंधन

बड़े PDF दस्तावेज़ों के साथ काम करते समय या एकाधिक ड्रॉपडाउन घटक जोड़ते समय:

```csharp
// संसाधनों का उचित निपटान सुनिश्चित करें
using (Annotator annotator = new Annotator(inputPath))
{
    // अनेक ड्रॉपडाउन जोड़ें
    for (int i = 0; i < numberOfDropdowns; i++)
    {
        // ड्रॉपडाउन बनाएं और जोड़ें
        DropdownComponent dropdown = CreateDropdown(i);
        annotator.Add(dropdown);
    }
    
    annotator.Save(outputPath);
} // यहां संसाधनों का उचित ढंग से निपटान किया जाता है
```

### बड़े दस्तावेज़ों का प्रसंस्करण

बड़े दस्तावेज़ों के साथ बेहतर प्रदर्शन के लिए:

```csharp
// मेमोरी उपयोग को अनुकूलित करने के लिए लोड विकल्पों का उपयोग करें
LoadOptions loadOptions = new LoadOptions
{
    // बड़े दस्तावेज़ों के लिए विशिष्ट विकल्प सेट करें
};

using (Annotator annotator = new Annotator(inputPath, loadOptions))
{
    // अपने ड्रॉपडाउन घटक जोड़ें
    // ...
}
```

## निष्कर्ष

.NET के लिए GroupDocs.Annotation का उपयोग करके PDF दस्तावेज़ों में ड्रॉपडाउन घटक जोड़ने से अन्तरक्रियाशीलता और कार्यक्षमता में उल्लेखनीय वृद्धि होती है। इस ट्यूटोरियल ने आपको दिखाया है कि अपने PDF में ड्रॉपडाउन फ़ील्ड कैसे बनाएँ, कस्टमाइज़ करें और लागू करें, जिससे फ़ॉर्म ऑटोमेशन, डेटा संग्रह और इंटरैक्टिव दस्तावेज़ अनुभवों की संभावनाएँ खुलती हैं।

GroupDocs.Annotation की शक्तिशाली सुविधाओं का लाभ उठाकर, आप स्थिर PDF को गतिशील, इंटरैक्टिव दस्तावेज़ों में बदल सकते हैं जो उपयोगकर्ताओं से संरचित डेटा एकत्र करते हैं। जैसे-जैसे आप लाइब्रेरी का पता लगाना जारी रखेंगे, आपको अपने दस्तावेज़ वर्कफ़्लो और उपयोगकर्ता अनुभव को बेहतर बनाने के और भी तरीके मिलेंगे।

चाहे आप फॉर्म, सर्वेक्षण या इंटरैक्टिव दस्तावेज बना रहे हों, ड्रॉपडाउन घटक सीधे पीडीएफ दस्तावेजों के भीतर संरचित इनपुट एकत्र करने का एक उपयोगकर्ता-अनुकूल तरीका प्रदान करता है।

## अक्सर पूछे जाने वाले प्रश्न अनुभाग

### क्या मैं ड्रॉपडाउन के लिए डिफ़ॉल्ट चयनित विकल्प सेट कर सकता हूँ?

हां, आप एक मान निर्दिष्ट करके एक डिफ़ॉल्ट विकल्प सेट कर सकते हैं `SelectedOption` संपत्ति:

```csharp
dropdown.Options = new List<string> { "Option 1", "Option 2", "Option 3" };
dropdown.SelectedOption = "Option 2"; // डिफ़ॉल्ट चयन सेट करता है
```

### मैं सबमिट किए गए फॉर्म में ड्रॉपडाउन से चयनित मान कैसे प्राप्त करूं?

चयनित मान को पुनः प्राप्त करने के लिए, आप GroupDocs.Annotation पार्सर कार्यक्षमता का उपयोग करेंगे:

```csharp
using (Annotator annotator = new Annotator("submitted-form.pdf"))
{
    // ड्रॉपडाउन सहित सभी एनोटेशन प्राप्त करें
    List<AnnotationBase> annotations = annotator.Get();
    
    // ड्रॉपडाउन घटक खोजें
    foreach (var annotation in annotations)
    {
        if (annotation is DropdownComponent dropdown)
        {
            Console.WriteLine($"Selected value: {dropdown.SelectedOption}");
        }
    }
}
```

### क्या मैं PDF के अलावा अन्य दस्तावेज़ों में ड्रॉपडाउन घटक जोड़ सकता हूँ?

GroupDocs.Annotation मुख्य रूप से PDF दस्तावेज़ों में ड्रॉपडाउन जैसे फ़ॉर्म फ़ील्ड घटक जोड़ने का समर्थन करता है। अन्य प्रारूपों के लिए समर्थन भिन्न हो सकता है, इसलिए विशिष्ट प्रारूप क्षमताओं के लिए दस्तावेज़ देखें।

### मैं किसी फॉर्म में ड्रॉपडाउन को अनिवार्य कैसे बनाऊं?

ड्रॉपडाउन घटक में कोई अंतर्निहित "आवश्यक" प्रॉपर्टी नहीं है। आपको अपने एप्लिकेशन में सत्यापन तर्क लागू करना होगा जो फ़ॉर्म सबमिशन को संसाधित करता है।

### क्या मैं दस्तावेज़ में ड्रॉपडाउन जोड़ने के बाद उसका स्वरूप बदल सकता हूँ?

हां, आप किसी मौजूदा ड्रॉपडाउन को पुनः प्राप्त करके, उसके गुणों को संशोधित करके और उसे अपडेट करके अपडेट कर सकते हैं:

```csharp
using (Annotator annotator = new Annotator("document-with-dropdown.pdf"))
{
    // सभी एनोटेशन प्राप्त करें
    List<AnnotationBase> annotations = annotator.Get();
    
    // ड्रॉपडाउन खोजें और अपडेट करें
    foreach (var annotation in annotations)
    {
        if (annotation is DropdownComponent dropdown)
        {
            // गुण अपडेट करें
            dropdown.PenColor = 255; // लाल रंग में बदलें
            dropdown.Options = new List<string> { "New Option 1", "New Option 2" };
            
            // एनोटेशन अपडेट करें
            annotator.Update(dropdown);
        }
    }
    
    // अद्यतन दस्तावेज़ सहेजें
    annotator.Save("updated-document.pdf");
}
```

## संसाधन

- [GroupDocs.Annotation दस्तावेज़ीकरण](https://docs.groupdocs.com/annotation/net/)
- [एपीआई संदर्भ](https://reference.groupdocs.com/annotation/net/)
- [.NET के लिए GroupDocs.Annotation डाउनलोड करें](https://releases.groupdocs.com/annotation/net/)
- [लाइसेंस खरीदें](https://purchase.groupdocs.com/buy)
- [मुफ्त परीक्षण](https://releases.groupdocs.com/annotation/net/)
- [अस्थायी लाइसेंस](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs.Annotation सहायता फ़ोरम](https://forum.groupdocs.com/c/annotation)