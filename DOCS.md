# Documentation technique
Un genre de uberaeat mais avec des franchisées

## Les critères du projet (Poid maximal : 11):
- Performance, Poid : 7
- Scalabilité, Poid : 11
- Sécurité/Conformité, Poid : 3
- Accesibilité/UI/UX, Poid : 4
- Innovation, Poid : 5
- Maintenabilité, Poid : 8
- Disponibilité, Poid : 9

## Architecture 
Décision Architecture : Micro-service
Décision Back-end : Spring boot
Décision Front-end pour web : React
Décision Front-end pour app mobile : React Native

## Découpage en service
Api gateway (avec bastion) → Routeur gigantesque
ClientConnect  → Authentification des clients
RestoConnect → Authentification des restaurateurs
LivreurConnect → Authentification des livreurs
Commande service → Gestion des commandes
Resto Service → Gestion des restaurants (stock, menu, etc)
Livreur Service  → Gestion de la localisation des livreurs 

## Solutions
site web
appli mobile 
appli livreur 

## Dictionnaire de données
### site web
Pour le site web de Good Food, voici un dictionnaire de données simplifié basé sur les informations fournies et les fonctionnalités attendues :

## Dictionnaire de données - Site Web

### Utilisateur
- ID_Utilisateur (Clé primaire)
- Nom
- Prénom
- Email
- Mot_de_passe (haché)
- Adresse
- Téléphone
- Date_inscription
- Statut (actif, inactif)

### Restaurant
- ID_Restaurant (Clé primaire)
- Nom_restaurant
- Adresse
- Téléphone
- Horaires_ouverture
- Type_cuisine
- Statut (ouvert, fermé, en pause)

### Menu
- ID_Menu (Clé primaire)
- ID_Restaurant (Clé étrangère)
- Nom_menu
- Description
- Prix
- Disponibilité (oui/non)

### Plat
- ID_Plat (Clé primaire)
- ID_Menu (Clé étrangère)
- Nom_plat
- Description
- Prix
- Allergènes
- Image_URL

### Commande
- ID_Commande (Clé primaire)
- ID_Utilisateur (Clé étrangère)
- ID_Restaurant (Clé étrangère)
- Date_commande
- Statut_commande (en attente, préparation, en livraison, livrée)
- Montant_total
- Mode_paiement
- Adresse_livraison
- Heure_livraison_souhaitée

### Ligne_Commande
- ID_Ligne_Commande (Clé primaire)
- ID_Commande (Clé étrangère)
- ID_Plat (Clé étrangère)
- Quantité
- Prix_unitaire

### Paiement
- ID_Paiement (Clé primaire)
- ID_Commande (Clé étrangère)
- Montant
- Date_paiement
- Statut_paiement (en attente, validé, refusé)
- Méthode_paiement

### Avis
- ID_Avis (Clé primaire)
- ID_Utilisateur (Clé étrangère)
- ID_Restaurant (Clé étrangère)
- Note
- Commentaire
- Date_avis

### Promotion
- ID_Promotion (Clé primaire)
- ID_Restaurant (Clé étrangère)
- Code_promo
- Description
- Pourcentage_réduction
- Date_début
- Date_fin

### Réservation
- ID_Réservation (Clé primaire)
- ID_Utilisateur (Clé étrangère)
- ID_Restaurant (Clé étrangère)
- Date_réservation
- Heure_réservation
- Nombre_personnes
- Statut_réservation (confirmée, annulée, en attente)

Ce dictionnaire de données couvre les principales entités nécessaires pour le site web de Good Food, en tenant compte des fonctionnalités mentionnées comme la gestion des clients, l'authentification, la gestion des menus, les commandes, les paiements, les livraisons, les réservations et les promotions. Il peut être adapté ou étendu selon les besoins spécifiques du projet.

Voici le dictionnaire de données sous forme de tableau avec le type et la taille pour le site web et l'application mobile de Good Food :

