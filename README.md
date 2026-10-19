# TP 5 : Intégration de Spring et Hibernate dans une Architecture Microservices

## 1. Présentation du projet

Ce projet consiste à intégrer **Spring, Hibernate et MySQL** dans une application Java organisée en plusieurs couches.

L'objectif est de gérer des produits en utilisant :
- **Spring** pour la gestion des composants et l'injection des dépendances.
- **Hibernate** pour la persistance des données et la communication avec la base de données.
- **MySQL** pour stocker les produits.
- **Maven** pour gérer les dépendances du projet.

## 2. Objectifs du TP

Les objectifs de ce travail pratique sont les suivants :

- Configurer un projet Java avec Maven.
- Configurer la connexion entre l'application et MySQL.
- Créer une entité `Product` avec Hibernate.
- Implémenter une couche DAO pour accéder aux données.
- Implémenter une couche Service pour gérer la logique métier.
- Configurer Spring pour gérer les composants et injecter leurs dépendances.
- Gérer les transactions avec Spring.
- Tester l'insertion et la récupération des produits.

## 3. Architecture du projet

Le projet suit une architecture en couches :

```text
microservice-product
│
├── src
│   └── main
│       ├── java
│       │   └── com.microservice.product
│       │       ├── config
│       │       │   ├── AppConfig.java
│       │       │   ├── HibernateConfig.java
│       │       │   └── TransactionConfig.java
│       │       │
│       │       ├── dao
│       │       │   ├── IDao.java
│       │       │   └── ProductDaoImpl.java
│       │       │
│       │       ├── entity
│       │       │   └── Product.java
│       │       │
│       │       ├── service
│       │       │   └── ProductServiceImpl.java
│       │       │
│       │       └── TestHibernate.java
│       │
│       └── resources
│           └── application.properties
│
├── pom.xml
└── README.md
```

La classe `MainApp.java`, si elle existe dans le projet, permet de tester les opérations métier.

## 4. Résultats des tests

### Test 1 : Initialisation du contexte

Le test `TestHibernate` a été exécuté avec succès.

Message obtenu :

<img width="763" height="92" alt="TP5" src="https://github.com/user-attachments/assets/f9ff31e4-e5d0-401c-99d3-164a805b964d" />

Hibernate a également créé la table `products` automatiquement.

### Test 2 : Ajout d'un produit

<img width="512" height="93" alt="TP50" src="https://github.com/user-attachments/assets/ac3c4986-e283-40c7-9227-586090f0d9d3" />
