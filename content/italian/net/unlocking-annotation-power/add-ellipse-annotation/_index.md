---
"description": "Scopri come aggiungere annotazioni ellittiche ai documenti in .NET utilizzando GroupDocs.Annotation. Migliora la collaborazione e la comunicazione senza sforzo."
"linktitle": "Aggiungi annotazione ellittica al documento"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Aggiungi annotazione ellittica al documento"
"url": "/it/net/unlocking-annotation-power/add-ellipse-annotation/"
"weight": 13
---

# Aggiungi annotazione ellittica al documento

## Introduzione
In questo tutorial imparerai come aggiungere un'annotazione ellittica a un documento utilizzando GroupDocs.Annotation per .NET. Questa guida passo passo ti guiderà passo passo attraverso il processo, assicurandoti di comprendere chiaramente ogni passaggio.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
1. GroupDocs.Annotation per .NET: assicurati di aver scaricato e installato GroupDocs.Annotation per .NET. Puoi scaricarlo da [Qui](https://releases.groupdocs.com/annotation/net/).
2. IDE (Integrated Development Environment): per scrivere ed eseguire il codice, è necessario che sul sistema sia installato un IDE, ad esempio Visual Studio.

## Importa spazi dei nomi
Per prima cosa, importa gli spazi dei nomi necessari nel tuo progetto:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Passaggio 1: impostare il percorso di output
Definisci il percorso di output in cui verrà salvato il documento annotato:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Passaggio 2: inizializzare l'annotatore
Inizializzare l'annotatore fornendo il percorso del documento di input:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Passaggio 3: creare un'annotazione ellittica
Crea un'istanza di `EllipseAnnotation` classe e impostarne le proprietà:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
    Replies = new List<Reply>
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
    }
};
```
## Passaggio 4: aggiungere annotazioni
Aggiungere l'annotazione ellisse al documento:
```csharp
annotator.Add(ellipse);
```
## Passaggio 5: Salva il documento
Salvare il documento annotato nel percorso di output:
```csharp
annotator.Save(outputPath);
```

## Conclusione
Congratulazioni! Hai aggiunto correttamente un'annotazione ellittica a un documento utilizzando GroupDocs.Annotation per .NET. Ora puoi integrare questa funzionalità nelle tue applicazioni .NET per migliorare la collaborazione e la comunicazione sui documenti.
## Domande frequenti
### Posso personalizzare l'aspetto dell'annotazione dell'ellisse?
Sì, puoi personalizzare varie proprietà, come il colore di sfondo, il colore del bordo, l'opacità, ecc., in base alle tue esigenze.
### GroupDocs.Annotation per .NET è compatibile con tutti i formati di documento?
GroupDocs.Annotation per .NET supporta un'ampia gamma di formati di documenti, tra cui PDF, DOCX, PPTX, XLSX e altri.
### Posso aggiungere più annotazioni a un singolo documento?
Sì, puoi aggiungere più annotazioni, tra cui ellissi, rettangoli, testo, ecc., a un singolo documento.
### Esiste una versione di prova disponibile per scopi di test?
Sì, puoi scaricare una versione di prova gratuita da [Qui](https://releases.groupdocs.com/) per valutarne le caratteristiche.
### Dove posso ottenere supporto tecnico per GroupDocs.Annotation per .NET?
Puoi ottenere supporto tecnico dal forum della community GroupDocs.Annotation [Qui](https://forum.groupdocs.com/c/annotation/10).