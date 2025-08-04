**TP : Différenciation essentiel / accessoire dans une application bancaire**

---

### Objectif du TP
Comprendre et appliquer la notion de différenciation entre fonctionnalités essentielles et accessoires lors de la conception d'une application logicielle, ici dans le contexte d'une application bancaire.

---

### Contexte
Vous travaillez sur la conception d’une application mobile bancaire. Afin de prioriser le développement, il est important de distinguer les fonctionnalités essentielles, indispensables au fonctionnement de base de l’application, des fonctionnalités accessoires qui améliorent l’expérience utilisateur mais ne sont pas critiques au démarrage.

---

### Enoncé du TP
Vous devez analyser un ensemble de fonctionnalités présentées sous forme de QCM et déterminer lesquelles sont essentielles pour une application bancaire, et lesquelles peuvent être considérées comme accessoires.

---

### Liste des fonctionnalités :

1. **Authentification** (connexion sécurisée de l’utilisateur)
2. **Mode sombre** (affichage avec thème sombre pour réduction de la fatigue oculaire)
3. **Gestion des comptes** (consultation et modification des informations de compte, visualisation du solde)
4. **Notifications visuelles** (alertes visuelles pour événements, par ex. transaction suspecte)

---

### Travail à réaliser

1. **Phase 1 – Analyse individuelle :**

   - Répondez au QCM en cochant les fonctionnalités que vous considérez essentielles à la première version d’une application bancaire.
   - Justifiez brièvement votre choix en expliquant pourquoi chaque fonctionnalité cochée est essentielle, et pourquoi les autres sont accessoires.

2. **Phase 2 – Discussion en groupe :**

   - Comparez vos réponses et justifications avec celles de vos pairs.
   - Essayez de construire une définition commune des critères qui rendent une fonctionnalité essentielle ou accessoire dans ce contexte.

3. **Phase 3 – Mini projet de modélisation :**

   En vous appuyant sur votre sélection de fonctionnalités, réalisez :

   - Un diagramme de cas d'utilisation UML qui illustre les interactions principales entre utilisateurs (clients bancaires) et le système en mettant l’accent sur les fonctionnalités essentielles.
   - Un classement des fonctionnalités accompagné d’un bref compte-rendu expliquant votre choix du périmètre fonctionnel "essentiel" pour la première version.

---

### Ressources

- Rappel sur la notion de fonctionnalité essentielle vs accessoire
- Modèles simples de diagramme de cas d'utilisation (exemple UML)
- Outils recommandés (ex : draw.io, Lucidchart) ou papier-crayon

---

### Notes spécifiques au contexte IA

- Vous êtes encouragés à utiliser des outils d’IA pour vous aider à comprendre les notions, générer des diagrammes ou rédiger des justifications.
- Veillez cependant à toujours comprendre et valider par vous-même les réponses proposées par l’IA afin de développer vos compétences en esprit critique et conception logicielle.

---

### Exemple de correction possible

| Fonctionnalité         | Essentielle | Justification                                           |
|-----------------------|-------------|--------------------------------------------------------|
| Authentification      | Oui         | Garantit la sécurité et l’accès uniquement à l’utilisateur légitime |
| Mode sombre           | Non         | Améliore le confort mais n’impacte pas la fonctionnalité de base |
| Gestion des comptes   | Oui         | Permet de consulter et gérer les comptes, cœur de l’application bancaire |
| Notifications visuelles| Non / Oui*  | Utile pour informer, mais peut être mise en place après la version initiale |

(* Le caractère essentiel ou accessoire des notifications peut varier selon le contexte, mais on les considère souvent non essentielles au strict fonctionnement initial.)

---

### Durée estimée : 2h

---

**Bonne pratique :** Gardez toujours en mémoire que la différenciation essentiel/accessoire permet de maîtriser la complexité et d’optimiser les ressources lors du développement logiciel.