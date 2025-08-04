# Concepts SOLID

## 3. Liskov Substitution Principle (LSP)

### 2. Exemple Java avec classe `Animal` et classes dérivées `Chat` et `Chien`

Le **Liskov Substitution Principle (LSP)** est un pilier essentiel de la programmation orientée objet, garantissant que les sous-classes peuvent remplacer leurs classes parentes sans modifier le comportement attendu d’un programme.

Pour bien comprendre ce principe, voyons un exemple concret en Java avec une classe de base `Animal` et deux classes dérivées `Chat` et `Chien`.

---

### Rappel du principe LSP

> *Les objets d'une classe dérivée doivent pouvoir remplacer les objets de la classe de base sans altérer le comportement attendu.*

Cela veut dire qu’une instance d’une sous-classe doit pouvoir être utilisée partout où une instance de la classe parente est attendue, sans casser la logique ou provoquer des effets inattendus.

---

### Définition de la classe de base `Animal`

```java
public abstract class Animal {
    public abstract void emettreSon();

    public void seDeplacer() {
        System.out.println("L'animal se déplace.");
    }
}
```

Ici, `Animal` est une classe abstraite avec une méthode abstraite `emettreSon()` que chaque sous-classe doit implémenter, et une méthode concrète `seDeplacer()`.

---

### Classes dérivées `Chat` et `Chien`

```java
public class Chat extends Animal {
    @Override
    public void emettreSon() {
        System.out.println("Le chat miaule.");
    }
}

public class Chien extends Animal {
    @Override
    public void emettreSon() {
        System.out.println("Le chien aboie.");
    }
}
```

Chaque classe dérivée fournit sa propre implementation de la méthode `emettreSon()`, sans modifier la méthode `seDeplacer()` de la classe de base.

---

### Utilisation polymorphique dans un programme principal

```java
public class Main {
    public static void faireEmettreSon(Animal animal) {
        animal.emettreSon();
        animal.seDeplacer();
    }

    public static void main(String[] args) {
        Animal monChat = new Chat();
        Animal monChien = new Chien();

        faireEmettreSon(monChat);   // Affiche : Le chat miaule. + L'animal se déplace.
        faireEmettreSon(monChien);  // Affiche : Le chien aboie. + L'animal se déplace.
    }
}
```

---

### Respect du LSP dans cet exemple

- La fonction `faireEmettreSon` accepte un objet de type `Animal`.
- Elle peut recevoir indifféremment des objets `Chat` ou `Chien`.
- Le comportement observé correspond toujours aux attentes définies par la classe `Animal`.
- Il n’y a aucune surprise ou effet déstabilisant sur le programme.

Toutes les sous-classes peuvent remplacer la classe de base sans compromettre la cohérence.

---

### Ce qu’il faut éviter pour ne pas violer le LSP

- Modifier l’état interne de la classe de manière inattendue.
- Changer ou restreindre les invariants de la classe parente.
- Lancer des exceptions non prévues dans les sous-classes.
- Introduire des comportements incompatibles avec la classe de base.

---

### Références et ressources pour approfondir

- [Liskov Substitution Principle - martinFowler.com](https://martinfowler.com/bliki/LiskovSubstitutionPrinciple.html)  
- *Head First Design Patterns* par Eric Freeman et Elisabeth Robson — exemple concret de LSP en Java  
- *Clean Code* de Robert C. Martin — notions clés pour coder proprement en respectant les principes SOLID.

---

### En résumé

Le principe de substitution de Liskov garantit que les sous-classes soient de véritables extensions fiables de leurs classes parentes. L’exemple Java avec `Animal`, `Chat`, et `Chien` montre comment on peut concevoir des hiérarchies de classes respectueuses du LSP : les sous-classes peuvent être utilisées partout où la classe de base est attendue, sans perturber le fonctionnement du code.

Ce principe est fondamental pour écrire des programmes évolutifs, robustes et maintenables dans un contexte orienté objet.

---

Intégrez le LSP dans vos pratiques pour rendre vos architectures plus solides et compréhensibles !