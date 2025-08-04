# Principes de conception

## 1. Principe de séparation des préoccupations

### 2. Exemple Java : séparation des classes de gestion métier et d'interface utilisateur (code commenté)

Le principe de séparation des préoccupations recommande de diviser un logiciel en modules ou classes qui gèrent chacun une responsabilité spécifique. En Java, cela se traduit fréquemment par la séparation entre les classes dédiées à la **gestion métier** (logique fonctionnelle) et celles responsables de l’**interface utilisateur** (affichage, interactions).

---

### Pourquoi séparer gestion métier et interface utilisateur ?

Cette séparation permet de simplifier le développement, la maintenance et l’évolution de chaque partie indépendamment. Modifier la logique métier ne doit pas nécessiter de changer le code d’affichage, et vice versa. De plus, cela favorise la testabilité et la réutilisation des composants métiers dans différentes interfaces.

---

### Exemple simple en Java

Imaginons une application Java qui affiche des informations sur un compte bancaire.

#### Classe de gestion métier : Account.java

```java
// Classe représentant un compte bancaire avec gestion des opérations simples
public class Account {
    private String owner;
    private double balance;

    public Account(String owner, double initialBalance) {
        this.owner = owner;
        this.balance = initialBalance;
    }

    // Méthode pour déposer de l'argent sur le compte
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    // Méthode pour retirer de l'argent, avec vérification du solde
    public boolean withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            return true;
        }
        return false;
    }

    public String getOwner() {
        return owner;
    }

    public double getBalance() {
        return balance;
    }
}
```

#### Classe d’interface utilisateur : AccountUI.java

```java
import java.util.Scanner;

// Classe responsable de l'interaction avec l'utilisateur
public class AccountUI {
    private Account account;
    private Scanner scanner;

    public AccountUI(Account account) {
        this.account = account;
        this.scanner = new Scanner(System.in);
    }

    // Méthode pour afficher le menu et gérer les choix utilisateur
    public void displayMenu() {
        while (true) {
            System.out.println("Compte de : " + account.getOwner());
            System.out.println("Solde actuel : " + account.getBalance());
            System.out.println("1 - Déposer de l'argent");
            System.out.println("2 - Retirer de l'argent");
            System.out.println("3 - Quitter");
            System.out.print("Choisissez une option: ");

            int choix = scanner.nextInt();
            switch (choix) {
                case 1:
                    deposit();
                    break;
                case 2:
                    withdraw();
                    break;
                case 3:
                    System.out.println("Au revoir !");
                    return;
                default:
                    System.out.println("Option invalide.");
            }
        }
    }

    private void deposit() {
        System.out.print("Montant à déposer: ");
        double amount = scanner.nextDouble();
        account.deposit(amount);
        System.out.println("Dépôt effectué.");
    }

    private void withdraw() {
        System.out.print("Montant à retirer: ");
        double amount = scanner.nextDouble();
        if (account.withdraw(amount)) {
            System.out.println("Retrait effectué.");
        } else {
            System.out.println("Fonds insuffisants.");
        }
    }
}
```

#### Classe principale pour lancer l’application

```java
public class Main {
    public static void main(String[] args) {
        Account account = new Account("Alice", 1000);
        AccountUI ui = new AccountUI(account);
        ui.displayMenu();
    }
}
```

---

### Ce que cet exemple illustre

- La **classe `Account`** gère la logique métier liée au compte bancaire : dépôt, retrait, consultation du solde.
- La **classe `AccountUI`** s’occupe uniquement de l’interaction avec l’utilisateur : afficher le menu, récupérer les entrées, afficher les résultats.
- Cette séparation permet de modifier, tester ou remplacer la partie interface sans toucher à la logique métier, et vice versa.

---

### Références et ressources complémentaires

- [Oracle Documentation - Separation of Concerns](https://docs.oracle.com/javase/tutorial/java/concepts/interface.html) explique les bonnes pratiques de division des responsabilités en Java.
- Le [Design Pattern MVC (Model-View-Controller)](https://refactoring.guru/fr/design-patterns/mvc) est un exemple avancé de séparation des préoccupations appliqué à la GUI.
- Sur [GeeksforGeeks](https://www.geeksforgeeks.org/separation-of-concerns-in-software-engineering/), vous trouverez une introduction détaillée au principe de séparation des préoccupations et des exemples pratiques.

---

### En résumé

La séparation des classes de gestion métier et d’interface utilisateur est une illustration concrète du principe de séparation des préoccupations en programmation Java. Cela rend le code plus propre, plus facile à maintenir et à faire évoluer, et améliore la qualité globale du logiciel.

---

Cet article vous a permis de découvrir un exemple pratique de mise en œuvre du principe fondamental qu’est la séparation des préoccupations, clé d’une bonne conception logicielle.