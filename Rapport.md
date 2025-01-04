
# Rapport de gestion du projet

## Introduction

Ce projet a été développé en utilisant la méthodologie **Trunk-Based Development (TBD)**, où le travail est effectué sur une seule branche principale, **`main`**, afin de permettre des intégrations fréquentes et un flux de développement rapide. L'objectif principal était de maintenir une **intégration continue** (CI), d'assurer la qualité du code avec des tests automatisés et d'assurer une cohésion entre les différentes parties de l'application (frontend et backend).

### Contexte du Projet
Le projet consiste en deux parties principales :
1. **`vote-api`** : Le backend, qui fournit une API permettant de voter pour des films.
2. **`web-client`** : Le frontend, une application web permettant aux utilisateurs de voir les films et de voter pour leurs préférés via une interface utilisateur.

Le but était de garantir un flux de développement fluide, d'assurer une qualité continue du code, et de rendre les versions testables au fur et à mesure de leur développement.

## Objectifs du Projet

1. **Maintenir une base de code stable et évolutive**.
2. **Automatiser les tests et le contrôle qualité** à chaque modification de code.
3. **Faciliter la collaboration au sein de l'équipe** en limitant les conflits de fusion grâce à un développement basé sur le tronc.
4. **Assurer la validation des fonctionnalités** avec des tests unitaires et des tests de bout en bout (E2E).

## Méthodologie

### **Trunk-Based Development**

Nous avons utilisé l'approche **Trunk-Based Development (TBD)**, où tout le travail de développement est effectué dans une **seule branche** (`main`). Cette approche nous a permis de garantir une **intégration continue rapide** et de limiter les conflits de fusion, en gardant tous les développeurs concentrés sur une base de code principale.

### **Branches de fonctionnalité temporaires**

Bien que nous utilisions principalement la branche **`main`** pour le développement, des **branches de fonctionnalité temporaires** étaient créées pour les nouvelles fonctionnalités. Celles-ci étaient régulièrement fusionnées dans la branche **`main`** après avoir passé les tests et revues de code.

### **Processus de revue de code**

Chaque modification apportée à la branche **`main`** passait par une **pull request (PR)** afin d'être examinée et validée par d'autres membres de l'équipe. Cela permet de s'assurer que les changements apportés respectent les bonnes pratiques de codage et n'introduisent pas de régressions.

## Processus d'intégration continue (CI)

### 1. **Mise en place des tests unitaires**

Des tests unitaires ont été mis en place pour **le backend** et **le frontend**.

#### **Backend (`vote-api`)**
- **Tests unitaires Go** : Nous avons utilisé le framework **Go testing** pour vérifier que les fonctions backend (comme la gestion des votes) fonctionnaient correctement.
- **Commandes utilisées** :
  - `go test ./...` : Exécution des tests unitaires pour valider que le backend répond aux attentes de l'équipe.

#### **Frontend (`web-client`)**
- **Tests unitaires avec Vitest** : Le frontend utilise **Vitest** pour exécuter des tests unitaires en JavaScript/TypeScript. Ces tests sont utilisés pour vérifier que les composants de l'application frontend fonctionnent comme prévu.
- **Commandes utilisées** :
  - `yarn test` : Exécution des tests unitaires pour s'assurer que les fonctionnalités frontend ne sont pas cassées.

### 2. **Linter et Contrôle de la qualité du code**

Afin de garantir la qualité du code et éviter l'introduction d'erreurs liées au style, nous avons mis en place des outils de **linter** pour les deux parties du projet :

- **Backend (`vote-api`)** : Nous avons utilisé **golangci-lint** pour vérifier la qualité du code Go et détecter les erreurs potentielles.
  - **Commandes utilisées** :
    - `golangci-lint run` : Exécution du linter pour valider le style et la qualité du code Go.
  
- **Frontend (`web-client`)** : Nous avons utilisé **ESLint** pour vérifier les erreurs de style et les mauvaises pratiques dans le code JavaScript/TypeScript.
  - **Commandes utilisées** :
    - `yarn lint` : Exécution du linter pour s'assurer que le frontend respecte les règles de style définies.

### 3. **Tests E2E (End-to-End)**

Pour tester l'intégration complète de l'application (frontend et backend), nous avons mis en place des tests **E2E** :

- **Frontend (`web-client`)** : Les tests E2E sont utilisés pour vérifier le bon fonctionnement de l'application du point de vue de l'utilisateur. Nous avons utilisé un framework comme **Cypress** ou un outil similaire pour vérifier que les interactions de l'utilisateur avec l'interface se déroulent correctement.
  - **Commandes utilisées** :
    - `yarn e2e` : Exécution des tests E2E pour valider l'intégration du frontend.

- **Backend (`vote-api`)** : Nous avons écrit des tests d'intégration ou des tests E2E pour vérifier que le backend répond comme prévu aux différentes demandes (par exemple, récupérer les votes d'un film).
  - **Commandes utilisées** :
    - `go run e2e-tests.go` : Exécution des tests d'intégration pour valider que l'API backend fonctionne correctement avec l'interface.

### 4. **Automatisation du build**

Le processus de **build** a été automatisé pour garantir que les deux parties du projet se construisent correctement à chaque commit.

- **Backend (`vote-api`)** : Nous avons utilisé la commande `go build` pour compiler le backend et générer un binaire de production.
- **Frontend (`web-client`)** : Nous avons utilisé **Yarn** pour construire l'application frontend en mode production avec `yarn build`.

### 5. **GitHub Actions**

Nous avons utilisé **GitHub Actions** pour automatiser tout le pipeline CI. À chaque **push** ou **pull request**, les actions suivantes sont exécutées :
- **Linter** : Vérification de la qualité du code.
- **Tests unitaires** : Exécution des tests unitaires pour le backend et le frontend.
- **Tests E2E** : Vérification de l'intégration complète de l'application.
- **Build** : Construction des applications frontend et backend pour s'assurer qu'elles peuvent être déployées correctement.
