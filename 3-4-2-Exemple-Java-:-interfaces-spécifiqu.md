# Concepts SOLID

## 4. Interface Segregation Principle (ISP)

### 2. Exemple Java : interfaces spécifiques plutôt qu'une interface générale trop large

Le **Interface Segregation Principle (ISP)** conseille aux développeurs de **préférer plusieurs interfaces spécifiques, plutôt qu’une interface générale trop large**. Ce principe permet de rendre le code plus propre, modulaire et facile à maintenir.

---

### Rappel rapide du principe ISP

> *Les clients ne doivent pas être forcés de dépendre d'interfaces qu'ils n'utilisent pas.*

En d’autres termes, une interface doit décrire un ensemble cohérent et minimaliste de fonctionnalités, adaptées aux besoins spécifiques d’un client.

---

### Pourquoi éviter une interface trop générale ?

Une interface générale contenant plusieurs méthodes que toutes les classes n’utilisent pas peut entraîner plusieurs problèmes :

- Classes contraintes d’implémenter des méthodes inutiles.
- Risque d’implémenter des méthodes avec un comportement par défaut ou d’exception, ce qui peut provoquer des bugs.
- Maintenance et compréhension plus difficiles, car les interfaces deviennent trop volumineuses.

---

### Exemple concret : gestion d’un périphérique multifonction en Java

Supposons qu’on crée une interface `ImprimanteToutEnUn` regroupant impression, numérisation et fax :

```java
public interface ImprimanteToutEnUn {
    void imprimer(Document doc);
    void scanner(Document doc);
    void faxer(Document doc);
}
```

---

#### Problème avec cette interface

Une classe représentant une imprimante simple, ne gérant que l’impression, devra tout de même implémenter toutes ces méthodes :

```java
public class ImprimanteBasique implements ImprimanteToutEnUn {

    @Override
    public void imprimer(Document doc) {
        System.out.println("Imprimer le document.");
    }

    @Override
    public void scanner(Document doc) {
        throw new UnsupportedOperationException("Scanner non supporté.");
    }

    @Override
    public void faxer(Document doc) {
        throw new UnsupportedOperationException("Fax non supporté.");
    }
}
```

Le comportement `UnsupportedOperationException` est un signal clair que la classe est forcée de dépendre d’une interface qu’elle n’utilise pas, ce qui contrevient au principe ISP.

---

### Mise en œuvre respectueuse du ISP : interfaces spécifiques

Une meilleure conception consiste à décomposer l’interface en interfaces plus petites, chacune représentant une fonctionnalité autonome :

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

---

#### Implémentation ciblée des classes

Les classes implémentent uniquement les interfaces correspondant à leurs capacités réelles :

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
        System.out.println("Numérisation.");
    }

    @Override
    public void faxer(Document doc) {
        System.out.println("Fax envoyé.");
    }
}
```

---

### Bénéfices concrets de cette approche

- Les classes ne dépendent que des méthodes dont elles ont réellement besoin.
- Réduction du code inutile ou à comportement factice.
- Code plus clair, plus compréhensible et plus facile à maintenir.
- Facilitation de l’évolution, en ajoutant de nouvelles fonctionnalités sans modification des anciennes.

---

### Références et ressources supplémentaires

- [Martin Fowler - Interface Segregation Principle](https://martinfowler.com/bliki/InterfaceSegregationPrinciple.html)  
- [GeeksforGeeks - Interface Segregation Principle in Java](https://www.geeksforgeeks.org/interface-segregation-principle-in-java/)  
- *Clean Architecture* de Robert C. Martin, une référence incontournable pour les architectures robustes.

---

### Conclusion

Le principe ISP est un guide précieux pour créer des interfaces justes, précises et adaptées aux besoins réels des clients. En préférant des interfaces fines plutôt qu’une interface générale et trop large, vous facilitez la lisibilité, la maintenance et l’évolution de votre logiciel.

Adoptez dès aujourd’hui l’**Interface Segregation Principle** pour améliorer la qualité de vos architectures logicielles !