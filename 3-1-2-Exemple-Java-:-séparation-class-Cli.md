# Concepts SOLID

## 1. Single Responsibility Principle (SRP)

### 2. Exemple Java : séparation des classes `ClientManager` et `ClientReport`

Le **Single Responsibility Principle (SRP)** affirme que chaque classe ne doit avoir qu’une seule responsabilité, c’est-à-dire une raison unique de changer. Cette règle favorise un design clair, flexible et facile à maintenir.

Cet article illustre ce principe avec un exemple en Java : la séparation des responsabilités dans deux classes distinctes, `ClientManager` et `ClientReport`.

---

### Problématique initiale : classe avec deux responsabilités

Supposons une classe qui gère à la fois les opérations liées à la gestion des clients (ajout, modification…) et la génération de rapports sur ces clients.

```java
public class ClientManager {
    public void ajouterClient(Client client) {
        // Code pour ajouter un client à la base de données
    }

    public void genererRapportClients() {
        // Code pour générer un rapport des clients
    }
}
```

Ici, la classe `ClientManager` a deux raisons de changer :

- Modification des règles métier liées à la gestion des clients.
- Modification des exigences concernant les rapports.

Cela viole le SRP et mène souvent à du code difficile à maintenir.

---

### Application du SRP : séparation claire des responsabilités

Pour respecter ce principe, on sépare les responsabilités dans deux classes :

```java
public class ClientManager {
    public void ajouterClient(Client client) {
        // Code pour ajouter un client à la base de données
        System.out.println("Client ajouté : " + client.getNom());
    }
}

public class ClientReport {
    public void genererRapportClients() {
        // Code pour générer un rapport des clients
        System.out.println("Rapport clients généré.");
    }
}
```

- `ClientManager` gère les opérations métier sur les clients.
- `ClientReport` s’occupe exclusivement des rapports.

---

### Exemple concret avec usage

```java
public class Client {
    private String nom;

    public Client(String nom) {
        this.nom = nom;
    }

    public String getNom() {
        return nom;
    }
}

public class Main {
    public static void main(String[] args) {
        Client client = new Client("Durand");

        ClientManager manager = new ClientManager();
        ClientReport report = new ClientReport();

        manager.ajouterClient(client);      // Gestion métier
        report.genererRapportClients();    // Rapport
    }
}
```

---

### Avantages de cette séparation

- **Maintenance facilitée** : Modifier la manière de générer un rapport ne touche pas au code métier.
- **Tests simplifiés** : On peut tester séparément la logique métier et la génération de rapports.
- **Extension aisée** : Il est plus simple d’ajouter de nouvelles fonctionnalités dans l’une ou l’autre classe.

---

### Références utiles

- [Single Responsibility Principle – Martin Fowler](https://martinfowler.com/bliki/SingleResponsibilityPrinciple.html)  
- Documentation officielle Java [Java Tutorials – Classes and Objects](https://docs.oracle.com/javase/tutorial/java/javaOO/classes.html)  
- *Clean Code* de Robert C. Martin, qui explique en profondeur le SRP.

---

### En résumé

Le **Single Responsibility Principle** vise à ce que chaque classe ait une seule responsabilité. L’exemple Java présenté avec `ClientManager` et `ClientReport` montre qu’en séparant les responsabilités métier et présentation (ou rapport), on obtient un code plus propre, facile à maintenir et à étendre.

---

Cet article vous aide à comprendre la mise en pratique du SRP, première étape vers la maîtrise d’une architecture logicielle saine et durable.