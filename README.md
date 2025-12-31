# PROJET JEE BACKEND -SPRING-ANGULAR-SPRING SECURITY-JWT 
## Introduction

Le projet de gestion bancaire vise à développer une application 
complète permettant la gestion efficace des comptes bancaires.
Chaque compte est associé à un client et peut être sujet à diverses 
opérations telles que le débit et le crédit. Le système prend en charge
deux types de comptes : les comptes courants et les comptes épargnes.


## Architecture de l'application
<img src="captures/architectureebanking.PNG">

## Couche DAO
Dans cette section, nous avons créé un projet Spring Boot et
mis en place la couche d'accès aux données (DAO). Les entités JPA telles que Customer,
BankAccount, Saving Account, CurrentAccount, et AccountOperation ont été définies. 
Les interfaces JPA Repository basées sur Spring Data ont été mises en place pour interagir 
avec la base de données.Des tests ont été effectués pour valider le bon fonctionnement de la couche DAO.

# Entités JPA 
**H2 DATABASE**<br>
     *SINGLE TABLE
<p>générer single table</p>
<img src="captures/db_st_entity.PNG">
<p>la valeur du type Saving Account</p>
<img src="captures/db_st_entity_sa.PNG">
<p>la valeur du type Current Account</p>
<img src="captures/db_stçentity_ca.PNG">
<p>table Bank Account</p>

<img src="captures/single_table_bankAccount.PNG">
<p>table Customer</p>

<img src="captures/single_table_customer.PNG">
<p>table Account Operation</p>

<img src="captures/single_table_Account_operation.PNG">
     *PER TABLE

<p> Les autres tables restent les mêmes, sauf bankAccount qui ne sera pas présente, et à la place, nous aurons deux tables : CurrentAccount et SavingAccount.</p>
<p>générer per table Bank Account </p>
<img src="captures/per_table_entity.PNG">
<p>table Current Account</p>
<img src="captures/per_table_current_account.PNG">
<p>table Saving Account</p>
<img src="captures/per_table_saving_account.PNG">

   *Joined
<p> Les autres tables restent les mêmes, sauf bankAccount, CurrentAccount, SavingAccount qui seront modifiées.</p>
<p>générer joined table</p>
<img src="captures/joined_table_entity.PNG">
<p>table Saving Account</p>
<img src="captures/joined_saving_account.PNG">
<p>table Current Account</p>
<img src="captures/joined_current_account.PNG">
<p>table Bank Account</p>
<img src="captures/joined_bank_account.PNG">

**SQL**

<img src="captures/ebank_db_SQL.PNG">
<li>Interfaces JPA Repository :</li>




# Swagger
Swagger a été intégré pour la documentation automatique des API REST. Cet outil génère une documentation interactive basée sur les annotations dans le code source. Grâce à Swagger, les développeurs peuvent explorer et comprendre facilement les endpoints disponibles, les paramètres requis, et les réponses attendues, tout en facilitant l'intégration avec d'autres parties du système. stp redonne moi ca en fonction de mon projet et comment j'ai pu les exploiter dans mon projet et utilise on
1. Consulter les Endpoints

    1.1 .Clients
   <img src="captures/swagger-first.PNG">
    1.2  .Banque et Sécurité
   <img src="captures/swagger1.PNG">


# Postman
Postman a été utilisé comme un outil essentiel pour tester les API exposées par l'application. Il offre une interface conviviale pour envoyer des requêtes HTTP aux endpoints spécifiés, permettant ainsi aux développeurs de tester les fonctionnalités de manière interactive. Les collections Postman peuvent être créées pour regrouper les requêtes associées à différentes fonctionnalités.
  **OpenAPI definition**
l'importation d'un fichier OpenAPI dans Postman offre une intégration fluide entre la documentation de l'API et les tests pratiques, améliorant ainsi l'efficacité du développement et de la validation de l'API.
<img src="captures/postman.PNG">
les étapes:
=> Ouvrez Postman 
=> Ouvrez Postman
=> Choisissez "OpenAPI"
=> Importez le fichier OpenAPI
## Sécurisation de l'Application avec un Système d'Authentification basé sur Spring Security et JSON Web Token
La sécurisation de l'application bancaire a été réalisée en mettant en place un système d'authentification basé sur Spring Security et l'utilisation de JSON Web Token (JWT). Cette approche renforce la sécurité de l'application en assurant un accès sécurisé aux fonctionnalités tout en prévenant les accès non autorisés.
1. Dépendance: ```spring-boot-starter-oauth2-resource-server```
<img src="captures/pring_oauth2.PNG">
La dépendance spring-boot-starter-oauth2-resource-server dans
un projet Spring Boot sert à configurer l'application en tant que
serveur de ressources OAuth 2.0. Elle permet à l'application de valider
les jetons d'accès OAuth 2.0, vérifier les autorisations et sécuriser les 
ressources sensibles. Cela est utile dans les architectures où l'authentification 
et l'autorisation sont gérées par un serveur d'authentification externe, et l'application
agit en tant que serveur de ressources sécurisé.
2. Login
   <img src="captures/login_apres.PNG">


