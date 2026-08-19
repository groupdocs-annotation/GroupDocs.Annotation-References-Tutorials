---
categories:
- Java Development
date: '2026-08-19'
description: Apprenez à définir la licence GroupDocs via InputStream pour Java Annotation.
  Guide étape par étape avec dépannage, bonnes pratiques et exemples concrets pour
  une intégration fluide.
keywords:
- set groupdocs license
- groupdocs annotation java inputstream
- java licensing with inputstream
- groupdocs license configuration
- java annotation licensing guide
lastmod: '2026-08-19'
linktitle: Configuration de la licence InputStream en Java
og_description: Définissez la licence GroupDocs à l'aide d'InputStream en Java Annotation.
  Suivez ce tutoriel étape par étape, découvrez les meilleures pratiques et évitez
  les pièges courants de licence.
og_image_alt: Developer guide showing Java code to load GroupDocs license via InputStream
og_title: Définir la licence GroupDocs InputStream en Java Annotation – Guide complet
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to set GroupDocs license InputStream for Java Annotation.
    Step-by-step guide with troubleshooting, best practices, and real-world examples
    for seamless integration.
  headline: How to set groupdocs license InputStream in Java Annotation
  type: TechArticle
- description: Learn how to set GroupDocs license InputStream for Java Annotation.
    Step-by-step guide with troubleshooting, best practices, and real-world examples
    for seamless integration.
  name: How to set groupdocs license InputStream in Java Annotation
  steps:
  - name: robust license path definition
    text: Define the path to the license file in a way that can be overridden by an
      environment variable. This makes the code portable across dev, test, and production
      environments. **Pro tip:** Store the path in a configuration property (e.g.,
      `groupdocs.license.path`) instead of hard‑coding it. This elimina
  - name: enhanced file existence check
    text: Before opening the file, verify that it exists and is readable. This prevents
      cryptic `FileNotFoundException` later in the startup sequence. If the file is
      missing, you can fall back to a classpath resource or abort with a clear log
      message.
  - name: proper inputstream management
    text: Use Java’s try‑with‑resources statement to guarantee that the `InputStream`
      is closed, even if an exception occurs. Leaking streams in a long‑running service
      can eventually exhaust file descriptors.
  - name: license application with validation
    text: '`setLicense(InputStream)` applies the provided license stream to all GroupDocs
      components. Immediately after setting, call `License.isValidLicense()` to ensure
      the license was parsed correctly. If validation fails, log the error and optionally
      switch to a fallback (e.g., a trial license) to keep the'
  - name: comprehensive license verification
    text: LicenseInfo holds details about the loaded license such as expiration date,
      feature flags, and allowed domains. This extra check is useful in multi‑tenant
      SaaS scenarios.
  type: HowTo
- questions:
  - answer: Yes, but review your license agreement—some plans are per‑application
      or per‑server. InputStream loading makes sharing straightforward.
    question: Can I use the same license file for multiple applications?
  - answer: GroupDocs.Annotation falls back to trial mode, adding watermarks and limiting
      premium features. Continuously monitor `License.isValidLicense()` to trigger
      renewal workflows.
    question: What happens if my license expires during runtime?
  - answer: At the moment a full JVM restart is required for a new license to take
      effect. Use blue‑green deployments or rolling restarts to minimise downtime.
    question: How do I handle license updates without restarting the app?
  - answer: Log the error message and stack trace, but never log the raw license content
      or private keys. Keep logs actionable yet secure.
    question: Is it safe to log license validation errors?
  - answer: Absolutely. Retrieve the bytes, wrap them in a `ByteArrayInputStream`,
      and pass it to `License.setLicense()`. This works with S3, Azure Blob, Google
      Cloud Storage, and even private HTTP endpoints.
    question: Can I load the license from a cloud storage bucket?
  type: FAQPage
tags:
- groupdocs
- java
- licensing
- inputstream
- configuration
title: Comment définir le flux d'entrée (InputStream) de la licence GroupDocs en Java
  Annotation
type: docs
url: /fr/java/licensing-and-configuration/groupdocs-annotation-java-inputstream-license-setup/
weight: 1
---

# Définir la licence GroupDocs

## Introduction

