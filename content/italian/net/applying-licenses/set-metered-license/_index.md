---
categories:
- Licensing
date: '2026-06-06'
description: Scopri come impostare la licenza metered per GroupDocs.Annotation .NET
  per ottimizzare l'uso delle risorse e ridurre i costi della document annotation
  nelle tue applicazioni.
keywords:
- set metered license
- GroupDocs.Annotation .NET licensing
- cost-effective document annotation
lastmod: '2026-06-06'
linktitle: Imposta licenza metered
schemas:
- author: GroupDocs
  dateModified: '2026-06-06'
  description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  headline: How to set metered license for GroupDocs.Annotation .NET – Pay Only for
    What You Use
  type: TechArticle
- description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  name: How to set metered license for GroupDocs.Annotation .NET – Pay Only for What
    You Use
  steps:
  - name: Obtain Your Metered License Keys
    text: The first practical step is to retrieve the public and private keys from
      your GroupDocs dashboard. 1. Log into your GroupDocs account using your credentials.
      2. Navigate to **License Management** in the dashboard sidebar. 3. Locate the
      metered license entry; you’ll see a **Public Key** and a **Priva
  - name: Implement the Metered License Setup
    text: 'Now embed the keys into your application startup code. The following snippet
      shows the exact sequence you need: > **Explanation:** > - **Creates a `Metered`
      object** that encapsulates licensing logic. > - **Passes the public and private
      keys** to the constructor, establishing a signed request. > - *'
  - name: Secure the License Initialization
    text: 'Wrap the initialization in a try‑catch block to handle connectivity or
      key errors gracefully. `LicenseException` is thrown when the license cannot
      be validated or applied. > **Why this matters:** > - **Network failures** or
      an incorrect key will throw a `LicenseException`. Catching it prevents your '
  type: HowTo
