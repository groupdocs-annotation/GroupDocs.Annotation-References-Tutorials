---
categories:
- Java Development
date: '2026-03-30'
description: Scopri come aggiungere annotazioni di barratura in Java usando GroupDocs.Annotation.
  Guida passo passo con esempi di codice, consigli per la risoluzione dei problemi
  e migliori pratiche per il markup dei documenti.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: Aggiungi annotazione barrata tutorial Java con GroupDocs
type: docs
url: /it/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Aggiungi annotazione barrata Java - Guida completa GroupDocs

Ti è mai capitato di fissare un documento pensando, “Devo cancellare questo testo, ma non posso semplicemente prendere una penna rossa”? Non sei solo. Che tu stia costruendo un sistema di revisione documenti, creando un flusso di lavoro di editing, o semplicemente abbia bisogno di contrassegnare del testo per la cancellazione nella tua applicazione Java, **add strikeout annotation java** è una competenza essenziale. In questo tutorial vedremo tutto ciò che devi sapere per implementare la funzionalità di barratura del testo che funziona davvero in produzione.

## Risposte rapide
- **Quale libreria supporta le annotazioni barrate in Java?** GroupDocs.Annotation for Java  
- **Quale parola chiave principale dovrei mirare per SEO?** add strikeout annotation java  
- **Ho bisogno di una licenza per eseguire il codice di esempio?** Una prova gratuita o una licenza temporanea funziona per lo sviluppo; è necessaria una licenza completa per la produzione.  
- **Posso usarlo con file PDF, DOCX e PPTX?** Sì – GroupDocs.Annotation supporta tutti i principali formati di documento.  
- **Quale versione di Java è richiesta?** JDK 8 o superiore (consigliato JDK 11+).  

## Cos'è add strikeout annotation java?
Un'annotazione barrata traccia una linea attraverso il testo selezionato, indicando visivamente che il contenuto dovrebbe essere rimosso o ignorato. È un modo non distruttivo per suggerire cancellazioni mantenendo intatto il testo originale per tracciamenti di audit o revisioni collaborative.

## Perché usare le annotazioni barrate nelle applicazioni Java?
- **Flussi di revisione dei documenti** – i revisori possono segnalare testo indesiderato senza alterare la sorgente.  
- **Modifica collaborativa** – i membri del team vedono le cancellazioni suggerite istantaneamente.  
- **Legale e conformità** – mantieni una chiara traccia di audit delle modifiche.  
- **Migrazione di contenuti** – contrassegna le sezioni obsolete prima di spostare il contenuto tra sistemi.  

## Prerequisiti e configurazione dell'ambiente
Avrai bisogno dei seguenti elementi prima di immergerti nel codice:

- **Java Development Kit (JDK)** 8+ (consigliato JDK 11+)  
- **Maven o Gradle** per la gestione delle dipendenze  
- **IDE** – IntelliJ IDEA, Eclipse o VS Code con estensioni Java  
- **Libreria GroupDocs.Annotation** – useremo la versione 25.2 negli esempi  

*Nice to have:* conoscenza di base delle annotazioni Java e della gestione dei PDF.

## Configurazione di GroupDocs.Annotation per Java

### Configurazione Maven che funziona davvero
Aggiungi il repository e la dipendenza al tuo `pom.xml` esattamente come mostrato:

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

### Ottenere la licenza
GroupDocs offre diverse opzioni di licenza:

- **Prova gratuita** – perfetta per i test (nessuna carta di credito richiesta)  
- **Licenza temporanea** – ideale per sviluppo e staging  
- **Licenza completa** – necessaria per l'uso in produzione; vedi la [pagina di acquisto](https://purchase.groupdocs.com/buy)

> **Consiglio professionale:** Inizia con la prova gratuita per esplorare l'API, poi passa a una licenza temporanea quando sei pronto a costruire una funzionalità reale.

### Configurazione rapida di verifica
Esegui questo programma minimale per verificare che la libreria venga caricata correttamente:

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

Se la console stampa il messaggio di successo senza errori, sei pronto per aggiungere annotazioni barrate.

## Come aggiungere annotazione barrata java

Di seguito trovi un'implementazione completa, pronta per la produzione, suddivisa in passaggi chiari.

### Passo 1 – Inizializzare l'Annotator
Crea un'istanza `Annotator` che punti al documento sorgente:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Perché è importante:** Usare un percorso assoluto o relativo correttamente risolto previene le eccezioni “file non trovato”.

### Passo 2 – (Opzionale) Preparare le risposte ai commenti
Aggiungere risposte rende l'annotazione collaborativa:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

Questi commenti appaiono quando un utente passa il mouse sopra la barratura.

### Passo 3 – Definire l'area della barratura
Specifica il rettangolo che racchiude il testo che vuoi barrare:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Suggerimento coordinate:** L'origine (0,0) è l'angolo in alto a sinistra della pagina; X cresce verso destra, Y verso il basso. Usa un visualizzatore PDF che mostri le coordinate per affinare questi valori.

### Passo 4 – Configurare l'annotazione barrata
Imposta l'aspetto, il numero di pagina e allega i commenti:

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

*Nota colore:* `65535` corrisponde al giallo nel formato RGB intero. Cambia il valore per usare altri colori.

### Passo 5 – Applicare l'annotazione e salvare
Aggiungi l'annotazione al documento e scrivi il file di output:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Passo 6 – Pulire le risorse (Critico!)
Disporre sempre dell'annotator per liberare le risorse native:

