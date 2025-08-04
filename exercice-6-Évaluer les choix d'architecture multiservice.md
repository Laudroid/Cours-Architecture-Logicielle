---
# TP : Évaluation des choix d'architecture multiservice à travers un mini-projet

## Objectif pédagogique
- Comprendre et évaluer les avantages des architectures basées sur les microservices.
- Illustrer les concepts clés par un mini projet pratique.
- Développer un sens critique sur les impacts des choix d'architecture.
- S’adapter à l’utilisation d’outils d’IA dans le processus d’apprentissage et de développement.

---

## Contexte / Introduction

Les architectures multiservice — souvent incarnées par les microservices — gagnent en popularité pour leurs capacités à rendre les applications plus modulaires, scalables et faciles à maintenir. Ce TP vise à vous faire expérimenter ces principes dans un mini projet simple, en vous confrontant aux principaux avantages et défis liés à ce type d’architecture.

---

## Enoncé du TP

### Partie 1 : QCM - Compréhension théorique

Avant de démarrer, répondez à la question suivante :

**Quel avantage majeur offrent les microservices ?**

1. Un code monolithique  
2. Déploiement autonome  
3. Couplage fort  
4. Gestion des transactions complexe  

*(Réfléchissez et donnez votre réponse avant de poursuivre !)*

---

### Partie 2 : Mini projet pratique

Vous allez développer une petite application "Gestion de bibliothèque" **simulée**. L’application doit permettre :  
- de gérer les livres (CRUD livres)  
- de gérer les utilisateurs (CRUD utilisateurs)  
- d’emprunter et rendre des livres  

#### Consignes

1. **Architecture monolithique** :  
   Implémentez une première version monolithique (tout dans un seul service / projet).  
   Utilisez le langage et framework de votre choix (Java/Spring Boot, Node.js/Express, Python/Flask, etc.).  
   
2. **Architecture microservices** :  
   Divisez ensuite cette application en 3 microservices :  
   - Service Livre  
   - Service Utilisateur  
   - Service Emprunt  

3. **Communication** :  
   Faites communiquer ces services via API REST. Vous pouvez simuler la communication sans déploiement réseau (ex : appels locaux, mocks).  

4. **Déploiement autonome** :  
   Simulez un déploiement autonome : par exemple, chaque microservice peut être démarré / arrêté indépendamment, éventuellement sur différents ports/processus.

#### Résultats attendus

- Le code source des deux versions (monolithique et microservices).  
- Un document court de comparaison (1 page) listant les points clés  
  - Facilité de modification/évolution  
  - Indépendance de déploiement  
  - Couplage entre composants  
  - Complexité de gestion  
  - Impact sur les performances possibles

---

### Partie 3 : Synthèse - Retour sur le QCM

Revenez à la question initiale du QCM.  
En vous basant sur votre expérience avec le mini projet, justifiez votre réponse.  
Explorez aussi les autres choix et pourquoi ils ne correspondent pas aux avantages principaux.

---

## Notes sur l’utilisation de l’IA

Votre usage d’outils d’IA (ChatGPT, Copilot, etc.) est autorisé pour :  
- Génération d’exemples de code  
- Explications conceptuelles  
- Aide à la rédaction  

**Attention** : Ne vous contentez pas de copier-coller ! Analysez les réponses aidées par l’IA, comprenez les concepts, et personnalisez votre travail. Le but est un apprentissage durable et la capacité critique.

---

## Ressources recommandées

- Article : Introduction aux microservices - Martin Fowler  
- Tutoriel REST API simple (selon votre langage préféré)  
- Documentation sur la communication interservices  

---

## Livrables

1. Code source des deux versions (monolithe et microservices)  
2. Document de comparaison (max 1 page)  
3. Réponses au QCM avec explications  

---

Bon travail et soyez curieux des choix d’architecture qui façonnent les systèmes modernes !