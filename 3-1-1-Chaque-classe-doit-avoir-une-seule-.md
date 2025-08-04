# Concepts SOLID

## 1. Single Responsibility Principle (SRP)

### 1. Chaque classe doit avoir une seule responsabilité et donc une seule raison de changer

Le **Single Responsibility Principle (SRP)** est l’un des cinq principes SOLID, fondamentaux pour une bonne conception logicielle. Il stipule qu’une classe doit avoir une unique responsabilité, c’est-à-dire qu’elle doit se concentrer sur une seule fonctionnalité ou un seul aspect du système. Cette simplicité lui confère une **raison unique de changer**.

---

### Pourquoi ce principe est-il important ?

Quand une classe remplit plusieurs responsabilités, plusieurs problèmes apparaissent :

- **Maintenance difficile :** Une modification liée à une responsabilité peut impacter d’autres fonctions non reliées, ce qui complique la compréhension et la modification.
- **Faible réutilisabilité :** Une classe trop polyvalente est difficile à réutiliser dans un contexte différent.
- **Tests compliqués :** Tester une classe qui fait trop de choses nécessite des scénarios plus complexes.

Suivre le SRP permet de concevoir des composants **clairs**, **faciles à comprendre**, et **plus robustes**.

---

### Illustration par un exemple simple en Java

Supposons une classe qui gère à la fois la logique métier et l’envoi d’emails :

```java
public class UserManager {
    public void addUser(String username) {
        // Ajouter l'utilisateur à la base de données
        System.out.println("User " + username + " added to the database.");

        // Envoyer un email de bienvenue
        sendWelcomeEmail(username);
    }

    private void sendWelcomeEmail(String username) {
        System.out.println("Email de bienvenue envoyé à " + username);
    }
}
```

#### Quels problèmes ?

- La classe gère à la fois la persistance des données (`addUser`) et la communication (`sendWelcomeEmail`).
- Si la manière de stocker les utilisateurs change, la classe doit être modifiée.
- Si la procédure d’email évolue, cela impacte aussi cette classe multifonctions.

---

### Application du SRP : séparation des responsabilités

On divise la classe en deux :

```java
public class UserManager {
    private EmailService emailService;

    public UserManager(EmailService emailService) {
        this.emailService = emailService;
    }

    public void addUser(String username) {
        // Ajouter l'utilisateur à la base de données
        System.out.println("User " + username + " added to the database.");

        // Déléguer l'envoi d'email à EmailService
        emailService.sendWelcomeEmail(username);
    }
}

public class EmailService {
    public void sendWelcomeEmail(String username) {
        System.out.println("Email de bienvenue envoyé à " + username);
    }
}
```

Ici :

- La classe `UserManager` ne s’occupe que de la gestion des utilisateurs.
- La classe `EmailService` prend en charge l’envoi des emails.

Chaque classe a une responsabilité claire, donc une raison unique de changer.

---

### Références et ressources

- [What is the Single Responsibility Principle? – Microsoft Docs](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/srp-single-responsibility-principle)  
- [Martin Fowler – Single Responsibility Principle](https://martinfowler.com/bliki/SingleResponsibilityPrinciple.html)  
- *Clean Architecture* par Robert C. Martin, une référence incontournable en conception orientée objet.

---

### En résumé

Le **Single Responsibility Principle** est un principe clé pour concevoir des classes simples, maintenables et robustes. En donnant à chaque classe une seule responsabilité, on s’assure qu’elle aura une unique raison de changer. Cela réduit le couplage, améliore la lisibilité du code, et facilite les tests.

---

Cet article vous a permis de comprendre et d’illustrer le SRP, un pilier des bonnes pratiques de conception orientée objet, indispensable pour toute personne souhaitant produire des logiciels de qualité.