Dans ce guide, vous apprendrez **comment définir la licence GroupDocs** en utilisant un `InputStream` pour Java Annotation. Configurer la licence pour GroupDocs.Annotation en Java peut sembler intimidant, surtout lorsque vous travaillez avec des environnements dynamiques ou des applications conteneurisées. Bonne nouvelle ? Utiliser **InputStream** pour la configuration de la licence est en fait l’une des approches les plus flexibles et fiables disponibles.

Vous parcourrez une implémentation complète prête pour la production, verrez comment gérer les erreurs de manière élégante et découvrirez des astuces pour le cloud, Docker et les déploiements on‑prem. À la fin, vous serez sûr que votre application valide correctement la licence et peut se remettre des problèmes courants sans redémarrage pénible.

**Ce que vous maîtriserez à la fin :**
- Configuration complète de la licence via InputStream (avec gestion réelle des erreurs)
- Dépannage des problèmes courants de licence
- Meilleures pratiques pour différents scénarios de déploiement
- Conseils d’optimisation des performances qui comptent réellement

## Réponses rapides
`License.isValidLicense()` est une méthode qui renvoie **true** lorsque la licence chargée est valide.

- **Quelle est la façon principale de charger une licence GroupDocs ?** En utilisant un `InputStream` avec `License.setLicense(stream)`.
- **Puis‑je stocker la licence dans un bucket cloud ?** Oui, lisez‑la dans un `InputStream` depuis n’importe quelle source de stockage.
- **Dois‑je redémarrer après avoir changé la licence ?** Actuellement, un redémarrage est requis pour que la nouvelle licence prenne effet.
- **La licence via InputStream est‑elle adaptée aux conteneurs ?** Absolument – aucune dépendance de chemin de fichier.
- **Comment vérifier que la licence est active ?** Appelez `License.isValidLicense()` après l’avoir définie.

## Pourquoi choisir InputStream pour la licence GroupDocs ?

La licence via InputStream vous permet de charger la licence depuis n’importe quelle source — disque local, stockage cloud ou ressource intégrée—sans dépendre d’un chemin de fichier fixe. Cette approche fonctionne de manière uniforme sur les environnements de développement, les conteneurs et les environnements serverless, simplifie la gestion des secrets et réduit le risque d’échecs liés aux chemins.

## Prérequis et configuration de l’environnement

Avant d’implémenter la configuration de licence GroupDocs.Annotation Java via InputStream, assurez‑vous d’avoir :

### Exigences essentielles
- **Kit de développement Java :** JDK 8 ou supérieur (JDK 11+ recommandé pour de meilleures performances)  
- **GroupDocs.Annotation pour Java :** Version 25.2 ou ultérieure (la bibliothèque prend en charge **plus de 50** formats d’entrée et de sortie)  
- **Outil de construction :** Maven ou Gradle (les exemples utilisent Maven)  
- **Licence valide :** licence d’essai, temporaire ou complète de GroupDocs  

### Environnement de développement
- **IDE :** IntelliJ IDEA, Eclipse ou VS Code avec extensions Java  
- **Mémoire :** Au moins 4 Go de RAM pour un développement fluide (8 Go+ pour les gros documents)  
- **Stockage :** Espace disque suffisant pour vos besoins de traitement de documents  

## Configurer groupdocs.annotation pour Java

### Configuration Maven

Ajoutez la dépendance suivante à votre `pom.xml`. L’entrée du dépôt est requise pour récupérer les derniers paquets GroupDocs :

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

### Configuration Gradle (alternative)

Si vous préférez Gradle, utilisez le fragment équivalent :

```gradle
repositories {
    maven {
        url 'https://releases.groupdocs.com/annotation/java/'
    }
}

dependencies {
    implementation 'com.groupdocs:groupdocs-annotation:25.2'
}
```

### Préparation du fichier de licence

Votre fichier de licence GroupDocs (généralement avec une extension `.lic`) doit être :

- **Accessible :** Placez‑le dans `src/main/resources` ou dans un emplacement externe sécurisé.  
- **Valide :** Vérifiez la date d’expiration et les autorisations de fonctionnalités dans le portail de licence.  
- **Lisible :** Assurez‑vous que l’utilisateur d’exécution possède les permissions de lecture (`chmod 600` sous Linux).  

