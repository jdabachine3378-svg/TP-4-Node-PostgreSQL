# TP-4-Node.-Express-EJS-et-PostgreSQL

Application web full-stack pour la gestion d'une bibliothèque, développée avec Node.js, Express, EJS et PostgreSQL.

## Fonctionnalités

- **Gestion des auteurs** : Création, lecture, mise à jour et suppression (CRUD)
- **Gestion des livres** : CRUD complet avec recherche
- **Relation auteurs-livres** : Affichage des livres par auteur et des détails d'auteur par livre
- **Interface moderne** : Design responsive avec EJS

## Prérequis

- Node.js (v14 ou supérieur)
- PostgreSQL (v12 ou supérieur)
- npm ou yarn

## Installation

1. Installer les dépendances :
```bash
npm install
```

2. Configurer la base de données :
   - Créer une base de données PostgreSQL nommée `bibliotheque_db`
   - Modifier le fichier `.env` avec vos identifiants PostgreSQL

3. Créer les tables et insérer les données de test :

## Configuration

Le fichier `.env` doit contenir :
```
DB_USER=utilisateur
DB_PASSWORD=mot_de_passe
DB_HOST=localhost
DB_PORT=5432
DB_DATABASE=bibliotheque_db
PORT=3000
```

## Lancement

### Mode développement
```bash
npm run dev
```

### Mode production
```bash
npm start
```

L'application sera accessible sur http://localhost:3000
<img width="1755" height="840" alt="image" src="https://github.com/user-attachments/assets/049fd04f-c3cc-41f0-afe6-3cfada52dc47" />


## Structure du projet

```
bibliotheque-app/
├── config/
│   └── db.js              # Configuration de la base de données
├── controllers/
│   ├── auteurController.js
│   └── livreController.js
├── models/
│   ├── auteurModel.js
│   └── livreModel.js
├── routes/
│   ├── auteurRoutes.js
│   └── livreRoutes.js
├── views/
│   ├── partials/          # Partials EJS (header, navigation, footer)
│   └── pages/             # Pages principales
│       ├── auteurs/       # Pages CRUD auteurs
│       └── livres/        # Pages CRUD livres
├── public/
│   ├── css/
│   │   └── style.css
│   └── js/
│       └── main.js
├── app.js                 # Point d'entrée
├── package.json
└── .env                   # Variables d'environnement
```

## Pages disponibles

- `/` : Page d'accueil
- `/auteurs` : Liste des auteurs
- `/auteurs/ajouter` : Ajouter un auteur
- `/auteurs/:id` : Détails d'un auteur
- `/auteurs/:id/modifier` : Modifier un auteur
- `/livres` : Liste des livres
- `/livres/ajouter` : Ajouter un livre
- `/livres/recherche` : Rechercher un livre
- `/livres/:id` : Détails d'un livre
- `/livres/:id/modifier` : Modifier un livre

## Technologies utilisées

- **Node.js** : Runtime JavaScript
- **Express** : Framework web
- **EJS** : Moteur de template
- **PostgreSQL** : Base de données relationnelle
- **pg (node-postgres)** : Client PostgreSQL pour Node.js
- **dotenv** : Gestion des variables d'environnement
- **nodemon** : Outil de développement pour rechargement automatique

## Auteur :
DABACHINE JAMILA 
