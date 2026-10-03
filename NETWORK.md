# 📡 Téléphonie, réseau et localisation sur Ubuntu Touch

Ce document regroupe les informations nécessaires pour configurer et utiliser les fonctions de **communication et de connectivité** d'Ubuntu Touch.

Il couvre notamment :

* 📱 carte SIM ;
* 📞 appels téléphoniques ;
* 💬 SMS ;
* 📨 MMS ;
* 📶 réseau mobile / GSM / 3G / 4G ;
* 🌐 données mobiles ;
* ⚙️ APN ;
* 📡 Wi-Fi ;
* 🛰️ localisation et GPS ;
* 📍 permissions de localisation ;
* 📞 VoLTE ;
* 🔵 Bluetooth ;
* 🔧 diagnostic et dépannage.

> **Ce document concerne un Ubuntu Touch déjà installé.**
>
> Pour découvrir Ubuntu Touch et apprendre à l'installer sur un téléphone compatible, consulter le [README principal](./README.md).

---

# 📚 Sommaire

* [1. Comprendre la connectivité d'Ubuntu Touch](#1-comprendre-la-connectivité-dubuntu-touch)
* [2. Carte SIM](#2-carte-sim)
* [3. Réseau mobile](#3-réseau-mobile)
* [4. Données mobiles](#4-données-mobiles)
* [5. Configurer un APN](#5-configurer-un-apn)
* [6. Appels téléphoniques](#6-appels-téléphoniques)
* [7. SMS](#7-sms)
* [8. MMS](#8-mms)
* [9. VoLTE](#9-volte)
* [10. Wi-Fi](#10-wi-fi)
* [11. Partage de connexion](#11-partage-de-connexion)
* [12. Bluetooth](#12-bluetooth)
* [13. Localisation et GPS](#13-localisation-et-gps)
* [14. Permissions de localisation](#14-permissions-de-localisation)
* [15. Vérifier l'état du réseau](#15-vérifier-létat-du-réseau)
* [16. Dépannage](#16-dépannage)
* [17. Architecture de la téléphonie](#17-architecture-de-la-téléphonie)
* [18. Compatibilité matérielle](#18-compatibilité-matérielle)
* [19. Ressources](#19-ressources)

---

# 1. Comprendre la connectivité d'Ubuntu Touch

Un smartphone Ubuntu Touch ne fait pas que lancer des applications.

Le système doit également gérer plusieurs composants matériels :

```text
                       📱 TÉLÉPHONE
                            │
          ┌─────────────────┼─────────────────┐
          │                 │                 │
          ▼                 ▼                 ▼
       📶 Modem          📡 Wi-Fi         🛰️ GPS
          │                 │                 │
          │                 │                 │
       SIM / GSM         Internet        Localisation
          │
     ┌────┼────┐
     │    │    │
     ▼    ▼    ▼
   Appels SMS  Data
```

Ces fonctions ne sont pas toutes indépendantes.

Par exemple :

```text
SIM
 │
 ├── Authentification opérateur
 │
 ├── Réseau mobile
 │      │
 │      ├── Appels
 │      ├── SMS
 │      └── Données mobiles
 │
 └── APN
        │
        └── Accès Internet
```

La compatibilité réelle dépend donc du **téléphone**, de son **modem**, de son **firmware**, de son **port Ubuntu Touch** et parfois de l'opérateur.

Les ports Ubuntu Touch peuvent utiliser différentes architectures matérielles, notamment des ports basés sur Halium ou des ports Linux natifs.

---

# 2. Carte SIM

## 💳 Insérer la SIM

Avant de démarrer Ubuntu Touch, insérer une carte SIM compatible avec le téléphone.

Selon l'appareil, il peut s'agir de :

* Nano-SIM ;
* Micro-SIM ;
* SIM standard ;
* eSIM lorsque le matériel et le port le permettent.

⚠️ **La présence d'un emplacement SIM ne garantit pas que toutes les fonctions de téléphonie fonctionneront sous Ubuntu Touch.**

---

## 🔐 Code PIN

Si la carte SIM possède un code PIN, Ubuntu Touch peut demander ce code au démarrage ou lorsque le modem est activé.

Le principe est :

```text
Téléphone démarré
       │
       ▼
Détection de la SIM
       │
       ▼
SIM verrouillée ?
       │
      Oui
       │
       ▼
Demande du PIN
       │
       ▼
SIM déverrouillée
       │
       ▼
Connexion au réseau
```

### ⚠️ Attention au code PIN

Ne pas essayer des codes au hasard.

Après plusieurs tentatives incorrectes, la SIM peut être bloquée et demander un **code PUK**.

Le PUK est généralement fourni par l'opérateur.

---

# 3. Réseau mobile

Ubuntu Touch peut utiliser le modem du téléphone pour se connecter au réseau mobile.

Selon l'appareil et l'opérateur, différentes technologies peuvent être disponibles :

```text
2G / GSM
3G / UMTS
4G / LTE
VoLTE
```

⚠️ La disponibilité réelle dépend du matériel et du port Ubuntu Touch.

---

## 📶 Sélection du réseau

Les paramètres réseau mobile se trouvent généralement dans :

```text
Paramètres système
    ↓
Cellulaire
    ↓
Opérateur et APN
```

Le nom exact des menus peut varier légèrement selon la version d'Ubuntu Touch.

On peut notamment y retrouver :

* l'opérateur ;
* le type de réseau ;
* les APN ;
* les données mobiles ;
* les paramètres VoLTE lorsqu'ils sont disponibles.

---

# 4. Données mobiles

Les données mobiles permettent au téléphone d'accéder à Internet via le réseau de l'opérateur.

```text
📱 Ubuntu Touch
       │
       ▼
     Modem
       │
       ▼
     Réseau
       │
       ▼
    Opérateur
       │
       ▼
    Internet
```

Pour les utiliser, plusieurs conditions doivent être réunies :

```text
☑ SIM fonctionnelle
☑ Réseau mobile disponible
☑ Abonnement avec données mobiles
☑ APN correctement configuré
☑ Modem correctement pris en charge
```

---

# 5. Configurer un APN

## 🌐 Qu'est-ce qu'un APN ?

**APN** signifie :

> **Access Point Name**

Il indique au modem comment accéder au réseau de données de l'opérateur.

Un APN peut être représenté ainsi :

```text
Téléphone
    │
    ▼
  Modem
    │
    ▼
   APN
    │
    ▼
Réseau opérateur
    │
    ▼
 Internet
```

---

## ⚙️ Où configurer l'APN ?

Ouvrir :

```text
Paramètres système
    ↓
Cellulaire
    ↓
Opérateur et APN
```

Puis sélectionner ou créer la configuration correspondant à l'opérateur.

---

## 🧾 Informations généralement nécessaires

Un opérateur peut fournir plusieurs paramètres :

| Paramètre       | Exemple           |
| --------------- | ----------------- |
| Nom             | Mon opérateur     |
| APN             | `internet`        |
| Nom utilisateur | parfois vide      |
| Mot de passe    | parfois vide      |
| MCC             | code opérateur    |
| MNC             | code réseau       |
| Type d'APN      | `default`         |
| Proxy           | généralement vide |
| Port            | généralement vide |

> ⚠️ **Ne pas recopier ces valeurs au hasard.**
>
> Les paramètres APN dépendent de l'opérateur et peuvent changer. Utiliser les paramètres fournis par son opérateur.

---

# 6. Appels téléphoniques

Ubuntu Touch possède une application de téléphonie permettant notamment :

* composer un numéro ;
* recevoir un appel ;
* consulter l'historique ;
* gérer les contacts ;
* utiliser le haut-parleur ;
* utiliser le microphone.

Les composants de téléphonie sont intégrés au système Ubuntu Touch ; l'application Téléphone fait partie des applications installées avec le système.

---

## 📞 Passer un appel

Ouvrir :

```text
Téléphone
   ↓
Clavier
   ↓
Numéro
   ↓
📞 Appeler
```

Ou sélectionner un contact :

```text
Contacts
   ↓
Contact
   ↓
📞 Appeler
```

---

## 🔊 Pendant un appel

Selon le matériel et le port, différentes fonctions peuvent être disponibles :

```text
🔊 Haut-parleur
🎙️ Microphone
🔇 Muet
📞 Clavier
```

Tester ces fonctions après l'installation d'Ubuntu Touch.

---

# 7. SMS

L'application de messagerie d'Ubuntu Touch permet de gérer les SMS.

```text
📱 Téléphone
      │
      ▼
   Modem
      │
      ▼
  Réseau mobile
      │
      ▼
     SMS
```

L'application Messages fait partie des applications système d'Ubuntu Touch.

---

## 💬 Envoyer un SMS

Ouvrir :

```text
Messages
    ↓
Nouveau message
    ↓
Destinataire
    ↓
Texte
    ↓
Envoyer
```

---

## 📥 Recevoir un SMS

Lorsqu'un SMS arrive :

```text
Réseau mobile
      │
      ▼
    Modem
      │
      ▼
  Service téléphonie
      │
      ▼
  Application Messages
      │
      ▼
 Notification
```

Le système de téléphonie Ubuntu Touch utilise notamment **oFono** pour communiquer avec le modem.

---

# 8. MMS

Les MMS sont différents des SMS.

Un MMS nécessite notamment une connexion de données et une configuration adaptée de l'opérateur.

L'architecture MMS d'Ubuntu Touch utilise plusieurs composants :

```text
Messaging App
      │
      ▼
Telepathy
      │
      ▼
   Nuntium
      │
      ▼
    oFono
      │
      ▼
 Modem / réseau
      │
      ▼
    MMSC
```

UBports documente notamment le rôle d'**oFono**, **nuntium**, **telepathy-ofono**, **history-service** et de l'application de messagerie dans la gestion des MMS.

⚠️ Les MMS sont donc particulièrement dépendants :

* de l'opérateur ;
* de l'APN ;
* du port Ubuntu Touch ;
* de la configuration du modem.

---

# 9. VoLTE

## 📞 Qu'est-ce que VoLTE ?

**VoLTE** signifie :

> **Voice over LTE**

Il permet de transporter les appels téléphoniques sur le réseau 4G/LTE.

```text
Sans VoLTE

4G ───── Internet
 │
 └── appel → bascule éventuelle vers un ancien réseau


Avec VoLTE

4G ───── Internet
 │
 └────── appel vocal
```

Ubuntu Touch prend en charge VoLTE sur **certains appareils seulement**.

UBports précise que cette compatibilité dépend notamment :

* du chipset ;
* de la version Android servant de base au port ;
* de la configuration VoLTE du port ;
* de l'opérateur ;
* de la carte SIM.

---

## 🔎 Vérifier la présence de VoLTE

Aller dans :

```text
Paramètres système
    ↓
Cellulaire
    ↓
Opérateur et APN
```

Si l'option est disponible :

```text
☑ Appels 4G / VoLTE
```

peut être activée.

Si le réglage n'existe pas, cela peut simplement signifier que le port Ubuntu Touch de l'appareil ne prend pas en charge VoLTE.

---

## 📡 Vérifier que VoLTE fonctionne

Lorsque la connexion VoLTE est correctement établie, l'indicateur du réseau peut afficher :

```text
4G / LTE / VoLTE
```

à côté du nom de l'opérateur.

---

# 10. Wi-Fi

Ubuntu Touch peut utiliser une connexion Wi-Fi pour accéder à Internet.

```text
Paramètres
    ↓
Wi-Fi
    ↓
Réseau
    ↓
Mot de passe
    ↓
Connexion
```

Une fois connecté :

```text
📱 Ubuntu Touch
       │
       ▼
     Wi-Fi
       │
       ▼
 Routeur / Box
       │
       ▼
   Internet
```

---

## 📶 Wi-Fi ou données mobiles ?

Lorsqu'un Wi-Fi fonctionnel est disponible, il est généralement préférable de l'utiliser pour les téléchargements importants.

Cela permet notamment d'éviter de consommer inutilement le forfait mobile.

---

# 11. Partage de connexion

Ubuntu Touch peut également permettre de partager sa connexion mobile avec d'autres appareils lorsque cette fonction est supportée par le téléphone et le port.

Principe :

```text
             Réseau mobile
                   │
                   ▼
             📱 Ubuntu Touch
                   │
             Hotspot Wi-Fi
                   │
          ┌────────┴────────┐
          ▼                 ▼
       💻 PC             📱 Tablette
```

Le téléphone devient alors un point d'accès réseau.

---

## 🔌 USB

Le partage de connexion peut également être réalisé via USB dans certaines configurations.

UBports documente également le **reverse tethering**, qui permet à Ubuntu Touch d'utiliser la connexion Internet d'un ordinateur Linux via USB.

---

# 12. Bluetooth

Le Bluetooth permet notamment de connecter :

* écouteurs ;
* casques ;
* claviers ;
* souris ;
* systèmes audio ;
* certains périphériques.

```text
Paramètres
    ↓
Bluetooth
    ↓
Activer
    ↓
Rechercher un appareil
    ↓
Associer
```

---

## 🎧 Bluetooth et appels

Selon le téléphone et le port Ubuntu Touch, les fonctions Bluetooth disponibles peuvent varier.

Après association d'un casque Bluetooth, tester :

```text
☑ Audio
☑ Microphone
☑ Appels
☑ Contrôle du volume
```

---

# 13. Localisation et GPS

Ubuntu Touch possède un système de services de localisation.

Il permet notamment aux applications de connaître la position du téléphone lorsque l'utilisateur leur en donne l'autorisation.

Exemples :

```text
📍 Navigation
🗺️ Cartographie
🚲 Suivi de trajet
🚍 Transport
🌦️ Météo locale
```

UBports indique que les services de localisation sont conçus avec une attention particulière à la confidentialité et que l'utilisateur contrôle l'accès des applications à sa position.

---

# 🛰️ Activer la localisation

Il existe deux méthodes.

## Depuis les réglages rapides

Ouvrir les indicateurs système puis sélectionner :

```text
📍 Localisation
```

et activer :

```text
Localisation
```

---

## Depuis les paramètres

Ouvrir :

```text
Paramètres système
    ↓
Sécurité et confidentialité
    ↓
Localisation
```

Puis choisir :

```text
Utiliser le GPS
```

ou désactiver complètement la détection de position.

---

# 🔐 14. Permissions de localisation

Une application ne devrait pas automatiquement avoir accès à la localisation simplement parce que le GPS est activé.

Ubuntu Touch permet de contrôler les applications autorisées à accéder à la position.

```text
Localisation activée
        │
        ▼
Application demande la position
        │
        ▼
┌─────────────────────────┐
│ Autoriser ?             │
│                         │
│  [Autoriser] [Refuser]  │
└─────────────────────────┘
```

Les permissions peuvent ensuite être modifiées dans les paramètres de localisation.

---

# ⏱️ Temps de première localisation

Lorsqu'un GPS n'a pas été utilisé depuis longtemps, l'obtention de la première position peut prendre du temps.

UBports indique notamment qu'un appareil disposant d'une connexion Internet mobile peut généralement obtenir son premier *fix* en environ **1 à 4 minutes**, tandis que dans certaines situations sans connexion mobile, le premier fix peut être beaucoup plus long.

Il ne faut donc pas conclure immédiatement que le GPS est défectueux après quelques secondes.

---

# 📍 Indicateur de localisation

Ubuntu Touch possède un indicateur permettant de voir l'activité du service de localisation.

De manière générale :

```text
📍 Indicateur peu visible
    ↓
Service disponible

📍 Indicateur actif
    ↓
Une application utilise actuellement
les données de localisation
```

---

# 🔧 15. Vérifier l'état du réseau

Lorsqu'une fonction réseau ne fonctionne pas, il faut déterminer **quelle couche est responsable**.

```text
SIM
 │
 ▼
Modem
 │
 ▼
Réseau mobile
 │
 ├── Appels
 ├── SMS
 └── Données
       │
       ▼
      APN
       │
       ▼
    Internet
```

Cela permet de distinguer plusieurs problèmes.

### Exemple

```text
Appels fonctionnels
SMS fonctionnels
Internet mobile KO
```

Le problème est probablement plus proche de :

```text
APN / données mobiles
```

que de :

```text
SIM / modem
```

---

# 🧪 16. Dépannage

## ❌ La SIM n'est pas détectée

Vérifier :

```text
☑ SIM correctement insérée
☑ Téléphone redémarré
☑ SIM fonctionnelle dans un autre téléphone
☑ Modèle correctement supporté
☑ Port Ubuntu Touch compatible avec le modem
```

---

## ❌ La SIM est détectée mais aucun réseau

Vérifier :

```text
☑ Mode avion désactivé
☑ Réseau mobile activé
☑ Opérateur correctement sélectionné
☑ Zone couverte
☑ SIM active
```

Tester également la sélection automatique de l'opérateur.

---

## ❌ Appels impossibles mais réseau présent

Si :

```text
📶 réseau OK
💬 SMS OK
📞 appels KO
```

il faut notamment vérifier :

```text
VoLTE
compatibilité du modem
configuration opérateur
configuration du port Ubuntu Touch
```

C'est particulièrement important dans les environnements où les anciens réseaux utilisés pour les appels ne sont plus disponibles.

---

## ❌ Internet mobile ne fonctionne pas

Si :

```text
📞 appels OK
💬 SMS OK
🌐 Internet mobile KO
```

commencer par vérifier l'APN.

```text
Paramètres
    ↓
Cellulaire
    ↓
Opérateur et APN
```

Comparer les paramètres avec ceux fournis officiellement par l'opérateur.

---

## ❌ Wi-Fi fonctionne mais données mobiles non

Cela indique généralement que le problème se situe du côté :

```text
SIM
   ↓
Modem
   ↓
Réseau mobile
   ↓
APN
```

et non du côté de la connexion Wi-Fi.

---

## ❌ GPS ne trouve aucune position

Vérifier :

```text
☑ Localisation activée
☑ Permission accordée à l'application
☑ Vue dégagée vers le ciel
☑ Quelques minutes d'attente
☑ Application compatible avec Ubuntu Touch
```

Un premier fix peut prendre plusieurs minutes selon les conditions.

---

# 🧰 Diagnostic par couches

Lorsqu'un problème apparaît, utiliser cette grille :

| Fonction    | Vérification               |
| ----------- | -------------------------- |
| SIM         | SIM détectée ?             |
| PIN         | SIM déverrouillée ?        |
| Modem       | Modem reconnu ?            |
| Réseau      | Opérateur visible ?        |
| Signal      | Barres réseau présentes ?  |
| Appels      | Appel sortant possible ?   |
| SMS         | SMS sortant possible ?     |
| MMS         | APN MMS configuré ?        |
| Data        | Données mobiles actives ?  |
| APN         | APN correct ?              |
| VoLTE       | Option disponible ?        |
| Wi-Fi       | Réseau Wi-Fi fonctionnel ? |
| Bluetooth   | Périphérique détecté ?     |
| GPS         | Localisation activée ?     |
| Permissions | Application autorisée ?    |

---

# 🏗️ 17. Architecture de la téléphonie

La téléphonie d'Ubuntu Touch repose sur plusieurs composants logiciels.

Une représentation simplifiée peut être faite ainsi :

```text
                     APPLICATIONS
                          │
          ┌───────────────┼───────────────┐
          │               │               │
          ▼               ▼               ▼
      Téléphone        Messages        Localisation
          │               │               │
          └───────┬───────┘               │
                  ▼                         │
             Services système              │
                  │                         │
                  ▼                         ▼
                oFono                  Location Service
                  │
                  ▼
                Modem
                  │
                  ▼
          Réseau de l'opérateur
```

Pour les MMS, l'architecture comporte notamment :

```text
Messaging App
      │
      ▼
Telepathy
      │
      ▼
   nuntium
      │
      ▼
    oFono
      │
      ▼
 Modem / réseau
```

Cette architecture est documentée par UBports.

---

# 📱 18. Compatibilité matérielle

La compatibilité réseau est l'une des raisons pour lesquelles il faut toujours consulter la page **Device** correspondant à son téléphone.

Deux appareils Android qui semblent identiques commercialement peuvent posséder :

* des modems différents ;
* des bandes radio différentes ;
* des firmwares différents ;
* des kernels différents ;
* des configurations VoLTE différentes.

Ubuntu Touch dépend donc fortement du **port matériel**.

UBports distingue notamment les ports basés sur Android/Halium et les appareils utilisant directement un kernel Linux.

---

# ⚠️ Le mot « compatible » ne suffit pas

Un appareil peut être :

```text
🟢 Ubuntu Touch démarre
```

mais avoir :

```text
🟡 GPS partiellement fonctionnel
🟡 Bluetooth limité
🔴 VoLTE absent
🔴 caméra problématique
```

Il faut donc vérifier les fonctions individuellement.

Pour un téléphone destiné à un usage quotidien, tester au minimum :

```text
☑ Appel entrant
☑ Appel sortant
☑ SMS entrant
☑ SMS sortant
☑ Données mobiles
☑ Wi-Fi
☑ Bluetooth
☑ GPS
☑ Appareil photo
☑ Microphone
☑ Haut-parleur
☑ Veille / réveil
```

---

# 🛠️ 19. Méthode de diagnostic recommandée

Lorsqu'une fonction ne marche pas, ne pas modifier immédiatement des fichiers système.

Procéder progressivement :

```text
                    Problème
                       │
                       ▼
              Le matériel est-il
                  détecté ?
                 /           \
               NON            OUI
               │               │
               ▼               ▼
        Vérifier le port    Le service
        et le matériel      fonctionne ?
                              │
                         ┌────┴────┐
                        NON       OUI
                         │         │
                         ▼         ▼
                    Vérifier     Vérifier
                    config.      l'application
```

Cette méthode permet d'éviter de modifier inutilement le système.

---

# 🔒 Sécurité et confidentialité

Les fonctions réseau et de localisation peuvent exposer des informations sensibles.

Quelques principes simples :

* ne partager son code PIN ou PUK avec personne ;
* utiliser un verrouillage d'écran ;
* contrôler les permissions de localisation ;
* ne pas installer de profils APN provenant de sources inconnues ;
* utiliser les paramètres officiels de son opérateur ;
* vérifier les applications qui demandent l'accès à la localisation.

Ubuntu Touch permet notamment à l'utilisateur de contrôler quelles applications ont accès à sa position.

---

# 🔗 Documents associés

| Document                         | Contenu                                 |
| -------------------------------- | --------------------------------------- |
| [`README.md`](./README.md)       | Découvrir et installer Ubuntu Touch     |
| [`LIBERTINE.md`](./LIBERTINE.md) | Utiliser les applications Linux desktop |
| [`APPS.md`](./APPS.md)           | Catalogue d'applications compatibles    |
| **`NETWORK.md`**                 | Téléphonie, SIM, réseau et localisation |

---

# 📚 Documentation officielle

### Ubuntu Touch

👉 [Documentation UBports](https://docs.ubports.com/)

### Localisation

👉 [Location Services — UBports](https://docs.ubports.com/en/latest/userguide/dailyuse/location.html)

### VoLTE

👉 [Voice over LTE — UBports](https://docs.ubports.com/en/latest/userguide/dailyuse/volte.html)

### Libertine

👉 [Libertine — UBports](https://docs.ubports.com/en/latest/userguide/dailyuse/libertine.html)

### Waydroid

👉 [Waydroid — UBports](https://docs.ubports.com/en/latest/userguide/dailyuse/waydroid.html)

---

# 📌 Résumé

Ubuntu Touch transforme le téléphone en un véritable système Linux mobile, mais son fonctionnement téléphonique repose sur plusieurs couches matérielles et logicielles.

```text
                         📱
                         │
             ┌───────────┴───────────┐
             │                       │
          CONNECTIVITÉ           LOCALISATION
             │                       │
       ┌─────┼─────┐                 │
       │     │     │                 ▼
      📞    💬    🌐               🛰️ GPS
    Appels  SMS   Data
       │     │     │
       └─────┼─────┘
             │
           📡 Modem
             │
             ▼
          SIM / GSM
             │
             ▼
        Opérateur
```

Pour diagnostiquer un problème, il faut toujours remonter cette chaîne **du matériel vers le logiciel** plutôt que de modifier directement la configuration du système.

> **Un téléphone Ubuntu Touch fonctionnel ne se résume pas à démarrer Lomiri : il faut également que le modem, la SIM, le réseau, la téléphonie, les données mobiles et les services de localisation soient correctement pris en charge par le port de l'appareil.**
