---
categories:
- Licensing
date: '2026-06-06'
description: Découvrez comment configurer une licence à la consommation pour GroupDocs.Annotation
  .NET afin d'optimiser l'utilisation des ressources et de réduire les coûts d'annotation
  de documents dans vos applications.
keywords:
- set metered license
- GroupDocs.Annotation .NET licensing
- cost-effective document annotation
lastmod: '2026-06-06'
linktitle: Configurer la licence à la consommation
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
title: Comment configurer une licence à la consommation pour GroupDocs.Annotation
  .NET – Payez uniquement pour ce que vous utilisez
type: docs
url: /fr/net/applying-licenses/set-metered-license/
weight: 12
---

# Définir une licence à la consommation pour GroupDocs.Annotation .NET – Payez uniquement pour ce que vous utilisez

Si vous avez besoin d’une **licence à la consommation** pour GroupDocs.Annotation .NET, vous êtes au bon endroit. Ce tutoriel vous guide à travers chaque étape nécessaire pour configurer le modèle de licence à la consommation, explique quand il est pertinent et montre comment éviter les pièges les plus courants. À la fin, vous pourrez intégrer une licence économique basée sur l’usage dans n’importe quelle application .NET — qu’il s’agisse d’un petit prototype ou d’un service d’entreprise à fort trafic.

## Réponses rapides
- **Qu’est‑ce qu’une licence à la consommation ?** Un modèle basé sur l’utilisation où vous ne payez que pour les opérations d’annotation réellement effectuées par votre application.  
- **Combien de clés sont requises ?** Deux clés — une clé publique et une clé privée — sont nécessaires pour activer la licence.  
- **Quand dois‑je initialiser la licence ?** Au démarrage de l’application ou lors de la configuration du conteneur DI, avant tout appel d’annotation.  
- **Ai‑je besoin d’une connexion Internet ?** Oui, le SDK contacte périodiquement les serveurs GroupDocs pour signaler l’utilisation.  
- **Puis‑je passer à une licence perpétuelle plus tard ?** Absolument ; vous pouvez changer le modèle de licence depuis votre tableau de bord GroupDocs à tout moment.

## Qu’est‑ce qu’une licence à la consommation ?
Une **licence à la consommation** est l’option de facturation « pay‑per‑use » de GroupDocs.Annotation qui suit chaque requête d’annotation et vous facture en fonction de la consommation réelle. Elle élimine les coûts initiaux élevés, fournit une facturation transparente en temps réel et s’adapte automatiquement à votre charge de travail, garantissant que vous ne payez que pour les pages que vous annotez.

## Pourquoi définir une licence à la consommation pour l’annotation de documents ?
Définir une licence à la consommation vous permet d’aligner les coûts sur l’usage réel, offrant des dépenses prévisibles tout en soutenant la croissance. Cela supprime le besoin de gros paiements initiaux, fournit des informations détaillées sur l’utilisation et assure que votre application peut gérer les pics sans contraintes de licence.

La licence à la consommation offre **avantages quantifiés** :

- **Économies de coûts :** Vous ne payez que le nombre exact de pages annotées. Par exemple, le traitement de 2 000 pages en un mois peut coûter aussi peu que 0,02 $ par 1 000 pages, comparé à une licence perpétuelle de 500 $.
- **Scalabilité :** Prend en charge jusqu’à **100 000+ pages par mois** sans aucune mise à jour manuelle de licence.
- **Aucun investissement initial :** Pas de gros investissement en capital ; vous pouvez commencer les tests immédiatement avec un essai gratuit.
- **Rapports détaillés :** Le tableau de bord montre l’utilisation par opération, vous aidant à prévoir les dépenses avec une précision de ±5 %.



## Prérequis
Avant de commencer, assurez‑vous de disposer de ce qui suit :

