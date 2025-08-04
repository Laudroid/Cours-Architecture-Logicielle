# Architecture multiservice

## 1. Microservices : principes et avantages

### 2. Code Java simple illustrant un microservice REST

L’architecture microservices repose sur la création de services légers, autonomes et spécialisés, souvent exposés via des API REST. Pour comprendre concrètement comment concevoir un microservice, rien ne vaut un exemple simple en Java, l’un des langages les plus utilisés dans l’industrie pour cela.

---

## Qu’est-ce qu’un microservice REST ?

Un microservice REST (Representational State Transfer) est un service web qui expose ses fonctionnalités via des appels HTTP simples (GET, POST, PUT, DELETE). Ces services communiquent généralement au format JSON, ce qui facilite l’interopérabilité.

---

## Exemple pédagogique d’un microservice REST en Java avec Spring Boot

Spring Boot est un framework Java très populaire pour développer rapidement des applications REST grâce à sa simplicité et son intégration étroite avec Spring.

---

### Étape 1 : Créer une application Spring Boot

Vous pouvez générer l’ossature de l’application avec Spring Initializr (https://start.spring.io/) :

- Choisir « Maven Project », Java 11+ ou supérieur
- Ajouter la dépendance **Spring Web**

---

### Étape 2 : Exemple de code d’un microservice REST simple

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.*;

import java.util.ArrayList;
import java.util.List;
import java.util.concurrent.atomic.AtomicLong;

@SpringBootApplication
public class DemoApplication {
    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}

@RestController
@RequestMapping("/api/greetings")
class GreetingController {

    private final AtomicLong counter = new AtomicLong();
    private final List<Greeting> greetings = new ArrayList<>();

    @GetMapping
    public List<Greeting> getAllGreetings() {
        return greetings;
    }

    @PostMapping
    public Greeting addGreeting(@RequestBody Greeting newGreeting) {
        newGreeting.setId(counter.incrementAndGet());
        greetings.add(newGreeting);
        return newGreeting;
    }

    @GetMapping("/{id}")
    public Greeting getGreeting(@PathVariable Long id) {
        return greetings.stream()
                .filter(g -> g.getId().equals(id))
                .findFirst()
                .orElseThrow(() -> new RuntimeException("Greeting not found"));
    }
}

class Greeting {
    private Long id;
    private String message;

    public Greeting() {}

    public Greeting(Long id, String message) {
        this.id = id;
        this.message = message;
    }

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getMessage() {
        return message;
    }

    public void setMessage(String message) {
        this.message = message;
    }
}
```

---

### Explications

- La classe `DemoApplication` lance le microservice Spring Boot.
- Le contrôleur REST `GreetingController` expose trois endpoints :
  - `GET /api/greetings` : récupère toutes les salutations.
  - `POST /api/greetings` : ajoute une nouvelle salutation.
  - `GET /api/greetings/{id}` : récupère une salutation par son identifiant.
- La classe `Greeting` est un simple **DTO** (Data Transfer Object) utilisé pour échanger les données.

Ce microservice minimaliste illustre les concepts d’**indépendance**, d’**exposition via API REST** et de **statelessness** propre aux microservices.

---

## Tester le microservice

Vous pouvez tester le microservice avec des outils comme [Postman](https://www.postman.com/) ou `curl`.

```bash
# Ajouter une salutation
curl -X POST http://localhost:8080/api/greetings -H "Content-Type: application/json" -d '{"message":"Bonjour"}'

# Récupérer toutes les salutations
curl http://localhost:8080/api/greetings
```

---

## Avantages d’utiliser Spring Boot pour les microservices

- Démarrage rapide et configuration automatique (`auto-configuration`).
- Support natif des services REST via annotations simples (`@RestController`, etc.).
- Intégration avec tout l’écosystème Spring (sécurité, bases de données, messaging, etc.).
- Large communauté et documentation abondante.

---

## Références utiles

- [Spring Boot Official Documentation](https://spring.io/projects/spring-boot)  
- [Building a RESTful Web Service - Spring](https://spring.io/guides/gs/rest-service/)  
- [Microservices with Spring Boot - Baeldung](https://www.baeldung.com/spring-boot-microservices)  
- [REST API Tutorial](https://restfulapi.net/)

---

## Conclusion

Un microservice REST en Java, bien que simple dans cet exemple, illustre parfaitement les principes fondamentaux de l’architecture microservices : modularité, indépendance, exposition claire via API. En maîtrisant ce type de développement, vous pouvez concevoir des systèmes distribués, scalables et facilement maintenables.

---

**N’hésitez pas à expérimenter ce code pour mieux comprendre comment construire vos propres microservices Java !**