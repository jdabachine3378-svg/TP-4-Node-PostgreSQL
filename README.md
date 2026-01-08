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
```sql
CREATE DATABASE bibliotheque_db;
\c bibliotheque_db

CREATE TABLE auteurs (
    id SERIAL PRIMARY KEY,
    nom VARCHAR(100) NOT NULL,
    prenom VARCHAR(100) NOT NULL,
    date_naissance DATE,
    nationalite VARCHAR(50),
    biographie TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE livres (
    id SERIAL PRIMARY KEY,
    titre VARCHAR(200) NOT NULL,
    auteur_id INTEGER REFERENCES auteurs (id) ON DELETE CASCADE,
    annee_publication INTEGER,
    genre VARCHAR(50),
    isbn VARCHAR(20) UNIQUE,
    resume TEXT,
    disponible BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

INSERT INTO auteurs (nom, prenom, date_naissance, nationalite, biographie) VALUES
('Hugo', 'Victor', '1802-02-26', 'Française', 'Poète et romancier.'),
('Camus', 'Albert', '1913-11-07', 'Française', 'Philosophe et écrivain.'),
('Rowling', 'J.K.', '1965-07-31', 'Britannique', 'Auteure de Harry Potter.');

INSERT INTO livres (titre, auteur_id, annee_publication, genre, isbn, resume, disponible) VALUES
('Les Misérables', 1, 1862, 'Historique', '9782253096344', 'Jean Valjean...', true),
('L''Étranger', 2, 1942, 'Philosophique', '9782070360024', 'Meursault...', true),
('Harry Potter à l''école des sorciers', 3, 1997, 'Fantasy', '9782070643028', 'Aventure...', true);
```

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

## Notes

Cette application démontre l'utilisation d'Express, de `pg.Pool` et d'EJS, ainsi que la gestion d'une relation « un-à-plusieurs » entre deux tables PostgreSQL.
