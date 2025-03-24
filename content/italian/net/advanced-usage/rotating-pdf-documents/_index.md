---
title: Rotazione di documenti PDF
linktitle: Rotazione di documenti PDF
second_title: API GroupDocs.Annotation .NET
description: Scopri come ruotare facilmente i documenti PDF utilizzando Groupdocs.Annotation per .NET. Migliorare l'efficienza della gestione dei documenti.
weight: 22
url: /it/net/advanced-usage/rotating-pdf-documents/
---

# Rotazione di documenti PDF

## introduzione
La rotazione dei documenti PDF può essere un compito cruciale quando si ha a che fare con file che devono essere visualizzati o elaborati in modo diverso. In questo tutorial esploreremo come ruotare i documenti PDF passo dopo passo utilizzando Groupdocs.Annotation per .NET.
## Prerequisiti
Prima di immergerti nel tutorial, assicurati di avere i seguenti prerequisiti:
1.  Groupdocs.Annotation per la libreria .NET: assicurarsi di aver scaricato e installato la libreria Groupdocs.Annotation per .NET. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/annotation/net/).
2. Conoscenza di base della programmazione C#: questo tutorial presuppone una conoscenza di base del linguaggio di programmazione C# e di come lavorare con le librerie .NET.

## Importa spazi dei nomi
Innanzitutto, devi importare gli spazi dei nomi necessari nel tuo progetto C# per accedere alle funzionalità fornite dalla libreria Groupdocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Passaggio 1: caricare il documento PDF
 Inizia caricando il documento PDF che desideri ruotare utilizzando il file`Annotator` classe.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Passaggio 2: impostare la rotazione e l'elaborazione delle pagine
Specifica l'angolo di rotazione e le pagine che desideri ruotare. In questo esempio, ruoteremo la prima pagina di 90 gradi in senso orario.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Passaggio 3: salvare il documento ruotato
Salva il documento PDF ruotato con le modifiche specificate.
```csharp
annotator.Save("result.pdf");
```
## Passaggio 4: Visualizza conferma
Informare l'utente che il documento è stato ruotato correttamente.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Conclusione
Ruotare i documenti PDF è un'operazione fondamentale e con Groupdocs.Annotation per .NET diventa semplice ed efficiente. Seguendo i passaggi descritti in questo tutorial, puoi facilmente ruotare i file PDF in base alle tue esigenze.
## Domande frequenti
### Posso ruotare più pagine in un documento PDF utilizzando Groupdocs.Annotation per .NET?
 Sì, puoi specificare più pagine da ruotare regolando il file`ProcessPages` proprietà di conseguenza.
### Groupdocs.Annotation per .NET è compatibile con tutte le versioni di .NET framework?
Groupdocs.Annotation per .NET supporta un'ampia gamma di versioni di .NET framework, garantendo la compatibilità per la maggior parte degli ambienti di sviluppo.
### Groupdocs.Annotation per .NET fornisce opzioni per ruotare i documenti PDF in direzioni diverse?
Sì, puoi ruotare i documenti PDF in senso orario, antiorario o con angoli personalizzati in base alle tue esigenze.
### Posso integrare Groupdocs.Annotation for .NET nel mio sistema di gestione dei documenti esistente?
Assolutamente sì, Groupdocs.Annotation per .NET offre opzioni di integrazione perfetta, consentendoti di migliorare facilmente le funzionalità di gestione dei documenti.
### È disponibile una versione di prova per Groupdocs.Annotation per .NET?
 Sì, puoi ottenere una versione di prova gratuita da[Qui](https://releases.groupdocs.com/).