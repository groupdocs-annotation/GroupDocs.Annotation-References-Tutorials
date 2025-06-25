---
"date": "2025-05-06"
"description": "Scopri come aggiungere e rimuovere le annotazioni sottolineate nei documenti Java utilizzando GroupDocs.Annotation. Migliora la gestione dei tuoi documenti con questa guida dettagliata."
"title": "Aggiungere e rimuovere annotazioni sottolineate in Java utilizzando GroupDocs - Una guida completa"
"url": "/it/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
"weight": 1
---

# Come implementare Java: aggiungere e rimuovere le annotazioni sottolineate con GroupDocs

## Introduzione

Vuoi migliorare il tuo sistema di gestione documentale aggiungendo o rimuovendo annotazioni a livello di codice? Questo tutorial ti guiderà nell'utilizzo della potente libreria GroupDocs.Annotation in Java per aggiungere annotazioni sottolineate e rimuoverle da documenti come i PDF.

**Cosa imparerai:**
- Inizializzare la classe Annotator.
- Aggiungere un'annotazione sottolineata con commenti utilizzando GroupDocs.Annotation per Java.
- Rimuovi tutte le annotazioni da un documento.
- Configura il tuo ambiente per utilizzare GroupDocs.Annotation in modo efficiente.

Scopriamo come queste funzionalità possono essere sfruttate nei tuoi progetti. Assicurati di avere i prerequisiti necessari prima di iniziare.

## Prerequisiti

### Librerie e dipendenze richieste
Per seguire questo tutorial in modo efficace, assicurati di avere:
- **GroupDocs.Annotation per Java**: Si consiglia la versione 25.2 o successiva.
- **Kit di sviluppo Java (JDK)**: È richiesta la versione 8 o successiva.

### Requisiti di configurazione dell'ambiente
Assicurati che il tuo ambiente di sviluppo includa un IDE come IntelliJ IDEA o Eclipse e uno strumento di compilazione come Maven.

### Prerequisiti di conoscenza
Sarà utile una conoscenza di base della programmazione Java, in particolare per quanto riguarda l'uso delle librerie tramite Maven.

## Impostazione di GroupDocs.Annotation per Java

Per iniziare a utilizzare GroupDocs.Annotation nei tuoi progetti Java, segui questi passaggi di configurazione:

**Configurazione Maven:**
Aggiungi la seguente configurazione al tuo `pom.xml` file da scaricare e integrare GroupDocs.Annotation.

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

**Acquisizione della licenza:**
Inizia scaricando una versione di prova gratuita o ottenendo una licenza temporanea da GroupDocs per esplorare tutte le funzionalità della loro libreria. Per l'uso in produzione, è necessario acquistare una licenza.

## Guida all'implementazione

### Funzionalità 1: inizializza l'annotatore e aggiungi l'annotazione sottolineata

Questa sezione ti guida attraverso l'inizializzazione del `Annotator` classe e aggiungendo un'annotazione sottolineata al documento.

#### Panoramica
Aggiungere annotazioni aiuta a evidenziare parti specifiche di un documento. Qui ci concentriamo sulla sottolineatura del testo con commenti per chiarimenti o feedback.

#### Implementazione passo dopo passo

**1. Inizializza l'annotatore**
Crea un `Annotator` oggetto e carica il tuo file PDF.

```java
import com.groupdocs.annotation.Annotator;

// Carica il documento che vuoi annotare
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. Crea commenti con risposte**
Definisci i commenti associati all'annotazione sottolineata.

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**3. Definire i punti per l'annotazione sottolineata**
Imposta le coordinate per determinare dove deve apparire la sottolineatura.

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**4. Creare e configurare l'annotazione sottolineata**
Crea l'annotazione sottolineata e impostane le proprietà come colore, opacità e commenti.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Giallo in formato ARGB
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. Salvare il documento annotato**
Salva le modifiche in un nuovo file.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### Suggerimenti per la risoluzione dei problemi
- Assicurarsi che tutte le coordinate dei punti rientrino nei limiti del documento.
- Verificare che il `outputPath` la directory esiste ed è scrivibile.

### Funzionalità 2: Salva il documento senza annotazioni

Questa sezione spiega come rimuovere tutte le annotazioni da un documento precedentemente annotato.

#### Panoramica
Potrebbe essere necessario salvare una versione pulita del documento, senza annotazioni, per scopi di condivisione o archiviazione.

#### Implementazione passo dopo passo

**1. Inizializzare l'annotatore con il documento annotato**
Carica il documento che contiene annotazioni esistenti.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. Configurare le opzioni di salvataggio per rimuovere le annotazioni**
Specificare che nessuna annotazione deve essere salvata nel file di output.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. Salvare il documento senza annotazioni**
Definire il percorso per il documento pulito e salvarlo.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## Applicazioni pratiche

Ecco alcuni scenari concreti in cui queste funzionalità possono rivelarsi utili:
1. **Revisione dei documenti**: Evidenziare e commentare sezioni di un contratto o di un rapporto per la revisione.
2. **Strumenti educativi**: Annotare i libri di testo con note o correzioni per gli studenti.
3. **Editing collaborativo**: Condivisione di bozze annotate tra i membri del team per ricevere feedback.
4. **Documentazione legale**: Sottolineare le clausole chiave nei documenti legali durante le discussioni.
5. **Materiali di marketing**: Evidenziare le informazioni importanti nelle brochure prima della distribuzione.

## Considerazioni sulle prestazioni
Quando lavori con GroupDocs.Annotation, tieni a mente questi suggerimenti per ottimizzare le prestazioni:
- **Gestione della memoria**: Smaltire correttamente `Annotator` oggetti per liberare risorse.
- **Elaborazione batch**: Se si annotano più documenti, elaborarli in batch per gestire efficacemente il carico del sistema.
- **Allocazione delle risorse**: assicurati che il tuo ambiente disponga di memoria e potenza di elaborazione sufficienti per gestire file di grandi dimensioni.

## Conclusione
Hai imparato come aggiungere e rimuovere annotazioni sottolineate utilizzando GroupDocs.Annotation per Java. Questo tutorial ha trattato l'inizializzazione della classe Annotator, la configurazione delle annotazioni con commenti e il salvataggio dei documenti senza annotazioni. 

Per approfondire ulteriormente, valuta la possibilità di integrare queste funzionalità nei tuoi sistemi di gestione dei documenti esistenti o di sperimentare altri tipi di annotazione forniti da GroupDocs.

## Sezione FAQ
1. **Come posso configurare più annotazioni sottolineate in un'unica esecuzione?**
   - Crea più `UnderlineAnnotation` oggetti e aggiungerli in sequenza utilizzando il `annotator.add()` metodo.
2. **Posso annotare le immagini nei PDF utilizzando questa libreria?**
   - Sì, GroupDocs.Annotation supporta l'annotazione delle immagini all'interno di documenti come i PDF.
3. **Quali formati di file supporta GroupDocs.Annotation?**
   - Supporta vari formati di documenti, tra cui PDF, Word, Excel e altri.