## Comment définir la licence GroupDocs via InputStream

Charger la licence depuis un `InputStream` est un processus en quatre étapes incluant la validation et la gestion élégante des erreurs.

### Réponse directe
`License` est la classe GroupDocs qui active une licence pour la bibliothèque.  
`FileInputStream` est une classe Java qui lit les octets bruts d’un fichier.  
`InputStream` est une classe abstraite Java représentant un flux d’octets pour la lecture de données.  

Chargez le fichier de licence dans un `FileInputStream` (ou tout autre `InputStream`), transmettez‑le à `new License().setLicense(stream)`, puis appelez `license.isValidLicense()` pour confirmer le succès. Enveloppez l’opération complète dans un bloc *try‑with‑resources* afin que le flux se ferme automatiquement, et journalisez toute exception pour un dépannage rapide.

### Étape 1 : définition robuste du chemin de licence

Définissez le chemin du fichier de licence de manière à pouvoir le remplacer via une variable d’environnement. Cela rend le code portable entre les environnements de dev, test et production.

```java
String licensePath = YOUR_DOCUMENT_DIRECTORY + "/your-license-file.lic";
```

**Astuce :** Stockez le chemin dans une propriété de configuration (par ex., `groupdocs.license.path`) au lieu de le coder en dur. Cela élimine le besoin de reconstruire lors du déplacement entre serveurs.

### Étape 2 : vérification renforcée de l’existence du fichier

Avant d’ouvrir le fichier, vérifiez qu’il existe et qu’il est lisible. Cela évite les `FileNotFoundException` cryptiques plus tard dans la séquence de démarrage.

```java
if (new File(licensePath).isFile()) {
    // Proceed with setting the license
} else {
    System.err.println("License file not found at: " + licensePath);
    // Handle the missing file scenario appropriately
}
```

Si le fichier est absent, vous pouvez revenir à une ressource du classpath ou interrompre le démarrage avec un message de journal clair.

### Étape 3 : gestion correcte de l’InputStream

Utilisez l’instruction *try‑with‑resources* de Java pour garantir que l’`InputStream` est fermé, même en cas d’exception. Les fuites de flux dans un service de longue durée peuvent finir par épuiser les descripteurs de fichiers.

```java
try (InputStream stream = new FileInputStream(licensePath)) {
    // Continue with setting the license using this stream
} catch (FileNotFoundException e) {
    System.err.println("License file could not be opened: " + e.getMessage());
    // Handle appropriately - maybe fall back to trial mode
} catch (IOException e) {
    System.err.println("Error reading license file: " + e.getMessage());
    // Log and handle the error
}
```

### Étape 4 : application de la licence avec validation

`setLicense(InputStream)` applique le flux de licence fourni à tous les composants GroupDocs. Immédiatement après l’appel, invoquez `License.isValidLicense()` pour vous assurer que la licence a été correctement analysée.

```java
License license = new License();
try {
    license.setLicense(stream);
    System.out.println("License applied successfully");
} catch (Exception e) {
    System.err.println("Failed to apply license: " + e.getMessage());
    // Handle license application failure
}
```

Si la validation échoue, journalisez l’erreur et, éventuellement, basculez vers une solution de secours (par ex., une licence d’essai) pour maintenir le service en vie.

### Étape 5 : vérification complète de la licence

`LicenseInfo` contient les détails de la licence chargée tels que la date d’expiration, les drapeaux de fonctionnalités et les domaines autorisés. Cette vérification supplémentaire est utile dans les scénarios SaaS multi‑locataires.

```java
if (!License.isValidLicense()) {
    System.out.println("License validation failed - running in trial mode");
    // Implement fallback behavior for trial mode
} else {
    System.out.println("License is valid and active");
}
```

## Comparaison des méthodes de licence alternatives

Comprendre vos options vous aide à choisir la bonne approche pour votre cas d’utilisation spécifique :

### Chemin de fichier vs. InputStream vs. licence intégrée

**Licence par chemin de fichier :**  
- ✅ Simple à implémenter avec une seule ligne de code.  
- ❌ Pose problème dans les conteneurs où les chemins absolus diffèrent entre les builds.  

