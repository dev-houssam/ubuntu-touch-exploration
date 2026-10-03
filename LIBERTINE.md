# 🐧 Libertine sur Ubuntu Touch

**Libertine** est le système d'Ubuntu Touch permettant d'exécuter des **applications Linux desktop classiques** dans un environnement isolé.

Il permet notamment d'installer des paquets Debian (`.deb`) et d'utiliser des logiciels qui n'ont pas été développés spécifiquement pour Ubuntu Touch.

> **Ubuntu Touch n'est pas nécessairement limité aux applications mobiles.**
>
> Avec Libertine, il est possible de disposer d'un environnement Linux supplémentaire dans lequel installer des applications desktop.

---

## 📚 À propos d'Ubuntu Touch

Si vous découvrez Ubuntu Touch, commencez par le README principal :

👉 **[📱 Découvrir et installer Ubuntu Touch](./README.md)**

Ce document explique notamment :

* ce qu'est Ubuntu Touch ;
* son architecture ;
* la compatibilité des téléphones ;
* le déverrouillage du bootloader ;
* les précautions avant installation ;
* l'installation avec UBports Installer ;
* les problèmes pouvant survenir lors de l'installation.

**Ce document-ci suppose qu'Ubuntu Touch est déjà installé et fonctionnel.**

---

# 🧩 Qu'est-ce que Libertine ?

Ubuntu Touch possède son propre environnement mobile.

Cependant, certaines applications Linux classiques ne sont pas conçues pour cet environnement.

Libertine fournit alors un **conteneur Linux séparé** dans lequel ces applications peuvent être installées.

```text
┌──────────────────────────────────────────┐
│              Ubuntu Touch                │
│                                          │
│                 Lomiri                   │
│                    │                     │
│          Applications mobiles            │
│                    │                     │
│                    ▼                     │
│              ┌───────────┐               │
│              │ Libertine │               │
│              └─────┬─────┘               │
│                    │                     │
│             Conteneur Linux              │
│                    │                     │
│       ┌────────────┼────────────┐        │
│       │            │            │        │
│      Vim         Gedit        Git        │
│       │            │            │        │
│       └────────────┴────────────┘        │
│                    │                     │
│              Paquets Debian             │
│                                          │
└──────────────────────────────────────────┘
```

Le système principal d'Ubuntu Touch utilise notamment une racine en lecture seule pour permettre son système de mises à jour. Libertine fournit un environnement dans lequel le système de fichiers peut être modifié et où des logiciels desktop peuvent être installés.

---

# ⚙️ Comment fonctionne Libertine ?

Un conteneur Libertine possède son propre environnement utilisateur Linux.

Il ne s'agit cependant **pas d'une machine virtuelle complète**.

Le principe est plutôt :

```text
                    Téléphone
                       │
                 Kernel Linux
                       │
                Ubuntu Touch
                       │
                    Lomiri
                       │
                   Libertine
                       │
                ┌──────┴──────┐
                │  Conteneur  │
                │    Linux    │
                └──────┬──────┘
                       │
              Applications .deb
```

Selon le support du périphérique, Libertine peut utiliser un conteneur `chroot` ou `lxc`.

`chroot` est le mode compatible avec tous les appareils, tandis que `lxc` est recommandé lorsque le kernel de l'appareil le permet.

---

# ⚠️ Avant de commencer

Libertine est puissant, mais toutes les applications Linux desktop ne sont pas adaptées à un smartphone.

Une application peut rencontrer des problèmes liés à :

* l'écran tactile ;
* la taille de l'interface ;
* la mise à l'échelle ;
* la résolution ;
* l'architecture ARM ;
* certaines dépendances ;
* l'accès au matériel.

Les applications Libertine **ne sont pas destinées à fonctionner en arrière-plan**.

Libertine ne doit donc pas être considéré comme un moyen de transformer le téléphone en serveur permanent.

---

# 📦 Créer un conteneur Libertine

La méthode la plus simple consiste à passer par les paramètres d'Ubuntu Touch.

Ouvrir :

```text
Paramètres
   ↓
Système
   ↓
Libertine
   ↓
Gérer les conteneurs Libertine
   ↓
+
```

Un assistant permet ensuite de choisir :

* un identifiant ;
* un nom ;
* éventuellement un mot de passe.

La création du conteneur peut prendre un certain temps car plusieurs centaines de mégaoctets peuvent être nécessaires.

---

# 💻 Créer un conteneur depuis le terminal

La création peut également être réalisée avec :

```bash
libertine-container-manager create -i mon-conteneur
```

