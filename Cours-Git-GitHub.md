# 🚀 Git & GitHub
## Le guide pratique pour débuter, versionner et collaborer

> **Du premier `git init` à la Pull Request :** apprenez à garder une trace claire de votre travail et à construire des projets à plusieurs, sans perdre vos modifications en chemin.

**Niveau :** débutant · **Format :** cours + travaux pratiques · **Durée :** 3 h 45 · **Langue :** français

> **🖼️ IMAGE DE COUVERTURE À AJOUTER ICI**  
> Choisissez une illustration panoramique et épurée montrant plusieurs développeurs qui collaborent autour d’un projet, avec un terminal, des branches reliées et un logo GitHub discret. Palette conseillée : violet, indigo et orange. Évitez une capture d’écran trop chargée.

---

## ✨ À la fin de ce cours, vous saurez…

- expliquer le rôle de Git et la différence entre Git et GitHub ;
- enregistrer et retrouver des versions de votre travail ;
- créer une branche, fusionner des changements et résoudre un conflit simple ;
- relier un dépôt local à GitHub et envoyer ou récupérer des changements ;
- proposer une modification avec une Pull Request ;
- adopter de bonnes habitudes pour travailler en équipe.

### 🧭 Parcours du cours

1. [Comprendre le contrôle de version](#1--comprendre-le-contrôle-de-version)
2. [Installer et configurer Git](#2--installer-et-configurer-git)
3. [Comprendre le fonctionnement de Git](#3--comprendre-le-fonctionnement-de-git)
4. [Maîtriser les commandes fondamentales](#4--les-commandes-fondamentales)
5. [Travailler avec des branches](#5--travailler-avec-des-branches)
6. [Fusionner des branches](#6--fusionner-des-branches)
7. [Découvrir GitHub](#7--découvrir-github)
8. [Connecter Git à GitHub](#8--connecter-git-à-github)
9. [Collaborer avec des Pull Requests](#9--collaborer-sur-un-projet)
10. [Appliquer les bonnes pratiques](#10--bonnes-pratiques-et-outils-complémentaires)
11. [Réaliser les travaux pratiques](#-travaux-pratiques)
12. [Mener le projet final](#-projet-final--un-site-pour-votre-club)

---

## 1 · Comprendre le contrôle de version

### Qu’est-ce que le contrôle de version ?

Le **contrôle de version** consiste à conserver l’historique des modifications apportées à un ensemble de fichiers. On peut ainsi savoir **ce qui a changé, quand, et par qui**, comparer deux versions et revenir à un état précédent.

Imaginez un document avec une fonction « historique des versions », mais adaptée au code et au travail en équipe.

### Pourquoi utiliser un système de contrôle de version ?

- **Se protéger des erreurs :** retrouver une version fonctionnelle après une modification ratée.
- **Comprendre l’historique :** savoir pourquoi un changement a été fait.
- **Travailler en parallèle :** chacun peut développer une fonctionnalité sans écraser le travail des autres.
- **Partager son travail :** échanger les changements avec une équipe ou les publier.
- **Expérimenter sereinement :** essayer une idée sur une branche séparée.

Sans Git, on finit souvent par échanger des fichiers comme `projet-final-v2-bon-cette-fois.zip` ou à copier le dossier entier avant chaque modification. Ces solutions prennent de la place, rendent les comparaisons difficiles et créent facilement des versions contradictoires.

### Git et GitHub : deux choses différentes

| Git | GitHub |
|---|---|
| Logiciel de contrôle de version. | Service en ligne de développement collaboratif. |
| Fonctionne sur votre ordinateur, même sans Internet. | Héberge des dépôts Git et facilite le travail d’équipe. |
| Enregistre les modifications sous forme de commits. | Propose notamment les Pull Requests, Issues et Discussions. |
| Exemple : `git status` | Exemple : une page de dépôt sur `github.com` |

**Git n’est pas GitHub.** Git est l’outil ; GitHub est une plateforme qui peut héberger un dépôt Git. D’autres plateformes, comme GitLab et Bitbucket, peuvent aussi héberger des dépôts Git.

### Git face aux autres systèmes

Git est un système **distribué** : chaque clone contient normalement l’historique du dépôt. D’autres outils, comme SVN, reposent davantage sur un serveur central. Git est devenu très populaire pour le développement logiciel grâce à sa rapidité, à ses branches et à son vaste écosystème.

> **🖼️ IMAGE À AJOUTER — Git n’est pas GitHub**  
> Créez un visuel simple en deux colonnes : à gauche, un ordinateur avec Git et un historique local ; à droite, GitHub dans le nuage avec plusieurs personnes qui collaborent. Reliez-les par une flèche « push / pull ».

**À retenir :** Git suit l’évolution de vos fichiers ; GitHub facilite l’hébergement et la collaboration autour d’un dépôt Git.

---

## 2 · Installer et configurer Git

### Installation

- **Windows :** téléchargez Git depuis [git-scm.com/downloads](https://git-scm.com/downloads), puis ouvrez **Git Bash** ou le terminal intégré à votre éditeur.
- **macOS :** installez Git depuis le site officiel ou avec un gestionnaire de paquets, par exemple `brew install git` si Homebrew est déjà installé.
- **Linux :** utilisez le gestionnaire de paquets de votre distribution, par exemple `sudo apt install git` sur Ubuntu ou Debian.

Suivez les choix d’installation recommandés si vous débutez. Git Bash fournit sous Windows un terminal pratique pour utiliser les commandes présentées dans ce cours.

Vérifiez que Git est disponible :

```bash
git --version
```

La commande affiche la version installée, par exemple `git version 2.x.x`.

### Configuration de votre identité

Git ajoute le nom et l’adresse configurés à l’auteur de vos commits. Indiquez une identité que vous souhaitez voir associée à vos modifications :

```bash
git config --global user.name "Votre Nom"
git config --global user.email "vous@example.com"
```

Le paramètre `--global` applique ce réglage à vos dépôts pour votre compte utilisateur. Sans `--global`, la configuration faite depuis un dépôt s’applique uniquement à celui-ci.

Pour régler une identité différente **uniquement dans le dépôt courant** :

```bash
git config user.name "Nom du projet"
git config user.email "projet@example.com"
```

Pour consulter les réglages :

```bash
git config --list
git config user.name
git config user.email
```

> **Confidentialité :** si vous ne souhaitez pas exposer votre adresse personnelle dans des commits publics, configurez l’adresse de confidentialité fournie par GitHub dans votre compte et utilisez-la comme adresse Git.

### Choisir l’éditeur de texte

Vous pouvez définir l’éditeur utilisé par certaines commandes Git. Par exemple, pour Visual Studio Code :

```bash
git config --global core.editor "code --wait"
```

L’option `--wait` demande à Git d’attendre la fermeture de l’éditeur avant de poursuivre.

> **🖼️ IMAGE À AJOUTER — Installation et premier terminal**  
> Utilisez une capture d’écran claire de Git Bash ou du terminal de VS Code affichant `git --version`, sans nom d’utilisateur, chemin privé ni autre donnée personnelle visible.

**Mini-vérification :** exécutez `git --version`, puis `git config user.name`. Si votre nom apparaît, votre identité est prête.

---

## 3 · Comprendre le fonctionnement de Git

### Dépôt local et dépôt distant

Un **dépôt** (repository ou *repo*) est un projet suivi par Git, avec ses fichiers et son historique.

- Le **dépôt local** est la copie de travail présente sur votre ordinateur.
- Le **dépôt distant** est une copie hébergée ailleurs, souvent sur GitHub, avec laquelle vous échangez des changements.

### Les trois espaces de travail

Git organise le travail en trois zones :

1. **Working Directory — répertoire de travail :** vos fichiers tels qu’ils existent actuellement sur le disque.
2. **Staging Area — zone de préparation (index) :** les modifications sélectionnées pour le prochain commit.
3. **Repository — dépôt Git (`.git`) :** les commits déjà enregistrés et l’historique.

```text
┌─────────────────────┐    git add     ┌────────────────────┐   git commit   ┌───────────────────┐
│ Répertoire de travail│ ─────────────▶ │ Zone de préparation│ ─────────────▶ │ Historique Git    │
│ Working Directory    │                │ Staging Area       │                │ Repository (.git) │
└─────────────────────┘                └────────────────────┘                └───────────────────┘
          ▲                                      │
          └────────────── git restore --staged ──┘
```

Le `git add` **ne crée pas encore** de commit : il prépare le contenu sélectionné. Le `git commit` enregistre ensuite un instantané de ce qui a été préparé.

### Les commits et les snapshots

Un **commit** est un point nommé de l’historique qui enregistre l’état du projet préparé. Il contient notamment un identifiant, un auteur, une date et un message.

On parle souvent d’**instantané** (*snapshot*) : un commit décrit l’état du projet à un moment donné. Les commits sont reliés entre eux, ce qui forme un historique que l’on peut parcourir.

### Cycle de vie simplifié d’un fichier

```text
Non suivi ── git add ──▶ Préparé ── git commit ──▶ Suivi et enregistré
                              ▲                          │
                              └──── modification ────────┘
```

- **Non suivi (untracked) :** Git ne suit pas encore ce fichier.
- **Modifié (modified) :** un fichier suivi a changé depuis le dernier commit.
- **Préparé (staged) :** les changements sont sélectionnés pour le prochain commit.
- **Enregistré (committed) :** les changements font partie de l’historique local.

> **🖼️ IMAGE À AJOUTER — Les trois zones de Git**  
> Préparez une infographie en trois blocs reliés par des flèches `git add` et `git commit` : dossier de travail, index / zone de préparation, historique `.git`. Ajoutez une flèche de retour `git restore --staged` vers le dossier de travail.

**À retenir :** on choisit d’abord ce qui entre dans un commit avec `git add`, puis on enregistre ce choix avec `git commit`.

---

## 4 · Les commandes fondamentales

### Créer ou récupérer un projet

Initialiser Git dans un nouveau dossier :

```bash
git init
```

Git crée un dépôt dans le dossier courant. Le dossier caché `.git` contient les données de l’historique ; ne le modifiez pas manuellement.

Pour récupérer une copie d’un dépôt déjà hébergé :

```bash
git clone https://github.com/organisation/projet.git
```

### Vérifier, préparer et enregistrer

```bash
git status
git add README.md
git commit -m "Ajouter la présentation du projet"
```

- `git status` indique la branche courante et les fichiers modifiés, préparés ou non suivis.
- `git add README.md` prépare le fichier indiqué.
- `git add .` prépare tous les changements du dossier courant : vérifiez `git status` avant le commit pour éviter d’ajouter des fichiers indésirables.
- `git commit -m "..."` enregistre les changements préparés avec un message descriptif.

**Cycle de base :**

```text
Modifier → git status → git add → git status → git commit → git status
```

### Lire l’historique et comparer

```bash
git log --oneline
git diff
git diff --staged
```

- `git log --oneline` affiche l’historique sous une forme compacte.
- `git diff` montre les changements non encore préparés.
- `git diff --staged` montre les changements déjà préparés pour le prochain commit.

### Ignorer des fichiers avec `.gitignore`

Le fichier `.gitignore` indique à Git quels fichiers **non suivis** ignorer, par exemple des dépendances installées, des fichiers temporaires ou des secrets locaux.

Exemple :

```gitignore
node_modules/
.env
*.log
```

Ajoutez un fichier `.gitignore` à la racine du projet. Ignorer un fichier avec `.gitignore` ne retire pas automatiquement de l’historique un fichier que Git suit déjà.

> ⚠️ **Ne publiez jamais de mot de passe, clé API, jeton d’accès ou fichier contenant des secrets.** Ajoutez les fichiers sensibles à `.gitignore`, utilisez des variables d’environnement et révoquez immédiatement un secret publié par erreur. Le supprimer dans un commit ultérieur ne l’efface pas de l’historique.

### Annuler avec prudence

Ces commandes n’ont pas le même effet :

```bash
git restore fichier.txt
git restore --staged fichier.txt
```

- `git restore fichier.txt` abandonne les changements locaux non préparés de ce fichier.
- `git restore --staged fichier.txt` retire le fichier de la zone de préparation, mais conserve les changements dans le répertoire de travail.

**Attention :** la première commande peut supprimer des modifications locales. Vérifiez `git status` et `git diff` avant de l’utiliser.

`git reset` peut déplacer la référence de la branche et, selon les options, modifier la zone de préparation ou le répertoire de travail. C’est une notion avancée : ne l’utilisez pas pour effacer un commit partagé sans comprendre les conséquences.

### Écrire un bon message de commit

Préférez un message court qui décrit l’action et son objectif :

```text
Ajouter la section installation
Corriger le lien vers la documentation
Mettre à jour les consignes du TP
```

Évitez les messages vagues comme `modifs`, `test` ou `final`.

> **🖼️ IMAGE À AJOUTER — Lire un diff et le statut des fichiers**  
> Insérez une capture propre du terminal montrant un `git status` puis un petit `git diff` avec une ligne ajoutée en vert et une supprimée en rouge. Utilisez un dépôt d’exemple sans informations personnelles.

---

## 5 · Travailler avec des branches

### Qu’est-ce qu’une branche ?

Une **branche** est une ligne de travail indépendante, pratique pour développer une fonctionnalité ou corriger un bug sans perturber la branche principale.

La branche principale s’appelle généralement `main`. Une branche n’est pas une copie complète du projet à chaque étape : elle pointe vers un commit de l’historique.

### Créer, afficher et changer de branche

```bash
git branch
git branch nom-de-branche
git switch nom-de-branche
```

La commande suivante crée une branche et vous y place immédiatement :

```bash
git switch -c feature/page-accueil
```

Pour supprimer une branche locale déjà fusionnée :

```bash
git branch -d feature/page-accueil
```

Si Git refuse de la supprimer, vérifiez d’abord si son travail a bien été conservé. N’utilisez pas `-D` à la légère : cette option force la suppression.

### Comprendre `HEAD`

`HEAD` désigne l’endroit de l’historique où vous travaillez actuellement — généralement la branche et son commit courant. Après `git switch`, `HEAD` suit la branche choisie.

> **🖼️ IMAGE À AJOUTER — Une branche comme ligne de travail**  
> Créez un schéma d’historique simple : une ligne `main` et une branche `feature/page-accueil` qui part d’un commit commun, avance avec deux commits, puis rejoint `main`. Indiquez clairement `HEAD` sur la branche courante.

**Rituel conseillé :** vérifiez la branche avec `git branch` ou `git status` avant de commencer à modifier des fichiers.

---

## 6 · Fusionner des branches

### Pourquoi fusionner ?

Une fois une fonctionnalité terminée, on souhaite intégrer ses commits dans une autre branche, souvent `main`. Cette opération s’appelle un **merge**.

Exemple : revenir sur `main`, puis intégrer la branche de fonctionnalité :

```bash
git switch main
git merge feature/page-accueil
```

### Fast-forward et merge à trois voies

- **Fast-forward :** si `main` n’a pas avancé depuis la création de la branche, Git peut simplement déplacer son pointeur jusqu’au commit le plus récent.
- **Merge à trois voies :** si les deux branches ont avancé séparément, Git compare leur ancêtre commun et leurs deux versions pour créer une fusion.

### Résoudre un conflit

Un conflit arrive lorsque Git ne peut pas décider automatiquement comment combiner des changements — souvent lorsque deux branches ont modifié la même partie d’un fichier.

1. Lancez le merge et lisez le message de Git.
2. Exécutez `git status` pour repérer les fichiers en conflit.
3. Ouvrez chaque fichier et choisissez le contenu final. Les marqueurs ressemblent à ceci :

```text
<<<<<<< HEAD
Version de la branche courante
=======
Version de la branche fusionnée
>>>>>>> feature/ma-fonctionnalite
```

4. Supprimez les marqueurs et gardez le résultat voulu.
5. Préparez la résolution et terminez le merge :

```bash
git add fichier-en-conflit.txt
git commit
```

Lors d’un merge classique, Git fournit un message de commit par défaut ; vérifiez-le avant de l’enregistrer. Si vous devez interrompre un merge en cours, `git merge --abort` permet généralement de revenir à l’état précédant le merge. Vérifiez l’état du dépôt avant et après.

> **🖼️ IMAGE À AJOUTER — Comprendre un conflit**  
> Montrez un exemple annoté des marqueurs `<<<<<<<`, `=======` et `>>>>>>>`, avec une étape visuelle où ils sont remplacés par la version finale choisie. Ne présentez pas le conflit comme une erreur irréversible : c’est une décision à prendre.

**Conseil :** communiquez avec l’équipe et relisez le fichier complet avant de choisir une version.

---

## 7 · Découvrir GitHub

### Qu’est-ce qu’un dépôt GitHub ?

Un dépôt GitHub héberge un projet Git en ligne et ajoute des outils de collaboration. La page d’un dépôt peut présenter :

- **Code :** fichiers, branches et historique ;
- **README.md :** présentation et instructions du projet ;
- **Commits :** enregistrements successifs des changements ;
- **Releases :** versions publiées du projet ;
- **Issues :** tâches, questions ou bugs à suivre ;
- **Pull Requests :** propositions de modifications à examiner.

Vous pouvez créer un compte sur [github.com](https://github.com/). Pour créer un dépôt, choisissez **New repository**, indiquez son nom et sa visibilité, puis confirmez.

### Public ou privé ?

- **Public :** le dépôt est visible par tous. Utilisez ce mode pour partager un projet ouvert.
- **Privé :** le dépôt est accessible uniquement aux personnes autorisées.

Dans les deux cas, ne considérez pas un dépôt comme un coffre-fort : n’y mettez aucun secret.

> **🖼️ IMAGE À AJOUTER — Anatomie d’un dépôt GitHub**  
> Ajoutez une capture annotée de la page principale d’un dépôt de démonstration public : nom du dépôt, onglet Code, branche, historique et README. Évitez une capture de compte privé ou contenant des notifications personnelles.

---

## 8 · Connecter Git à GitHub

### Local et distant

Un dépôt distant est souvent nommé `origin` par convention. Après un clonage, Git configure normalement cette adresse automatiquement.

```bash
git remote -v
```

Pour associer un dépôt local existant à un dépôt GitHub :

```bash
git remote add origin https://github.com/organisation/projet.git
git remote -v
```

### Envoyer son travail : `push`

Pour publier votre branche locale sur GitHub et définir son lien de suivi lors du premier envoi :

```bash
git push -u origin main
```

Pour publier une branche de fonctionnalité :

```bash
git push -u origin feature/page-accueil
```

Après avoir défini le lien de suivi, `git push` suffit souvent à envoyer les prochains commits de cette branche.

### Récupérer le travail : `fetch` et `pull`

```bash
git fetch
git pull
```

- `git fetch` récupère les informations et commits distants, sans les intégrer automatiquement à votre branche courante.
- `git pull` récupère les changements puis tente de les intégrer à votre branche courante. Il peut donc provoquer un merge ou des conflits.

Avant de commencer une session en équipe, vérifiez votre branche et récupérez les changements appropriés. Ne lancez pas aveuglément `git pull` si vous avez des modifications locales non enregistrées : vérifiez d’abord `git status`.

### HTTPS et SSH

- **HTTPS :** connexion avec une URL HTTPS ; GitHub peut demander une authentification via son mécanisme de connexion ou un gestionnaire d’identifiants. Un mot de passe de compte GitHub n’est pas un mot de passe Git en ligne de commande.
- **SSH :** connexion avec une clé SSH configurée dans votre compte GitHub. Ne partagez jamais votre clé privée.

Les deux méthodes permettent d’échanger avec GitHub. Si vous débutez, utilisez la méthode et les consignes de connexion recommandées par votre organisation.

> **🖼️ IMAGE À AJOUTER — Le trajet local ↔ distant**  
> Créez un diagramme montrant deux ordinateurs qui échangent avec un dépôt distant GitHub : `push` vers GitHub, `fetch` depuis GitHub et `pull` pour récupérer puis intégrer. Distinguez bien le dépôt local du service en ligne.

---

## 9 · Collaborer sur un projet

### Fork ou clone ?

- **Clone :** crée une copie locale d’un dépôt auquel vous avez accès.
- **Fork :** crée une copie du dépôt sous votre propre compte GitHub. C’est utile lorsque vous n’avez pas le droit d’écrire dans le dépôt original.

Dans une équipe ayant accès au même dépôt, chaque personne peut cloner ce dépôt et publier sa branche. Dans un projet ouvert auquel vous ne contribuez pas directement, un fork est souvent utilisé.

### Le flux d’une Pull Request

Une **Pull Request (PR)** est une proposition de changements sur GitHub. Elle permet de discuter du code, de demander une revue et de vérifier les changements avant leur intégration.

1. Récupérer le projet avec `git clone` (ou créer un fork puis cloner son fork).
2. Créer une branche pour une tâche :

   ```bash
   git switch -c feature/ajouter-contact
   ```

3. Modifier les fichiers, puis vérifier et enregistrer les changements :

   ```bash
   git status
   git add .
   git commit -m "Ajouter la section contact"
   ```

4. Envoyer la branche sur GitHub :

   ```bash
   git push -u origin feature/ajouter-contact
   ```

5. Sur GitHub, ouvrir une Pull Request de cette branche vers `main`.
6. Expliquer le changement : quel problème est résolu, qu’est-ce qui a été fait, et comment le vérifier ?
7. Les collègues examinent la PR et laissent des commentaires constructifs.
8. Mettre à jour la branche si nécessaire, puis fusionner la PR après validation.
9. Synchroniser le travail local et supprimer les branches terminées si cela convient à l’équipe.

> **🖼️ IMAGE À AJOUTER — Pull Request et revue de code**  
> Insérez un schéma du parcours « branche de fonctionnalité → Pull Request → revue / commentaires → fusion dans `main` ». Vous pouvez compléter par une capture d’une PR de démonstration, sans noms de personnes ni notifications privées.

### Code Review : examiner avec bienveillance

Une revue de code sert à améliorer le projet ensemble. Posez des questions précises, expliquez pourquoi un changement pourrait poser problème et proposez une piste. Une PR claire, de taille raisonnable et accompagnée d’une description facilite la revue.

Les **Issues** servent à suivre des tâches ou des problèmes. Les **Discussions** permettent d’échanger des idées et des questions qui ne sont pas forcément des tâches à corriger.

---

## 10 · Bonnes pratiques et outils complémentaires

### Habitudes utiles

- Faites des commits **petits et cohérents** : un changement principal par commit.
- Écrivez un message compréhensible qui décrit le changement.
- Utilisez une branche par fonctionnalité ou correction.
- Vérifiez `git status` avant chaque commit et avant un push.
- En équipe, ne poussez pas directement sur `main`, sauf si les règles du projet le permettent explicitement.
- Récupérez les changements régulièrement et communiquez en cas de conflit.
- Maintenez un README avec l’objectif, l’installation et les instructions d’utilisation.
- Ne publiez jamais de mot de passe, clé API, jeton ou donnée privée.

### Outils GitHub à découvrir

- **GitHub Projects :** organiser le travail avec des tableaux, tâches et vues de suivi.
- **GitHub Actions :** automatiser des vérifications, tests ou déploiements, par exemple à chaque Pull Request. C’est une première approche de la CI/CD (intégration et déploiement continus).

### Checklist avant un push

- [ ] Je suis sur la bonne branche.
- [ ] `git status` ne montre pas de fichier sensible ou inutile.
- [ ] Mes changements sont enregistrés avec un message clair.
- [ ] J’ai vérifié la destination de mon push.
- [ ] Je n’ai inclus aucun secret ni donnée privée.

> **🖼️ IMAGE À AJOUTER — La checklist du développeur**  
> Ajoutez une illustration en forme de carte ou de tableau de bord, avec les étapes « vérifier la branche », « relire le diff », « commit clair », « aucun secret » et « push ».

---

## 🧪 Travaux pratiques

Prévoyez du temps pour pratiquer : la progression ci-dessous transforme les notions en gestes concrets.

| TP | Sujet | Commandes / notions | Objectif |
|---|---|---|---|
| 1 | Premier dépôt Git | `init`, `status`, `add`, `commit` | Créer un dépôt et enregistrer un premier fichier. |
| 2 | Historique Git | `log`, `diff`, `restore` | Lire les changements et annuler une modification locale avec prudence. |
| 3 | Branches | `branch`, `switch` | Créer une branche, y travailler et revenir sur `main`. |
| 4 | Merge | `merge` | Fusionner deux branches et résoudre un conflit simple. |
| 5 | GitHub | `clone`, `remote`, `push`, `pull` | Créer un dépôt distant et échanger des changements. |
| 6 | Collaboration | fork, branche, Pull Request, revue | Proposer un changement et commenter celui d’un camarade. |

### TP 1 — Premier dépôt

1. Créez un dossier de projet et ouvrez un terminal à cet endroit.
2. Lancez `git init`.
3. Créez un fichier `README.md` qui présente le projet.
4. Vérifiez les fichiers avec `git status`.
5. Préparez le README avec `git add README.md`.
6. Vérifiez à nouveau le statut puis créez un commit avec un message explicite.

### TP 2 — Lire et corriger l’historique

1. Modifiez le README sans préparer le changement.
2. Consultez `git status` et `git diff`.
3. Préparez le changement et consultez `git diff --staged`.
4. Enregistrez-le, puis consultez `git log --oneline`.
5. Dans un autre changement non préparé, testez `git restore` uniquement sur un contenu que vous pouvez abandonner.

### TP 3 — Créer une branche

1. Créez une branche `feature/presentation`.
2. Ajoutez une section au README et enregistrez-la sur cette branche.
3. Revenez sur `main` et observez ce qui est présent.
4. Comparez les branches avec `git log --oneline --all --graph`.

### TP 4 — Fusionner et résoudre un conflit

1. Créez une branche à partir de `main`.
2. Sur cette branche, modifiez une ligne du README et faites un commit.
3. Sur `main`, modifiez **la même ligne** différemment et faites aussi un commit.
4. Lancez `git merge nom-de-branche`.
5. Examinez le conflit, choisissez le texte final, retirez les marqueurs et terminez le merge.
6. Vérifiez le résultat avec `git status` et `git log --oneline --graph`.

### TP 5 — Publier sur GitHub

1. Créez un dépôt GitHub vide, sans secret.
2. Reliez le dépôt local avec `git remote add origin URL_DU_DEPOT`.
3. Vérifiez l’adresse avec `git remote -v`.
4. Publiez la branche principale avec `git push -u origin main`.
5. Vérifiez sur GitHub que le README et l’historique sont visibles.

### TP 6 — Première collaboration

En binôme, faites un fork si nécessaire, clonez le projet, créez chacun une branche avec une petite modification, poussez les branches puis ouvrez une Pull Request. Chaque personne examine la PR de l’autre avant la fusion.

> **🖼️ IMAGE À AJOUTER — Vue d’ensemble des TP**  
> Utilisez une frise ou un parcours illustré qui relie les six étapes : dépôt local, historique, branches, merge, GitHub, Pull Request. Gardez les intitulés courts pour que le visuel reste lisible.

---

## 🎓 Projet final — Un site pour votre club

### Mission

À plusieurs, développez un petit site de présentation du club : son activité, ses événements, ses membres ou ses moyens de contact. L’objectif principal est de pratiquer un flux de collaboration GitHub complet, pas de réaliser un site complexe.

### Déroulement

1. Une personne crée un dépôt GitHub et ajoute un README décrivant le projet.
2. Les autres membres clonent le projet (ou créent un fork si l’organisation le demande).
3. Chaque membre choisit une tâche et crée sa propre branche.
4. Chacun développe une fonctionnalité distincte — par exemple une section, une carte d’événement ou une page contact.
5. Chaque membre vérifie ses changements et crée un ou plusieurs commits clairs.
6. Chacun pousse sa branche sur GitHub et ouvre une Pull Request vers `main`.
7. Les autres participants relisent les PR et donnent des retours constructifs.
8. Les auteurs mettent à jour leur code si nécessaire.
9. Le responsable fusionne les Pull Requests validées dans `main`.
10. L’équipe récupère les changements finaux et vérifie que le projet est cohérent.

### Critères de réussite

- Le dépôt contient un README utile et aucun secret.
- Chaque personne a travaillé sur sa propre branche.
- Les commits sont compréhensibles.
- Les Pull Requests ont une description et ont été relues.
- Les changements finaux sont présents dans `main`.
- L’équipe sait expliquer où se trouvaient les changements à chaque étape.

> **🖼️ IMAGE À AJOUTER — Le projet collaboratif terminé**  
> Placez une maquette ou une capture d’un site fictif de club étudiant : page d’accueil, événements et contact. Utilisez des données inventées et des images libres de droits ou créées par votre équipe.

---

## ⏱️ Organisation recommandée du cours

| Partie | Durée |
|---|---:|
| Introduction et concepts | 20 min |
| Installation et configuration | 15 min |
| Architecture et fonctionnement de Git | 25 min |
| Commandes fondamentales | 35 min |
| Branches et merge | 35 min |
| Introduction à GitHub | 20 min |
| Collaboration et Pull Requests | 30 min |
| TP final | 45 min |
| **Total** | **3 h 45** |

> **🖼️ IMAGE À AJOUTER — Programme en un coup d’œil**  
> Créez un planning visuel sur une ligne du temps ou en huit étapes. Faites ressortir la pratique et le TP final ; indiquez le total de 3 h 45.

---

## 🧠 Fiche mémo

| Besoin | Commande |
|---|---|
| Vérifier la version de Git | `git --version` |
| Créer un dépôt | `git init` |
| Voir l’état du dépôt | `git status` |
| Préparer un fichier | `git add fichier` |
| Enregistrer un commit | `git commit -m "Message clair"` |
| Lire l’historique | `git log --oneline` |
| Voir les changements non préparés | `git diff` |
| Lister les branches | `git branch` |
| Changer de branche | `git switch nom-branche` |
| Créer et rejoindre une branche | `git switch -c nom-branche` |
| Fusionner une branche | `git merge nom-branche` |
| Voir les dépôts distants | `git remote -v` |
| Envoyer une branche | `git push -u origin nom-branche` |
| Récupérer puis intégrer | `git pull` |
| Récupérer sans intégrer automatiquement | `git fetch` |

---

## ✅ Le message à retenir

> **Git conserve l’historique de votre travail. GitHub aide votre équipe à le partager, le discuter et le construire ensemble.**

**Votre premier réflexe à chaque étape :** `git status`. 🌱
