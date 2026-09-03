# Portail Xeler — guide

Page d'accueil unique pour toute l'équipe : elle rassemble tous les outils
de chiffrage (et les futurs) derrière une seule adresse, facile à retrouver
sur téléphone.

## 1. Mettre le portail en ligne sur GitHub

1. Aller sur **https://github.com/new**
2. Nom du dépôt : `xeler-portail` (compte `burgatregis-cloud`, comme pour
   les deux autres outils)
3. Laisser "Public" (nécessaire pour GitHub Pages gratuit), ne rien cocher
   d'autre, cliquer "Create repository"
4. Sur la page du dépôt vide, cliquer **"uploading an existing file"**,
   glisser-déposer tout le contenu de ce dossier (`index.html`,
   `manifest.json`, les dossiers `assets/` et `icons/`), puis
   **"Commit changes"**
5. **Settings → Pages** → Source : **"Deploy from a branch"**, branche
   **main**, dossier **/ (root)**, **Save**
6. Après 1 à 2 minutes, l'adresse apparaît en haut de cette page :
   `https://burgatregis-cloud.github.io/xeler-portail/`

C'est cette adresse qu'il faut partager avec l'équipe, et c'est vers elle
que pointe déjà le bouton "← Portail" ajouté dans les deux outils de
chiffrage (robots et copieurs).

*(Si vous préférez un autre nom de dépôt, remplacez `xeler-portail` par ce
nom dans les deux fichiers `index.html` des outils de chiffrage, à
l'endroit indiqué par le commentaire `PORTAIL_URL`.)*

## 2. Installer le portail comme application

- **iPhone** : ouvrir l'adresse dans Safari → icône Partager → "Sur l'écran
  d'accueil"
- **Android** : ouvrir l'adresse dans Chrome → menu ⋮ → "Ajouter à l'écran
  d'accueil" / "Installer l'application"
- **PC** : icône d'installation dans la barre d'adresse de Chrome/Edge, ou
  menu ⋮ → "Installer Portail Xeler"

## 3. Tout se règle en haut du fichier `index.html`

Le bloc `<script id="portal-config">` en haut du fichier (juste après
`<body>`) contient tout ce qui est amené à changer — aucune autre partie du
fichier n'a besoin d'être touchée :

- **`tools`** : les 4 cartes "Chiffrage & devis". Pour brancher un nouvel
  outil (ex. abonnements informatique) dès qu'il existe, il suffit de
  passer son `status` de `"soon"` à `"live"` et de renseigner son `url`.
  Pour ajouter un 5ᵉ outil plus tard, copier un des objets du tableau.
- **`fournisseurs`** / **`constructeurs`** : simples badges d'information
  (pas des liens) — ajouter/retirer une entrée `{ label, color }`. Couleurs
  disponibles : `blue`, `teal`, `purple`, `cyan`, `pink`, `green`,
  `salmon`, `orange`, `indigo`, `amber`.
- **`liensUtiles`** : CRM / Drive équipe / Grille tarifaire sont prévus
  mais **sans URL pour l'instant** (`url: ""`) — le chip reste affiché en
  pointillés avec la mention "à renseigner". Dès que vous renseignez
  l'adresse réelle dans `url`, le lien devient actif automatiquement.
- **`accessCode`** / **`requireCode`** : le code d'accès de la page
  d'entrée (`080425` par défaut, comme convenu). **Attention : ce n'est
  pas une vraie sécurité** — le code est visible en clair dans le code
  source de la page, il ne fait que décourager les visites non désirées.
  Passer `requireCode` à `false` pour supprimer complètement la page
  d'entrée.

Le bouton **"🔒 Verrouiller"** en haut à droite du portail efface l'accès
mémorisé sur l'appareil (utile sur un poste partagé) ; sinon, une fois le
code entré une première fois, l'appareil reste "déverrouillé"
indéfiniment (mémorisé dans le navigateur).

## 4. Images utilisées

`assets/xeler-groupe.png` (logo), `assets/robot-keenon.jpg` et
`assets/copieur-ricoh.jpg` (fonds des deux cartes "en ligne") — toutes
redimensionnées et compressées pour un chargement rapide sur mobile.