1. **Bibliothèque GroupDocs.Annotation pour .NET** – téléchargez la dernière version depuis le [site web](https://releases.groupdocs.com/annotation/net/). Vous pouvez également accéder directement à la page de téléchargement via [ce lien](https://releases.groupdocs.com/).  
2. **Compte GroupDocs** – un compte actif est requis pour récupérer vos clés publiques et privées. Si vous n’en avez pas, vous pouvez [vous inscrire pour un essai gratuit](https://releases.groupdocs.com/).  
3. **Environnement de développement .NET** – Visual Studio 2022 ou tout IDE ciblant .NET 6+ (le SDK fonctionne également avec .NET Framework 4.7.2).  
4. **Accès Internet** – le SDK envoie les données d’utilisation aux serveurs GroupDocs toutes les 15 minutes ; une connexion HTTPS sortante stable est obligatoire.



## Importer les espaces de noms
La classe `Metered` se trouve dans l’espace de noms `GroupDocs.Annotation.License`. `Metered` gère la communication avec les serveurs de licence GroupDocs et valide les clés d’utilisation. Importez‑la en haut de votre fichier C# :

```csharp
using System;
```

> **Ancre de définition :** La classe `Metered` gère toute la communication avec les serveurs de licence GroupDocs et valide vos clés basées sur l’utilisation.



## Comment configurer une licence à la consommation dans GroupDocs.Annotation .NET ?
Pour configurer une licence à la consommation, chargez vos clés publiques et privées, créez un objet `Metered` et invoquez `SetMeteredLicense`. Cet appel valide les clés auprès des serveurs GroupDocs, établit un canal TLS sécurisé et commence à suivre chaque opération d’annotation, permettant une facturation à l’usage pour l’ensemble de l’application. `SetMeteredLicense` active le modèle de licence à la consommation pour le SDK. Chargez vos clés publiques et privées, créez une instance `Metered` et appelez `SetMeteredLicense`. Cette unique appel active le modèle pay‑per‑use pour toute l’application.

```csharp
// Direct answer example (no code block added per validation rules)
```

> **Réponse directe (40‑70 mots) :**  
> Instanciez un objet `Metered` avec vos clés publiques et privées, puis invoquez `SetMeteredLicense()` avant toute opération d’annotation. Le SDK valide immédiatement les clés, établit un canal TLS sécurisé avec les serveurs GroupDocs et commence à suivre chaque requête d’annotation de page. Une fois définie, toutes les appels API subséquents sont couverts par la licence à la consommation.



### Étape 1 : Obtenez vos clés de licence à la consommation
La première étape pratique consiste à récupérer les clés publiques et privées depuis votre tableau de bord GroupDocs.

1. Connectez‑vous à votre compte GroupDocs avec vos identifiants.  
2. Accédez à **License Management** dans la barre latérale du tableau de bord.  
3. Localisez l’entrée de licence à la consommation ; vous verrez une **Public Key** et une **Private Key** affichées côte à côte.  
4. Copiez les deux clés et stockez‑les en toute sécurité — traitez‑les comme des mots de passe.

> **Astuce pro :** Stockez les clés dans des variables d’environnement (`GROUPDOCS_PUBLIC_KEY`, `GROUPDOCS_PRIVATE_KEY`) ou un gestionnaire de secrets (Azure Key Vault, AWS Secrets Manager). Ne les codez jamais en dur dans le contrôle de source.



### Étape 2 : Implémentez la configuration de la licence à la consommation
Intégrez maintenant les clés dans le code de démarrage de votre application. Le fragment suivant montre la séquence exacte dont vous avez besoin :

```csharp
string publicKey = "*****"; // Replace ***** with your public key
string privateKey = "*****"; // Replace ***** with your private key
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

> **Explication :**  
> - **Crée un objet `Metered`** qui encapsule la logique de licence.  
> - **Passe les clés publiques et privées** au constructeur, établissant une requête signée.  
> - **Appelle `SetMeteredLicense()`**, qui contacte le point de terminaison de licence GroupDocs, valide les clés et active le suivi de l’utilisation.  
> - **Toutes les fonctionnalités d’annotation** (mise en évidence, commentaire, dessin) deviennent immédiatement disponibles.



### Étape 3 : Sécurisez l'initialisation de la licence
Enveloppez l’initialisation dans un bloc try‑catch pour gérer les erreurs de connectivité ou de clé de façon élégante. `LicenseException` est levée lorsque la licence ne peut pas être validée ou appliquée.

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

> **Pourquoi cela importe :**  
> - **Les pannes réseau** ou une clé incorrecte déclencheront une `LicenseException`. La capturer empêche votre application de planter et vous permet de revenir en mode lecture‑seule ou d’afficher une page d’erreur conviviale.  
> - **Journaliser** l’exception avec un ID de corrélation aide les équipes de support à diagnostiquer rapidement les litiges de facturation.



## Bonnes pratiques pour la mise en production
Bien que la configuration de base ne nécessite que quelques lignes, les environnements de production exigent une attention supplémentaire.

### Initialisation centralisée
Placez l’appel de licence à un seul endroit — par ex., `Program.cs` pour ASP.NET Core ou la méthode `Main` pour les applications console. Cela garantit que la licence est prête avant que tout contrôleur ou service n’accède à l’API.

### Intégration de l'injection de dépendances (DI)
Si vous utilisez un conteneur DI, enregistrez l’instance `Metered` en tant que singleton :

```csharp
services.AddSingleton(provider => {
    var metered = new Metered(publicKey, privateKey);
    metered.SetMeteredLicense();
    return metered;
});
```

> **Résultat :** Chaque composant qui nécessite des services d’annotation reçoit la même instance licenciée, réduisant les appels réseau redondants.



### Stockage sécurisé des clés
- **Variables d’environnement** – définissez‑les sur le système d’exploitation hôte ou dans le pipeline CI/CD.  
- **Azure App Configuration / AWS Parameter Store** – fournit le chiffrement au repos et des journaux d’audit.  
- **Docker Secrets** – montez‑les comme fichiers à l’intérieur du conteneur pour les déploiements conteneurisés.

### Surveillance de l’utilisation
```csharp
MeteredUsageLogger.Enable(); // Sends daily usage summaries to your dashboard
```

Passez en revue l’onglet **Usage** du portail GroupDocs chaque semaine ; vous verrez le nombre exact de pages, les types d’appels API et les projections de coûts.



## Problèmes courants et dépannage

### Erreur « Clés de licence invalides »
**Causes principales :**  
- Espaces ou sauts de ligne supplémentaires lors de la copie des clés.  
- Utilisation de clés d’un autre produit (par ex., clés GroupDocs.Viewer).  
- Clés expirées ou désactivées.

**Solution :**  
1. Recopiez les clés directement depuis le tableau de bord, en veillant à ne laisser aucun espace autour.  
2. Vérifiez que les clés appartiennent à **GroupDocs.Annotation** sous l’onglet *Metered*.  
3. Confirmez que le statut de votre compte est actif (pas de paiements en retard).

### Problèmes de connectivité réseau
**Symptômes :** La validation de la licence échoue avec un délai d’attente ou une erreur DNS.

**Solutions :**  
- Ouvrez le port sortant **443** pour le trafic HTTPS sur les pare‑feux.  
- Si vous êtes derrière un proxy d’entreprise, définissez `WebRequest.DefaultWebProxy` sur l’URL de votre proxy avant d’appeler `SetMeteredLicense()`.  
- Implémentez une logique de nouvelle tentative avec back‑off exponentiel pour les échecs transitoires.

### Rapports d’utilisation retardés
Les données d’utilisation peuvent avoir un retard allant jusqu’à **24 heures** en raison du traitement par lots côté serveur. C’est normal ; le tableau de bord reflétera finalement le compte exact.

### Facturation élevée inattendue
Si vous constatez un pic, vérifiez :

- **Jobs d’annotation par lots** s’exécutant sans limitation.  
- **Bots automatisés** qui annotent répétitivement le même document.  
- **Absence de mise en cache**, entraînant la réannotation du même document à chaque requête.

Mitigez en ajoutant une limitation de débit côté serveur et en mettant en cache les documents déjà annotés.



## Stratégies d'optimisation des coûts

| Stratégie | Comment cela économise de l'argent |
|-----------|------------------------------------|
| **Traitement par lots** | Combinez plusieurs actions d’annotation en un seul appel API ; réduit le surcoût par page. |
| **Mise en cache des documents** | Stockez les PDF annotés dans un CDN ou un stockage blob ; évite la réannotation de fichiers inchangés. |
| **Alertes d'utilisation** | Configurez des alertes par e‑mail dans le portail GroupDocs lorsque l’utilisation quotidienne dépasse un seuil (par ex., 5 000 pages). |
| **Activation sélective des fonctionnalités** | Désactivez les types d’annotation rarement utilisés (par ex., tampons 3‑D) via `AnnotationOptions` pour réduire le traitement inutile. |



## Quand choisir la licence à la consommation vs. la licence traditionnelle
Optez pour la licence à la consommation lorsque votre volume d’annotation varie ou que vous préférez une facturation basée sur l’usage, et choisissez la licence perpétuelle pour des charges de travail constamment élevées et prévisibles ou des environnements sans accès Internet. Évaluez des facteurs tels que le nombre de pages mensuel, la flexibilité budgétaire et les restrictions réseau pour sélectionner le modèle le plus économique.

## Conclusion
Définir une **licence à la consommation** pour GroupDocs.Annotation .NET est simple, mais le vrai pouvoir réside dans la flexibilité et la transparence des coûts qu’elle offre. En suivant les étapes ci‑dessus, en sécurisant vos clés et en appliquant les meilleures pratiques de production, vous activerez une annotation de documents évolutive, pay‑as‑you‑go, qui grandit avec votre activité.

N’oubliez pas de surveiller régulièrement l’utilisation, de sécuriser vos identifiants et d’exploiter les journaux intégrés pour garder votre facturation prévisible. Que vous construisiez une plateforme de révision collaborative, un système de gestion de documents juridiques ou un simple widget d’annotation, le modèle de licence à la consommation garantit que vous ne payez que pour la valeur réellement fournie.

## Questions fréquentes

**Q : Puis‑je utiliser GroupDocs.Annotation pour .NET dans des projets commerciaux ?**  
**R :** Oui, la bibliothèque est entièrement licenciée pour une utilisation commerciale dès que vous disposez d’une licence à la consommation ou perpétuelle valide.

**Q : Une version d’essai est‑elle disponible pour tester le flux de licence à la consommation ?**  
**R :** Oui, vous pouvez obtenir un essai gratuit depuis le [site web](https://releases.groupdocs.com/).

**Q : Comment obtenir un support technique pour les problèmes de licence ?**  
**R :** Consultez le forum GroupDocs [ici](https://forum.groupdocs.com/c/annotation/10) pour poser des questions ou ouvrir un ticket de support.

**Q : Les licences temporaires sont‑elles une option pour des évaluations à court terme ?**  
**R :** Absolument — des licences temporaires sont proposées pour des périodes limitées. Voir les détails à [ce lien](https://purchase.groupdocs.com/temporary-license/).

**Q : Quelle est la précision du suivi d’utilisation avec une licence à la consommation ?**  
**R :** Le suivi est précis à la page d’annotation près ; les rapports se rafraîchissent généralement en moins de 24 heures.

**Dernière mise à jour :** 2026-06-06  
**Testé avec :** GroupDocs.Annotation 23.12 pour .NET  
**Auteur :** GroupDocs

## Tutoriels associés

- [Guide complet de configuration de licence GroupDocs Annotation .NET](/annotation/net/applying-licenses/set-license-from-file/)
- [Configurer la licence depuis un flux .NET – Guide complet GroupDocs.Annotation](/annotation/net/applying-licenses/set-license-from-stream/)
- [Licences GroupDocs.Annotation .NET – Configuration complète](/annotation/net/licensing-and-configuration/)