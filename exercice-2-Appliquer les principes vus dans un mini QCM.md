---
# TP : Application des principes de conception à travers un mini QCM

## Objectif du TP  
L'objectif de ce TP est de permettre aux apprenants de s'approprier les principes fondamentaux de conception logicielle, à travers la réalisation d’un mini QCM. Ils devront comprendre les principes proposés, justifier leurs choix, et coder une petite application mettant en œuvre ces notions. Ce TP favorise à la fois la réflexion, la recherche et la mise en pratique.

---

## Énoncé du TP  

Vous devez créer une application en ligne de commande (ou web simple) qui propose un QCM autour des principes de conception logicielle — un mini quiz interactif.

Le QCM portera sur la question suivante :

> **Q : Quel principe de conception recommande d'avoir une seule raison de changer pour une classe ?**

Choix proposés :  
1. DRY  
2. Responsabilité unique  
3. Open/Closed  
4. Principe de substitution de Liskov  

Les apprenants doivent :  

- Afficher la question et les réponses.  
- Laisser l’utilisateur répondre par le numéro de la proposition.  
- Indiquer si la réponse est correcte ou non.  
- Afficher une explication claire (quelle que soit la réponse donnée).  

---

## Consignes pédagogiques et bonnes pratiques  

1. **Principe de responsabilité unique**  
   La bonne réponse est **2. Responsabilité unique** (Single Responsibility Principle, SRP).  
   Ce principe recommande qu'une classe ait une unique raison de changer, ce qui améliore la maintenabilité et la clarté.  

2. **Permettre à l’apprenant d’expliquer son raisonnement**  
   Après l’affichage de la correction, le programme doit inviter l’utilisateur à saisir un court texte expliquant pourquoi le choix est correct ou incorrect (même s’il s’est trompé). Ceci encourage la réflexion et la formalisation des connaissances.

3. **Utilisation pédagogique de l’IA**  
   L’utilisation d’outils d’IA pour aider au codage ou à la recherche n’est pas un problème. Toutefois, les étudiants doivent s’efforcer de comprendre les résultats fournis et personnaliser leur code pour bien assimiler les notions de conception.

4. **Structure logicielle**  
   Le code doit être organisé en suivant un principe simple (par exemple organisation en classes, ou modules selon le langage). Cette structure doit illustrer un principe de conception (par exemple le SRP en séparant la logique d’affichage et la logique métier).

---

## Étapes recommandées pour le TP  

1. **Définition du modèle**  
   Créer une classe `Question` ou analogue contenant :  
   - le texte de la question,  
   - la liste des propositions,  
   - l’indice de la bonne réponse,  
   - une méthode pour afficher la question.  

2. **Gestion du QCM**  
   Créer une classe `Quiz` qui stocke les questions, récupère la réponse utilisateur, vérifie la validité, et affiche la correction + explication.  

3. **Exécution**  
   Dans la fonction principale, initialiser le quiz avec la question donnée et lancer la boucle d’interaction avec l’utilisateur.  

---

## Exemple d’explication à afficher (peut être enrichie par l’apprenant)  

> « Le principe de responsabilité unique (SRP) veut que chaque classe ne soit responsable que d’une seule chose et n’ait qu’une seule raison de changer. Cela facilite la maintenance et l’évolutivité du logiciel. Les autres principes proposés traitent d’autres aspects : DRY concerne la duplication de code, Open/Closed recommande que les entités soient ouvertes à l’extension mais fermées à la modification, et le principe de substitution de Liskov garantit que les sous-classes remplacent leurs superclasses sans altérer le comportement attendu. »

---

## Livrables attendus  

- Code source du mini QCM.  
- Courte documentation expliquant l’organisation du code et la mise en œuvre du principe de responsabilité unique.  
- Retour personnel sur la difficulté rencontrée et la compréhension du principe.  

---

**Bon travail et pensez à bien vous approprier la notion de conception derrière cet exercice !**