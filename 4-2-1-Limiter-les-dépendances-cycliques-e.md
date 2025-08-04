# Séparation des composants

## 2. Gestion des dépendances entre composants

### 1. Limiter les dépendances cycliques et privilégier les interfaces pour les échanges

Dans la conception de logiciels modulaires, la gestion des dépendances entre composants est essentielle pour garantir la maintenabilité, la compréhension et la qualité globale du système. Deux pratiques fondamentales pour cela sont **la limitation des dépendances cycliques** et **le recours aux interfaces pour faciliter les échanges entre composants**.

---

## Qu’est-ce qu’une dépendance cyclique ?

Une dépendance cyclique survient lorsque deux (ou plusieurs) composants dépendent directement ou indirectement l’un de l’autre, créant ainsi une boucle. Ce type de dépendance est problématique car :

- Il complique la compréhension du système.
- Il rend difficile la réutilisation indépendante des composants.
- Il crée des problèmes lors du processus de compilation ou de déploiement.
- Il augmente le couplage global rendant les changements risqués.

### Exemple simple de dépendance cyclique

Supposons deux classes `A` et `B` qui s’appellent mutuellement :

```java
public class A {
    private B b;

    public void methodeA() {
        b.methodeB();
    }
}

public class B {
    private A a;

    public void methodeB() {
        a.methodeA();
    }
}
```

Ici, `A` dépend de `B` et `B` dépend de `A`, formant un cycle.

---

## Pourquoi limiter ces cycles ?

- Découplage : rompre les cycles permet aux composants d’évoluer de manière plus autonome.
- Testabilité : facilite le test unitaire des composants isolés.
- Modifiabilité et réutilisation : réduit les effets d’une modification locale sur l’ensemble du système.

---

## Privilégier les interfaces pour les échanges

Une des solutions les plus efficaces pour limiter les dépendances cycliques est l’usage d’**interfaces**. Elles agissent comme des contrats abstraits que les composants peuvent utiliser sans connaître l’implémentation concrète.

### Avantages des interfaces

- **Faible couplage** : le composant A dépend d’une interface, pas d’une classe concrète.
- **Modularité améliorée** : permet de remplacer ou modifier une implémentation sans impacter le client.
- **Inversion des dépendances** (principe DIP) : les modules de haut niveau et bas niveau dépendent d’abstractions communes.

---

## Exemple Java illustrant l’utilisation d’interfaces pour éviter une dépendance cyclique

Supposons un système avec deux composants `GestionClient` et `GestionCommande` :

### Mauvaise pratique : dépendance cyclique entre classes concrètes

```java
public class GestionClient {
    private GestionCommande gestionCommande;

    public GestionClient(GestionCommande gestionCommande) {
        this.gestionCommande = gestionCommande;
    }

    public void notifierCommande() {
        gestionCommande.traiter();
    }
}

public class GestionCommande {
    private GestionClient gestionClient;

    public GestionCommande(GestionClient gestionClient) {
        this.gestionClient = gestionClient;
    }

    public void traiter() {
        System.out.println("Traitement commande");
    }
}
```

Ici, les deux classes dépendent directement l’une de l’autre : dépendance cyclique.

---

### Solution avec interfaces et injections

Définissons d’abord des interfaces :

```java
public interface INotificateurCommande {
    void notifierCommande();
}

public interface ITraitementCommande {
    void traiter();
}
```

Puis les classes implémentent ces interfaces sans dépendance mutuelle :

```java
public class GestionClient implements INotificateurCommande {
    private ITraitementCommande traitementCommande;

    public GestionClient(ITraitementCommande traitementCommande) {
        this.traitementCommande = traitementCommande;
    }

    @Override
    public void notifierCommande() {
        traitementCommande.traiter();
    }
}

public class GestionCommande implements ITraitementCommande {
    @Override
    public void traiter() {
        System.out.println("Traitement de la commande");
    }
}
```

Le `GestionClient` dépend uniquement de l’abstraction `ITraitementCommande`, pas de l’implémentation concrète `GestionCommande`. Cette dernière n’a aucune connaissance de `GestionClient`, rompant ainsi la dépendance cyclique.

---

## Résumé des bonnes pratiques

- **Détecter et éliminer systématiquement les dépendances cycliques.**
- **Utiliser des interfaces pour abstraire les interactions entre composants.**
- **Découpler les composants grâce à l’injection de dépendances ou autres mécanismes.**
- **Respecter les principes SOLID, notamment le Dependency Inversion Principle (DIP), pour guider la conception.**

---

## Ressources et lectures complémentaires

- [Martin Fowler - Circular Dependencies](https://martinfowler.com/bliki/CircularDependency.html)  
- [Clean Code - Robert C. Martin - Chapitre sur les dépendances](https://www.oreilly.com/library/view/clean-code/9780136083238/)  
- [Baeldung - Dependency Cycle in Java](https://www.baeldung.com/circular-dependencies)  
- [InfoQ - Managing Module Dependencies](https://www.infoq.com/articles/managing-module-dependencies/)

---

## Conclusion

Limiter les dépendances cycliques et privilégier les interfaces pour les échanges entre composants sont des leviers puissants pour construire des applications découplées, testables et évolutives. Ces pratiques facilitent non seulement la maintenance mais aussi la compréhension du système.

Incorporez ces principes dans votre démarche de conception pour améliorer la qualité de vos logiciels et préparer votre architecture aux futurs changements.

---

**Construisez des logiciels plus robustes en maîtrisant vos dépendances dès aujourd’hui !**