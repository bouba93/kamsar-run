# Kamsar Run

Jeu de course sans fin de **Randonnée Kamsar** (chaque samedi à 7h, Kamsar, Guinée).

Le randonneur saute la vase, les troncs, les rochers et les motos-taxis, ramasse étoiles et gourdes, et traverse pistes de latérite, rizières, fleuve, mangrove et coucher de soleil.

- Touche l'écran (ou Espace / Flèche haut) pour sauter, maintiens pour sauter plus haut, retouche en l'air pour un double saut.
- Site statique : `index.html` + `logo.jpg`, aucune dépendance.

## Application installable (PWA)
- `manifest.webmanifest` + icônes : « Installer l'appli » sur Android (bouton dans le jeu), « Partager → Sur l'écran d'accueil » sur iPhone.
- `sw.js` : le jeu reste jouable hors connexion après la première visite.

## Mode 2 joueurs
Écran partagé sur le même téléphone : le joueur 1 touche la moitié du bas (clavier : Espace), le joueur 2 la moitié du haut (clavier : Flèche haut). Les deux pistes ont exactement les mêmes obstacles.

## Noms et protection des données
- Chaque joueur enregistre son nom (2 à 16 caractères). Le classement « Meilleurs scores sur ce téléphone » affiche les 5 meilleurs.
- Noms et scores sont chiffrés en **AES-GCM 256 bits** (Web Crypto) avant d'être écrits dans le navigateur. La clé est générée sur l'appareil, non extractible, et gardée dans IndexedDB. Toute modification des données est détectée et rejetée.
- Aucune donnée n'est envoyée sur internet. Bouton « Effacer mes données » sur l'écran d'accueil.
- `vercel.json` ajoute des en-têtes de sécurité (CSP stricte, HSTS, anti-iframe, nosniff, Permissions-Policy).
