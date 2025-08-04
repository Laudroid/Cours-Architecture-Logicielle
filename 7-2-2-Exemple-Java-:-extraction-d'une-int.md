# Identifier les erreurs de conception et les corriger

## 2. Techniques de refactoring architectural

### 2. Exemple Java : extraction d'une interface pour découpler

Dans la pratique du développement logiciel, un problème fréquent est le **couplage fort** entre les composants. Cela complique la maintenance, les tests, et réduit la réutilisabilité du code. Une technique efficace pour **découpler les composants** est l’extraction d’une interface. Cette technique s’inscrit dans les bonnes pratiques architecturales recommandées pour améliorer la modularité et la flexibilité du code.

---

## Pourquoi extraire une interface ?

- **Séparer l’abstraction de l’implémentation** : En Java, une interface définit un contrat sans détailler la manière dont il est implémenté.
- **Faciliter le remplacement ou l’évolution d’implémentations** : Il est possible de faire évoluer les implémentations sans impacter les consommateurs de l’interface.
- **Améliorer la testabilité** : On peut facilement injecter des mocks ou stubs lors des tests unitaires.
- **Respecter le principe de l’Inversion des dépendances (D de SOLID)** : Les modules dépendent des abstractions et non des détails.

---

## Exemple concret en Java

Imaginons une application simple qui a un service d’envoi de notifications directement appelé dans une classe métier avec couplage fort :

```java
public class EmailService {
    public void sendEmail(String to, String msg) {
        // Code pour envoyer un email
        System.out.println("Envoi d'email à " + to + " avec le message : " + msg);
    }
}

public class UserService {
    private EmailService emailService = new EmailService();

    public void registerUser(String email) {
        // logique d’enregistrement utilisateur
        emailService.sendEmail(email, "Bienvenue !");
    }
}
```

### Limites ici :

- `UserService` connaît directement la classe concrète `EmailService`.
- Impossible de substituer facilement un autre service (par SMS, notification push…).
- Tests unitaires de `UserService` difficiles à isoler.

---

## Refactoring avec extraction d’une interface

### 1. Définir une interface abstraite

```java
public interface NotificationService {
    void send(String to, String message);
}
```

### 2. Adapter l'implémentation

```java
public class EmailService implements NotificationService {
    @Override
    public void send(String to, String message) {
        System.out.println("Envoi d'email à " + to + " avec le message : " + message);
    }
}
```

### 3. Modifier le service métier pour dépendre de l’interface

```java
public class UserService {
    private NotificationService notificationService;

    public UserService(NotificationService notificationService) {
        this.notificationService = notificationService;
    }

    public void registerUser(String email) {
        // logique d’enregistrement utilisateur
        notificationService.send(email, "Bienvenue !");
    }
}
```

### 4. Utilisation dans le code principal

```java
public class Main {
    public static void main(String[] args) {
        NotificationService emailService = new EmailService();
        UserService userService = new UserService(emailService);

        userService.registerUser("utilisateur@example.com");
    }
}
```

---

## Avantages de ce refactoring

- **Découplage statique** : `UserService` ne connaît plus que l’interface, pas l’implémentation concrète.
- **Extensibilité** : Ajouter un `SmsService` implémentant `NotificationService` est simple et ne modifie pas `UserService`.
- **Tests facilitée** : On peut injecter un mock de `NotificationService` pour tester `UserService`.

---

## Aller plus loin

Voici un exemple rapide d’implémentation pour un mock utilisé en test :

```java
public class MockNotificationService implements NotificationService {
    @Override
    public void send(String to, String message) {
        System.out.println("Mock : Simuler l’envoi à " + to);
    }
}
```

Dans un test unitaire, on peut injecter ce mock pour vérifier les appels sans envoyer d’emails réels.

---

## Références et ressources

- [Oracle Docs – Interfaces in Java](https://docs.oracle.com/javase/tutorial/java/IandI/createinterface.html)  
- [Baeldung – Guide to Dependency Injection in Java](https://www.baeldung.com/inversion-control-and-dependency-injection-in-spring)  
- [Martin Fowler – Dependency Injection](https://martinfowler.com/articles/injection.html)  
- [SOLID Principles Explained – Tutorialspoint](https://www.tutorialspoint.com/design_pattern/solid_principles.htm)

---

## Conclusion

L’extraction d’une interface est une technique de refactoring essentielle pour **découpler les composants**, respecter les principes SOLID et améliorer la flexibilité d’une application Java. Elle permet non seulement de préparer l’application à évoluer plus facilement, mais aussi de faciliter les tests et la maintenance.

---

**Intégrez cette pratique dans vos projets pour construire des logiciels plus propres, modulaires et évolutifs !**