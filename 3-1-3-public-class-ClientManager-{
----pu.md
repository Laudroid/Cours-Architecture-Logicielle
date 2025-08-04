# Concepts SOLID

## 1. Single Responsibility Principle (SRP)

### 3. Exemple Java : Classes `ClientManager` et `ClientReport` avec responsabilités distinctes

Le **Single Responsibility Principle (SRP)**, premier principe des concepts SOLID, affirme qu’une classe doit avoir une seule responsabilité, c’est-à-dire une seule raison de changer. Cela permet une meilleure organisation du code, plus simple à maintenir et à faire évoluer.

Ce principe s’illustre clairement avec deux classes en Java, `ClientManager` et `ClientReport`, qui respectent SRP en se concentrant chacune sur une tâche unique.

---

### Présentation des classes

```java
public class ClientManager {
    public void gererClient() {
        // Code pour gérer un client (ajout, modification, suppression, etc.)
        System.out.println("Gestion du client effectuée.");
    }
}

public class ClientReport {
    public void genererRapport() {
        // Code pour générer un rapport sur les clients
        System.out.println("Rapport généré.");
    }
}
```

- `ClientManager` est responsable de la **gestion des clients** dans le système.
- `ClientReport` est dédié uniquement à la **génération de rapports**.

---

### Pourquoi cette séparation est importante ?

1. **Clarté et lisibilité**  
   Chaque classe a un but précis, ce qui facilite la compréhension du code.

2. **Maintenance simplifiée**  
   Si l’on doit modifier la gestion des clients, on change uniquement `ClientManager`. Si les besoins sur les rapports évoluent, on modifie `ClientReport`, évitant d’introduire des erreurs dans l'autre responsabilité.

3. **Tests unitaires facilités**  
   Chaque classe peut être testée indépendamment, ce qui améliore la fiabilité du système.

---

### Exemple d’utilisation en contexte

```java
public class Main {
    public static void main(String[] args) {
        ClientManager clientManager = new ClientManager();
        ClientReport clientReport = new ClientReport();

        clientManager.gererClient();     // Gestion métier du client
        clientReport.genererRapport();  // Génération du rapport
    }
}
```

---

### Ce que ce design évite

Sans SRP, on pourrait avoir une seule classe qui mélange gestion et rapport, rendant le code :

- Plus lourd et difficile à maintenir,
- Plus sujet à erreurs quand l’une des fonctions évolue,
- Moins clair et difficile à tester.

Le respect de SRP est donc un pas clé vers une architecture modulaire et robuste.

---

### Références et ressources complémentaires

- [Single Responsibility Principle (SRP) sur le site de Martin Fowler](https://martinfowler.com/bliki/SingleResponsibilityPrinciple.html)  
- Documentation officielle Oracle sur la [programmation orientée objet en Java](https://docs.oracle.com/javase/tutorial/java/javaOO/classes.html)  
- *Clean Code* de Robert C. Martin — un livre incontournable sur la qualité du code et les principes SOLID.

---

### En résumé

Le principe SRP recommande de limiter la responsabilité d’une classe à un seul domaine. L’exemple avec `ClientManager` et `ClientReport` en Java montre la séparation simple et efficace des responsabilités entre gestion métier et génération de rapport. Adopter ce principe améliore la maintenabilité, la clarté, et la qualité globale du logiciel.

---

Cet article vous a donné une vue claire et accessible sur la mise en œuvre pratique du Single Responsibility Principle, fondamental pour concevoir des applications durables et faciles à faire évoluer.