Par exemple :

```bash
libertine-container-manager create -i desktop
```

Pour choisir explicitement le type de conteneur :

```bash
libertine-container-manager create \
    -i desktop \
    -t lxc
```

ou :

```bash
libertine-container-manager create \
    -i desktop \
    -t chroot
```

`chroot` constitue le choix compatible avec tous les appareils. `lxc` peut être préférable lorsque le kernel le supporte.

### ⚠️ Terminal Ubuntu Touch

La commande `create` peut être bloquée directement depuis l'application Terminal à cause des restrictions AppArmor.

Dans ce cas, UBports indique qu'on peut passer par une connexion **ADB ou SSH**, ou utiliser une connexion SSH locale avec :

```bash
ssh localhost
```

---

# 🔎 Vérifier les conteneurs

Pour afficher les conteneurs disponibles :

```bash
libertine-container-manager list
```

Exemple :

```text
desktop
```

---

# 📦 Installer une application

Une fois le conteneur créé, les applications peuvent être installées depuis l'interface :

```text
Paramètres
   ↓
Système
   ↓
Libertine
   ↓
Gérer les conteneurs
   ↓
desktop
   ↓
+
```

On peut alors rechercher un paquet dans les dépôts disponibles.

---

## 🖥️ Installation avec le terminal

Pour installer directement un paquet :

```bash
libertine-container-manager install-package \
    -i desktop \
    -p PACKAGE-NAME
```

Par exemple :

```bash
libertine-container-manager install-package \
    -i desktop \
    -p gedit
```

Le paquet est alors installé **dans le conteneur**, et non dans le système principal Ubuntu Touch.

---

# 📋 Lister les applications installées

Pour afficher les applications du conteneur :

```bash
libertine-container-manager list-apps
```

Les applications installées deviennent normalement accessibles depuis le lanceur d'applications d'Ubuntu Touch.

---

# ▶️ Lancer une application

Dans la majorité des cas, il suffit de lancer l'application depuis le menu des applications Ubuntu Touch.

Il est également possible de lancer une application graphiquement depuis le terminal.

Exemple :

```bash
lomiri-app-launch focal_gedit_0.0
```

Le nom exact dépend du fichier `.desktop` créé par l'application.

---

# 🐚 Entrer dans le conteneur

Libertine permet également d'exécuter directement des commandes dans le conteneur.

## Avec `libertine-container-manager`

```bash
libertine-container-manager exec \
    -i desktop \
    -c "COMMAND"
```

Exemple :

```bash
libertine-container-manager exec \
    -i desktop \
    -c "apt-get --help"
```

Pour obtenir un shell `root` :

```bash
libertine-container-manager exec \
    -i desktop \
    -c "/bin/bash"
```

---

# 👤 Utiliser l'utilisateur `phablet`

Une autre méthode consiste à utiliser :

```bash
libertine-launch
```

Exemple :

```bash
libertine-launch -i desktop ls -a
```

Pour ouvrir un shell :

```bash
DISPLAY= libertine-launch \
    -i desktop \
    /bin/bash
```

Cette méthode permet d'exécuter les commandes en tant qu'utilisateur `phablet` dans un conteneur correctement configuré.

---

# 📁 Accéder aux fichiers personnels

Les applications Libertine peuvent accéder à certains répertoires personnels d'Ubuntu Touch :

```text
Documents/
Music/
Pictures/
Downloads/
Videos/
```

Cela permet par exemple à une application desktop de travailler sur des fichiers présents dans le stockage utilisateur.

---

# 💾 Installer un fichier `.deb`

Il est également possible d'installer manuellement un paquet Debian.

Supposons que le fichier soit :

```text
~/Downloads/application.deb
```

Il faut d'abord rendre le fichier accessible au conteneur.

Exemple :

```bash
cp ~/Downloads/application.deb \
   ~/.cache/libertine-container/desktop/rootfs/root/
```

Puis :

```bash
libertine-container-manager exec \
    -i desktop \
    -c "dpkg -i /root/application.deb"
```

Cette méthode est particulièrement utile lorsqu'un paquet `.deb` n'est pas disponible directement dans les dépôts du conteneur.

---

# 🗑️ Désinstaller une application

Depuis l'interface Libertine, il est possible de supprimer une application installée.

En ligne de commande :

```bash
libertine-container-manager remove-package \
    -i desktop \
    -p PACKAGE-NAME
```

---

# 🧹 Supprimer un conteneur

Si un conteneur n'est plus nécessaire :