| Entité | Attribut | Type | Taille |
|--------|----------|------|--------|
| Utilisateur | ID_Utilisateur | INT | 4 bytes |
| | Nom | VARCHAR | 50 |
| | Prénom | VARCHAR | 50 |
| | Email | VARCHAR | 100 |
| | Mot_de_passe | VARCHAR | 255 |
| | Adresse | VARCHAR | 200 |
| | Téléphone | VARCHAR | 20 |
| | Date_inscription | DATETIME | 8 bytes |
| | Statut | ENUM | ('actif', 'inactif') |
| Restaurant | ID_Restaurant | INT | 4 bytes |
| | Nom_restaurant | VARCHAR | 100 |
| | Adresse | VARCHAR | 200 |
| | Téléphone | VARCHAR | 20 |
| | Horaires_ouverture | TEXT | - |
| | Type_cuisine | VARCHAR | 50 |
| | Statut | ENUM | ('ouvert', 'fermé', 'en pause') |
| Menu | ID_Menu | INT | 4 bytes |
| | ID_Restaurant | INT | 4 bytes |
| | Nom_menu | VARCHAR | 100 |
| | Description | TEXT | - |
| | Prix | DECIMAL | (10, 2) |
| | Disponibilité | BOOLEAN | 1 byte |
| Plat | ID_Plat | INT | 4 bytes |
| | ID_Menu | INT | 4 bytes |
| | Nom_plat | VARCHAR | 100 |
| | Description | TEXT | - |
| | Prix | DECIMAL | (10, 2) |
| | Allergènes | TEXT | - |
| | Image_URL | VARCHAR | 255 |
| Commande | ID_Commande | INT | 4 bytes |
| | ID_Utilisateur | INT | 4 bytes |
| | ID_Restaurant | INT | 4 bytes |
| | Date_commande | DATETIME | 8 bytes |
| | Statut_commande | ENUM | ('en attente', 'préparation', 'en livraison', 'livrée') |
| | Montant_total | DECIMAL | (10, 2) |
| | Mode_paiement | VARCHAR | 50 |
| | Adresse_livraison | VARCHAR | 200 |
| | Heure_livraison_souhaitée | TIME | 3 bytes |
| Ligne_Commande | ID_Ligne_Commande | INT | 4 bytes |
| | ID_Commande | INT | 4 bytes |
| | ID_Plat | INT | 4 bytes |
| | Quantité | INT | 4 bytes |
| | Prix_unitaire | DECIMAL | (10, 2) |
| Paiement | ID_Paiement | INT | 4 bytes |
| | ID_Commande | INT | 4 bytes |
| | Montant | DECIMAL | (10, 2) |
| | Date_paiement | DATETIME | 8 bytes |
| | Statut_paiement | ENUM | ('en attente', 'validé', 'refusé') |
| | Méthode_paiement | VARCHAR | 50 |
| Avis | ID_Avis | INT | 4 bytes |
| | ID_Utilisateur | INT | 4 bytes |
| | ID_Restaurant | INT | 4 bytes |
| | Note | TINYINT | 1 byte |
| | Commentaire | TEXT | - |
| | Date_avis | DATETIME | 8 bytes |
| Promotion | ID_Promotion | INT | 4 bytes |
| | ID_Restaurant | INT | 4 bytes |
| | Code_promo | VARCHAR | 20 |
| | Description | TEXT | - |
| | Pourcentage_réduction | DECIMAL | (5, 2) |
| | Date_début | DATE | 3 bytes |
| | Date_fin | DATE | 3 bytes |
| Réservation | ID_Réservation | INT | 4 bytes |
| | ID_Utilisateur | INT | 4 bytes |
| | ID_Restaurant | INT | 4 bytes |
| | Date_réservation | DATE | 3 bytes |
| | Heure_réservation | TIME | 3 bytes |
| | Nombre_personnes | TINYINT | 1 byte |
| | Statut_réservation | ENUM | ('confirmée', 'annulée', 'en attente') |

