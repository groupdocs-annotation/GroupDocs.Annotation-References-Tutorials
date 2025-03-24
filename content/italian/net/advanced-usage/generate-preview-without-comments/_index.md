---
title: Genera anteprima senza commenti
linktitle: Genera anteprima senza commenti
second_title: API GroupDocs.Annotation .NET
description: Scopri come integrare perfettamente le funzionalità di annotazione dei documenti nelle tue applicazioni .NET utilizzando GroupDocs.Annotation per .NET.
weight: 14
url: /it/net/advanced-usage/generate-preview-without-comments/
---

# Genera anteprima senza commenti

## introduzione
GroupDocs.Annotation per .NET è un potente strumento che consente agli sviluppatori di incorporare funzionalità di annotazione nelle proprie applicazioni .NET senza problemi. Che tu stia lavorando su un sistema di gestione dei documenti, una piattaforma di collaborazione o qualsiasi altra applicazione che richieda funzionalità di annotazione dei documenti, GroupDocs.Annotation fornisce un set completo di strumenti per migliorare la funzionalità della tua applicazione.
## Prerequisiti
Prima di immergerti nell'utilizzo di GroupDocs.Annotation per .NET, assicurati di avere impostati i seguenti prerequisiti:
### 1. Installa GroupDocs.Annotation per .NET
 Per iniziare, devi scaricare e installare GroupDocs.Annotation per .NET. È possibile trovare il collegamento per il download[Qui](https://releases.groupdocs.com/annotation/net/). Seguire le istruzioni di installazione fornite nella documentazione per un processo di installazione agevole.
### 2. Ottieni la licenza
 GroupDocs.Annotation per .NET richiede una licenza per uso commerciale. È possibile acquisire una licenza da[Qui](https://purchase.groupdocs.com/buy) oppure optare per una licenza temporanea[Qui](https://purchase.groupdocs.com/temporary-license/) a scopo di test.
### 3. Familiarità con .NET Framework
La conoscenza di base di .NET Framework e del linguaggio di programmazione C# è essenziale per utilizzare in modo efficace GroupDocs.Annotation per .NET.

## Importa spazi dei nomi
Ora che hai impostato i prerequisiti, importiamo gli spazi dei nomi necessari nell'applicazione .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

Segui queste istruzioni dettagliate per generare un'anteprima senza commenti utilizzando GroupDocs.Annotation per .NET:
## Passaggio 1: inizializza Annotatore
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## Passaggio 2: configura le opzioni di anteprima
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## Passaggio 3: specificare il formato di anteprima e i numeri di pagina
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## Passaggio 4: disabilita il rendering dei commenti
```csharp
    previewOptions.RenderComments = false;
```
## Passaggio 5: genera anteprima
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Dopo aver seguito questi passaggi, l'applicazione .NET sarà in grado di generare un'anteprima delle pagine specificate dal documento senza visualizzare commenti.

## Conclusione
Incorporare funzionalità di annotazione nelle tue applicazioni .NET non è mai stato così semplice grazie a GroupDocs.Annotation per .NET. Seguendo i passaggi descritti in questo tutorial, puoi integrare perfettamente le funzionalità di annotazione dei documenti nelle tue applicazioni, migliorando la collaborazione e la gestione dei documenti.
## Domande frequenti
### GroupDocs.Annotation per .NET è compatibile con tutti i formati di documenti?
GroupDocs.Annotation per .NET supporta un'ampia gamma di formati di documenti, inclusi PDF, DOCX, PPTX, XLSX e altri.
### Posso personalizzare l'aspetto delle annotazioni generate utilizzando GroupDocs.Annotation per .NET?
Sì, GroupDocs.Annotation per .NET fornisce ampie opzioni di personalizzazione, consentendoti di personalizzare l'aspetto delle annotazioni in base alle esigenze della tua applicazione.
### GroupDocs.Annotation per .NET supporta la collaborazione multiutente?
Sì, GroupDocs.Annotation per .NET offre funzionalità di annotazione collaborativa, consentendo a più utenti di annotare documenti contemporaneamente.
### È disponibile supporto tecnico per GroupDocs.Annotation per .NET?
 Sì, il supporto tecnico per GroupDocs.Annotation per .NET è disponibile tramite[Forum di assistenza](https://forum.groupdocs.com/c/annotation/10).
### Posso provare GroupDocs.Annotation per .NET gratuitamente prima dell'acquisto?
 Sì, puoi esplorare le funzionalità di GroupDocs.Annotation per .NET scaricando la versione di prova gratuita[Qui](https://releases.groupdocs.com/).