# ChosMarket (Shop-Arma3‑RP)

Bienvenue dans **ChosMarket**, un mini‑site _responsive_ conçu pour les serveurs roleplay Arma 3 🎮. Il permet de présenter un **catalogue de produits** (bandages, pizzas, pièces automobiles, etc.) à vos clients en jeu, comme dans un vrai commerce. Le code ne nécessite pas de base de données : tout est 100 % statique (HTML/CSS/JavaScript). Les données modifiables sont centralisées dans un fichier JSON afin de faciliter la personnalisation sans compétences techniques.

## ✨ Fonctionnalités

- **Catalogue dynamique** : les produits sont chargés depuis `data.json`. Chaque article possède un nom, un prix, une catégorie, des étiquettes et une image associée.
- **Filtres par catégorie** : un système de filtres permet d’afficher uniquement les articles de la catégorie sélectionnée (Alimentation, Divers, Auto…).
- **Thème personnalisable** : couleurs principales/accent et police modifiables via `data.json` pour s’adapter à votre univers RP.
- **En‑tête configurable** : logo, titre du magasin, numéro de téléphone et fréquence radio peuvent être ajustés.
- **Mode ouverture/fermeture** : la clé `is_open` dans `data.json` permet d’afficher ou de masquer le catalogue selon vos heures d’ouverture.

## 🧰 Comment installer et mettre en ligne (méthode simple)

1. **Créer un compte GitHub** (gratuit) si vous n’en avez pas déjà un. Rendez‑vous sur [github.com](https://github.com) et cliquez sur _Sign up_.
2. **Forker le dépôt** :
   - Allez sur la page du dépôt d’origine : [YoumitCall/Shop‑Arma3‑RP](https://github.com/YoumitCall/Shop-Arma3-RP).
   - Cliquez sur le bouton **“Fork”** en haut à droite. Cela crée une copie du projet dans votre compte.
3. **Activer GitHub Pages** :
   - Dans votre dépôt forké, ouvrez l’onglet **“Settings”** puis la section **“Pages”**.
   - Sous **“Source”**, choisissez la branche `main` et le dossier racine (`/`). Enregistrez. Après quelques secondes, GitHub générera une URL publique du type `https://votrecompte.github.io/Shop-Arma3-RP/` où votre boutique sera accessible.
4. **Personnaliser votre boutique** (voir ci‑dessous), puis valider les modifications en cliquant sur **“Commit changes”** depuis l’interface Web GitHub. GitHub Pages se mettra à jour automatiquement.

💡 *Astuce : vous pouvez changer le nom du dépôt forké en `votrenom.github.io` pour publier votre boutique directement à la racine de votre domaine GitHub Pages.*

## 🖌️ Personnalisation des données

Toutes les variables modifiables sont regroupées dans le fichier [`data.json`](./data.json). Vous pouvez l’éditer directement depuis GitHub en cliquant dessus puis sur l’icône ✏️. Voici les champs principaux :

### Paramètres généraux (`settings`)

| Clé                 | Rôle                                                                              |
|---------------------|------------------------------------------------------------------------------------|
| `logo_url`          | Chemin de l’image du logo (dans le dossier `images/`).                             |
| `shop_title`        | Titre affiché dans la barre supérieure du site (nom de votre magasin).             |
| `phone`             | Numéro de téléphone fictif à afficher sous forme de « pilule » dans l’en‑tête.     |
| `radio`             | Fréquence radio pour communiquer avec vos clients RP.                              |
| `announcement`      | Slogan ou message d’accueil dans la section héro (majuscule automatiquement).      |
| `theme_primary`     | Couleur de fond principale du thème (hexadécimal, ex. `#111827`).                  |
| `theme_accent`      | Couleur d’accent utilisée pour les boutons et filtres (hexadécimal).               |
| `font_family`       | Police de caractères utilisée sur tout le site.                                    |

### Liste des produits (`products`)

Chaque produit est un objet JSON avec les champs suivants :

| Champ       | Description                                                                                            |
|-------------|--------------------------------------------------------------------------------------------------------|
| `id`        | Identifiant unique (non affiché).                                                                     |
| `title`     | Nom du produit.                                                                                       |
| `price`     | Prix du produit (en unités de votre choix, par exemple en € ou en dollars Arma).                       |
| `currency`  | Symbole de la monnaie (`EUR`, `USD`, etc.).                                                            |
| `category`  | Catégorie (ex. « Alimentation », « Divers », « Auto »). Cette valeur alimente les filtres automatiques. |
| `tags`      | Mots‑clés internes (non affichés) pour trier ou rechercher plus facilement.                            |
| `image`     | Chemin vers l’image correspondante dans `images/`.                                                     |
| `in_stock`  | `true` si l’article est disponible, `false` pour afficher « Indisponible ».                             |
| `order`     | Ordre d’affichage au sein de la catégorie (plus petit = affiché en premier).                           |
| `description` | Courte description affichée sous le titre et le prix.                                               |

Pour **ajouter un produit** :
1. Importez votre image dans le dossier `images/` (depuis GitHub, cliquez sur **“Add file”** → **“Upload files”**).
2. Ajoutez un nouvel objet dans le tableau `products` de `data.json` en respectant le modèle ci‑dessus. N’oubliez pas de mettre le bon `image` (chemin relatif).

Pour **modifier un produit existant** (nom, prix, description, stock, etc.), modifiez directement les propriétés correspondantes et enregistrez.

## 🚀 Astuces de déploiement

- **Actualisation des données :** le fichier `index.html` récupère les données via `fetch('./data.json')` ; un rafraîchissement de la page suffit pour voir les changements.
- **Couleurs et thème :** les variables CSS se basent sur `theme_primary` et `theme_accent`. Utilisez des couleurs compatibles avec votre univers RP pour plus d’immersion.
- **Mode hors ligne :** en cas de problème de chargement du JSON, un jeu de données minimal est prévu comme secours dans `index.html` (FALLBACK_DATA).

## 🧑‍💻 Pour les utilisateurs plus avancés

Le site n’utilise ni framework ni backend. Tout se trouve dans trois fichiers : `index.html`, `data.json` et le dossier `images/`. Vous pouvez :

- Modifier `index.html` pour ajuster la structure, les classes CSS ou ajouter des effets visuels.
- Adapter le design en ajoutant vos propres styles dans la balise `<style>`.
- Utiliser votre propre hébergement si vous ne souhaitez pas passer par GitHub Pages (il suffit de servir les fichiers statiques via un serveur HTTP).

## ✅ Exemple de workflow complet (utilisateur non technique)

1. Je crée un compte GitHub et je me connecte.
2. Je clique sur **“Fork”** sur la page du dépôt original.
3. J’active **GitHub Pages** via les paramètres afin d’obtenir l’URL de ma boutique.
4. Je clique sur `data.json`, puis sur le crayon ✏️ pour éditer les informations : je remplace le `shop_title`, j’ajoute mon numéro de téléphone RP et j’insère de nouveaux produits en copiant le modèle fourni.
5. Je valide les modifications en cliquant sur **“Commit changes”**. Mon site se met à jour en moins de deux minutes.
6. Je partage l’URL avec mes amis en jeu 🎉.

## 🤝 Contribution et droits d’auteur

Ce projet est open‑source et peut être adapté librement pour vos besoins personnels en jeu. Merci de laisser une mention au projet original si vous le partagez publiquement. Vous pouvez contribuer en proposant des améliorations via des _pull requests_ ou en signalant des problèmes via l’onglet **Issues**.

Bon roleplay et bonnes ventes ! 🛒