Ce tableau couvre les entités principales pour le site web et l'application mobile de Good Food. Les types et tailles sont basés sur des standards courants, mais peuvent être ajustés en fonction des besoins spécifiques du projet et du système de gestion de base de données utilisé.

## Dictionnaire de données - Application Mobile

### Utilisateur
- ID_Utilisateur (Clé primaire)
- Nom
- Prénom
- Email
- Mot_de_passe (haché)
- Adresse_livraison
- Téléphone
- Préférences_alimentaires

### Restaurant
- ID_Restaurant (Clé primaire)
- Nom_restaurant
- Adresse
- Horaires_ouverture
- Type_cuisine
- Note_moyenne
- Statut (ouvert, fermé, en pause)

### Menu
- ID_Menu (Clé primaire)
- ID_Restaurant (Clé étrangère)
- Nom_menu
- Description
- Prix
- Disponibilité

### Plat
- ID_Plat (Clé primaire)
- ID_Menu (Clé étrangère)
- Nom_plat
- Description
- Prix
- Image_URL
- Allergènes
- Temps_préparation

### Commande
- ID_Commande (Clé primaire)
- ID_Utilisateur (Clé étrangère)
- ID_Restaurant (Clé étrangère)
- Date_commande
- Statut_commande (en attente, préparation, en livraison, livrée)
- Montant_total
- Mode_paiement
- Adresse_livraison
- Heure_livraison_souhaitée

### Ligne_Commande
- ID_Ligne_Commande (Clé primaire)
- ID_Commande (Clé étrangère)
- ID_Plat (Clé étrangère)
- Quantité
- Prix_unitaire

### Paiement
- ID_Paiement (Clé primaire)
- ID_Commande (Clé étrangère)
- Montant
- Date_paiement
- Statut_paiement
- Méthode_paiement

### Avis
- ID_Avis (Clé primaire)
- ID_Utilisateur (Clé étrangère)
- ID_Restaurant (Clé étrangère)
- Note
- Commentaire
- Date_avis

### Promotion
- ID_Promotion (Clé primaire)
- Code_promo
- Description
- Pourcentage_réduction
- Date_début
- Date_fin

### Historique_Commandes
- ID_Historique (Clé primaire)
- ID_Utilisateur (Clé étrangère)
- ID_Commande (Clé étrangère)
- Date_commande

### Favoris
- ID_Favori (Clé primaire)
- ID_Utilisateur (Clé étrangère)
- ID_Restaurant (Clé étrangère)

Ce dictionnaire de données couvre les principales entités nécessaires pour l'application mobile Good Food, en tenant compte des fonctionnalités mentionnées comme la gestion des clients, l'authentification, la gestion des menus, les commandes, les paiements, les livraisons, et les promotions. Il inclut également des éléments spécifiques à l'expérience mobile comme les favoris et l'historique des commandes.

Voici le dictionnaire de données sous forme de tableau avec le type et la taille pour l'application mobile et l'application livreur de Good Food :