**Licence via InputStream (recommandée) :**  
- ✅ Fonctionne avec n’importe quel backend de stockage (local, S3, Azure Blob, base de données).  
- ✅ Aucun dépendance de système de fichiers codée en dur.  
- ❌ Un peu plus de code, mais la flexibilité l’emporte sur la surcharge.  

**Licence intégrée :**  
- ✅ Aucun fichier externe requis ; la licence est intégrée dans le JAR.  
- ❌ Mettre à jour la licence nécessite une nouvelle construction et un redéploiement.  

## Scénarios de déploiement courants

### Scénario 1 : déploiement serveur traditionnel

Pour les serveurs on‑prem, vous stockez généralement la licence dans un répertoire de configuration et la référencez via une variable d’environnement :

```java
// Example for server deployment
String licensePath = System.getProperty("app.config.dir", "/etc/myapp/") + "license.lic";
```

### Scénario 2 : déploiement conteneur Docker

Montez la licence comme volume secret ou injectez‑la via un script d’entrée qui écrit le fichier dans `/opt/groupdocs/license.lic` :

```java
// Docker-friendly approach
String licensePath = System.getenv("LICENSE_PATH");
if (licensePath == null) {
    licensePath = "/app/config/license.lic"; // default fallback
}
```

### Scénario 3 : applications cloud‑native

`ByteArrayInputStream` est une classe Java qui crée un `InputStream` à partir d’un tableau d’octets. Récupérez la licence depuis un bucket de stockage cloud (AWS S3, Azure Blob, Google Cloud Storage), convertissez le tableau d’octets en `ByteArrayInputStream`, puis transmettez‑le à `License.setLicense()` :

```java
// Example: Loading from cloud storage (pseudo-code)
// You'd implement the actual cloud storage client
InputStream licenseStream = cloudStorageClient.getObject("bucket", "license.lic");
```

## Guide avancé de dépannage

### Erreur courante : « license is not valid »

**Symptômes :** `License.isValidLicense()` renvoie `false`.  
**Causes :** licence expirée, édition du produit non correspondante, fichier corrompu ou mauvais format de fichier.  
**Solution :** Vérifiez le fichier de licence sur le portail GroupDocs, téléchargez‑le à nouveau et assurez‑vous que le flux d’octets n’est pas altéré pendant le transport.

```java
// Add detailed license validation
try {
    license.setLicense(stream);
    if (License.isValidLicense()) {
        System.out.println("License valid until: " + license.getExpirationDate());
    } else {
        System.out.println("License validation failed - check license file and expiration");
    }
} catch (Exception e) {
    System.err.println("License error details: " + e.getMessage());
}
```

### Erreur courante : `FileNotFoundException`

**Symptômes :** L’application ne peut pas localiser le fichier de licence à l’exécution.  
**Causes :** mauvaise configuration du chemin, fichier manquant dans l’image Docker ou permissions de fichier insuffisantes.  
**Solution :** Implémentez une solution de secours qui vérifie d’abord une variable d’environnement, puis recherche une ressource du classpath, et enfin journalise une erreur claire avant d’interrompre le démarrage.

```java
String[] possiblePaths = {
    System.getProperty("license.path"),
    "./license.lic",
    "/etc/myapp/license.lic",
    System.getProperty("user.home") + "/myapp/license.lic"
};

InputStream stream = null;
for (String path : possiblePaths) {
    if (path != null && new File(path).exists()) {
        stream = new FileInputStream(path);
        break;
    }
}
```

### Erreur courante : problèmes de mémoire avec de gros documents

`setMemoryOptimization(boolean)` active le mode d’économie de mémoire dans GroupDocs lorsqu’il est réglé sur **true**.  
**Symptômes :** `OutOfMemoryError` lors du traitement d’annotation.  
**Causes :** chargement du document entier en mémoire, heap JVM insuffisant ou absence d’options de traitement basées sur les flux.  
**Solution :** Augmentez le heap JVM (`-Xmx2g` ou plus), activez `License.setMemoryOptimization(true)` et traitez les documents par morceaux lorsque cela est possible.

```java
// Set appropriate JVM flags
// -Xmx4g -XX:+UseG1GC -XX:MaxGCPauseMillis=200
```

## Meilleures pratiques d’optimisation des performances

### Gestion de la mémoire