```bash
libertine-container-manager destroy \
    -i desktop
```

⚠️ **Cette opération supprime le conteneur et les applications qu'il contient.**

---

# 📂 Où sont stockés les conteneurs ?

Libertine utilise notamment deux emplacements :

```text
~/.cache/libertine-container/
```

pour le système du conteneur, et :

```text
~/.local/share/libertine-container/user-data/
```

pour les données utilisateur associées au conteneur.

---

# 💡 Exemple concret

Imaginons que l'on souhaite utiliser `git` dans un environnement Linux desktop.

On peut créer :

```text
desktop
```

puis installer :

```bash
libertine-container-manager install-package \
    -i desktop \
    -p git
```

On peut ensuite l'utiliser avec :

```bash
libertine-launch -i desktop git --version
```

On obtient alors conceptuellement :

```text
Ubuntu Touch
│
├── Applications Ubuntu Touch
│
└── Libertine
    │
    └── desktop
        │
        ├── git
        ├── bibliothèques
        ├── outils Linux
        └── fichiers utilisateur
```

---

# 🧠 Libertine ≠ Waydroid

Il est important de ne pas confondre les deux.

| Technologie      | Sert principalement à      |
| ---------------- | -------------------------- |
| **Libertine**    | Applications Linux desktop |
| **Waydroid**     | Applications Android       |
| **Ubuntu Touch** | Système mobile principal   |

On peut donc avoir :

```text
                 Ubuntu Touch
                      │
          ┌───────────┴───────────┐
          │                       │
      Libertine                 Waydroid
          │                       │
          ▼                       ▼
    Applications             Applications
       Linux                   Android
       (.deb)                    (.apk)
```

Waydroid est lui-même décrit par UBports comme un conteneur Android et une couche de compatibilité permettant d'exécuter des applications Android sous GNU/Linux, notamment Ubuntu Touch.

---

# 🚧 Limites importantes

Libertine est particulièrement intéressant pour expérimenter, mais il ne faut pas s'attendre à ce que **toute application Ubuntu Desktop fonctionne parfaitement sur un téléphone**.

### Interface

Une application desktop peut avoir :

```text
❌ petits boutons
❌ menus difficiles à utiliser
❌ mauvaise mise à l'échelle
❌ interface non tactile
```

### Performances

Les applications desktop peuvent également être plus lourdes que les applications conçues nativement pour Ubuntu Touch.

### Services en arrière-plan

Libertine n'est pas conçu pour maintenir des applications desktop en fonctionnement permanent en arrière-plan.

Il ne faut donc pas utiliser Libertine comme remplacement d'un serveur Linux classique.

---

# 🧪 Pourquoi utiliser Libertine ?

Libertine devient particulièrement intéressant pour expérimenter avec :

* Linux ;
* Debian ;
* les paquets `.deb` ;
* les environnements desktop ;
* les outils de développement ;
* Git ;
* éditeurs de texte ;
* scripts ;
* utilitaires système ;
* logiciels Linux compatibles avec l'architecture du téléphone.

Cela permet de rapprocher l'expérience d'un **petit ordinateur Linux de poche**, tout en conservant Ubuntu Touch comme système mobile.

---

# 🔗 Documentation officielle

### Ubuntu Touch

👉 [README principal — découvrir et installer Ubuntu Touch](./README.md)

### UBports

👉 [Documentation officielle UBports](https://docs.ubports.com/)

### Libertine

👉 [Documentation officielle — Libertine](https://docs.ubports.com/en/latest/userguide/dailyuse/libertine.html)

### Waydroid

👉 [Documentation officielle — applications Android](https://docs.ubports.com/en/latest/userguide/dailyuse/waydroid.html)

---

# 📌 Résumé

```text
1. Installer Ubuntu Touch
           │
           ▼
2. Ouvrir Libertine
           │
           ▼
3. Créer un conteneur
           │
           ▼
4. Installer des paquets Debian
           │
           ▼
5. Les applications apparaissent
   dans Ubuntu Touch
           │
           ▼
6. Utiliser des logiciels
   Linux desktop sur le téléphone
```

**Ubuntu Touch fournit le système mobile.**

**Libertine fournit l'environnement permettant d'exécuter des applications Linux desktop.**

Les deux sont donc complémentaires.

---

> 💡 **À retenir**
>
> Libertine ne transforme pas Ubuntu Touch en Ubuntu Desktop.
>
> Il fournit plutôt un **environnement Linux séparé à l'intérieur d'Ubuntu Touch**, destiné à accueillir des applications desktop classiques.
