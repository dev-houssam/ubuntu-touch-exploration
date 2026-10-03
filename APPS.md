# 📱 Applications pour Ubuntu Touch

Ce fichier recense des applications connues pour fonctionner sur **Ubuntu Touch**, avec une attention particulière portée à leur facilité d'installation et à leur utilisation sur téléphone.

L'objectif n'est pas simplement de savoir si une application peut être installée, mais de déterminer **comment elle fonctionne réellement sur Ubuntu Touch**.

> ⚠️ La compatibilité peut varier selon le téléphone, la version d'Ubuntu Touch et l'architecture du périphérique.

---

## 📚 Navigation

* [Légende](#-légende)
* [Applications natives Ubuntu Touch](#-applications-natives-ubuntu-touch)
* [Applications Libertine](#-applications-libertine)
* [Applications Android avec Waydroid](#-applications-android-avec-waydroid)
* [Tableau récapitulatif](#-tableau-récapitulatif)
* [Applications à utiliser avec précaution](#-applications-à-utiliser-avec-précaution)
* [Comment choisir une application](#-comment-choisir-une-application)
* [Sources](#-sources)

---

# 🟢 Légende

### Méthode d'installation

| Symbole          | Signification                                   |
| ---------------- | ----------------------------------------------- |
| 🟢 **OpenStore** | Installation directement depuis l'OpenStore     |
| 🟡 **Libertine** | Installation dans un conteneur Linux            |
| 🟠 **Waydroid**  | Application Android exécutée dans Waydroid      |
| 🔴 **Complexe**  | Installation manuelle ou procédure particulière |

### Niveau d'utilisation

| Symbole              | Signification                                                 |
| -------------------- | ------------------------------------------------------------- |
| 🟢 **Très bon**      | Installation simple et utilisation adaptée au mobile          |
| 🟢 **Bon**           | Fonctionne correctement avec peu de limitations               |
| 🟡 **Limité**        | Fonctionne mais certaines limitations existent                |
| 🟠 **Difficile**     | Fonctionnement possible mais expérience peu adaptée           |
| 🔴 **Problématique** | Installation ou utilisation fortement limitée                 |
| ⚪ **Variable**       | Dépend fortement du téléphone ou de la version d'Ubuntu Touch |

---

# 📱 Applications natives Ubuntu Touch

Les applications natives sont les applications les plus naturelles à utiliser sur Ubuntu Touch.

Elles sont généralement distribuées par **l'OpenStore**, qui constitue la logithèque officielle d'Ubuntu Touch. L'OpenStore est installé par défaut sur les images UBports.

---

## 🌐 Navigation Web

### Morph Browser

| Critère          | Compatibilité                       |
| ---------------- | ----------------------------------- |
| Installation     | 🟢 OpenStore                        |
| Interface mobile | 🟢 Très bon                         |
| Architecture     | arm64 / armhf / amd64 selon version |
| Niveau           | 🟢 Très bon                         |
| Type             | Application native                  |

**Morph Browser** est le navigateur Web principal fourni dans l'écosystème Ubuntu Touch / UBports.

Il est développé pour l'environnement mobile Ubuntu Touch et s'intègre à Lomiri.

👉 À privilégier pour la navigation Web quotidienne.

---

# 📧 E-mail

### Dekko

| Critère           | Compatibilité      |
| ----------------- | ------------------ |
| Installation      | 🟢 OpenStore       |
| Interface mobile  | 🟢 Bon             |
| Comptes multiples | 🟢 Oui             |
| IMAP              | 🟢 Oui             |
| POP3              | 🟢 Oui             |
| Niveau            | 🟢 Bon             |
| Type              | Application native |

**Dekko** est un client e-mail conçu pour Ubuntu Touch.

Il permet de configurer plusieurs comptes et identités. La fiche OpenStore indique notamment la prise en charge d'IMAP et de POP3 ainsi que des configurations pour plusieurs fournisseurs courants.

⚠️ Certains fournisseurs peuvent nécessiter un **mot de passe d'application**.

---

# 💬 Telegram

### TELEports

| Critère          | Compatibilité           |
| ---------------- | ----------------------- |
| Installation     | 🟢 OpenStore            |
| Interface mobile | 🟢 Bon                  |
| Notifications    | 🟢 Oui                  |
| Audio            | 🟢 Oui                  |
| Microphone       | 🟢 Oui                  |
| Niveau           | 🟡 Bon avec limitations |
| Type             | Client Telegram natif   |

**TELEports** est un client Telegram développé spécifiquement pour Ubuntu Touch. Il est disponible dans l'OpenStore.

La version actuelle continue d'être développée.

⚠️ La fiche OpenStore précise toutefois que certaines fonctionnalités restent incomplètes. Les appels audio/vidéo, par exemple, peuvent ne pas offrir les mêmes possibilités que le client officiel Android/iOS.

---

# 🗺️ Cartographie et navigation

## Pure Maps

| Critère           | Compatibilité                 |
| ----------------- | ----------------------------- |
| Installation      | 🟢 OpenStore                  |
| Interface mobile  | 🟢 Très bon                   |
| GPS               | 🟢 Oui                        |
| Navigation        | 🟢 Oui                        |
| Cartes hors ligne | 🟢 Oui, avec OSM Scout Server |
| ARM64             | 🟢                            |
| ARMHF             | 🟢                            |
| Niveau            | 🟢 Très bon                   |

**Pure Maps** est une application de cartographie et de navigation particulièrement intéressante sur Ubuntu Touch.

Elle permet notamment :

* d'afficher des cartes ;
* de rechercher des adresses ;
* de rechercher des points d'intérêt ;
* de naviguer ;
* d'utiliser des cartes hors ligne avec **OSM Scout Server**.

La version actuelle propose notamment des builds pour Ubuntu Touch 24.04 en `amd64`, `arm64` et `armhf`.

👉 **Application recommandée pour la navigation.**

---

## uNav

| Critère          | Compatibilité      |
| ---------------- | ------------------ |
| Installation     | 🟢 OpenStore       |
| Interface mobile | 🟢 Bon             |
| GPS              | 🟢 Oui             |
| Cartes           | 🟢 Oui             |
| Niveau           | 🟡 Variable        |
| Architecture     | Toutes             |
| Type             | Application native |

**uNav** est une autre application de navigation basée notamment sur OpenStreetMap.

Elle existe depuis plusieurs années dans l'OpenStore et reste disponible sur les versions récentes d'Ubuntu Touch.

⚠️ Les retours récents indiquent cependant que certaines fonctions peuvent rencontrer des problèmes sur certains appareils et versions d'Ubuntu Touch.

👉 **Alternative intéressante à Pure Maps**, mais à tester sur son appareil.

---

# 🔭 Astronomie

## Stellarium

| Critère           | Compatibilité |
| ----------------- | ------------- |
| Installation      | 🟢 OpenStore  |
| Interface tactile | 🟢 Oui        |
| Zoom tactile      | 🟢 Oui        |
| Capteurs          | 🟢 Supportés  |
| ARM64             | 🟢            |
| ARMHF             | 🟢            |
| Niveau            | 🟢 Bon        |

**Stellarium** possède une version adaptée à Ubuntu Touch.

La version mobile prend notamment en charge le zoom tactile et certains modes de navigation utilisant les capteurs du téléphone.

L'application est disponible pour `armhf`, `arm64` et `amd64`.

---

# 📚 Lecture

## Sturm Reader

| Critère          | Compatibilité             |
| ---------------- | ------------------------- |
| Installation     | 🟢 OpenStore              |
| EPUB             | 🟢                        |
| PDF              | 🟢                        |
| CBZ              | 🟢                        |
| CBR              | 🟢                        |
| Interface mobile | 🟢 Bon                    |
| Niveau           | 🟡 Variable selon version |

**Sturm Reader** est un lecteur d'e-books et de bandes dessinées prenant notamment en charge EPUB, PDF, CBZ et CBR.

Il existe des builds pour `armhf`, `arm64` et `amd64`.

⚠️ Certains utilisateurs ont signalé des problèmes avec certaines versions d'Ubuntu Touch 24.04. La compatibilité peut donc dépendre du périphérique et de la version utilisée.

---

# 🎵 Musique

## Futify

| Critère          | Compatibilité |
| ---------------- | ------------- |
| Installation     | 🟢 OpenStore  |
| Spotify          | 🟢            |
| Compte Premium   | ⚠️ Requis     |
| Interface mobile | 🟢 Oui        |
| ARM64            | 🟢            |
| ARMHF            | 🟢            |
| AMD64            | 🟢            |
| Niveau           | 🟡 Variable   |

**Futify** est un client Spotify non officiel développé pour Ubuntu Touch.

Il est disponible pour `arm64`, `armhf` et `amd64`. La version actuelle publiée sur l'OpenStore est la **1.6.2**, mise à jour en juin 2026.

⚠️ Il nécessite un compte Spotify Premium.

⚠️ Certains utilisateurs signalent encore des problèmes de connexion ou des comportements différents selon les appareils et versions d'Ubuntu Touch.

👉 À considérer comme une solution pratique mais **pas équivalente au client Spotify officiel**.

---

# 🐧 Applications Linux avec Libertine

Certaines applications Linux classiques peuvent être exécutées dans un conteneur **Libertine**.

Voir :

👉 **[LIBERTINE.md](./LIBERTINE.md)**

Cette solution est particulièrement intéressante pour les logiciels Linux qui ne possèdent pas d'application native Ubuntu Touch.

---

## 🧰 Git

| Critère      | Compatibilité |
| ------------ | ------------- |
| Installation | 🟡 Libertine  |
| Interface    | 🟢 Terminal   |
| ARM64        | 🟢            |
| ARMHF        | 🟢            |
| Niveau       | 🟢 Très bon   |

Git étant principalement un outil en ligne de commande, il constitue un excellent candidat pour Libertine.

Exemple :

```bash
libertine-container-manager install-package \
    -i desktop \
    -p git
```

Puis :

```bash
libertine-launch \
    -i desktop \
    git --version
```

👉 **Excellent cas d'utilisation de Libertine.**

---

## 📝 Vim

| Critère                  | Compatibilité |
| ------------------------ | ------------- |
| Installation             | 🟡 Libertine  |
| Interface                | 🟢 Terminal   |
| Niveau                   | 🟢 Très bon   |
| Utilisation tactile      | 🟡            |
| Utilisation avec clavier | 🟢 Excellent  |

Vim est particulièrement adapté à un environnement Linux mobile lorsqu'un clavier physique est disponible.

```bash
libertine-container-manager install-package \
    -i desktop \
    -p vim
```

Puis :

```bash
libertine-launch \
    -i desktop \
    vim
```

---

## 🐍 Python

| Critère        | Compatibilité  |
| -------------- | -------------- |
| Installation   | 🟡 Libertine   |
| Interface      | 🟢 Terminal    |
| Scripts Python | 🟢             |
| Niveau         | 🟢 Très bon    |
| Architecture   | Dépend du port |

Python peut être utilisé depuis le conteneur Libertine pour exécuter des scripts et utiliser des outils Python disponibles pour l'architecture du téléphone.

Exemple :

```bash
libertine-container-manager install-package \
    -i desktop \
    -p python3
```

Puis :

```bash
libertine-launch \
    -i desktop \
    python3
```

---

## 🖼️ GIMP

| Critère          | Compatibilité       |
| ---------------- | ------------------- |
| Installation     | 🟡 Libertine        |
| Interface        | 🟡 Desktop          |
| Écran tactile    | 🟠 Peu adapté       |
| Performances     | ⚪ Variables         |
| Niveau           | 🟡                  |
| Usage recommandé | Avec clavier/souris |

GIMP est un logiciel Linux desktop beaucoup plus lourd qu'une application native Ubuntu Touch.

Il peut être intéressant pour expérimenter, mais son interface n'est pas conçue pour un petit écran tactile.

👉 **Fonctionnement possible ≠ expérience idéale.**

---

## 📊 LibreOffice

| Critère         | Compatibilité |
| --------------- | ------------- |
| Installation    | 🟡 Libertine  |
| Interface       | 🟡 Desktop    |
| Documents       | 🟢            |
| Écran tactile   | 🟠            |
| Niveau          | 🟡            |
| Clavier externe | 🟢 Recommandé |

LibreOffice est un autre exemple d'application Linux desktop pouvant être intéressante dans un environnement Libertine.

Il est toutefois préférable de l'utiliser avec :

* un écran suffisamment grand ;
* un clavier ;
* éventuellement une souris.

Sur un téléphone seul, l'expérience peut être difficile.

---

# 🤖 Applications Android avec Waydroid

Ubuntu Touch peut également utiliser **Waydroid** pour exécuter des applications Android lorsque le support est disponible sur l'appareil.

```text
Ubuntu Touch
     │
     ├── Applications natives
     │
     ├── Libertine
     │      └── Applications Linux
     │
     └── Waydroid
            └── Applications Android
```

⚠️ **Waydroid dépend fortement du téléphone et de son port Ubuntu Touch.**

Il ne faut donc pas considérer toutes les applications Android comme automatiquement compatibles.

La documentation et les retours communautaires indiquent également certaines limitations concernant l'accès aux fichiers Ubuntu Touch, les notifications et certaines fonctions matérielles.

---

# 📱 Applications Android courantes

| Application            | Méthode     | Compatibilité | Remarque                                                   |
| ---------------------- | ----------- | ------------- | ---------------------------------------------------------- |
| Telegram Android       | 🟠 Waydroid | 🟡            | Préférer TELEports si ses fonctions suffisent              |
| Firefox Android        | 🟠 Waydroid | 🟡            | Dépend de Waydroid                                         |
| VLC Android            | 🟠 Waydroid | 🟡            | Dépend du support matériel                                 |
| Signal                 | 🟠 Waydroid | ⚪             | Tester sur son appareil                                    |
| WhatsApp               | 🟠 Waydroid | ⚪             | Dépend de l'environnement Android                          |
| Spotify                | 🟠 Waydroid | ⚪             | Dépend notamment des services nécessaires                  |
| Applications bancaires | 🟠 Waydroid | 🔴/⚪          | Certaines peuvent refuser les environnements non certifiés |

> ⚠️ Cette catégorie ne constitue **pas une garantie de compatibilité**. Une application Android peut fonctionner sur un appareil et échouer sur un autre.

---

# 📊 Tableau récapitulatif

| Application          | Type    | Installation | Interface mobile | Compatibilité |
| -------------------- | ------- | ------------ | ---------------- | ------------- |
| **Morph Browser**    | Native  | 🟢 OpenStore | 🟢               | 🟢            |
| **Dekko**            | Native  | 🟢 OpenStore | 🟢               | 🟢            |
| **TELEports**        | Native  | 🟢 OpenStore | 🟢               | 🟡            |
| **Pure Maps**        | Native  | 🟢 OpenStore | 🟢               | 🟢            |
| **uNav**             | Native  | 🟢 OpenStore | 🟢               | 🟡            |
| **Stellarium**       | Native  | 🟢 OpenStore | 🟢               | 🟢            |
| **Sturm Reader**     | Native  | 🟢 OpenStore | 🟢               | 🟡            |
| **Futify**           | Native  | 🟢 OpenStore | 🟢               | 🟡            |
| **Git**              | Linux   | 🟡 Libertine | 🟢 Terminal      | 🟢            |
| **Vim**              | Linux   | 🟡 Libertine | 🟢 Terminal      | 🟢            |
| **Python**           | Linux   | 🟡 Libertine | 🟢 Terminal      | 🟢            |
| **GIMP**             | Linux   | 🟡 Libertine | 🟠               | 🟡            |
| **LibreOffice**      | Linux   | 🟡 Libertine | 🟠               | 🟡            |
| **Telegram Android** | Android | 🟠 Waydroid  | 🟡               | ⚪             |
| **Firefox Android**  | Android | 🟠 Waydroid  | 🟡               | ⚪             |
| **VLC Android**      | Android | 🟠 Waydroid  | 🟡               | ⚪             |
| **Signal**           | Android | 🟠 Waydroid  | 🟡               | ⚪             |
| **WhatsApp**         | Android | 🟠 Waydroid  | 🟡               | ⚪             |
| **Spotify**          | Android | 🟠 Waydroid  | 🟡               | ⚪             |

---

# ⭐ Applications particulièrement intéressantes

Pour commencer avec Ubuntu Touch, quelques applications permettent rapidement de voir ce que le système sait faire.

### 📱 Utilisation quotidienne

```text
Morph Browser
Dekko
TELEports
Pure Maps
```

### 🧭 GPS / exploration

```text
Pure Maps
Stellarium
```

### 🐧 Expérience Linux

```text
Git
Vim
Python
```

### 🖥️ Expérience desktop

```text
GIMP
LibreOffice
```

Ces dernières sont surtout intéressantes pour découvrir **Libertine**, plutôt que pour remplacer directement leurs versions desktop sur un ordinateur.

---

# ⚠️ Applications à utiliser avec précaution

Certaines catégories sont particulièrement susceptibles de poser problème.

## Applications bancaires

Les applications bancaires peuvent utiliser :

* Google Play Services ;
* SafetyNet / Play Integrity ;
* vérification de l'environnement Android ;
* DRM ;
* mécanismes de sécurité spécifiques.

Une application Android qui fonctionne dans Waydroid n'est donc pas nécessairement utilisable pour une opération bancaire.

---

## DRM et streaming

Les services utilisant des DRM propriétaires peuvent présenter des limitations.

Il faut notamment distinguer :

```text
Application Web
      ≠
Application native
      ≠
Application Android
      ≠
Service DRM
```

---

## Applications nécessitant des services Google

Une application Android peut dépendre de :

```text
Google Play Services
Google Maps
Firebase
Google Play Integrity
Google Cloud Messaging
```

Dans ce cas, l'application peut ne pas fonctionner correctement dans Waydroid sans environnement ou services supplémentaires.

---

# 🔍 Comment vérifier une application ?

Avant d'installer une application, vérifier dans cet ordre :

```text
1. OpenStore
       │
       ▼
2. Vérifier la version Ubuntu Touch
       │
       ▼
3. Vérifier l'architecture
       │
       ▼
4. Lire les notes de version
       │
       ▼
5. Lire les derniers retours utilisateurs
       │
       ▼
6. Tester sur son appareil
```

Une application peut être disponible pour `arm64` mais rencontrer malgré tout un problème spécifique à un modèle donné.

---

# 🧭 Quelle méthode choisir ?

```text
                 Application recherchée
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
        OpenStore       Linux .deb    Android
             │             │             │
             ▼             ▼             ▼
          Native        Libertine    Waydroid
             │             │             │
             ▼             ▼             ▼
        🟢 priorité    🟡 utile      🟠 dernier recours
```

### 🟢 OpenStore

À privilégier lorsque l'application native existe.

### 🟡 Libertine

À utiliser lorsqu'un logiciel Linux desktop est nécessaire.

### 🟠 Waydroid

À utiliser lorsque l'application Android est indispensable et qu'elle ne possède pas d'alternative native satisfaisante.

---

# 📚 Sources

### OpenStore

👉 [OpenStore — applications Ubuntu Touch](https://open-store.io/)

L'OpenStore est la logithèque officielle d'Ubuntu Touch.

### UBports

👉 [Documentation UBports](https://docs.ubports.com/)

### Libertine

👉 [Documentation Libertine](https://docs.ubports.com/en/latest/userguide/dailyuse/libertine.html)

### Waydroid

👉 [Documentation Waydroid](https://docs.ubports.com/en/latest/userguide/dailyuse/waydroid.html)

---

# 🔗 Autres documents de ce projet

| Document                         | Contenu                                                     |
| -------------------------------- | ----------------------------------------------------------- |
| [`README.md`](./README.md)       | Découvrir et installer Ubuntu Touch                         |
| [`LIBERTINE.md`](./LIBERTINE.md) | Installer et utiliser des applications Linux avec Libertine |
| **`APPS.md`**                    | Catalogue des applications compatibles                      |

---

> **Principe du catalogue**
>
> Une application n'est pas considérée comme réellement « compatible » simplement parce qu'elle peut être installée.
>
> Le niveau de compatibilité doit tenir compte de **l'installation, de l'interface, des fonctionnalités disponibles et du matériel utilisé**.