| Entité | Attribut | Type | Taille |
|--------|----------|------|--------|
| Utilisateur | ID_Utilisateur | INT | 4 bytes |
| | Nom | VARCHAR | 50 |
| | Prénom | VARCHAR | 50 |
| | Email | VARCHAR | 100 |
| | Mot_de_passe | VARCHAR | 255 |
| | Adresse_livraison | VARCHAR | 200 |
| | Téléphone | VARCHAR | 20 |
| | Préférences_alimentaires | TEXT | - |
| Restaurant | ID_Restaurant | INT | 4 bytes |
| | Nom_restaurant | VARCHAR | 100 |
| | Adresse | VARCHAR | 200 |
| | Horaires_ouverture | TEXT | - |
| | Type_cuisine | VARCHAR | 50 |
| | Note_moyenne | DECIMAL | (3, 2) |
| | Statut | ENUM | ('ouvert', 'fermé', 'en pause') |
| Menu | ID_Menu | INT | 4 bytes |
| | ID_Restaurant | INT | 4 bytes |
| | Nom_menu | VARCHAR | 100 |
| | Description | TEXT | - |
| | Prix | DECIMAL | (10, 2) |
| | Disponibilité | BOOLEAN | 1 byte |
| Plat | ID_Plat | INT | 4 bytes |
| | ID_Menu | INT | 4 bytes |
| | Nom_plat | VARCHAR | 100 |
| | Description | TEXT | - |
| | Prix | DECIMAL | (10, 2) |
| | Image_URL | VARCHAR | 255 |
| | Allergènes | TEXT | - |
| | Temps_préparation | INT | 4 bytes |
| Commande | ID_Commande | INT | 4 bytes |
| | ID_Utilisateur | INT | 4 bytes |
| | ID_Restaurant | INT | 4 bytes |
| | Date_commande | DATETIME | 8 bytes |
| | Statut_commande | ENUM | ('en attente', 'préparation', 'en livraison', 'livrée') |
| | Montant_total | DECIMAL | (10, 2) |
| | Mode_paiement | VARCHAR | 50 |
| | Adresse_livraison | VARCHAR | 200 |
| | Heure_livraison_souhaitée | TIME | 3 bytes |
| Ligne_Commande | ID_Ligne_Commande | INT | 4 bytes |
| | ID_Commande | INT | 4 bytes |
| | ID_Plat | INT | 4 bytes |
| | Quantité | INT | 4 bytes |
| | Prix_unitaire | DECIMAL | (10, 2) |
| Paiement | ID_Paiement | INT | 4 bytes |
| | ID_Commande | INT | 4 bytes |
| | Montant | DECIMAL | (10, 2) |
| | Date_paiement | DATETIME | 8 bytes |
| | Statut_paiement | ENUM | ('en attente', 'validé', 'refusé') |
| | Méthode_paiement | VARCHAR | 50 |
| Avis | ID_Avis | INT | 4 bytes |
| | ID_Utilisateur | INT | 4 bytes |
| | ID_Restaurant | INT | 4 bytes |
| | Note | TINYINT | 1 byte |
| | Commentaire | TEXT | - |
| | Date_avis | DATETIME | 8 bytes |
| Promotion | ID_Promotion | INT | 4 bytes |
| | Code_promo | VARCHAR | 20 |
| | Description | TEXT | - |
| | Pourcentage_réduction | DECIMAL | (5, 2) |
| | Date_début | DATE | 3 bytes |
| | Date_fin | DATE | 3 bytes |
| Historique_Commandes | ID_Historique | INT | 4 bytes |
| | ID_Utilisateur | INT | 4 bytes |
| | ID_Commande | INT | 4 bytes |
| | Date_commande | DATETIME | 8 bytes |
| Favoris | ID_Favori | INT | 4 bytes |
| | ID_Utilisateur | INT | 4 bytes |
| | ID_Restaurant | INT | 4 bytes |
| Livreur | ID_Livreur | INT | 4 bytes |
| | Nom | VARCHAR | 50 |
| | Prénom | VARCHAR | 50 |
| | Email | VARCHAR | 100 |
| | Mot_de_passe | VARCHAR | 255 |
| | Téléphone | VARCHAR | 20 |
| | Statut | ENUM | ('disponible', 'en livraison', 'hors service') |
| | Localisation_actuelle | POINT | 16 bytes |
| Itinéraire | ID_Itinéraire | INT | 4 bytes |
| | ID_Commande | INT | 4 bytes |
| | ID_Livreur | INT | 4 bytes |
| | Point_départ | POINT | 16 bytes |
| | Point_arrivée | POINT | 16 bytes |
| | Distance_estimée | DECIMAL | (10, 2) |
| | Temps_estimé | INT | 4 bytes |
| Livraison | ID_Livraison | INT | 4 bytes |
| | ID_Commande | INT | 4 bytes |
| | ID_Livreur | INT | 4 bytes |
| | Heure_départ | DATETIME | 8 bytes |
| | Heure_arrivée | DATETIME | 8 bytes |
| | Statut_livraison | ENUM | ('en cours', 'terminée', 'problème') |
| Notification | ID_Notification | INT | 4 bytes |
| | ID_Livreur | INT | 4 bytes |
| | Type_notification | ENUM | ('nouvelle commande', 'annulation', 'mise à jour') |
| | Contenu | TEXT | - |
| | Date_heure | DATETIME | 8 bytes |
| | Statut | ENUM | ('lue', 'non lue') |
| Performance_Livreur | ID_Performance | INT | 4 bytes |
| | ID_Livreur | INT | 4 bytes |
| | Nombre_livraisons | INT | 4 bytes |
| | Temps_moyen_livraison | INT | 4 bytes |
| | Note_moyenne | DECIMAL | (3, 2) |
| | Période | ENUM | ('jour', 'semaine', 'mois') |
| Problème_Livraison | ID_Problème | INT | 4 bytes |
| | ID_Livraison | INT | 4 bytes |
| | Type_problème | ENUM | ('retard', 'commande endommagée', 'adresse introuvable') |
| | Description | TEXT | - |
| | Date_heure_signalement | DATETIME | 8 bytes |
| | Statut_résolution | ENUM | ('en cours', 'résolu', 'non résolu') |