Lorsque vous travaillez avec GroupDocs.Annotation, activez le chargement paresseux et libérez les ressources rapidement :

```java
// Always close resources properly
try (Annotator annotator = new Annotator("document.pdf")) {
    // Process annotations
    annotator.save("output.pdf");
} // Automatically closes and frees resources
```

### Optimisation du traitement par lots

Pour les travaux d’annotation en masse, réutilisez une seule instance `License` et traitez les documents dans un exécuteur à pool de threads afin de maximiser l’utilisation du CPU sans surcharger la mémoire.

```java
// Process documents in batches to manage memory
List<String> documents = getDocumentList();
int batchSize = 10;

for (int i = 0; i < documents.size(); i += batchSize) {
    List<String> batch = documents.subList(i, Math.min(i + batchSize, documents.size()));
    processBatch(batch);
    // Force garbage collection between batches if needed
    System.gc();
}
```

### Mise en cache de la validation de licence

Mettez en cache le résultat de `License.isValidLicense()` dans une variable statique ou un cache distribué (par ex., Redis) afin d’éviter des lectures répétées du système de fichiers à chaque requête.

```java
private static Boolean licenseValid = null;

public static boolean isLicenseValid() {
    if (licenseValid == null) {
        licenseValid = License.isValidLicense();
    }
    return licenseValid;
}
```

## Considérations de sécurité

### Protection des fichiers de licence

**Chiffrement :** Stockez la licence chiffrée au repos et déchiffrez‑la en mémoire avant de créer l’`InputStream`.

```java
// Example: Reading encrypted license file
byte[] encryptedLicense = Files.readAllBytes(Paths.get(licensePath));
byte[] decryptedLicense = decrypt(encryptedLicense);
InputStream stream = new ByteArrayInputStream(decryptedLicense);
```

**Contrôle d’accès :** Définissez les permissions du fichier à `600` (lecture/écriture uniquement pour le propriétaire) sous Linux ou restreignez les ACL sous Windows.  

**Variables d’environnement :** Utilisez un gestionnaire de secrets (AWS Secrets Manager, Azure Key Vault) pour conserver le chemin de la licence ou le contenu de la licence encodé en Base64, et lisez‑le au démarrage.

```java
String licensePath = System.getenv("GROUPDOCS_LICENSE_PATH");
```

## Checklist de déploiement en production

- [ ] Accessibilité du fichier de licence vérifiée dans l’environnement cible  
- [ ] Gestion des erreurs implémentée pour tous les scénarios d’échec  
- [ ] Journalisation configurée pour les événements liés à la licence (INFO en cas de succès, WARN en cas d’échec)  
- [ ] Tests de performance réalisés avec des tailles de documents réalistes (par ex., PDF de 200 pages)  
- [ ] Revue de sécurité de la gestion du fichier de licence (chiffrement, permissions)  
- [ ] Plan de secours pour les scénarios d’expiration de licence (alertes de surveillance)  
- [ ] Surveillance mise en place pour les échecs de validation de licence (métrique Prometheus `groupdocs_license_valid`)  

## Exemples d’intégration réels

### Intégration Spring Boot

Intégrez la logique de licence dans une méthode `@PostConstruct` d’un bean Spring afin qu’elle s’exécute une fois au démarrage de l’application :

```java
@Component
public class GroupDocsLicenseManager {
    
    @Value("${groupdocs.license.path:license.lic}")
    private String licensePath;
    
    @PostConstruct
    public void initializeLicense() {
        try (InputStream stream = new FileInputStream(licensePath)) {
            License license = new License();
            license.setLicense(stream);
            
            if (License.isValidLicense()) {
                log.info("GroupDocs license applied successfully");
            } else {
                log.warn("GroupDocs license validation failed");
            }
        } catch (Exception e) {
            log.error("Failed to initialize GroupDocs license", e);
        }
    }
}
```

### Modèle microservices

Exposez un **Service de licence** dédié que les autres microservices appellent via gRPC ou REST pour obtenir un `InputStream` validé. Cela centralise la gestion des secrets et réduit les duplications.

```java
@Service
public class LicenseService {
    private static final AtomicBoolean licenseInitialized = new AtomicBoolean(false);
    
    public void ensureLicense() {
        if (licenseInitialized.compareAndSet(false, true)) {
            // Initialize license once per service instance
            initializeLicense();
        }
    }
}
```

