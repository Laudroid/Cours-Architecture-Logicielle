# Concepts SOLID

## 2. Open/Closed Principle (OCP)

### 1. Les entités doivent être ouvertes à l'extension mais fermées à la modification

Le **Open/Closed Principle (OCP)** est le deuxième principe du groupe SOLID, un ensemble de recommandations destinées à améliorer la qualité et la maintenabilité du code. L’OCP affirme que :

> **"Les entités logicielles (classes, modules, fonctions, etc.) doivent être ouvertes à l’extension, mais fermées à la modification."**

Autrement dit, vous devez pouvoir modifier le comportement d’une entité sans altérer son code source existant.

---

### Pourquoi appliquer l’OCP ?

Modifier une entité directement peut entraîner des régressions, casser d'autres fonctionnalités, et compliquer la maintenance. En suivant l’OCP, la stabilité du code est mieux assurée, et on facilite son évolution.

L’idée est d’anticiper les évolutions en concevant un système **extensible** via l’ajout de nouveau code plutôt que la modification d’un code éprouvé.

---

### Illustration conceptuelle

- **Ouvert à l’extension** : on peut ajouter de nouvelles fonctionnalités ou comportements.
- **Fermé à la modification** : on évite de toucher au code déjà testé et en production.

---

### Exemple en Java : gestion de différentes formes et calcul de leur surface

#### Sans OCP (code à modifier lors de chaque ajout de forme)

```java
public class CalculSurface {
    public double calculerSurface(Object forme) {
        if (forme instanceof Cercle) {
            Cercle cercle = (Cercle) forme;
            return Math.PI * cercle.getRayon() * cercle.getRayon();
        } else if (forme instanceof Rectangle) {
            Rectangle rectangle = (Rectangle) forme;
            return rectangle.getLongueur() * rectangle.getLargeur();
        }
        // ajout d'une nouvelle forme nécessite de modifier cette méthode
        return 0;
    }
}
```

Le problème ici est clair : lorsqu’on veut ajouter un nouveau type de forme, on doit modifier `CalculSurface`, ce qui viole l’OCP.

---

#### Avec OCP (code extensible sans modification)

On commence par créer une interface ou classe abstraite que toutes les formes vont implémenter :

```java
public interface Forme {
    double calculerSurface();
}

public class Cercle implements Forme {
    private double rayon;
    public Cercle(double rayon) {
        this.rayon = rayon;
    }
    public double getRayon() { return rayon; }
    @Override
    public double calculerSurface() {
        return Math.PI * rayon * rayon;
    }
}

public class Rectangle implements Forme {
    private double longueur;
    private double largeur;
    public Rectangle(double longueur, double largeur) {
        this.longueur = longueur;
        this.largeur = largeur;
    }
    public double getLongueur() { return longueur; }
    public double getLargeur() { return largeur; }
    @Override
    public double calculerSurface() {
        return longueur * largeur;
    }
}
```

Le calcul des surfaces devient très simple :

```java
public class CalculSurface {
    public double calculerSurface(Forme forme) {
        return forme.calculerSurface();
    }
}
```

Lorsqu’une nouvelle forme est créée (par exemple, un triangle), il suffit d’implémenter l’interface `Forme` avec sa propre méthode `calculerSurface()` sans modifier `CalculSurface`.

---

### Avantages de ce principe

- **Facilité d’évolution** du logiciel sans risque de casse.
- **Respect du principe de fermeture** pour améliorer la robustesse.
- **Clarification de la structure** avec des abstractions et des implémentations spécifiques.

---

### Références et ressources complémentaires

- [Open/Closed Principle - Martin Fowler](https://martinfowler.com/bliki/OpenClosedPrinciple.html)  
- [Guide du principe OCP - TutorialsPoint](https://www.tutorialspoint.com/design_pattern/open_closed_principle.htm)  
- *Clean Code* de Robert C. Martin : chapitre clé sur les principes SOLID.

---

### En résumé

Le **Open/Closed Principle (OCP)** est un guide essentiel permettant de concevoir des applications évolutives. En rendant vos entités ouvertes à l’extension (via l’héritage, l’implémentation d’interfaces ou d’abstractions), mais fermées à la modification, vous limitez les risques et facilitez la maintenabilité.

---

Cet article vous a permis de découvrir ce principe fondamental à travers un exemple concret qui vous aidera à mieux organiser votre code pour des projets évolutifs et robustes.