# Gestion des Demandes de Changement/Annulation de Séances

## 📝 Description du Projet

Ce projet est une application web complète et sécurisée, développée en **PHP/MySQL**, conçue pour la gestion du flux de travail (workflow) des demandes de modification ou d'annulation de séances de cours au sein d'un établissement d'enseignement supérieur (tel que l'Université Euromed de Fès, UEMF).

L'application implémente un système de validation multi-niveaux (Professeur, Assistante, Directeur) garantissant la traçabilité, la cohérence des plannings et la sécurité des données.

## ✨ Fonctionnalités Clés

Le système est structuré autour de trois rôles utilisateurs distincts, chacun avec des permissions et des tableaux de bord personnalisés.

### 👨‍🏫 Rôle Professeur

*   **Création de Demandes**: Soumission de demandes de modification ou d'annulation de séances avec justification obligatoire.
*   **Pièces Jointes**: Possibilité d'uploader des documents justificatifs (PDF, images).
*   **Suivi**: Affichage clair du statut de toutes les demandes soumises.
*   **Interaction**: Acceptation ou refus des dates alternatives proposées par l'Assistante.
*   **Gestion**: Suppression des demandes tant qu'elles sont en attente de traitement.

### 👩‍💼 Rôle Assistante

*   **Vue Globale**: Accès à toutes les demandes soumises par les professeurs.
*   **Validation Initiale**: Validation ou refus des demandes avec ajout de commentaires.
*   **Proposition d'Alternatives**: Formulaire dédié pour proposer une nouvelle date, heure et salle en cas de conflit, avec vérification automatique de la disponibilité.
*   **Rapports**: Génération de rapports et statistiques détaillés au format Excel (filtrage par période, statistiques par professeur, utilisation des salles).

### 👨‍💼 Rôle Directeur

*   **Validation Finale**: Approbation finale des demandes déjà validées par l'Assistante.
*   **Gestion des Utilisateurs**: Administration complète des comptes (modification, suppression, désactivation/réactivation temporaire).
*   **Statistiques Avancées**: Exportation de statistiques globales et détaillées.
*   **Audit**: Consultation des logs d'activité pour la traçabilité des actions sensibles.

### 🌐 Fonctionnalités Communes

*   **Tableau de Bord**: Interface personnalisée en fonction du rôle.
*   **Notifications**: Système de notifications en temps réel avec badge de non-lus.
*   **Calendrier**: Vue mensuelle des séances avec code couleur et affichage des disponibilités.
*   **Profil**: Modification sécurisée des informations personnelles (email, téléphone, mot de passe) avec vérification.

## 🛡️ Sécurité et Robustesse

L'application a été développée en mettant l'accent sur la sécurité, intégrant les meilleures pratiques pour une application PHP moderne :

*   **Protection CSRF**: Utilisation de tokens CSRF sur **tous** les formulaires.
*   **Prévention XSS/SQLi**: Utilisation de requêtes préparées (PDO) et échappement HTML (`htmlspecialchars`) systématique des entrées utilisateur.
*   **Authentification Sécurisée**: Hachage des mots de passe, limitation des tentatives de connexion (brute-force protection), gestion du "Se souvenir de moi" par tokens sécurisés.
*   **Gestion des Sessions**: Session timeout après 30 minutes d'inactivité.
*   **Upload Sécurisé**: Validation stricte des fichiers uploadés (taille, extension, vérification MIME).

## 💻 Technologies Utilisées

| Catégorie | Technologie | Détails |
| :--- | :--- | :--- |
| **Backend** | PHP | Langage de programmation principal. |
| **Base de Données** | MySQL | Système de gestion de base de données relationnelle. |
| **Communication** | PHPMailer | Utilisé pour l'envoi d'emails de notification. |
| **Frontend** | HTML5, CSS3, JavaScript | Structure et interactivité de base. |
| **Dépendances** | Radix UI, Next.js/React (via `package.json`) | Indication d'une utilisation potentielle de composants modernes pour l'interface utilisateur. |

## ⚙️ Installation et Configuration

### Prérequis

*   Serveur Web (Apache ou Nginx)
*   PHP 7.4+ (avec extensions PDO et MySQLi)
*   MySQL / MariaDB

### Étapes d'Installation

1.  **Cloner le dépôt**
    ```bash
    git clone [URL_DU_DEPOT] gestion_seances
    cd gestion_seances/workflowapplication18
    ```

2.  **Configuration de la Base de Données**
    *   Créez une base de données nommée `gestion_seances`.
    *   Importez le schéma et les données de test :
        ```bash
        mysql -u [VOTRE_UTILISATEUR] -p gestion_seances < database.sql
        ```

3.  **Configuration de l'Application**
    *   Ouvrez le fichier `config.php`.
    *   Mettez à jour les informations de connexion à la base de données si nécessaire (par défaut : `DB_USER: root`, `DB_PASS: ''`).
        ```php
        // config.php
        define('DB_HOST', 'localhost');
        define('DB_NAME', 'gestion_seances');
        define('DB_USER', 'root'); // À modifier
        define('DB_PASS', ''); // À modifier
        ```

4.  **Accès à l'Application**
    *   Déployez le dossier `workflowapplication18` sur votre serveur web.
    *   Accédez à l'application via votre navigateur (ex: `http://localhost/gestion_seances/workflowapplication18/`).

### Identifiants de Test

Les identifiants de test pour chaque rôle sont disponibles dans le fichier `IDENTIFIANTS_TEST.txt` (non inclus dans ce README mais présent dans le projet original).

## 🤝 Contribution

Les contributions sont les bienvenues. Veuillez soumettre une *pull request* ou ouvrir une *issue* pour toute suggestion ou rapport de bug.

## 📄 Licence

Ce projet est sous licence [Insérer le nom de la licence, ex: MIT].
