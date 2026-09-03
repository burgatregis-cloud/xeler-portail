# Portail Xeler — guide

Page d'accueil unique pour toute l'équipe : elle rassemble tous les outils
de chiffrage (et les futurs) derrière une seule adresse, facile à retrouver
sur téléphone.

## 1. Le portail est en ligne

Dépôt GitHub : `burgatregis-cloud/xeler-portail`, publié via GitHub Pages
(Settings → Pages → branche `main`, dossier `/root`).

Adresse officielle à partager avec l'équipe : **https://portail.xeler.com/**
— un sous-domaine de `xeler.com` (enregistrement CNAME ajouté dans la zone
DNS chez Online.net/Scaleway, pointant vers
`burgatregis-cloud.github.io.`). L'ancienne adresse
`https://burgatregis-cloud.github.io/xeler-portail/` continue de
fonctionner en parallèle.

C'est vers `https://portail.xeler.com/` que pointe déjà le bouton
"🏠 Portail" ajouté dans les deux outils de chiffrage (robots et
copieurs).

Pour mettre à jour le portail : modifier les fichiers dans ce dossier,
committer et pousser sur la branche `main` — GitHub Pages redéploie
automatiquement en moins d'une minute.

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
- **`fournisseurs`** / **`constructeurs`** : chips cliquables vers le site
  de chaque partenaire (ouverture dans un nouvel onglet) — ajouter/retirer
  une entrée `{ label, color, url }`. Couleurs disponibles : `blue`,
  `teal`, `purple`, `cyan`, `pink`, `green`, `salmon`, `orange`, `indigo`,
  `amber`.
- **`liensUtiles`** : CRM / Drive équipe / Grille tarifaire sont prévus
  mais **sans URL pour l'instant** (`url: ""`) — le chip reste affiché en
  pointillés avec la mention "à renseigner". Dès que vous renseignez
  l'adresse réelle dans `url`, le lien devient actif automatiquement.
- **`accessCode`** / **`requireCode`** : le code d'accès de la page
  d'entrée (`180640` par défaut, comme convenu). **Attention : ce n'est
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