```java
if (annotator != null) {
    annotator.dispose();
}
```

In produzione, avvolgi l'uso in un blocco try‑with‑resources o in una struttura `try/finally`.

## Problemi comuni e come risolverli

| Problema | Sintomo | Soluzione |
|----------|---------|-----------|
| **File non trovato** | `Annotator` genera un'eccezione | Usa percorsi assoluti, verifica i permessi di lettura, assicurati che nessun altro processo blocchi il file |
| **Coordinate errate** | La barratura appare lontano dal testo previsto | Controlla nuovamente il sistema di coordinate del visualizzatore PDF; regola i punti di conseguenza |
| **Annotazione invisibile** | Nessuna barratura visibile dopo il salvataggio | Aumenta `opacity` (es., `0.9`), verifica `pageNumber` (basato su 0), assicurati che i punti formino un rettangolo corretto |
| **OutOfMemoryError** | L'applicazione si blocca su PDF di grandi dimensioni | Aumenta l'heap JVM (`-Xmx2048m`), elabora i documenti in batch, chiama sempre `dispose()` |

## Best practice di performance per la produzione

### Gestione della memoria
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

### Strategia di elaborazione batch
Quando devi annotare decine o centinaia di file:

- Elabora 10‑20 documenti per batch.  
- Registra successi/fallimenti per ogni file.  
- Re‑inizializza l'`Annotator` per ogni documento per evitare perdite di memoria.  

### Suggerimenti per il caching
- Metti in cache i modelli di documento usati frequentemente.  
- Conserva mappe di coordinate pre‑calcolate per layout standard.  

## Casi d'uso reali

1. **Sistemi di revisione dei documenti** – gli editor suggeriscono cancellazioni senza alterare il contratto originale.  
2. **Emendamenti legali** – gli avvocati tracciano la rimozione di clausole mantenendo la formulazione originale per l'audit.  
3. **Revisione accademica tra pari** – i revisori segnalano sezioni da rimuovere e aggiungono commenti in linea.  
4. **Migrazione di contenuti** – Durante le migrazioni CMS, le barrature evidenziano copie obsolete che necessitano di sostituzione.  

## Personalizzazione avanzata

### Stile personalizzato
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Aggiungere metadati
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Lista di controllo per la risoluzione dei problemi
- ✅ Puoi aprire manualmente il file sorgente?  
- ✅ Tutte le dipendenze GroupDocs sono presenti nel classpath?  
- ✅ I punti formano un rettangolo valido?  
- ✅ Il numero di pagina è corretto (basato su 0)?  
- ✅ C'è sufficiente memoria heap?  
- ✅ Hai i permessi di scrittura per la cartella di output?  
- ✅ Il formato del documento è supportato (PDF, DOCX, PPTX, ecc.)?  

## Domande frequenti

**Q: Posso usare GroupDocs.Annotation all'interno di un servizio Spring Boot?**  
A: Sì. Aggiungi la dipendenza Maven, inietta una classe di servizio che crea l'`Annotator` e gestisci il suo ciclo di vita con gli scope dei bean di Spring.

**Q: Quali formati di documento supportano le annotazioni barrate?**  
A: PDF, DOCX, PPTX e molti altri formati supportati da GroupDocs.Annotation. PDF offre la gestione delle coordinate più precisa.

**Q: Come gestisco documenti con dimensioni di pagina variabili?**  
A: Recupera le dimensioni della pagina tramite `annotator.getPageInfo(pageNumber)` e scala le coordinate di conseguenza.

**Q: È possibile modificare o eliminare un'annotazione barrata esistente?**  
A: Assolutamente. Usa `annotator.getAnnotations(pageNumber)` per recuperare, poi `annotator.update(updatedAnnotation)` o `annotator.delete(annotationId)`.

**Q: Qual è l'impatto sulle prestazioni dell'aggiunta di molte annotazioni?**  
A: Aggiungere centinaia di annotazioni è generalmente accettabile, ma monitora l'uso della memoria. Per set di annotazioni molto grandi, considera la paginazione della vista o il caricamento lazy delle annotazioni su richiesta.

## Conclusione
Ora hai una guida completa, pronta per la produzione, su **add strikeout annotation java** usando GroupDocs.Annotation. Inizia con l'esempio di verifica semplice, poi scala all'elaborazione batch, allo stile personalizzato e all'arricchimento dei metadati. Ricorda di testare le coordinate con attenzione, gestire le risorse in modo responsabile e scegliere il modello di licenza appropriato per il tuo ambiente.

Pronto a esplorare di più? Dai un'occhiata ad altri tipi di annotazione — evidenziazione, nota, immagine, freccia e filigrana — per costruire una suite completa di collaborazione documentale.

---

**Ultimo aggiornamento:** 2026-03-30  
**Testato con:** GroupDocs.Annotation 25.2 per Java  
**Autore:** GroupDocs  

**Risorse aggiuntive**

- [Documentazione GroupDocs Annotation](https://docs.groupdocs.com/annotation/java/)
- [Guida di riferimento API](https://reference.groupdocs.com/annotation/java/)
- [Scarica l'ultima versione](https://releases.groupdocs.com/annotation/java/)
- [Acquista licenza completa](https://purchase.groupdocs.com/buy)
- [Inizia prova gratuita](https://releases.groupdocs.com/annotation/java/)
- [Ottieni licenza temporanea](https://purchase.groupdocs.com/temporary-license/)
- [Forum di supporto della community](https://forum.groupdocs.com/c/annotation/)