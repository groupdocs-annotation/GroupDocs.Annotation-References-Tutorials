---
categories:
- Java PDF Processing
date: '2026-05-21'
description: Scopri come aggiungere annotazioni di barratura a PDF in Java usando
  GroupDocs. Questo tutorial passo‑passo copre l'installazione, il codice, la risoluzione
  dei problemi e consigli sulle prestazioni.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Guida Java PDF Text Strikeout
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: Come aggiungere annotazioni di barratura a PDF in Java – Guida completa di
  GroupDocs
type: docs
url: /it/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Come aggiungere annotazioni di barratura ai PDF in Java

Hai mai avuto bisogno di barrare del testo in un PDF in modo programmatico? Che tu stia costruendo un sistema di revisione dei documenti, creando un flusso di lavoro di editing, o semplicemente abbia bisogno di contrassegnare del testo per l'eliminazione, le annotazioni **how to add strikeout** in Java sono una competenza pratica che fa risparmiare tempo e riduce lo sforzo manuale. In questa guida completa scoprirai tutto ciò che devi sapere per implementare le annotazioni di barratura con GroupDocs.Annotation per Java, dalla configurazione del progetto all'ottimizzazione delle prestazioni.

## Risposte rapide
- **Qual è il primo passo?** Aggiungi la dipendenza Maven di GroupDocs.Annotation al tuo `pom.xml`.  
- **Come creo una barratura?** Istanzia `Annotator`, definisci `StrikeoutAnnotation` con i punti, imposta colore/opacità, quindi chiama `addAnnotation`.  
- **Posso aggiungere commenti?** Sì, allega un oggetto `Comment` all'annotazione per la collaborazione.  
- **Cosa fare se l'annotazione è posizionata in modo errato?** Regola i punti di coordinate; il PDF utilizza un sistema di origine in basso a sinistra.  
- **Esiste un limite alla dimensione del documento?** GroupDocs elabora PDF di centinaia di pagine senza caricare l'intero file in memoria.

## Cos'è “how to add strikeout” nell'annotazione PDF?
La frase “how to add strikeout” si riferisce al processo di disegnare programmaticamente una linea attraverso il testo selezionato all'interno di un documento PDF utilizzando un'API di annotazione. In Java, GroupDocs.Annotation fornisce una classe dedicata `StrikeoutAnnotation` che gestisce il rendering, lo stile e la persistenza dei segni di barratura.

## Perché usare GroupDocs per la barratura PDF in Java?
GroupDocs.Annotation supporta **oltre 50 formati di input e output** — inclusi PDF, DOCX, XLSX, PPTX, HTML e i comuni tipi di immagine — così non sei vincolato a un unico tipo di file. Fornisce un'API di alto livello che astrae la struttura PDF a basso livello, gestendo automaticamente l'incorporamento dei font, il rendering delle pagine e la persistenza delle annotazioni, consentendo agli sviluppatori di concentrarsi sulla logica di business anziché sugli internals del PDF.

## Prerequisiti e requisiti di configurazione

### Requisiti essenziali
- **Java Development Kit (JDK):** Versione 8 o successiva (JDK 11+ consigliato per una raccolta dei rifiuti ottimale).  
- **GroupDocs.Annotation per Java:** Integrato via Maven (vedi lo snippet Maven sotto).  
- **IDE:** IntelliJ IDEA, Eclipse o qualsiasi editor compatibile con Java.

### Configurazione delle dipendenze Maven
Aggiungi il seguente blocco di dipendenza al tuo `pom.xml`:

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

**Suggerimento:** Verifica sempre l'ultima versione nella pagina di rilascio di GroupDocs; le versioni più recenti aggiungono funzionalità e correggono bug che possono influire sul rendering delle annotazioni.

### Ottenere la licenza
GroupDocs.Annotation richiede una licenza valida per l'uso in produzione. Hai tre opzioni:

