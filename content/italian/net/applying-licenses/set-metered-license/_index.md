---
title: Imposta la licenza a consumo
linktitle: Imposta la licenza a consumo
second_title: API GroupDocs.Annotation .NET
description: Scopri come impostare una licenza a consumo per GroupDocs.Annotation .NET per l'utilizzo delle risorse e le funzionalità di annotazione dei documenti nelle tue applicazioni .NET.
type: docs
weight: 12
url: /it/net/applying-licenses/set-metered-license/
---
## introduzione
GroupDocs.Annotation per .NET è una potente libreria che consente agli sviluppatori di aggiungere facilmente funzionalità di annotazione di documenti alle proprie applicazioni .NET. Che tu stia creando un sistema di gestione dei documenti, una piattaforma di collaborazione o qualsiasi applicazione che implichi la revisione e il markup dei documenti, GroupDocs.Annotation per .NET fornisce un set completo di strumenti per semplificare il processo.
In questo tutorial approfondiremo il processo di configurazione di una licenza a consumo per GroupDocs.Annotation .NET. Una licenza a consumo ti consente di pagare solo per le risorse che consumi, rendendola una soluzione conveniente per progetti di qualsiasi scala. Seguendo i passaggi descritti di seguito, sarai in grado di integrare perfettamente GroupDocs.Annotation nella tua applicazione .NET ottimizzando l'utilizzo delle risorse e mantenendo il controllo del budget.
## Prerequisiti
Prima di immergerti nel tutorial, assicurati di possedere i seguenti prerequisiti:
1.  GroupDocs.Annotation per .NET Library: scarica la libreria da[sito web](https://releases.groupdocs.com/annotation/net/).
2. Accesso all'account GroupDocs: avrai bisogno di un account GroupDocs per ottenere le chiavi pubbliche e private necessarie per impostare la licenza a consumo. Se non hai ancora un account, puoi registrarti per una prova gratuita[Qui](https://releases.groupdocs.com/).
3. Comprensione di base di C# e .NET Framework: la familiarità con il linguaggio di programmazione C# e .NET Framework sarà utile per implementare i passaggi descritti in questo tutorial.

## Importa spazi dei nomi
Per iniziare, assicurati di importare gli spazi dei nomi necessari nel tuo progetto C#. Questi spazi dei nomi sono essenziali per interagire con la funzionalità GroupDocs.Annotation.
```csharp
using System;
```
## Passaggio 1: ottenere le chiavi pubbliche e private
Prima di impostare la licenza a consumo, devi ottenere le chiavi pubbliche e private dalla dashboard del tuo account GroupDocs.
1. Accedi al tuo account GroupDocs.
2. Passare alla sezione di gestione delle licenze.
3. Copia le chiavi pubbliche e private fornite da GroupDocs.
## Passaggio 2: imposta la licenza a consumo
Una volta ottenute le chiavi pubblica e privata, puoi impostare la licenza a consumo nella tua applicazione .NET.
```csharp
string publicKey = "*****"; // Sostituisci ***** con la tua chiave pubblica
string privateKey = "*****"; // Sostituisci ***** con la tua chiave privata
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Conclusione
In conclusione, impostare una licenza a consumo per GroupDocs.Annotation .NET è un processo semplice che garantisce un utilizzo efficiente delle risorse e un rapporto costo-efficacia per i progetti di annotazione dei documenti. Seguendo i passaggi descritti in questa esercitazione, puoi integrare perfettamente GroupDocs.Annotation nella tua applicazione .NET e migliorare la collaborazione dei documenti e le funzionalità di revisione.
## Domande frequenti
### Posso utilizzare GroupDocs.Annotation for .NET in progetti commerciali?
Sì, GroupDocs.Annotation per .NET può essere utilizzato sia in progetti commerciali che non commerciali. Tuttavia, è necessario acquisire una licenza appropriata in base ai requisiti del progetto.
### È disponibile una versione di prova per GroupDocs.Annotation per .NET?
 Sì, puoi usufruire di una prova gratuita di GroupDocs.Annotation per .NET visitando[questo link](https://releases.groupdocs.com/).
### Come posso ottenere supporto tecnico per GroupDocs.Annotation per .NET?
 È possibile richiedere supporto tecnico visitando il forum GroupDocs[Qui](https://forum.groupdocs.com/c/annotation/10).
### Sono disponibili opzioni di licenza temporanea?
 Sì, puoi ottenere una licenza temporanea da GroupDocs per l'utilizzo a breve termine o per scopi di valutazione. Visita[questo link](https://purchase.groupdocs.com/temporary-license/) per maggiori informazioni.
### Posso personalizzare le funzionalità di annotazione in base ai requisiti del mio progetto?
Sì, GroupDocs.Annotation per .NET offre ampie opzioni di personalizzazione, consentendoti di personalizzare le funzionalità di annotazione in base alle esigenze specifiche del tuo progetto.