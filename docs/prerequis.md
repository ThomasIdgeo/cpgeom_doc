# Mon repo de doc

Objectif : 

- décourvrir l'environnement github
- appréhender le versionnement avec git
- générer un site github pages

## Prérequis

### 1. Arborescence (locale)
  - un répertoire *cpgeom_doc*
    - ce fichier readme.md
    - un dossier **docs/**
      - un fichier index.md
      - tous les fichiers Markdown nécessaires (qui seront autant de pages de mon site)  

### 2. Activer / Installer WSL sur son PC (Windows 11)
  ```bash
  wsl --install
  ```
  - Voir les listes des distributions disponibles
  ```bash
  wsl --list --online
  ```
  - Installer une distribution. Conseillée Debian ou Ubuntu
  ```bash
  wsl --install -d Debian
  ```
  - Redémarrer l'ordinateur
  - Ouvrir Terminal Debain ou Ubuntu

**Il faut peut-être redémarrer plusieurs fois le PC pour que la mise à jour soit effective.**  
Si la commande précédente n'a pas installé Ubuntu, il faut passer par le Windows Store pour *Obtenir* Ubuntu.  
Un nouveau redémarrage et votre console ubuntu doit être fonctionnelle.

> [!WARNING]
> Choisir l'utilisateur **idgeo** et le mdp **idgeo**

### 3. Installer git

```bash
sudo apt install git
```

## Git local et Repo distant sur Github

### Association ou création de la passerelle entre un repo local et un repo distant

- Il s'agit d'initier notre répertoire local comme un repository au sens git du terme. Notre répertoire local devient un repository "local".  
`git init`
- Ensuite, on crée notre repository sur la plateforme github. On parle ici de repository distant.  

- Dans un troisième temps, on associe les deux répertoires.
  `git add remote -u origin https://url-de-votre-repo-nouvellement-creer.html`

### Mécanisme de publication des mises à jour

- je mets à jour mon repo local pour le pousser vers le distant
  - j'aoute les fichiers modifiés ou ajoutés avec `git add *`
  - je commit avec un message `git commit -m "modif ..."`
  - je "push" avec git push `git push`

- la publication d'un site github pages s'effectue dans les paramètres du repo sur github. 
  - le plus simple est de désigner un sous dossier du repo, ici "docs" que nous avons judicieusement choisi de créer dans l'arborescence.
  - Pour générer un site plus *moderne*, on va utiliser des utilitaires python avec la lobrairie mkdocs et des templates comme Read The Docs.

### Pré-requis pour générer un site Mkdocs

#### Les outils à installer

En local, il faut utiliser python et pip pour installer et utiliser Mkdocs.  
Depuis le terminal Ubuntu (installé à l'étape ci-dessus) : 

- installer python3 

```bash
sudo apt install python3
```

- installer le gestionnaire de paquet python **pip** et le gestionnaire d'environnement virtuel **python-venv**

```bash
 sudo apt install python3-venv &&
 sudo apt install python3-pip
```

#### Création de l'environnement virtuel

**A faire la première fois depuis le répertoire local (celui correspondant au repo local git)**
- Générer l'envionnement virtuel : ça va permettre d'installer mkodcs dans cet environnement et de na pas avoir d'impact sur notre système, c'est à dire que les outils Mkdocs ne fonctionneront que dans cet environnement virtuel et pas en dehors.
```bash
sudo python3 -m venv .venv
```
=> Le dossier **.venv** est généré

**A reproduire à chaque fois que vous souhaiterez mettre à jour votre site en ajoutant une nouvelle page par exemple.**  
 - On active l'envionnement virtuel avec la commande :  
  ```bash
  source .venv/bin/activate
  ```
=> On obtient le "message" **(.venv)** qui précéde user@nom_pc:/path/vers/repo_local/$, soit  

```bash
(.venv)user@nom_pc:/path/vers/repo_local/$
```

> [!IMPORTANT]
> Notre contexte virtuel python est fonctionnel !

#### Installation de mkdocs

```python
pip install mkdocs
```

### Utilisation de Mkdocs

- Se positionner dans le repo local et activer l'environnement virtuel python (cf ci-dessus)

- Pour générer un site en localhost (avant de le mettre sur le repo github)  
```bash
mkdocs serve
```
Le site local est accessible [http://127.0.0.1:8000](http://127.0.0.1:8000)

- La commande gh-deploy permet de générer la branche gh-pages qui sera utilisée pour générer notre site Mkdocs sur le Github Pages.

```bash
mkdocs gh-deploy
```

**Le site est accessible avec l'url github.**

- Dans votre repo Github, se rendre dans **Settings** puis dans l'onglet **Pages** et définir la branche **gh-pages** et le dossier racine **/root**.  
Le site est accessible à l'url [thomasidgeo.github.io/cpgeom_doc/](
thomasidgeo.github.io/cpgeom_doc/), soit votre_nom.github.io/nom_repo/