- **Prova gratuita:** Scarica da [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)
- **Licenza temporanea:** Richiedi una chiave di sviluppo su [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Licenza completa:** Acquista per la produzione su [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

La prova aggiunge una leggera filigrana, quindi pianifica i test di conseguenza.

## Guida all'implementazione passo‑passo

### Comprendere i componenti principali
Le seguenti definizioni ti forniscono un modello mentale rapido:

- **Annotator:** L'oggetto API principale che carica un PDF e espone i metodi di annotazione.  
- **StrikeoutAnnotation:** Rappresenta la linea di barratura visiva e le sue opzioni di stile.  
- **Point:** Una coppia di coordinate (X, Y) che indica alla libreria dove inizia e finisce la linea.  
- **Comment:** Testo opzionale allegato a un'annotazione per la collaborazione.

### Passo 1: Configurare i percorsi dei file
Definisci le posizioni del tuo PDF di origine e del file di destinazione. Percorsi errati sono una causa comune di errori “File Not Found”.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Avviso errore comune:** Assicurati che la directory di output esista e sia scrivibile; GroupDocs non creerà automaticamente le cartelle mancanti.

### Passo 2: Inizializzare l'Annotator
Crea un'istanza di `Annotator` che carica il PDF in memoria.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**Cosa succede qui?** La libreria analizza la struttura del PDF, costruisce una rappresentazione interna e prepara una tela di annotazione per pagina. Per file con centinaia di pagine questo passo può richiedere qualche secondo.

### Passo 3: Aggiungere commenti (opzionale ma consigliato)
`Comment` è una classe che rappresenta una nota testuale allegata a un'annotazione, permettendo ai collaboratori di spiegare il motivo della barratura.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Consiglio pratico:** Usa i commenti per spiegare perché il testo viene rimosso — è particolarmente utile nei flussi di lavoro di revisione legale o editoriale.

### Passo 4: Definire le coordinate dell'annotazione
Gli oggetti `Point` memorizzano coppie di coordinate X‑Y che definiscono la posizione esatta di un'annotazione su una pagina PDF.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Spiegazione del sistema di coordinate:** Le coordinate PDF partono dall'angolo in basso a sinistra (0,0). L'esempio crea una linea orizzontale da (80,730) a (240,730) sulla pagina target.

**Trovare le coordinate corrette:** Molti sviluppatori creano un helper che converte le percentuali della larghezza/altezza della pagina in punti assoluti, rendendo il codice resiliente a diverse dimensioni di pagina.

### Passo 5: Creare l'annotazione di barratura
`StrikeoutAnnotation` incapsula la linea visiva, le sue proprietà di stile come colore e opacità, e qualsiasi metadato associato per un segno di barratura.

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**Valori colore:** `fontColor` utilizza valori RGB decimali (ad esempio, 65535 per giallo brillante). Usa un convertitore online se ti servono tonalità specifiche del brand.

**Raccomandazione opacità:** Un'opacità di `0.7` (70 %) offre un chiaro indicatore visivo mantenendo il testo sottostante leggibile.

### Passo 6: Applicare l'annotazione
`addAnnotation` è un metodo di `Annotator` che registra l'annotazione preparata nel documento affinché venga renderizzata e salvata.

```java
annotator.add(strikeout);
```

### Passo 7: Salvare e pulire
`dispose()` rilascia le risorse native detenute dall'istanza `Annotator`, prevenendo perdite di memoria al termine dell'elaborazione.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Nota sulla gestione della memoria:** Chiamare `dispose()` libera le risorse native e previene perdite di memoria quando si elaborano batch di PDF.

## Problemi comuni e come risolverli

### Problema 1: Errori “File Not Found”
**Sintomi:** Eccezione lanciata durante la costruzione di `Annotator`.  
**Soluzione:** Verifica entrambi i percorsi di input e output e conferma che l'applicazione abbia i permessi di lettura/scrittura.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Problema 2: La barratura appare nella posizione sbagliata
**Sintomi:** La linea non è allineata con il testo previsto.  
**Soluzione:** Ricorda che le coordinate Y del PDF aumentano verso l'alto. Usa uno strumento di debug visivo o stampa le dimensioni della pagina per affinare i punti.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Problema 3: L'annotazione non è visibile
**Sintomi:** Nessuna barratura appare dopo il salvataggio.  
**Possibili cause e soluzioni:**
- **Opacità troppo bassa:** Imposta temporaneamente l'opacità a `1.0` per verificare la visibilità.  
- **Mischia di colore:** Usa un colore ad alto contrasto come il rosso (`255`).  
- **Indice di pagina errato:** I numeri di pagina partono da zero; assicurati di puntare alla pagina corretta.

### Problema 4: Problemi di memoria con file di grandi dimensioni
**Sintomi:** `OutOfMemoryError` o prestazioni lente.  
**Soluzioni:**  
- Elabora i documenti in batch più piccoli.  
- Usa l'API di streaming se disponibile.  
- Invoca sempre `dispose()` dopo ogni documento.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Applicazioni reali e casi d'uso

### Revisione di documenti legali
Gli studi legali annotano i contratti con barrature per indicare clausole eliminate mantenendo una traccia di audit.

### Editing di articoli accademici
I professori usano le barrature per suggerire rimozioni durante la revisione tra pari, mantenendo il testo originale visibile per il contesto.

### Sistemi di gestione dei contenuti
Le piattaforme di pubblicazione segnalano automaticamente le sezioni che violano le politiche con barrature prima della moderazione manuale.

### Controllo versione per documenti
Le aziende trattano le annotazioni di barratura come “marcatori di cancellazione” in un flusso di lavoro di versionamento centrato sui documenti, simile ai diff di codice.

## Suggerimenti per l'ottimizzazione delle prestazioni

### Strategia di elaborazione batch
Quando si gestiscono molti PDF, riutilizza una singola istanza di `Annotator` dove possibile ed elabora i file in thread paralleli.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Best practice per la gestione della memoria
- Chiama `dispose()` su ogni `Annotator`.  
- Limita i caricamenti simultanei di documenti per evitare pressione sull'heap.  
- Monitora l'uso della memoria JVM con strumenti come VisualVM.

### Caching delle coordinate
Se applichi lo stesso layout di annotazione su più file, memorizza nella cache gli oggetti `Point` per evitare ricalcoli.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Opzioni avanzate di personalizzazione

### Selezione dinamica del colore
Scegli i colori a runtime in base a regole di business (ad esempio, rosso per cancellazioni critiche, giallo per quelle provvisorie).

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### Barrature multilinea
Crea una serie di coppie `Point` per disegnare una linea a zig‑zag che attraversa più linee di testo.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Checklist di risoluzione dei problemi
1. **Permessi file:** Verifica l'accesso in lettura/scrittura.  
2. **Versione della libreria:** Assicurati di usare una versione supportata di GroupDocs.Annotation.  
3. **Stato della licenza:** Conferma che il file di licenza sia correttamente referenziato.  
4. **Compatibilità PDF:** Verifica che il PDF non sia corrotto e rientri nei limiti di dimensione supportati.  
5. **Validazione coordinate:** Assicurati che tutti i punti siano all'interno dei limiti della pagina.  
6. **Spazio heap:** Incrementa il JVM `-Xmx` se elabori file molto grandi.

## Domande frequenti

**D: Posso barrare testo su più linee?**  
R: Sì. Crea diversi oggetti `Point` che tracciano il percorso desiderato; l'annotazione seguirà la polilinea fornita.

**D: Cosa succede se specifico coordinate al di fuori dei limiti della pagina?**  
R: L'annotazione verrà ritagliata e potrebbe diventare invisibile. Valida sempre le coordinate rispetto alla larghezza e altezza della pagina.

**D: Posso rimuovere le annotazioni di barratura dopo averle aggiunte?**  
R: Assolutamente. Usa il metodo `removeAnnotation` con l'ID dell'annotazione o filtra per tipo per eliminarle programmaticamente.

**D: Esiste un limite al numero di annotazioni che posso aggiungere a un singolo PDF?**  
R: GroupDocs non impone un limite rigido, ma le prestazioni possono degradarsi dopo migliaia di annotazioni. Considera la paginazione o la sintesi delle annotazioni per insiemi molto grandi.

**D: Come gestisco i PDF protetti da password?**  
R: Passa la password al costruttore `Annotator`. La libreria decritterà il documento in memoria prima di applicare le annotazioni.

**D: Come posso gestire PDF con diverse dimensioni e orientamenti di pagina?**  
R: Recupera le dimensioni di ogni pagina tramite `annotator.getPageInfo(pageNumber)` e calcola le coordinate relative a quelle dimensioni per garantire un posizionamento coerente.

## Conclusione
Ora hai una soluzione completa e pronta per la produzione per le annotazioni **how to add strikeout** su PDF in Java usando GroupDocs.Annotation. Padroneggiando la gestione dei percorsi dei file, il calcolo delle coordinate e la gestione delle risorse, puoi integrare questa funzionalità in strumenti di revisione dei documenti, pipeline di contenuti o qualsiasi applicazione Java che necessiti di un feedback visivo preciso.

**Passi successivi**
1. Clona il progetto di esempio ed eseguilo su un PDF di prova.  
2. Sperimenta con diversi colori, opacità e testi dei commenti.  
3. Integra il flusso di lavoro di annotazione nel tuo servizio di elaborazione documenti esistente.  
4. Esplora tipi di annotazione correlati — evidenziazioni, note adesive e annotazioni di forma — per ampliare il tuo toolkit di manipolazione PDF.  

Pronto per altro? Immergiti nella documentazione ufficiale per approfondire le funzionalità dell'API.

## Risorse aggiuntive

- [Documentazione GroupDocs](https://docs.groupdocs.com/annotation/java/) - Documentazione generale per le librerie GroupDocs  
- [Documentazione GroupDocs.Annotation](https://docs.groupdocs.com/annotation/java/) - Riferimento API completo  
- [Guida di riferimento API](https://reference.groupdocs.com/annotation/java/) - Dettagli metodo per metodo  
- [Scarica l'ultima versione](https://releases.groupdocs.com/annotation/java/) - Mantieni la tua libreria aggiornata  
- [Acquista licenza](https://purchase.groupdocs.com/buy) - Licenza pronta per la produzione  
- [Download prova gratuita](https://releases.groupdocs.com/annotation/java/) - Valuta prima di acquistare  
- [Richiesta licenza temporanea](https://purchase.groupdocs.com/temporary-license/) - Test di sviluppo  
- [Forum di supporto](https://forum.groupdocs.com/c/annotation/) - Aiuto della community e supporto ufficiale  

---

**Ultimo aggiornamento:** 2026-05-21  
**Testato con:** GroupDocs.Annotation 23.12 per Java  
**Autore:** GroupDocs

## Tutorial correlati

- [Aggiungi annotazione PDF Java – Guida completa GroupDocs](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [Tutorial annotazione PDF Java - Guida completa all'evidenziazione dei PDF](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)  
- [Come aggiungere frecce al PDF in Java – Tutorial completo GroupDocs](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)