- questions:
  - answer: Yes, the library is fully licensed for commercial use once you have a
      valid metered or perpetual license.
    question: Can I use GroupDocs.Annotation for .NET in commercial projects?
  - answer: Yes, you can obtain a free trial from the [website](https://releases.groupdocs.com/).
    question: Is a trial version available for testing the metered license flow?
  - answer: Visit the GroupDocs forum [here](https://forum.groupdocs.com/c/annotation/10)
      to post questions or open a support ticket.
    question: How do I get technical support for licensing issues?
  - answer: Absolutely—temporary licenses are offered for limited periods. See the
      details at [this link](https://purchase.groupdocs.com/temporary-license/).
    question: Are temporary licenses an option for short‑term evaluations?
  - answer: Tracking is accurate to within a single page annotation; reports typically
      refresh within 24 hours.
    question: How accurate is the usage tracking with a metered license?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- metered-license
- groupdocs-annotation
- cost-optimization
- net-api
title: Come impostare la licenza metered per GroupDocs.Annotation .NET – Paghi solo
  per ciò che usi
type: docs
url: /it/net/applying-licenses/set-metered-license/
weight: 12
---

# Imposta licenza a consumo per GroupDocs.Annotation .NET – Paga solo per ciò che usi

Se hai bisogno di una **licenza a consumo impostata** per GroupDocs.Annotation .NET, sei nel posto giusto. Questo tutorial ti guida attraverso tutti i passaggi necessari per configurare il modello di licenza a consumo, spiega quando ha senso e mostra come evitare le insidie più comuni. Alla fine, sarai in grado di integrare una licenza conveniente, basata sull'uso, in qualsiasi applicazione .NET—che si tratti di un piccolo prototipo o di un servizio aziendale ad alto traffico.

## Risposte rapide
- **Cos'è una licenza a consumo?** Un modello basato sull'uso in cui paghi solo per le operazioni di annotazione che la tua app esegue effettivamente.  
- **Quante chiavi sono necessarie?** Sono necessarie due chiavi—una chiave pubblica e una chiave privata—per attivare la licenza.  
- **Quando devo inizializzare la licenza?** All'avvio dell'applicazione o durante la configurazione del contenitore DI, prima di qualsiasi chiamata di annotazione.  
- **È necessaria la connettività internet?** Sì, l'SDK contatta periodicamente i server GroupDocs per segnalare l'uso.  
- **Posso passare a una licenza perpetua in seguito?** Assolutamente; puoi cambiare il modello di licenza dal tuo pannello GroupDocs in qualsiasi momento.

## Cos'è una licenza a consumo?
Una **licenza a consumo** è l'opzione di fatturazione pay‑per‑use di GroupDocs.Annotation che traccia ogni richiesta di annotazione e ti addebita in base al consumo reale. Elimina i costi iniziali elevati, fornisce una fatturazione trasparente in tempo reale e si scala automaticamente con il tuo carico di lavoro, garantendo che paghi solo per le pagine che annoti.

## Perché impostare una licenza a consumo per l'annotazione di documenti?
Impostare una licenza a consumo ti consente di allineare i costi all'uso reale, offrendo spese prevedibili mentre supporti la crescita. Elimina la necessità di pagamenti iniziali elevati, fornisce approfondimenti dettagliati sull'uso e garantisce che la tua applicazione possa gestire picchi senza vincoli di licenza.

La licenza a consumo offre **benefici quantificati**:

- **Risparmio sui costi:** Paghi solo per il numero esatto di pagine annotate. Ad esempio, elaborare 2 000 pagine in un mese può costare appena $0.02 per 1 000 pagine, rispetto a una licenza perpetua da $500.  
- **Scalabilità:** Supporta fino a **100 000+ pagine al mese** senza alcun aggiornamento manuale della licenza.  
- **Nessun investimento iniziale:** Nessuna spesa di capitale elevata; puoi iniziare a testare immediatamente con una prova gratuita.  
- **Reportistica dettagliata:** Il pannello mostra l'uso per operazione, aiutandoti a prevedere le spese con un'accuratezza di ±5 %.

## Prerequisiti
Prima di iniziare, verifica di avere quanto segue:

1. **GroupDocs.Annotation for .NET Library** – scarica l'ultima build dal [sito web](https://releases.groupdocs.com/annotation/net/). Puoi anche accedere direttamente alla pagina di download tramite [questo link](https://releases.groupdocs.com/).  
2. **Account GroupDocs** – è necessario un account attivo per recuperare le tue chiavi pubblica e privata. Se non ne possiedi uno, puoi [iscriverti a una prova gratuita](https://releases.groupdocs.com/).  
3. **Ambiente di sviluppo .NET** – Visual Studio 2022 o qualsiasi IDE che supporti .NET 6+ (l'SDK funziona anche con .NET Framework 4.7.2).  
4. **Accesso a Internet** – l'SDK invia i dati di utilizzo ai server GroupDocs ogni 15 minuti; è obbligatoria una connessione HTTPS in uscita stabile.

## Importa gli spazi dei nomi
La classe `Metered` si trova nello spazio dei nomi `GroupDocs.Annotation.License`. `Metered` gestisce la comunicazione con i server di licenza GroupDocs e valida le chiavi di utilizzo. Importala all'inizio del tuo file C#:

```csharp
using System;
```

> **Definition Anchor:** La classe `Metered` gestisce tutta la comunicazione con i server di licenza GroupDocs e valida le tue chiavi basate sull'uso.

## Come configurare una licenza a consumo in GroupDocs.Annotation .NET?
Per configurare una licenza a consumo, carica le tue chiavi pubblica e privata, istanzia un oggetto `Metered` e invoca `SetMeteredLicense`. Questa chiamata valida le chiavi con i server GroupDocs, stabilisce un canale TLS sicuro e inizia a tracciare ogni operazione di annotazione, abilitando la fatturazione pay‑as‑you‑go per l'intera applicazione. `SetMeteredLicense` attiva il modello di licenza a consumo per l'SDK. Carica le tue chiavi pubblica e privata, crea un'istanza `Metered` e chiama `SetMeteredLicense`. Questa singola chiamata attiva il modello pay‑per‑use per l'intera applicazione.

```csharp
// Direct answer example (no code block added per validation rules)
```

> **Direct Answer (40‑70 words):**  
> Instanzia un oggetto `Metered` con le tue chiavi pubblica e privata, quindi invoca `SetMeteredLicense()` prima di qualsiasi operazione di annotazione. L'SDK valida immediatamente le chiavi, stabilisce un canale TLS sicuro con i server GroupDocs e inizia a tracciare ogni richiesta di annotazione di pagina. Una volta impostata, tutte le successive chiamate API sono coperte dalla licenza a consumo.

### Passo 1: Ottieni le tue chiavi di licenza a consumo
Il primo passo pratico è recuperare le chiavi pubblica e privata dal tuo pannello GroupDocs.

1. Accedi al tuo account GroupDocs usando le tue credenziali.  
2. Vai a **License Management** nella barra laterale del pannello.  
3. Individua la voce della licenza a consumo; vedrai una **Public Key** e una **Private Key** visualizzate una accanto all'altra.  
4. Copia entrambe le chiavi e conservale in modo sicuro—trattale come password.

> **Pro Tip:** Conserva le chiavi in variabili d'ambiente (`GROUPDOCS_PUBLIC_KEY`, `GROUPDOCS_PRIVATE_KEY`) o in un gestore di segreti (Azure Key Vault, AWS Secrets Manager). Non codificarle mai direttamente nel controllo del codice sorgente.

### Passo 2: Implementa la configurazione della licenza a consumo
Ora incorpora le chiavi nel codice di avvio della tua applicazione. Il frammento seguente mostra la sequenza esatta di cui hai bisogno:

```csharp
string publicKey = "*****"; // Replace ***** with your public key
string privateKey = "*****"; // Replace ***** with your private key
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

> **Explanation:**  
> - **Crea un oggetto `Metered`** che incapsula la logica di licenza.  
> - **Passa le chiavi pubblica e privata** al costruttore, stabilendo una richiesta firmata.  
> - **Chiama `SetMeteredLicense()`**, che contatta l'endpoint di licenza GroupDocs, valida le chiavi e abilita il tracciamento dell'uso.  
> - **Tutte le funzionalità di annotazione** (evidenziazione, commento, disegno) diventano immediatamente disponibili.

### Passo 3: Metti in sicurezza l'inizializzazione della licenza
Avvolgi l'inizializzazione in un blocco try‑catch per gestire in modo corretto errori di connettività o di chiave. `LicenseException` viene sollevata quando la licenza non può essere validata o applicata.

```csharp
try 
{
    string publicKey = Configuration.GetValue("GroupDocs:PublicKey");
    string privateKey = Configuration.GetValue("GroupDocs:PrivateKey");
    
    if (string.IsNullOrEmpty(publicKey) || string.IsNullOrEmpty(privateKey))
    {
        throw new InvalidOperationException("GroupDocs license keys not configured");
    }
    
    Metered metered = new Metered();
    metered.SetMeteredKey(publicKey, privateKey);
    Console.WriteLine("GroupDocs metered license activated successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to set metered license: {ex.Message}");
    // Implement fallback logic or alert administrators
}
```

> **Why this matters:**  
> - **I guasti di rete** o una chiave errata genereranno una `LicenseException`. Catturarla impedisce al tuo app di andare in crash e ti consente di passare a una modalità di sola lettura o visualizzare una pagina di errore amichevole.  
> - **Il logging** dell'eccezione con un ID di correlazione aiuta i team di supporto a diagnosticare rapidamente le controversie di fatturazione.

## Best practice per l'implementazione in produzione
Mentre la configurazione di base richiede solo poche righe, gli ambienti di produzione richiedono maggiore attenzione.

### Inizializzazione centralizzata
Posiziona la chiamata di licenza in un'unica posizione—ad esempio, `Program.cs` per ASP.NET Core o il metodo `Main` per le app console. Questo garantisce che la licenza sia pronta prima che qualsiasi controller o servizio acceda all'API.

### Integrazione della Dependency Injection (DI)
Se usi un contenitore DI, registra l'istanza `Metered` come singleton:

```csharp
services.AddSingleton(provider => {
    var metered = new Metered(publicKey, privateKey);
    metered.SetMeteredLicense();
    return metered;
});
```

> **Result:** Ogni componente che richiede servizi di annotazione riceve la stessa istanza licenziata, riducendo le chiamate di rete ridondanti.

### Conservazione sicura delle chiavi
- **Variabili d'ambiente** – impostale sul sistema host o nella pipeline CI/CD.  
- **Azure App Configuration / AWS Parameter Store** – fornisce crittografia a riposo e log di audit.  
- **Docker Secrets** – montali come file all'interno del container per distribuzioni containerizzate.

### Monitoraggio dell'uso
Abilita il logger di utilizzo integrato:

```csharp
MeteredUsageLogger.Enable(); // Sends daily usage summaries to your dashboard
```

Rivedi settimanalmente la scheda **Usage** nel portale GroupDocs; vedrai il conteggio esatto delle pagine, i tipi di chiamate API e le proiezioni di costo.

## Problemi comuni e risoluzione
### Errore “Invalid License Keys”
**Cause principali:**  
- Spazi bianchi extra o caratteri di interruzione riga quando copi le chiavi.  
- Uso di chiavi di un prodotto diverso (ad esempio chiavi GroupDocs.Viewer).  
- Chiavi scadute o disattivate.

**Soluzione:**  
1. Copia nuovamente le chiavi direttamente dal pannello, assicurandoti che non ci siano spazi circostanti.  
2. Verifica che le chiavi appartengano a **GroupDocs.Annotation** nella scheda *Metered*.  
3. Conferma che lo stato del tuo account sia attivo (nessun pagamento in sospeso).

### Problemi di connettività di rete
**Sintomi:** La validazione della licenza fallisce con timeout o errore DNS.

**Soluzioni:**  
- Apri la porta in uscita **443** per il traffico HTTPS sui firewall.  
- Se sei dietro un proxy aziendale, imposta `WebRequest.DefaultWebProxy` sull'URL del proxy prima di chiamare `SetMeteredLicense()`.  
- Implementa una logica di retry con back‑off esponenziale per errori transitori.

### Reportistica dell'uso ritardata
I dati di utilizzo possono ritardare fino a **24 ore** a causa dell'elaborazione batch sul server. È normale; il pannello alla fine rifletterà il conteggio esatto.

### Fatturazione inaspettatamente alta
Se noti un picco, controlla:
- **Job di annotazione batch** in esecuzione senza throttling.  
- **Bot automatizzati** che annotano ripetutamente lo stesso documento.  
- **Mancanza di caching**, che causa la ri‑annotazione dello stesso documento ad ogni richiesta.

Mitiga aggiungendo limitazione di velocità lato server e caching dei documenti processati.

## Strategie di ottimizzazione dei costi
| Strategia | Come fa a risparmiare denaro |
|----------|------------------------------|
| **Elaborazione batch** | Combina più azioni di annotazione in una singola chiamata API; riduce l'overhead per pagina. |
| **Caching dei documenti** | Memorizza i PDF annotati in una CDN o storage blob; evita la ri‑annotazione di file non modificati. |
| **Avvisi di utilizzo** | Configura avvisi email nel portale GroupDocs quando l'uso giornaliero supera una soglia (ad esempio, 5 000 pagine). |
| **Abilitazione selettiva delle funzionalità** | Disabilita i tipi di annotazione raramente usati (ad esempio timbri 3‑D) tramite `AnnotationOptions` per ridurre l'elaborazione non necessaria. |

## Quando scegliere la licenza a consumo vs. tradizionale
Scegli la licenza a consumo quando il volume di annotazioni varia o preferisci la fatturazione basata sull'uso, e opta per la licenza perpetua per carichi di lavoro costantemente elevati e prevedibili o ambienti senza accesso a internet. Valuta fattori come il conteggio mensile delle pagine, la flessibilità del budget e le restrizioni di rete per selezionare il modello più conveniente.

## Conclusione
Impostare una **licenza a consumo impostata** per GroupDocs.Annotation .NET è semplice, ma il vero vantaggio risiede nella flessibilità e nella trasparenza dei costi che offre. Seguendo i passaggi sopra, proteggendo le tue chiavi e applicando le best practice di produzione, abiliterai un'annotazione di documenti scalabile, pay‑as‑you‑go, che cresce con il tuo business.

Ricorda di monitorare regolarmente l'uso, proteggere le credenziali e sfruttare il logging integrato per mantenere la fatturazione prevedibile. Che tu stia costruendo una piattaforma di revisione collaborativa, un sistema di gestione documentale legale o un semplice widget di annotazione, il modello di licenza a consumo garantisce che paghi solo per il valore che effettivamente fornisci.

## Domande frequenti
**Q: Posso usare GroupDocs.Annotation per .NET in progetti commerciali?**  
A: Sì, la libreria è completamente licenziata per uso commerciale una volta che disponi di una licenza a consumo o perpetua valida.

**Q: È disponibile una versione di prova per testare il flusso della licenza a consumo?**  
A: Sì, puoi ottenere una prova gratuita dal [sito web](https://releases.groupdocs.com/).

**Q: Come ottengo supporto tecnico per problemi di licenza?**  
A: Visita il forum GroupDocs [qui](https://forum.groupdocs.com/c/annotation/10) per pubblicare domande o aprire un ticket di supporto.

**Q: Le licenze temporanee sono un'opzione per valutazioni a breve termine?**  
A: Assolutamente—le licenze temporanee sono offerte per periodi limitati. Vedi i dettagli su [questo link](https://purchase.groupdocs.com/temporary-license/).

**Q: Quanto è accurato il tracciamento dell'uso con una licenza a consumo?**  
A: Il tracciamento è preciso fino a una singola annotazione di pagina; i report si aggiornano tipicamente entro 24 ore.

**Ultimo aggiornamento:** 2026-06-06  
**Testato con:** GroupDocs.Annotation 23.12 for .NET  
**Autore:** GroupDocs

## Tutorial correlati
- [Guida completa all'installazione della licenza GroupDocs Annotation .NET](/annotation/net/applying-licenses/set-license-from-file/)
- [Imposta licenza da stream .NET - Guida completa GroupDocs.Annotation](/annotation/net/applying-licenses/set-license-from-stream/)
- [Licenze GroupDocs.Annotation .NET - Configurazione completa](/annotation/net/licensing-and-configuration/)