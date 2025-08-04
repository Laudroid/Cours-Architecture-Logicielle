# Architecture multiservice

## 1. Microservices : principes et avantages

### 3. Comprendre l’annotation `@RestController` dans un microservice Java

Dans l’architecture microservices, exposer des API REST est une pratique standard pour permettre la communication entre services ou avec des clients externes comme des applications web, mobiles, ou autres systèmes. En Java, avec le framework Spring Boot, l’annotation `@RestController` joue un rôle fondamental pour définir un contrôleur REST.

---

## Qu’est-ce que `@RestController` ?

- `@RestController` est une annotation de Spring utilisée pour créer des contrôleurs web qui gèrent les requêtes HTTP.
- Elle combine les fonctionnalités de `@Controller` et `@ResponseBody` :  
  - `@Controller` identifie la classe en tant que contrôleur dans le modèle MVC de Spring,  
  - `@ResponseBody` indique que les méthodes retournent directement le corps de la réponse (au format JSON ou XML) et non plus une vue (template HTML).
- Autrement dit, une classe annotée avec `@RestController` expose des endpoints RESTful, répondant souvent avec des données JSON.

---

## Exemple concret avec `ClientController`

```java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;
import java.util.List;

@RestController
public class ClientController {

    private final ClientService clientService;

    public ClientController(ClientService clientService) {
        this.clientService = clientService;
    }

    @GetMapping("/clients")
    public List<Client> getClients() {
        return clientService.tousLesClients();
    }
}
```

### Description de l’exemple

- La classe `ClientController` est un contrôleur REST qui gère les requêtes HTTP liées aux clients.
- L’annotation `@RestController` indique que cette classe expose des API REST.
- La méthode `getClients()` est mappée sur la route HTTP GET `/clients` grâce à l’annotation `@GetMapping("/clients")`.
- Lorsqu’un client fait une requête GET sur `/clients`, le microservice retourne une liste d’objets `Client` (habituellement au format JSON).
- `clientService.tousLesClients()` est appelé pour récupérer la liste des clients, séparant ainsi la logique métier du contrôleur.

---

## Pourquoi utiliser `@RestController` dans un microservice ?

- **Simplicité** : facilite la création de services REST en réduisant la configuration nécessaire.
- **Clarté** : automatiquement configure les méthodes pour retourner des objets JSON.
- **Productivité** : développeurs peuvent se concentrer sur la logique métier plutôt que la sérialisation ou configuration HTTP.
- **Interopérabilité** : JSON est un format largement utilisé, idéal pour les APIs consommées par divers types d’applications.

---

## Tester et consommer ce service

Une fois déployé, vous pouvez tester ce microservice via un navigateur, un client HTTP (`curl`) ou des outils comme Postman.

```bash
curl http://localhost:8080/clients
```

Cela renvoie la liste des clients sous forme JSON, par exemple :

```json
[
  {"id":1, "nom":"Dupont", "email":"dupont@example.com"},
  {"id":2, "nom":"Martin", "email":"martin@example.com"}
]
```

---

## Compléments et bonnes pratiques

- Utiliser des services métier (`ClientService`) pour séparer la logique applicative des contrôleurs.
- Documenter les API avec Swagger/OpenAPI pour faciliter l’intégration.
- Gérer les exceptions dans les contrôleurs pour retourner des erreurs HTTP appropriées.
- Ajouter la pagination et les filtres pour gérer des listes potentiellement volumineuses.

---

## Références et documentation officielle

- [Spring Framework - @RestController](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/web/bind/annotation/RestController.html)  
- [Building a RESTful Web Service - Spring Guide](https://spring.io/guides/gs/rest-service/)  
- [Baeldung - Guide to @RestController in Spring](https://www.baeldung.com/spring-rest-controller)  
- [Postman - API Testing Tool](https://www.postman.com/)

---

## Conclusion

L’annotation `@RestController` est au cœur du développement des microservices en Java avec Spring Boot. Elle simplifie grandement la création d’API REST en unifiant contrôleur et réponse HTTP. Comprendre son fonctionnement est essentiel pour tout développeur souhaitant construire des architectures multiservices modernes, modulaires et rapides à déployer.

---

**En maîtrisant ces concepts, vous pourrez concevoir des microservices REST performants et facilement maintenables, répondant aux exigences complexes des systèmes distribués d’aujourd’hui.**