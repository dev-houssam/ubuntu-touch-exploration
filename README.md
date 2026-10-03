# ubuntu-touch-exploration

**Ubuntu Touch** est un système d'exploitation mobile libre basé sur l'écosystème Ubuntu et maintenu aujourd'hui par la communauté **UBports**.

Son objectif est de proposer une alternative aux systèmes mobiles traditionnels comme Android et iOS, en donnant davantage de contrôle à l'utilisateur sur son appareil.

> ⚠️ **Attention : installer Ubuntu Touch sur un smartphone n'est pas une simple installation d'application.**
>
> Le processus peut nécessiter le déverrouillage du bootloader et l'effacement complet du téléphone. Il faut donc vérifier la compatibilité de l'appareil et sauvegarder ses données **avant toute manipulation**.

---

## 🧭 Sommaire

* [Qu'est-ce qu'Ubuntu Touch ?](#-quest-ce-quubuntu-touch)
* [Qui développe Ubuntu Touch ?](#-qui-développe-ubuntu-touch)
* [Comment ça fonctionne ?](#-comment-ça-fonctionne)
* [Ubuntu Touch vs Android](#-ubuntu-touch-vs-android)
* [Compatibilité des appareils](#-compatibilité-des-appareils)
* [⚠️ Précautions avant installation](#️-précautions-avant-installation)
* [Installation avec UBports Installer](#-installation-avec-ubports-installer)
* [Installation étape par étape](#-installation-étape-par-étape)
* [Que se passe-t-il pendant l'installation ?](#-que-se-passe-t-il-pendant-linstallation)
* [Après l'installation](#-après-linstallation)
* [Applications Android](#-applications-android)
* [Problèmes et récupération](#-problèmes-et-récupération)
* [Retour vers Android](#-retour-vers-android)
* [Limitations](#-limitations)
* [Ressources officielles](#-ressources-officielles)

---

# 🌍 Qu'est-ce qu'Ubuntu Touch ?

Ubuntu Touch est un **système d'exploitation mobile basé sur Linux**.

Il est destiné principalement aux :

* smartphones ;
* tablettes ;
* appareils mobiles compatibles avec les ports UBports.

Le projet était à l'origine développé par **Canonical**, l'entreprise derrière Ubuntu.

Canonical a ensuite arrêté le développement officiel d'Ubuntu Touch. Le projet a été repris et poursuivi par la communauté **UBports**.

Aujourd'hui, UBports maintient donc le système, son infrastructure, ses outils et de nombreux ports pour différents appareils.

[Site officiel des appareils Ubuntu Touch](https://devices.ubuntu-touch.io/)

---

# 🏗️ Comment ça fonctionne ?

Ubuntu Touch n'est pas simplement une version d'Ubuntu Desktop adaptée à un écran de téléphone.

Un smartphone possède une architecture matérielle particulière :

```text
┌──────────────────────────────┐
│        Applications          │
├──────────────────────────────┤
│       Ubuntu Touch           │
│                              │
│        Interface             │
│         Lomiri               │
├──────────────────────────────┤
│       Services système       │
├──────────────────────────────┤
│       Couche matérielle      │
│          Halium               │
├──────────────────────────────┤
│       Kernel Linux           │
├──────────────────────────────┤
│       Matériel téléphone     │
│ CPU / GPU / écran / caméra   │
│ modem / Wi-Fi / Bluetooth    │
└──────────────────────────────┘
```

Une partie importante de la compatibilité repose sur **Halium**, qui permet à Ubuntu Touch de fonctionner avec certaines parties de l'écosystème matériel Android.

C'est notamment pour cette raison qu'un même système Ubuntu Touch ne peut pas être installé indistinctement sur tous les smartphones.

---

# 📱 Ubuntu Touch vs Android

Ubuntu Touch et Android utilisent tous les deux le noyau Linux, mais leur environnement logiciel est différent.

| Élément                    | Android                 | Ubuntu Touch                                                |
| -------------------------- | ----------------------- | ----------------------------------------------------------- |
| Kernel                     | Linux                   | Linux                                                       |
| Système utilisateur        | Android                 | GNU/Linux                                                   |
| Interface                  | Android UI              | Lomiri                                                      |
| Applications               | APK                     | Applications Ubuntu Touch / Web / Waydroid selon l'appareil |
| Gestion du système         | Android                 | Ubuntu / technologies Linux                                 |
| Bootloader                 | Généralement verrouillé | Doit généralement être déverrouillé                         |
| Installation d'un autre OS | Limitée                 | Possible sur appareils compatibles                          |

Ubuntu Touch n'est donc **pas un launcher Android**.

Il remplace réellement le système d'exploitation installé sur le téléphone.

---

# 🖥️ Interface graphique : Lomiri

L'interface graphique principale d'Ubuntu Touch est **Lomiri**.

Elle est conçue pour une utilisation tactile et mobile.

L'idée est de conserver une expérience Linux tout en proposant une interface adaptée à un petit écran.

On retrouve notamment :

* écran d'accueil ;
* applications ;
* paramètres ;
* notifications ;
* multitâche ;
* terminal ;
* gestion réseau ;
* stockage ;
* comptes utilisateur.

---

# 📱 Compatibilité des appareils

C'est probablement **la vérification la plus importante avant toute installation**.

Ubuntu Touch ne fonctionne pas automatiquement sur tous les téléphones Android.

Il faut vérifier :

1. la marque ;
2. le modèle exact ;
3. le numéro de modèle ;
4. le nom de code de l'appareil ;
5. la version Android/ROM requise ;
6. les fonctionnalités réellement fonctionnelles.

Par exemple, deux téléphones portant des noms commerciaux proches peuvent utiliser des composants matériels complètement différents.

### ⚠️ Ne jamais se contenter du nom commercial

Il faut vérifier le **modèle exact**.

Exemple :

```text
❌ "J'ai un Xiaomi Redmi"

✅ "J'ai un Xiaomi Redmi Note 9 M2003J6A2G"
```

Le second niveau d'information permet de déterminer si le port Ubuntu Touch correspond réellement à l'appareil.

[Liste officielle des appareils compatibles](https://devices.ubuntu-touch.io/)

---

# ⚠️ Précautions avant installation

## 1. Sauvegarder toutes ses données

L'installation peut entraîner l'effacement du téléphone.

Sauvegarder notamment :

* photos ;
* vidéos ;
* contacts ;
* documents ;
* conversations importantes ;
* fichiers téléchargés ;
* authentificateurs ;
* clés de récupération ;
* données d'applications.

### Principe simple

> **Considérer le téléphone comme s'il allait être entièrement formaté.**

Ne commencez pas l'installation si vous avez encore des données importantes uniquement présentes sur l'appareil.

UBports indique explicitement qu'un passage depuis Android peut nécessiter l'effacement des données et recommande donc une sauvegarde externe.

---

# 2. Vérifier le modèle exact

Avant de télécharger quoi que ce soit :

```text
Téléphone
   ↓
Modèle exact
   ↓
Page UBports correspondante
   ↓
Vérification de la compatibilité
```

Ne pas installer une image destinée à un autre appareil simplement parce que celui-ci semble similaire.

---

# 3. Vérifier la version Android requise

Certains ports Ubuntu Touch nécessitent une version précise de la ROM Android d'origine.

Par exemple :

```text
Ubuntu Touch
      │
      └── Port basé sur Halium X
                   │
                   └── Android/firmware requis
```

La version nécessaire dépend donc du port.

La documentation officielle indique qu'il faut généralement installer la version Android/stock ROM demandée par le port avant d'utiliser l'installateur.

**Toujours lire la page spécifique à son appareil.**

---

# 4. Vérifier le bootloader

Le **bootloader** est le programme qui démarre le système avant le système d'exploitation.

Pour installer Ubuntu Touch sur la plupart des appareils Android compatibles, il faut déverrouiller le bootloader.

```text
Téléphone
   │
   ▼
Bootloader verrouillé
   │
   │ déverrouillage
   ▼
Bootloader déverrouillé
   │
   ▼
Installation Ubuntu Touch
```

La méthode pour déverrouiller le bootloader dépend du constructeur.

Il n'existe donc pas une procédure universelle.

---

# 5. Attention à la garantie

Le déverrouillage du bootloader peut avoir des conséquences sur la garantie selon le constructeur et la région.

Il faut vérifier les conditions applicables à son appareil avant de continuer.

---

# 6. Batterie

Avant de commencer :

```text
🔋 Batterie recommandée : suffisamment chargée
```

Éviter de commencer une installation critique avec une batterie presque vide.

Idéalement :

```text
🔋 > 50 %
```

et conserver le téléphone connecté à l'alimentation lorsque c'est possible.

---

# 7. Utiliser un câble USB de qualité

Une installation peut échouer si la communication USB est interrompue.

Utiliser :

* un câble USB permettant le transfert de données ;
* un port USB fiable ;
* éviter les hubs USB douteux ;
* éviter les câbles uniquement destinés à la recharge.

UBports recommande notamment de changer de câble ou de port USB lorsqu'une connexion est perdue pendant l'installation.

---

# 8. Ne pas improviser avec Fastboot

On trouve beaucoup de tutoriels sur Internet contenant des commandes du type :

```bash
fastboot flash ...
```

ou :

```bash
adb shell ...
```

Ces commandes peuvent être parfaitement légitimes **pour le bon appareil**, mais dangereuses si elles sont appliquées au mauvais modèle ou avec les mauvais fichiers.

Pour une première installation :

> **Privilégier UBports Installer plutôt qu'une installation manuelle.**

UBports déconseille l'installation manuelle sauf lorsque l'on sait précisément ce que l'on fait.

---

# 🚀 Installation avec UBports Installer

La méthode recommandée est **UBports Installer**.

Il existe des versions pour :

* Windows ;
* macOS ;
* Ubuntu/Debian ;
* autres distributions Linux.

[Télécharger UBports Installer](https://devices.ubuntu-touch.io/installer/)

---

# 🧰 Préparation

Avant de lancer l'installation :

```text
☑ Téléphone compatible
☑ Modèle exact vérifié
☑ Sauvegarde terminée
☑ Bootloader déverrouillable
☑ Version Android requise vérifiée
☑ Batterie suffisamment chargée
☑ Câble USB de données
☑ Ordinateur disponible
☑ Connexion Internet disponible
```

---

# 1️⃣ Installer UBports Installer

Télécharger la version correspondant à son système.

Par exemple sous Debian/Ubuntu :

```text
ubports-installer-*.deb
```

Sous Windows :

```text
ubports-installer-*.exe
```

Sous macOS :

```text
ubports-installer-*.dmg
```

D'autres formats sont également disponibles pour Linux.

---

# 2️⃣ Ne pas lancer l'installateur avec sudo

Sous Linux, il peut être tentant de faire :

```bash
sudo ubports-installer
```

**À éviter.**

L'installateur est prévu pour être exécuté comme utilisateur normal.

Le lancer avec `sudo` peut provoquer des problèmes de permissions dans ses fichiers de cache.

---

# 3️⃣ Connecter le téléphone

Brancher le téléphone à l'ordinateur avec le câble USB.

Selon l'appareil, il peut être nécessaire d'activer :

```text
Options développeur
        │
        ▼
Débogage USB
```

Le téléphone peut également afficher une demande d'autorisation concernant la connexion ADB.

---

# 4️⃣ Lancer UBports Installer

L'interface va détecter le téléphone et demander les informations nécessaires.

Le principe général est :

```text
┌─────────────────────┐
│ UBports Installer   │
└──────────┬──────────┘
           │
           ▼
   Détection appareil
           │
           ▼
   Vérification port
           │
           ▼
    Déverrouillage
           │
           ▼
     Installation
           │
           ▼
       Redémarrage
           │
           ▼
     Ubuntu Touch
```

L'installateur effectue une grande partie des opérations automatiquement.

---

# 5️⃣ Lire attentivement les avertissements

À ce stade, **ne pas cliquer automatiquement sur "Next"**.

Lire chaque avertissement concernant :

* effacement des données ;
* bootloader ;
* version Android ;
* firmware ;
* partitionnement ;
* récupération éventuelle.

Si l'installateur indique que le téléphone n'est pas compatible :

> **Arrêter l'installation.**

Ne pas forcer l'opération.

---

# 6️⃣ Laisser l'installation se terminer

Pendant l'installation :

### ❌ Ne pas

* débrancher le câble ;
* éteindre volontairement le téléphone ;
* redémarrer l'ordinateur ;
* fermer brutalement l'installateur ;
* lancer simultanément d'autres outils de flash ;
* exécuter des commandes Fastboot trouvées au hasard.

### ✅ Faire

* attendre ;
* conserver le câble connecté ;
* suivre les instructions affichées ;
* lire les éventuelles erreurs.

---

# 🔧 Que se passe-t-il techniquement ?

L'installation peut être représentée de manière simplifiée comme ceci :

```text
Android existant
       │
       ▼
┌──────────────┐
│ Bootloader   │
└──────┬───────┘
       │
       ▼
Préparation du téléphone
       │
       ▼
Installation des composants
Ubuntu Touch / Halium / Kernel
       │
       ▼
Configuration des partitions
       │
       ▼
Redémarrage
       │
       ▼
┌──────────────────────────┐
│      Ubuntu Touch        │
│                          │
│        Lomiri            │
│           │              │
│       Applications       │
└──────────────────────────┘
```

Le détail exact dépend cependant du modèle et de son port Ubuntu Touch.

---

# 🎉 Premier démarrage

Le premier démarrage peut être plus long qu'un démarrage normal.

Une fois Ubuntu Touch lancé :

```text
🌐 Configurer le réseau
📱 Configurer l'appareil
🔐 Configurer les paramètres de sécurité
🕐 Configurer la date/heure
📦 Installer les applications nécessaires
```

Il est ensuite recommandé de tester progressivement :

```text
☑ Écran tactile
☑ Wi-Fi
☑ Bluetooth
☑ Appels
☑ SMS
☑ Données mobiles
☑ GPS
☑ Caméra
☑ Haut-parleurs
☑ Microphone
☑ USB
☑ Veille/réveil
```

---

# 🤖 Applications Android

Ubuntu Touch n'exécute pas directement les applications Android comme Android lui-même.

Certaines applications Android peuvent cependant être utilisées avec **Waydroid**, une couche permettant d'exécuter des applications Android dans un environnement conteneurisé.

Cela ne signifie pas que toutes les applications fonctionneront correctement.

Certaines applications dépendent notamment :

* de Google Play Services ;
* de DRM ;
* de fonctionnalités matérielles particulières ;
* de mécanismes propriétaires.

UBports indique notamment que l'écosystème applicatif est plus petit que celui d'Android et que Waydroid peut servir pour certaines applications Android.

---

# ⚠️ Limitations à connaître

Ubuntu Touch n'est pas actuellement un remplacement parfait d'Android ou d'iOS.

Selon l'appareil, certaines fonctionnalités peuvent être :

```text
🟢 Fonctionnelles
🟡 Fonctionnelles avec limitations
🔴 Non fonctionnelles
```

Cela peut concerner :

* caméra ;
* GPS ;
* Bluetooth ;
* VoLTE ;
* applications Android ;
* services Google ;
* certaines applications bancaires ;
* certains codecs ;
* certaines fonctions matérielles.

Le niveau de support dépend fortement du téléphone et de la communauté qui maintient son port.

---

# 🧩 Featured Devices et Community Devices

Tous les appareils compatibles ne bénéficient pas du même niveau de support.

UBports distingue notamment des appareils particulièrement mis en avant et des appareils maintenus par la communauté.

Il faut donc regarder **la page du téléphone lui-même**, plutôt que de considérer "compatible" comme synonyme de "tout fonctionne".

---

# 🆘 Que faire si l'installation échoue ?

Première règle :

> **Ne pas paniquer.**

Un téléphone bloqué sur un logo ne signifie pas automatiquement qu'il est définitivement inutilisable.

Vérifier d'abord :

```text
1. Le câble USB
2. Le port USB
3. Le modèle exact
4. La version Android requise
5. Le bootloader
6. Les instructions spécifiques au modèle
```

Les problèmes de connexion USB sont notamment une cause fréquente d'échec de communication avec l'installateur.

---

# 🔄 Fastboot / Recovery

De nombreux téléphones Android possèdent différents modes de récupération :

```text
                     Téléphone
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼
      Android        Bootloader      Recovery
                         │
                         ▼
                      Fastboot
```

Ces modes permettent notamment de récupérer un appareil lorsque le système installé ne démarre plus.

**Attention : les combinaisons de boutons et procédures diffèrent selon les constructeurs.**

---

# 🔙 Retour vers Android

Il est généralement possible de revenir à Android, mais il ne faut pas considérer cette opération comme automatique.

Avant l'installation, il est donc conseillé de savoir :

```text
"Si Ubuntu Touch ne me convient pas,
comment vais-je restaurer mon téléphone ?"
```

Pour certains appareils, la restauration vers l'état d'usine nécessite des fichiers ou procédures spécifiques au constructeur.

**Il faut donc rechercher la procédure de restauration avant de commencer l'installation.**

---

# 🧠 Règle d'or

Avant d'installer Ubuntu Touch :

```text
┌───────────────────────────────────────┐
│        NE PAS COMMENCER SI...         │
├───────────────────────────────────────┤
│ ❌ Le modèle n'est pas confirmé      │
│ ❌ Les données ne sont pas sauvegardées│
│ ❌ Le firmware requis est inconnu    │
│ ❌ La procédure de restauration est  │
│    inconnue                           │
│ ❌ Le téléphone n'est pas compatible │
└───────────────────────────────────────┘
```

Et inversement :

```text
┌───────────────────────────────────────┐
│          PRÊT À INSTALLER             │
├───────────────────────────────────────┤
│ ✅ Appareil compatible                │
│ ✅ Sauvegarde effectuée               │
│ ✅ Firmware vérifié                   │
│ ✅ Bootloader compris                 │
│ ✅ Procédure de restauration connue   │
│ ✅ UBports Installer installé         │
│ ✅ Câble USB fiable                   │
└───────────────────────────────────────┘
```

---

# 🧪 Pourquoi essayer Ubuntu Touch ?

Ubuntu Touch peut être intéressant pour :

* découvrir Linux sur mobile ;
* expérimenter avec un système libre ;
* reprendre davantage de contrôle sur son téléphone ;
* apprendre le fonctionnement d'un OS mobile ;
* développer des applications Linux/mobile ;
* recycler un ancien smartphone compatible ;
* expérimenter avec du matériel et des systèmes embarqués.

Ce n'est cependant pas nécessairement le meilleur choix pour quelqu'un qui dépend fortement de l'écosystème Android ou d'applications propriétaires.

---

# 📚 Ressources officielles

### Ubuntu Touch

[Ubuntu Touch — appareils compatibles](https://devices.ubuntu-touch.io/)

### UBports

[Site officiel UBports](https://ubports.com/)

### UBports Installer

[UBports Installer](https://devices.ubuntu-touch.io/installer/)

### Documentation

[Documentation UBports](https://docs.ubports.com/)

### FAQ

[FAQ Ubuntu Touch / UBports](https://ubports.com/faq)

---

# 📌 Résumé

Installer Ubuntu Touch revient globalement à :

```text
             ┌─────────────────┐
             │ 1. Identifier   │
             │ son téléphone   │
             └────────┬────────┘
                      ▼
             ┌─────────────────┐
             │ 2. Vérifier la  │
             │ compatibilité   │
             └────────┬────────┘
                      ▼
             ┌─────────────────┐
             │ 3. Sauvegarder  │
             │ ses données     │
             └────────┬────────┘
                      ▼
             ┌─────────────────┐
             │ 4. Vérifier     │
             │ firmware/ROM    │
             └────────┬────────┘
                      ▼
             ┌─────────────────┐
             │ 5. Déverrouiller│
             │ le bootloader   │
             └────────┬────────┘
                      ▼
             ┌─────────────────┐
             │ 6. Installer    │
             │ UBports Installer│
             └────────┬────────┘
                      ▼
             ┌─────────────────┐
             │ 7. Installer    │
             │ Ubuntu Touch    │
             └────────┬────────┘
                      ▼
             ┌─────────────────┐
             │ 8. Tester le    │
             │ matériel        │
             └─────────────────┘
```

**Le point le plus important :**

> **Ne jamais commencer par flasher le téléphone. Commencer par identifier précisément le modèle et lire sa page Ubuntu Touch.**

La procédure générale est commune, mais les précautions et prérequis peuvent changer complètement d'un appareil à l'autre.
