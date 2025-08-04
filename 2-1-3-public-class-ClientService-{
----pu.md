# Principes de conception

## 1. Principe de séparation des préoccupations

### 3. Exemple Java : séparation des classes de gestion métier et d'interface utilisateur avec `ClientService` et `ClientUI`

Le principe de séparation des préoccupations (SoC) est un concept fondamental qui consiste à diviser un logiciel en modules distincts, chacun dédié à une responsabilité spécifique. Cette organisation facilite la compréhension, la maintenance et l’évolution du code.

Cet article illustre ce principe à travers un exemple simple en Java avec deux classes : `ClientService` qui gère la logique métier liée aux clients, et `ClientUI` qui s’occupe de l’affichage.

---

### Présentation des classes

```java
public class ClientService {
    public void enregistrerClient(Client client) {
        // Logique métier pour enregistrer un client
    }
}

public class ClientUI {
    public void afficherClient(Client client) {
        // Code d'affichage de la fiche client
    }
}
```

- **`ClientService`** : Cette classe contient la méthode `enregistrerClient` qui encapsule toute la logique nécessaire à l’enregistrement d’un client (validation, persistance, règles métier…).
- **`ClientUI`** : Cette classe est responsable de la présentation des informations liées au client, par exemple afficher la fiche client à l’écran.

---

### Pourquoi cette séparation est-elle importante ?

1. **Clarté et organisation** : Chaque classe réalise un seul type de travail, ce qui rend le code plus lisible.
2. **Maintenance facilitée** : Une modification dans la gestion métier n’impacte pas directement l’interface utilisateur.
3. **Réutilisabilité** : Le service métier peut être réutilisé avec plusieurs interfaces différentes (application web, mobile, console).
4. **Testabilité** : On peut tester indépendamment la logique métier et l’affichage.

---

### Exemple complet simplifié

Imaginons une classe `Client` simple :

```java
public class Client {
    private String nom;
    private String email;

    public Client(String nom, String email) {
        this.nom = nom;
        this.email = email;
    }

    public String getNom() {
        return nom;
    }

    public String getEmail() {
        return email;
    }
}
```

Puis l’utilisation combinée :

```java
public class Main {
    public static void main(String[] args) {
        Client client = new Client("Dupont", "dupont@example.com");
        ClientService clientService = new ClientService();
        ClientUI clientUI = new ClientUI();

        clientService.enregistrerClient(client);  // Traitement métier
        clientUI.afficherClient(client);           // Affichage
    }
}
```

---

### À quoi ressemble la logique métier dans la méthode `enregistrerClient` ?

Bien que simplifiée ici, cette méthode pourrait inclure :

- Validation des données (email valide, nom non vide…).
- Un appel à une base de données pour sauvegarder le client.
- Gestion des erreurs et notifications.

---

### Références pour approfondir

- [Oracle Java Tutorials - Separation of Concerns](https://docs.oracle.com/javase/tutorial/java/concepts/interface.html) pour comprendre la conception modulaire en Java.
- Le principe [Single Responsibility Principle (SRP)](https://en.wikipedia.org/wiki/Single-responsibility_principle) du groupe SOLID, qui est très proche de la séparation des préoccupations.
- Le livre *Clean Architecture* de Robert C. Martin, un ouvrage de référence pour structurer ses applications autour de responsabilités claires.

---

### En résumé

La séparation des préoccupations, à travers la distinction entre classes métier (`ClientService`) et interface utilisateur (`ClientUI`), permet de rendre le code plus simple à comprendre, plus robuste et plus facile à faire évoluer. Ce principe reste une pierre angulaire dans la conception logicielle professionnelle.

---

Cet article a présenté un exemple concret pour illustrer ce principe clé, essentiel à maîtriser pour tout développeur ou architecte logiciel en formation.