Ce tableau couvre les entités principales pour l'application mobile et l'application livreur de Good Food. Les types et tailles sont basés sur des standards courants, mais peuvent être ajustés en fonction des besoins spécifiques du projet et du système de gestion de base de données utilisé.

## Dictionnaire de données - Application Livreur

### Livreur
- ID_Livreur (Clé primaire)
- Nom
- Prénom
- Email
- Mot_de_passe (haché)
- Téléphone
- Statut (disponible, en livraison, hors service)
- Localisation_actuelle

### Commande
- ID_Commande (Clé primaire)
- ID_Restaurant (Clé étrangère)
- ID_Client (Clé étrangère)
- ID_Livreur (Clé étrangère)
- Date_commande
- Statut_commande (en attente, en préparation, prête, en livraison, livrée)
- Adresse_livraison
- Heure_livraison_souhaitée

### Itinéraire
- ID_Itinéraire (Clé primaire)
- ID_Commande (Clé étrangère)
- ID_Livreur (Clé étrangère)
- Point_départ
- Point_arrivée
- Distance_estimée
- Temps_estimé

### Livraison
- ID_Livraison (Clé primaire)
- ID_Commande (Clé étrangère)
- ID_Livreur (Clé étrangère)
- Heure_départ
- Heure_arrivée
- Statut_livraison (en cours, terminée, problème)

### Restaurant
- ID_Restaurant (Clé primaire)
- Nom_restaurant
- Adresse
- Téléphone
- Coordonnées_GPS

### Notification
- ID_Notification (Clé primaire)
- ID_Livreur (Clé étrangère)
- Type_notification (nouvelle commande, annulation, mise à jour)
- Contenu
- Date_heure
- Statut (lue, non lue)

### Performance_Livreur
- ID_Performance (Clé primaire)
- ID_Livreur (Clé étrangère)
- Nombre_livraisons
- Temps_moyen_livraison
- Note_moyenne
- Période (jour, semaine, mois)

### Problème_Livraison
- ID_Problème (Clé primaire)
- ID_Livraison (Clé étrangère)
- Type_problème (retard, commande endommagée, adresse introuvable)
- Description
- Date_heure_signalement
- Statut_résolution

