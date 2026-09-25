# Projet-Pizzeria
Travailler sur les données d’une pizzeria afin d’analyser son activité commerciale grâce à MongoDB.
Analyse des ventes — Pizzeria MongoDB

1. Présentation du projet

Ce projet consiste à exploiter les données commerciales d'une pizzeria avec MongoDB afin de transformer des données de ventes brutes en informations exploitables et en indicateurs clés de performance (KPI).

L'objectif est d'analyser notamment :
le chiffre d'affaires ;
les volumes de pizzas vendues ;
les produits les plus populaires ;
les catégories de pizzas ;
les formats vendus ;
les périodes de forte activité ;
les clients générant le plus de chiffre d'affaires.

2. Données utilisées

Le jeu de données contient 299 lignes de ventes.

Les principales informations disponibles sont :

**Champ
Description
order_id
Identifiant de commande
order_date
Date de commande
order_time
Heure de commande
customer_id
Identifiant client
neighborhood
Zone du client / livraison
channel
Sur place / à emporter / livraison
payment_method
Mode de paiement
promotion
Promotion appliquée
pizza_id
Identifiant pizza
pizza_name
Nom de la pizza
pizza_category
Catégorie de pizza
size_cm
Diamètre en cm
dough_type
Type de pâte
quantity
Quantité vendue
unit_price_eur
Prix unitaire après options
line_total_eur
Chiffre d'affaires de la ligne**

3. Organisation MongoDB

Deux collections sont utilisées :

pizzeria_ventes_raw

Collection contenant les données brutes importées depuis le fichier CSV.

Elle est conservée comme source originale et n'est pas utilisée pour les analyses finales.

pizzeria_ventes

Collection contenant les données nettoyées et enrichies.

Des champs complémentaires ont été ajoutés pour faciliter les analyses :

**Champ ajouté
Utilisation
date_commande
Regroupement et analyse temporelle
quantite
Quantité numérique exploitable
prix_unitaire
Prix numérique exploitable
line_total_eur
Chiffre d'affaires de la ligne
mois
Analyse mensuelle
heure
Analyse des heures de vente**

4. Traitement des données

Les données brutes ont été transformées avec une agrégation MongoDB afin de :

convertir la date et l'heure en un véritable champ date ;

convertir les quantités et les prix en valeurs numériques ;

conserver le chiffre d'affaires réel de chaque ligne via line_total_eur ;

créer des variables d'analyse temporelle (mois et heure) ;

enregistrer les données préparées dans la collection pizzeria_ventes.

Schéma de traitement

Fichier CSV
    ↓
pizzeria_ventes_raw
    ↓
Nettoyage / transformation MongoDB
    ↓
pizzeria_ventes
    ↓
Requêtes KPI

5. KPI

Les requêtes sont sauvegardées dans Navicat sous forme d'onglets nommés.

**KPI 1 — Chiffre d'affaires total**

Résultat : 4 848,66 €

Capture d'écran

<img width="1065" height="605" alt="image" src="https://github.com/user-attachments/assets/8a50ea24-5c20-410b-91c1-a460ed3999e5" />

**KPI 2 — Nombre total de pizzas vendues**

Résultat : 329 pizzas

Capture d'écran

<img width="898" height="547" alt="image" src="https://github.com/user-attachments/assets/7e3ef017-1740-4e9b-b9e3-fdf8878391eb" />

**KPI 3 — Top 10 des pizzas les plus vendues**

Première place : Margherita — 55 pizzas vendues

Capture d'écran

<img width="888" height="811" alt="image" src="https://github.com/user-attachments/assets/be34dc53-0fee-4bb3-8e84-44355d55b0f1" />

**KPI 4 — Chiffre d'affaires par catégorie**

Catégorie générant le plus de CA : Viande — 1 271,04 €

Capture d'écran

<img width="915" height="698" alt="image" src="https://github.com/user-attachments/assets/da8143db-f3e2-457a-ba75-ec7f58614d4c" />

**KPI 5 — Quantité vendue par taille**

Format le plus vendu : 30 cm — 134 pizzas

Capture d'écran

<img width="880" height="729" alt="image" src="https://github.com/user-attachments/assets/c5e067c5-5e81-43a0-987c-9995abd4bf05" />

**KPI 6 — Jour le plus actif**

Capture à insérer après exécution de la requête

Capture d'écran

<img width="907" height="803" alt="image" src="https://github.com/user-attachments/assets/dce6981c-e2bf-4d77-9948-d4231873d139" />

**FIN **

6. Structure des fichiers / éléments du projet

Pizzeria-MongoDB/
│
├── README.md
│
├── data/
│   └── fichier_csv.csv
│
├── screenshots/
│   ├── kpi_01_ca_total.png
│   ├── kpi_02_pizzas_vendues.png
│   ├── kpi_03_top_10_pizzas.png
│   ├── kpi_04_ca_par_categorie.png
│   ├── kpi_05_ventes_par_taille.png
│   └── kpi_06_jour_plus_actif.png
│
└── queries/
    ├── KPI_01_CA_total.js
    ├── KPI_02_Pizzas_vendues.js
    ├── KPI_03_Top_10_pizzas.js
    ├── KPI_04_CA_par_categorie.js
    ├── KPI_05_Ventes_par_taille.js
    └── KPI_06_Jour_plus_actif.js

7. Contrôles de cohérence

Quelques contrôles ont été effectués afin de vérifier les résultats :

pizzeria_ventes_raw contient 299 documents ;

pizzeria_ventes contient 299 documents ;

la somme des quantités vendues est de 329 pizzas ;

la somme du chiffre d'affaires par catégorie correspond au CA total de 4 848,66 € ;

la somme des quantités par taille correspond également aux 329 pizzas vendues.

8. Conclusion

MongoDB permet ici de passer d'un jeu de données brut à une collection structurée et exploitable, puis de produire rapidement différents KPI permettant de mieux comprendre l'activité de la pizzeria.

