# Concepts SOLID

## 3. Liskov Substitution Principle (LSP)

### 1. Les objets d'une classe dérivée doivent pouvoir remplacer les objets de la classe de base sans altérer le comportement attendu

Le **Liskov Substitution Principle (LSP)** est l'un des cinq principes SOLID définis pour améliorer la qualité et la maintenabilité de la conception logicielle. Il a été formulé par Barbara Liskov en 1987 et joue un rôle fondamental dans la programmation orientée objet.

---

### Qu’est-ce que le LSP ?

Le principe stipule que :

> *"Les objets d'une classe dérivée doivent pouvoir remplacer les objets de la classe de base sans altérer le comportement attendu du programme."*

Autrement dit, une instance d’une sous-classe doit pouvoir être utilisée partout où une instance de la classe parente est attendue, sans provoquer d'erreurs ni de comportements inattendus.

---

### Pourquoi ce principe est-il important ?

Respecter le LSP garantit la **cohérence**, la **prévisibilité** et la **fiabilité** du code lorsqu'il utilise l’héritage. Si une sous-classe ne respecte pas le comportement de sa classe de base, cela peut causer des bugs subtils difficiles à détecter.

Le LSP est clé pour construire des systèmes **flexibles** et **extensibles**, capables d’évoluer sans casser les parties existantes.

---

### Exemple simple en Java

Imaginons une classe de base `Oiseau` avec une méthode `voler()` :

```java
public class Oiseau {
    public void voler() {
        System.out.println("L'oiseau vole.");
    }
}
```

Une sous-classe `Aigle` peut hériter de `Oiseau` et redéfinir `voler` :

```java
public class Aigle extends Oiseau {
    @Override
    public void voler() {
        System.out.println("L'aigle vole haut dans le ciel.");
    }
}
```

Cela fonctionne parfaitement car `Aigle` respecte le comportement attendu : il vole.

---

### Violation du LSP : exemple classique du rectangle et du carré

Prenons une autre hiérarchie :

```java
public class Rectangle {
    protected int largeur;
    protected int hauteur;

    public void setLargeur(int largeur) {
        this.largeur = largeur;
    }

    public void setHauteur(int hauteur) {
        this.hauteur = hauteur;
    }

    public int getSurface() {
        return largeur * hauteur;
    }
}

public class Carre extends Rectangle {
    @Override
    public void setLargeur(int largeur) {
        this.largeur = largeur;
        this.hauteur = largeur;  // côté égal à la largeur
    }

    @Override
    public void setHauteur(int hauteur) {
        this.hauteur = hauteur;
        this.largeur = hauteur;  // côté égal à la hauteur
    }
}
```

Ici, `Carre` est une sous-classe de `Rectangle`. Mais si on utilise le code suivant :

```java
public static void main(String[] args) {
    Rectangle r = new Carre();
    r.setLargeur(5);
    r.setHauteur(10);
    System.out.println("Surface attendue : 50, calculée : " + r.getSurface());
}
```

Le résultat ne correspond pas à ce qui est attendu (surface = 100 au lieu de 50), car la modification d’un côté modifie aussi l’autre dans la classe `Carre`. Cette incohérence viole le LSP, car `Carre` ne peut pas remplacer un `Rectangle` sans changer le comportement logique.

---

### Comment respecter le LSP ?

- **Ne pas modifier les comportements attendus** dans les sous-classes.
- Si une sous-classe ne peut pas respecter le contrat de la classe parente, il est préférable de ne pas utiliser l'héritage.
- Utiliser la composition plutôt que l’héritage lorsque la hiérarchie ne correspond pas à un véritable "est-un".

---

### Références utiles

- [Liskov Substitution Principle - Martin Fowler](https://martinfowler.com/bliki/LiskovSubstitutionPrinciple.html)  
- Article Wikipedia [Liskov Substitution Principle](https://fr.wikipedia.org/wiki/Principe_de_substitution_de_Liskov)  
- *Clean Code* et *Agile Software Development* de Robert C. Martin, pour approfondir les principes SOLID.

---

### En résumé

Le **Liskov Substitution Principle** guide la conception en orienté objet pour s’assurer que les sous-classes peuvent remplacer leurs classes parentes sans introduire d’erreurs ni de changements inattendus dans le comportement. Cela améliore grandement la fiabilité du code et facilite son évolution.

---

En intégrant ce principe dans vos développements, vous construisez des logiciels plus robustes, évolutifs et respectueux des attentes métier et techniques. C’est une étape incontournable pour devenir un architecte logiciel compétent.