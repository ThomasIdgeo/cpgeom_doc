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
> [!WARNING]
> CHoisir l'utilisateur **idgeo** et le mdp **idgeo**

### 3. Installer git

```bash
sudo apt install git
```

## Git local et github

- Il s'agit d'initier notre répertoire local comme un repository au sens git du terme. Notre répertoire local devient un repository "local".  
- Ensuite, on crée notre repository sur la plateforme github. On parle ici de repository distant.  
- Dans un troisième temps, on associe les deux répertoires.