# Concepts SOLID

## 3. Liskov Substitution Principle (LSP)

### 3. Exemple simple en Java avec classes `Animal`, `Chat` et `Chien`

Le **Liskov Substitution Principle (LSP)** est l’un des principes fondamentaux des bonnes pratiques en programmation orientée objet. Il garantit que les instances des sous-classes puissent remplacer celles de la classe de base sans perturber le comportement attendu.

Pour illustrer ce principe, étudions un exemple minimaliste en Java avec une classe `Animal` et deux classes dérivées `Chat` et `Chien`.

---

### Définition de la classe de base `Animal`

```java
public class Animal {
    public void deplacer() {
        System.out.println("L'animal se déplace.");
    }
}
```

Dans ce code, la méthode `deplacer` définit un comportement générique partagé par tous les animaux : ils peuvent se déplacer.

---

### Classes dérivées vides : `Chat` et `Chien`

```java
public class Chat extends Animal { }

public class Chien extends Animal { }
```

Ici, `Chat` et `Chien` héritent de `Animal` sans modifier ni redéfinir la méthode `deplacer`. Elles héritent donc du comportement par défaut.

---

### Utilisation et respect du LSP

On peut créer des instances des sous-classes et utiliser la méthode `deplacer` comme prévu :

```java
public class Main {
    public static void deplacerAnimal(Animal animal) {
        animal.deplacer();
    }

    public static void main(String[] args) {
        Animal monChat = new Chat();
        Animal monChien = new Chien();

        deplacerAnimal(monChat);   // Affiche : L'animal se déplace.
        deplacerAnimal(monChien);  // Affiche : L'animal se déplace.
    }
}
```

Grâce à l’héritage intact, le LSP est respecté :

- `Chat` et `Chien` peuvent remplacer `Animal` sans nécessiter de modification du code appelant.
- Le comportement reste cohérent et prévisible.

---

### Étendre le comportement en respectant le LSP

Si l’on souhaite enrichir le comportement propre à chaque animal, on peut surcharger la méthode `deplacer` :

```java
public class Chat extends Animal {
    @Override
    public void deplacer() {
        System.out.println("Le chat marche silencieusement.");
    }
}

public class Chien extends Animal {
    @Override
    public void deplacer() {
        System.out.println("Le chien court joyeusement.");
    }
}
```

Le programme principal reste fonctionnel sans changement, et le comportement est adapté à chaque sous-classe, démontrant une application parfaite du LSP.

---

### Pourquoi le LSP est-il important ?

- **Coopérabilité entre classes** : Permet la substitution d’objets sans surprises.
- **Extensibilité** : Facilite l’ajout de nouvelles sous-classes sans modifier le code existant.
- **Maintenance facilitée** : Réduit le risque d’introduire des bugs dans les classes de base.

---

### Références et approfondissements

- [Martin Fowler - Open/Closed and Liskov Substitution Principle](https://martinfowler.com/bliki/LiskovSubstitutionPrinciple.html)  
- [Liskov Substitution Principle - Wikipedia](https://fr.wikipedia.org/wiki/Principe_de_substitution_de_Liskov)  
- *Clean Code* de Robert C. Martin — Explications détaillées des principes SOLID.

---

### Résumé

L'exemple Java basique avec la classe `Animal` et ses sous-classes `Chat` et `Chien` illustre clairement le principe de substitution de Liskov : une hiérarchie d’héritage doit permettre d’utiliser les objets dérivés où qu'un objet de la classe mère soit attendu, sans changement du comportement ou de la structure du programme.

Maîtriser ce principe est indispensable pour concevoir des applications orientées objet propres, évolutives, et robustes.

---

Adopter le LSP est un pas solide vers une architecture logicielle respectueuse des bonnes pratiques et prête à évoluer sans douleur.