### Chargement de la licence depuis une base de données

Stockez le blob `.lic` dans une table sécurisée, lisez‑le avec JDBC, encapsulez les octets dans un `ByteArrayInputStream`, puis appliquez la licence :

```java
byte[] licenseData = loadLicenseFromDatabase();
InputStream stream = new ByteArrayInputStream(licenseData);
```

## Questions fréquentes

**Q : Puis‑je utiliser le même fichier de licence pour plusieurs applications ?**  
R : Oui, mais vérifiez votre contrat de licence — certains plans sont par application ou par serveur. Le chargement via InputStream rend le partage simple.

**Q : Que se passe‑t‑il si ma licence expire pendant l’exécution ?**  
R : GroupDocs.Annotation repasse en mode essai, ajoute des filigranes et limite les fonctionnalités premium. Surveillez continuellement `License.isValidLicense()` pour déclencher les workflows de renouvellement.

**Q : Comment gérer les mises à jour de licence sans redémarrer l’application ?**  
R : Pour l’instant, un redémarrage complet de la JVM est requis pour qu’une nouvelle licence prenne effet. Utilisez des déploiements blue‑green ou des redémarrages progressifs pour minimiser les temps d’arrêt.

**Q : Est‑il sûr de journaliser les erreurs de validation de licence ?**  
R : Journalisez le message d’erreur et la trace de la pile, mais ne journalisez jamais le contenu brut de la licence ni les clés privées. Gardez les journaux exploitables tout en restant sécurisés.

**Q : Puis‑je charger la licence depuis un bucket de stockage cloud ?**  
R : Absolument. Récupérez les octets, encapsulez‑les dans un `ByteArrayInputStream`, puis transmettez‑les à `License.setLicense()`. Cela fonctionne avec S3, Azure Blob, Google Cloud Storage et même des points de terminaison HTTP privés.

## Conclusion

Vous disposez maintenant d’un guide complet et prêt pour la production sur **comment définir la licence GroupDocs** en utilisant un `InputStream` pour Java Annotation. Cette méthode vous offre la flexibilité de déployer sur des serveurs traditionnels, des conteneurs Docker et des environnements cloud‑native tout en maintenant votre licence sécurisée et performante.

**Points clés**
- La licence via InputStream offre une flexibilité maximale de déploiement.  
- Validez toujours la licence et gérez les erreurs avant de traiter les documents.  
- Adaptez l’implémentation à votre scénario de déploiement (serveur, Docker, cloud).  
- Surveillez l’état de la licence en production et configurez des alertes d’expiration.

Commencez avec la configuration de base présentée ci‑dessus, puis évoluez vers les modèles avancés à mesure que votre application se développe. Bon codage !

## Ressources supplémentaires

- **Documentation :** [Documentation GroupDocs.Annotation pour Java](https://docs.groupdocs.com/annotation/java/)  
- **Référence API :** [Référence API complète](https://reference.groupdocs.com/annotation/java/)  
- **Télécharger la dernière version :** [GroupDocs Releases](https://releases.groupdocs.com/annotation/java/)  
- **Obtenir du support :** [Forum communautaire GroupDocs](https://forum.groupdocs.com/c/annotation/)  
- **Acheter une licence :** [Acheter une licence GroupDocs](https://purchase.groupdocs.com/buy)  
- **Essai gratuit :** [Essayer GroupDocs gratuitement](https://releases.groupdocs.com/annotation/java/)  
- **Licence temporaire :** [Obtenir une licence temporaire](https://purchase.groupdocs.com/temporary-license/)  

---

**Dernière mise à jour :** 2026-08-19  
**Testé avec :** GroupDocs.Annotation 25.2  
**Auteur :** GroupDocs

## Tutoriels associés

- [Vérifier le statut de la licence – Guide de licence Java GroupDocs Annotation](/annotation/java/licensing-and-configuration/)  
- [Définir la licence GroupDocs Java – Configuration de licence Java GroupDocs Annotation](/annotation/java/licensing-and-configuration/groupdocs-annotation-license-java-setup/)  
- [Charger un PDF Java avec GroupDocs Annotation : Guide de chargement de document](/annotation/java/document-loading/)