Ce dictionnaire de données couvre les principales entités nécessaires pour l'application livreur de Good Food, en tenant compte des fonctionnalités mentionnées comme la gestion des livraisons, le suivi des commandes, la localisation des livreurs, et la gestion des performances. Il peut être adapté ou étendu selon les besoins spécifiques du projet.

Voici le dictionnaire de données sous forme de tableau avec le type et la taille pour l'application livreur de Good Food :

| Entité | Attribut | Type | Taille |
|--------|----------|------|--------|
| Livreur | ID_Livreur | INT | 4 bytes |
| | Nom | VARCHAR | 50 |
| | Prénom | VARCHAR | 50 |
| | Email | VARCHAR | 100 |
| | Mot_de_passe | VARCHAR | 255 |
| | Téléphone | VARCHAR | 20 |
| | Statut | ENUM | ('disponible', 'en livraison', 'hors service') |
| | Localisation_actuelle | POINT | 16 bytes |
| Commande | ID_Commande | INT | 4 bytes |
| | ID_Restaurant | INT | 4 bytes |
| | ID_Client | INT | 4 bytes |
| | ID_Livreur | INT | 4 bytes |
| | Date_commande | DATETIME | 8 bytes |
| | Statut_commande | ENUM | ('en attente', 'en préparation', 'prête', 'en livraison', 'livrée') |
| | Adresse_livraison | VARCHAR | 200 |
| | Heure_livraison_souhaitée | TIME | 3 bytes |
| Itinéraire | ID_Itinéraire | INT | 4 bytes |
| | ID_Commande | INT | 4 bytes |
| | ID_Livreur | INT | 4 bytes |
| | Point_départ | POINT | 16 bytes |
| | Point_arrivée | POINT | 16 bytes |
| | Distance_estimée | DECIMAL | (10, 2) |
| | Temps_estimé | INT | 4 bytes |
| Livraison | ID_Livraison | INT | 4 bytes |
| | ID_Commande | INT | 4 bytes |
| | ID_Livreur | INT | 4 bytes |
| | Heure_départ | DATETIME | 8 bytes |
| | Heure_arrivée | DATETIME | 8 bytes |
| | Statut_livraison | ENUM | ('en cours', 'terminée', 'problème') |
| Restaurant | ID_Restaurant | INT | 4 bytes |
| | Nom_restaurant | VARCHAR | 100 |
| | Adresse | VARCHAR | 200 |
| | Téléphone | VARCHAR | 20 |
| | Coordonnées_GPS | POINT | 16 bytes |
| Notification | ID_Notification | INT | 4 bytes |
| | ID_Livreur | INT | 4 bytes |
| | Type_notification | ENUM | ('nouvelle commande', 'annulation', 'mise à jour') |
| | Contenu | TEXT | - |
| | Date_heure | DATETIME | 8 bytes |
| | Statut | ENUM | ('lue', 'non lue') |
| Performance_Livreur | ID_Performance | INT | 4 bytes |
| | ID_Livreur | INT | 4 bytes |
| | Nombre_livraisons | INT | 4 bytes |
| | Temps_moyen_livraison | INT | 4 bytes |
| | Note_moyenne | DECIMAL | (3, 2) |
| | Période | ENUM | ('jour', 'semaine', 'mois') |
| Problème_Livraison | ID_Problème | INT | 4 bytes |
| | ID_Livraison | INT | 4 bytes |
| | Type_problème | ENUM | ('retard', 'commande endommagée', 'adresse introuvable') |
| | Description | TEXT | - |
| | Date_heure_signalement | DATETIME | 8 bytes |
| | Statut_résolution | ENUM | ('en cours', 'résolu', 'non résolu') |

Ce tableau couvre les entités principales pour l'application livreur de Good Food. Les types et tailles sont basés sur des standards courants, mais peuvent être ajustés en fonction des besoins spécifiques du projet et du système de gestion de base de données utilisé.
