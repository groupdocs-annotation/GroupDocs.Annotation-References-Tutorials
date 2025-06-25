---
"description": "Scopri come impostare una licenza a consumo per GroupDocs.Annotation .NET per l'utilizzo delle risorse e le funzionalità di annotazione dei documenti nelle tue applicazioni .NET."
"linktitle": "Imposta licenza a consumo"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Imposta licenza a consumo"
"url": "/it/net/applying-licenses/set-metered-license/"
"weight": 12
---

# Imposta licenza a consumo

## Introduzione
GroupDocs.Annotation per .NET è una potente libreria che consente agli sviluppatori di aggiungere funzionalità di annotazione dei documenti alle proprie applicazioni .NET con estrema facilità. Che si stia sviluppando un sistema di gestione documentale, una piattaforma di collaborazione o qualsiasi applicazione che implichi la revisione e la marcatura dei documenti, GroupDocs.Annotation per .NET offre un set completo di strumenti per semplificare il processo.
In questo tutorial, approfondiremo il processo di configurazione di una licenza a consumo per GroupDocs.Annotation .NET. Una licenza a consumo consente di pagare solo per le risorse effettivamente utilizzate, rendendola una soluzione conveniente per progetti di qualsiasi dimensione. Seguendo i passaggi descritti di seguito, sarà possibile integrare GroupDocs.Annotation in modo ottimale nella propria applicazione .NET, ottimizzando l'utilizzo delle risorse e mantenendo il controllo del budget.
## Prerequisiti
Prima di immergerti nel tutorial, assicurati di disporre dei seguenti prerequisiti:
1. GroupDocs.Annotation per la libreria .NET: scarica la libreria da [sito web](https://releases.groupdocs.com/annotation/net/).
2. Accesso all'account GroupDocs: è necessario un account GroupDocs per ottenere le chiavi pubblica e privata necessarie per impostare la licenza a consumo. Se non si dispone ancora di un account, è possibile registrarsi per una prova gratuita. [Qui](https://releases.groupdocs.com/).
3. Nozioni di base di C# e .NET Framework: la familiarità con il linguaggio di programmazione C# e .NET Framework sarà utile per implementare i passaggi descritti in questo tutorial.

## Importa spazi dei nomi
Per iniziare, assicurati di importare gli spazi dei nomi necessari nel tuo progetto C#. Questi spazi dei nomi sono essenziali per interagire con la funzionalità GroupDocs.Annotation.
```csharp
using System;
```
## Passaggio 1: ottenere le chiavi pubbliche e private
Prima di impostare la licenza a consumo, è necessario ottenere le chiavi pubblica e privata dalla dashboard dell'account GroupDocs.
1. Accedi al tuo account GroupDocs.
2. Accedere alla sezione di gestione delle licenze.
3. Copia le tue chiavi pubblica e privata fornite da GroupDocs.
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
In conclusione, configurare una licenza a consumo per GroupDocs.Annotation .NET è un processo semplice che garantisce un utilizzo efficiente delle risorse e un ottimo rapporto costi-benefici per i vostri progetti di annotazione dei documenti. Seguendo i passaggi descritti in questo tutorial, potrete integrare perfettamente GroupDocs.Annotation nella vostra applicazione .NET e migliorare le funzionalità di collaborazione e revisione dei documenti.
## Domande frequenti
### Posso utilizzare GroupDocs.Annotation per .NET in progetti commerciali?
Sì, GroupDocs.Annotation per .NET può essere utilizzato sia in progetti commerciali che non commerciali. Tuttavia, è necessario acquistare una licenza appropriata in base ai requisiti del progetto.
### Esiste una versione di prova disponibile per GroupDocs.Annotation per .NET?
Sì, puoi usufruire di una prova gratuita di GroupDocs.Annotation per .NET visitando [questo collegamento](https://releases.groupdocs.com/).
### Come posso ottenere supporto tecnico per GroupDocs.Annotation per .NET?
Puoi cercare supporto tecnico visitando il forum GroupDocs [Qui](https://forum.groupdocs.com/c/annotation/10).
### Sono disponibili opzioni di licenza temporanea?
Sì, puoi ottenere una licenza temporanea da GroupDocs per un utilizzo a breve termine o per scopi di valutazione. Visita [questo collegamento](https://purchase.groupdocs.com/temporary-license/) per maggiori informazioni.
### Posso personalizzare le funzionalità di annotazione in base alle esigenze del mio progetto?
Sì, GroupDocs.Annotation per .NET offre ampie opzioni di personalizzazione, consentendo di adattare le funzionalità di annotazione alle esigenze specifiche del progetto.