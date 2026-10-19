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

## 4. Description des composants

### 4.1. Entité Product

La classe `Product` représente un produit dans la base de données.

Elle contient les attributs suivants :

- `id` : identifiant unique généré automatiquement.
- `name` : nom du produit.
- `price` : prix du produit.

Les annotations JPA permettent à Hibernate de faire correspondre cette classe à la table `products`.

### 4.2. Couche DAO

La couche DAO (*Data Access Object*) est responsable de l'accès aux données.

L'interface `IDao<T>` définit les opérations principales :

- `save(T entity)` : enregistrer une entité.
- `update(T entity)` : modifier une entité.
- `delete(T entity)` : supprimer une entité.
- `findById(Long id)` : rechercher une entité par son identifiant.
- `findAll()` : récupérer toutes les entités.

La classe `ProductDaoImpl` implémente ces opérations en utilisant Hibernate et `SessionFactory`.

### 4.3. Couche Service

La couche Service contient la logique métier de l'application.

La classe `ProductServiceImpl` utilise la couche DAO pour gérer les produits.

Elle permet notamment :
- D'ajouter un produit.
- De récupérer la liste des produits.
- De refuser un produit lorsque son prix est négatif, conformément à la règle métier implémentée.

Les annotations `@Service` et `@Transactional` permettent respectivement de déclarer le service comme composant Spring et de gérer les transactions.

### 4.4. Configuration Spring et Hibernate

La configuration permet de :
- Déclarer les composants Spring.
- Configurer la source de données MySQL.
- Créer la `SessionFactory` d'Hibernate.
- Activer la gestion des transactions.
- Injecter automatiquement les dépendances nécessaires.

Les annotations utilisées comprennent notamment `@Configuration`, `@ComponentScan`, `@Bean`, `@Autowired`, `@EnableTransactionManagement` et `@Transactional`.

## 5. Résultats des tests

### Test 1 : Initialisation du contexte

Le test `TestHibernate` a été exécuté avec succès.

Message obtenu :

<img width="763" height="92" alt="TP5" src="https://github.com/user-attachments/assets/f9ff31e4-e5d0-401c-99d3-164a805b964d" />

Hibernate a également créé la table `products` automatiquement.

### Test 2 : Ajout d'un produit

<img width="512" height="93" alt="TP50" src="https://github.com/user-attachments/assets/ac3c4986-e283-40c7-9227-586090f0d9d3" />
