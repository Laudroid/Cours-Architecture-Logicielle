# Concepts SOLID

## 4. Interface Segregation Principle (ISP)

### 1. Les clients ne doivent pas être forcés de dépendre d'interfaces qu'ils n'utilisent pas

Le **Interface Segregation Principle (ISP)** est le quatrième principe des cinq principes SOLID, largement reconnus pour guider les bonnes pratiques en conception logicielle. Ce principe met l'accent sur la conception d’interfaces spécifiques et adaptées afin de réduire la dépendance inutile entre les composants logiciels.

---

### Comprendre le principe ISP

Le principe se formule ainsi :

> *Les clients ne doivent pas être forcés de dépendre d'interfaces qu'ils n'utilisent pas.*

Autrement dit, une classe ne doit pas être contrainte à implémenter des méthodes dont elle n’a pas besoin. Cela permet de réduire la complexité, d’éviter d’introduire du code redondant ou inutile et de faciliter la maintenance.

---

### Pourquoi ce principe est-il essentiel ?

- **Réduction du couplage** : Moins une classe dépend de méthodes inutilisées, moins elle est sensible aux changements.
- **Flexibilité accrue** : Les interfaces précises permettent de faire évoluer plus facilement chaque partie du code.
- **Clarté et simplicité** : Les interfaces deviennent plus lisibles et reflètent mieux les responsabilités réelles des classes.

---

### Exemple illustratif en Java

Imaginons un système de gestion d’imprimantes multifonctions qui proposent des fonctionnalités diverses : impression, numérisation, fax.

---

#### Mauvaise conception : interface unique trop grande

```java
public interface ImprimanteToutEnUn {
    void imprimer(Document doc);
    void scanner(Document doc);
    void faxer(Document doc);
}
```

Toutes les fonctionnalités sont regroupées dans une seule interface. Un client ayant uniquement besoin d’imprimer doit malgré tout implémenter (ou supporter) les méthodes de numérisation et fax.

---

#### Classes concrètes

```java
// Imprimante basique ne gérant que l'impression
public class ImprimanteBasique implements ImprimanteToutEnUn {
    @Override
    public void imprimer(Document doc) {
        System.out.println("Impression du document.");
    }
    @Override
    public void scanner(Document doc) {
        // Non supporté mais doit être implémenté quand même
        throw new UnsupportedOperationException();
    }
    @Override
    public void faxer(Document doc) {
        throw new UnsupportedOperationException();
    }
}
```

Ce design force la classe `ImprimanteBasique` à dépendre d’interfaces qu’elle n’utilise pas, ce qui est une violation directe du **ISP**.

---

### Solution correcte : interfaces spécifiques

Il est préférable de décomposer l’interface en plusieurs interfaces plus fines et cohérentes :

```java
public interface IImpression {
    void imprimer(Document doc);
}

public interface IScan {
    void scanner(Document doc);
}

public interface IFax {
    void faxer(Document doc);
}
```

Les classes implémenteront uniquement les interfaces nécessaires :

```java
public class ImprimanteBasique implements IImpression {
    @Override
    public void imprimer(Document doc) {
        System.out.println("Impression du document.");
    }
}

public class ImprimanteMultifonction implements IImpression, IScan, IFax {
    @Override
    public void imprimer(Document doc) {
        System.out.println("Impression.");
    }
    @Override
    public void scanner(Document doc) {
        System.out.println("Scan.");
    }
    @Override
    public void faxer(Document doc) {
        System.out.println("Fax.");
    }
}
```

---

### Avantages de cette approche

- Chaque classe implémente uniquement ce qu’elle utilise réellement.
- Le code est plus simple à comprendre, maintenir et tester.
- Les changements sont localisés, ce qui réduit le risque de régressions.

---

### Références et ressources utiles

- [Interface Segregation Principle - Martin Fowler](https://martinfowler.com/bliki/InterfaceSegregationPrinciple.html)  
- [ISP et principes SOLID - GeeksforGeeks](https://www.geeksforgeeks.org/interface-segregation-principle-in-java/)  
- *Clean Architecture* de Robert C. Martin — une référence incontournable pour comprendre et appliquer les principes SOLID.

---

### Conclusion

Le **Interface Segregation Principle** nous enseigne à **privilégier des interfaces granulaires et spécifiques** plutôt que des interfaces volumineuses et généralistes. Ce principe garantit ainsi que les clients ne dépendent que des méthodes qui leur sont réellement utiles, rendant les architectures plus robustes, propres et faciles à faire évoluer.

---

Adoptez l’ISP pour écrire un code plus clair, plus modulaire, et plus maintenable dans vos projets logiciels !