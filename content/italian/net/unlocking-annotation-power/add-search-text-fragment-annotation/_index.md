---
"description": "Esplora la potenza di GroupDocs.Annotation per .NET e aggiungi senza sforzo funzionalità di annotazione dei documenti alle tue applicazioni."
"linktitle": "Aggiungi annotazione al frammento di testo di ricerca al documento"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Aggiungi annotazione al frammento di testo di ricerca al documento"
"url": "/it/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
type: docs
"weight": 20
---

# Aggiungi annotazione al frammento di testo di ricerca al documento

## Introduzione
Nell'ambito dello sviluppo .NET, GroupDocs.Annotation si distingue come un potente strumento per annotare i documenti in modo fluido. Che tu sia uno sviluppatore esperto o che tu stia appena muovendo i primi passi nel mondo .NET, questo tutorial completo ti guiderà attraverso gli elementi essenziali dell'utilizzo di GroupDocs.Annotation per .NET, dall'importazione di namespace alla padronanza delle complessità dell'aggiunta di annotazioni di frammenti di testo di ricerca ai tuoi documenti.
## Introduzione
GroupDocs.Annotation per .NET consente agli sviluppatori di integrare facilmente funzionalità di annotazione dei documenti nelle loro applicazioni. Grazie alla sua API intuitiva e alle sue funzionalità affidabili, gli sviluppatori possono annotare vari formati di documento, inclusi PDF, documenti di Microsoft Office, immagini e altro ancora.
## Prerequisiti
Prima di immergerti in GroupDocs.Annotation per .NET, assicurati di avere i seguenti prerequisiti:

## Importa spazi dei nomi
Per prima cosa, importa gli spazi dei nomi necessari per accedere alle classi e ai metodi GroupDocs.Annotation nel tuo progetto .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Passaggio 1: definire il percorso di output
Iniziamo definendo il percorso di output in cui verrà salvato il documento annotato:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Passaggio 2: inizializzare l'annotatore
Quindi, inizializza un'istanza di `Annotator` classe fornendo il percorso al documento che si desidera annotare:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Passaggio 3: creare un'annotazione del frammento di testo di ricerca
Crea un `SearchTextFragment` oggetto con le proprietà desiderate, come testo da cercare, dimensione del carattere, famiglia di caratteri, colore del carattere e colore di sfondo:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## Passaggio 4: aggiungere annotazioni
Aggiungere l'annotazione del frammento di testo di ricerca creato al documento utilizzando `Add` metodo dell'annotatore:
```csharp
annotator.Add(searchText);
```
## Passaggio 5: Salva il documento annotato
Salva il documento annotato nel percorso di output specificato:
```csharp
annotator.Save(outputPath);
```
## Passaggio 6: visualizzare il messaggio di successo
Informare l'utente che il documento è stato salvato correttamente:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In conclusione, GroupDocs.Annotation per .NET semplifica il processo di aggiunta di annotazioni ai documenti, migliorando la collaborazione e i processi di revisione dei documenti. Seguendo i passaggi descritti in questa guida, è possibile integrare perfettamente le funzionalità di annotazione dei documenti nelle applicazioni .NET.
## Domande frequenti
### GroupDocs.Annotation è compatibile con tutti i formati di documento?
Sì, GroupDocs.Annotation supporta un'ampia gamma di formati di documenti, tra cui PDF, documenti Microsoft Office, immagini e altro ancora.
### Posso personalizzare l'aspetto delle annotazioni?
Assolutamente sì! GroupDocs.Annotation offre ampie opzioni di personalizzazione per le annotazioni, consentendo di regolare proprietà come dimensione del carattere, colore e stile.
### È disponibile una prova gratuita per GroupDocs.Annotation?
Sì, puoi accedere a una prova gratuita di GroupDocs.Annotation per esplorare le sue funzionalità e capacità prima di effettuare un acquisto [Qui](https://releases.groupdocs.com/)..
### Dove posso trovare supporto per GroupDocs.Annotation?
Per supporto e assistenza con GroupDocs.Annotation, puoi visitare GroupDocs [foro](https://forum.groupdocs.com/c/annotation/10) dedicato a domande e discussioni relative alle annotazioni.
### Come posso ottenere una licenza temporanea per GroupDocs.Annotation?
È possibile acquisire una licenza temporanea per GroupDocs.Annotation tramite GroupDocs [sito web](https://purchase.groupdocs.com/temporary-license/), consentendoti di valutare il prodotto in modo completo.