4. JWT

   Avec l'approche HTTP Basic, il est nécessaire d'envoyer à chaque fois le nom d'utilisateur et le mot de passe. Pour simplifier cela, nous allons passer à l'utilisation de JSON Web Tokens (JWT).

Dans cette approche, un token est généré lors de l'authentification et deux beans sont utilisés :

  *Le bean encoder, qui signe et génère les tokens JWT.

  *Le bean decoder, un filtre qui intercepte les requêtes, récupère le JWT, vérifie la signature, et extrait les informations du token.

==>Cela permet de simplifier le processus d'authentification en utilisant des tokens signés pour transporter les informations d'identification de manière sécurisée.
  
4.1 Génération du JWT

Avec JWT, au lieu d'envoyer le nom d'utilisateur et le mot de passe à chaque requête, on envoie le token généré sous la forme d'un "Bearer".

L'utilisation du terme "Bearer" dans ce contexte signifie que le porteur (bearer) du token est authentifié. Lorsqu'on envoie une requête avec un token JWT, on inclut généralement l'en-tête Authorization avec la valeur "Bearer" suivie du token. Cela permet au serveur de comprendre que le token est utilisé pour l'authentification.
<img src="captures/jwt_generation.PNG">



## Conclusion 
En conclusion, le projet JEE Backend, construit sur les technologies Spring, Angular, Spring Security, et JWT, a été développé dans le but de fournir une solution complète pour la gestion bancaire. La première partie de l'architecture de l'application a été détaillée, mettant en avant la mise en place de la couche DAO avec des entités JPA telles que Customer, BankAccount, Saving Account, CurrentAccount, et AccountOperation.

Les tests et la documentation ont mis en avant l'intégration réussie de Swagger pour la documentation interactive des API REST. Les tests effectués avec Postman, ainsi que l'utilisation de l'OpenAPI definition, démontrent une approche solide pour la validation des fonctionnalités de l'application.

La sécurisation de l'application, une composante cruciale, a été implémentée avec succès en intégrant Spring Security et en adoptant JSON Web Token (JWT). Les dépendances nécessaires, le processus d'authentification avec JWT, et les différentes étapes telles que la génération du JWT ont été expliqués en détail.

En plus de la partie backend, la modélisation des entités, la mise en place des repositories, l'utilisation d'énumérations et de DTOs, la gestion des exceptions, les mappers, les services, et la partie web avec les contrôleurs ont été élaborés pour garantir une application bien structurée et facile à maintenir.

Ce projet offre une solution holistique pour la gestion bancaire en mettant l'accent sur la sécurité, la documentation, et la qualité du code. L'intégration réussie de différentes technologies témoigne d'une approche moderne et efficace pour le développement d'applications robustes et sécurisées.






 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 <h1>Projet JEE - Digital banking - Backend</h1>
<p>Système de gestion bancaire permettant aux clients de détenir plusieurs comptes (courants ou épargne) et d'effectuer des opérations de dépôt et retrait.</p>

----

<h2>Base de données MySQL</h2>
<p>La base de données MySQL a été conçue avec une structure relationnelle permettant de gérer les clients, leurs comptes bancaires et les opérations financières.</p>
<img width="622" height="243" alt="image" src="https://github.com/user-attachments/assets/a80c8291-ea17-47d9-9ff1-0638dcc3c9c4" />



<h2>Gestion des comptes bancaires</h2>
<p>La gestion des comptes bancaires permet d'afficher la liste complète de tous les comptes, de visualiser leurs détails (solde, type, statut), de créer de nouveaux comptes, et d'effectuer des opérations </p>
<h3>Affichage de la liste de tous les comptes bancaires</h3>
<img width="289" height="338" alt="image" src="https://github.com/user-attachments/assets/25844077-771a-43f1-b889-f3d715d6269b" />

<h3>Affichage d'un compte bancaire par son ID</h3>
<img width="314" height="152" alt="image" src="https://github.com/user-attachments/assets/72d25ed7-c5e0-4202-825a-cf24a7256c71" />

<h3>Affichage de la page des opérations d'un compte bancaire d'après son ID</h3>
<img width="376" height="350" alt="image" src="https://github.com/user-attachments/assets/4f9603a5-ec10-4dc4-b670-1d50012cc05f" />

<h3>Affichage de la liste de tous les comptes bancaires au niveau de Swagger</h3>
<img width="561" height="299" alt="image" src="https://github.com/user-attachments/assets/6f4e2021-4dda-49f2-ac30-715248cc0003" />

<h3>Affichage d'un compte bancaire par son ID au niveau de Swagger</h3>
<img width="562" height="208" alt="image" src="https://github.com/user-attachments/assets/5986a688-b986-4aa1-9c8c-b38e79790292" />

<h3>Affichage des opérations d'un compte bancaire d'après son ID au niveau de Swagger</h3>
<img width="563" height="344" alt="image" src="https://github.com/user-attachments/assets/79f7011e-bf0e-4a6d-9e47-eb2d41dbf7e0" />

<h3>Affichage de la page des opérations d'un compte bancaire d'après son ID au niveau de Swagger</h3>
<img width="566" height="349" alt="image" src="https://github.com/user-attachments/assets/16dda333-45b1-4241-86c8-4f2d673b5a89" />




<h2>Gestion des clients</h2>
<h3>Affichage de la liste des clients</h3>
<img width="658" height="448" alt="image" src="https://github.com/user-attachments/assets/0ea29ca2-b4b3-4998-9204-f732c2aae903" />
<h3>Affichage de la liste des clients au niveau de Swagger</h3>
<img width="1117" height="472" alt="image" src="https://github.com/user-attachments/assets/369e1170-9335-4f92-af1a-ec5972aa02a1" />
<h3>Rechercher tous les clients</h3>

<img width="658" height="448" alt="image" src="https://github.com/user-attachments/assets/0ea29ca2-b4b3-4998-9204-f732c2aae903" />

<h3>Rechercher un client par mot cle</h3>
<img width="562" height="198" alt="image" src="https://github.com/user-attachments/assets/6a97a39e-4663-4859-80ed-2c996ee16f74" />

<h3>Affichage d'un client par son ID</h3>
<img width="562" height="198" alt="image" src="https://github.com/user-attachments/assets/6a97a39e-4663-4859-80ed-2c996ee16f74" />

<h3>Affichage d'un client par son ID au niveau de Swagger</h3>
<img width="1130" height="444" alt="image" src="https://github.com/user-attachments/assets/62532431-74c3-44ae-9235-c7b205e481e4" />




# FrentendBanking

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 17.0.7.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

# Compte Rendu de Projet Angular avec API Spring Boot

## Introduction

Le projet vise à développer une application web utilisant Angular comme framework front-end et une API Spring Boot comme backend. L'application se concentre sur la gestion des clients, des comptes bancaires, des relations clients-comptes, et inclut un système d'authentification.

## Description des Modules

1. **Interfaces**
   - **Customers**: Interface dédiée à la gestion des clients.
   - **Accounts**: Interface pour la gestion des comptes bancaires.
   - **Customers-Accounts**: Interface gérant les relations entre clients et comptes.
   - **Login**: Interface d'authentification permettant aux utilisateurs de se connecter.

2. **Services**
   - **Customers-Services**: Service associé à la gestion des clients.
   - **Accounts-Services**: Service responsable de la gestion des comptes bancaires.
   - **Auth-Service**: Service d'authentification assurant la sécurité de l'application.

3. **Intercepteurs**
   - Des intercepteurs ont été créés pour gérer les requêtes HTTP sortantes et entrantes, assurant un contrôle et une gestion des erreurs appropriés.

4. **Guards**
   - **Authentication Guard**: Un garde-frontière qui protège les routes nécessitant une authentification.
   - **Authorization Guard**: Un garde-frontière qui gère l'autorisation d'accès aux différentes parties de l'application.

5. **Définition des Routes**
   - Les routes ont été définies de manière à permettre une navigation fluide et intuitive au sein de l'application. Des routes sont protégées par les guards d'authentification et d'autorisation pour garantir la sécurité.

6. **Tests des Composants**
   - Tous les composants, services, intercepteurs et guards ont été testés de manière exhaustive pour assurer un fonctionnement correct et identifier tout comportement indésirable.
     ![Gestion des Produits](https://github.com/elmehdibenhayoun/frontend-banking/blob/master/capture/adminlogin.png)
     ![Gestion des Produits](https://github.com/user-attachments/assets/7575354d-0a08-48d9-b558-8247f54b5a1e)


     ![Gestion des Produits](https://github.com/user-attachments/assets/4250e432-6886-4bc4-a448-fb07256d1c07)
     ![Gestion des Produits](https://github.com/user-attachments/assets/4371589c-1a2b-4887-8d34-66a597e8f576)
     ![Gestion des Produits](https://github.com/user-attachments/assets/a53fc08b-e0bb-4531-a148-ce189ec71d72)

     































