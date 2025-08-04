# Cours Architecture Logicielle

## Objectifs de la formation

- Comprendre le rôle et les responsabilités de l'architecte logiciel dans un projet de développement complexe.
- Appliquer les principes fondamentaux de conception logicielle pour améliorer la qualité et la maintenabilité du code.
- Maîtriser les concepts SOLID et leur application concrète en Java et C.
- Savoir séparer efficacement les composants d'une application pour favoriser la modularité et la réutilisation.
- Être capable de différencier les éléments essentiels des accessoires dans une architecture logicielle.
- Concevoir une architecture multiservice moderne en intégrant les tendances récentes telles que les microservices et l'architecture serverless.
- Identifier et corriger les erreurs courantes de conception grâce à des analyses critiques et des exemples concrets.
## Séance 1 : Le rôle et les objectifs de l'architecte logiciel

**Durée :** 50 minutes

### Objectifs pédagogiques

- Définir précisément les responsabilités de l'architecte logiciel.
- Comprendre l'importance stratégique de l'architecture logicielle dans le cycle de vie du développement.
### Contenus

#### Responsabilités clés de l'architecte logiciel

- L'architecte logiciel assure la cohérence technique et la qualité globale du système. Il fait le lien entre les exigences métier et les solutions technologiques adaptées.
- Il coordonne les choix technologiques majeurs : technologies, frameworks, patterns d'architecture.
#### Objectifs stratégiques de l'architecture logicielle

- Assurer l'évolutivité, la performance, la sécurité et la maintenabilité du système informatique.
- Optimiser le temps de développement par la mise en place de standards et bonnes pratiques.
## Séance 2 : Principes de conception

**Durée :** 50 minutes

### Objectifs pédagogiques

- Identifier et appliquer les principes de conception qui facilitent l'évolution et la maintenance.
### Contenus

#### Principe de séparation des préoccupations

- Chaque module doit avoir une responsabilité unique afin de favoriser la compréhension et la modification future.
- Exemple Java : séparation des classes de gestion métier et d'interface utilisateur (code commenté).
public class ClientService {
    public void enregistrerClient(Client client) {
        // Logique métier pour enregistrer un client
    }
}

public class ClientUI {
    public void afficherClient(Client client) {
        // Code d'affichage de la fiche client
    }
}#### Principe DRY (Don't Repeat Yourself)

- Éviter la duplication de code pour faciliter la maintenance et réduire les erreurs.
- Exemple C : fonction unique de calcul qu'on réutilise au lieu de copier-coller le code.
int calculerSomme(int a, int b) {
    return a + b;
}## Séance 3 : Concepts SOLID

**Durée :** 50 minutes

### Objectifs pédagogiques

- Comprendre et appliquer chaque principe SOLID à travers des exemples en Java et C.
### Contenus

#### Single Responsibility Principle (SRP)

- Chaque classe doit avoir une seule responsabilité et donc une seule raison de changer.
- Exemple Java : séparation class ClientManager et ClientReport.
public class ClientManager {
    public void gererClient() { /* gestion du client */ }
}

public class ClientReport {
    public void genererRapport() { /* génération de rapport */ }
}#### Open/Closed Principle (OCP)

- Les entités doivent être ouvertes à l'extension mais fermées à la modification.
- Exemple en C : usage de pointeurs de fonction pour étendre le comportement.
typedef void (*Operation)(void);

void operationInitiale() {
    // Code initial
}

// pour étendre, on remplace la fonction sans modifier le reste#### Liskov Substitution Principle (LSP)

- Les objets d'une classe dérivée doivent pouvoir remplacer les objets de la classe de base sans altérer le comportement attendu.
- Exemple Java avec classe Animal et classes dérivées Chat et Chien.
public class Animal {
    public void deplacer() { }
}
public class Chat extends Animal { }
public class Chien extends Animal { }#### Interface Segregation Principle (ISP)

- Les clients ne doivent pas être forcés de dépendre d'interfaces qu'ils n'utilisent pas.
- Exemple Java : interfaces spécifiques plutôt qu'une interface générale trop large.
#### Dependency Inversion Principle (DIP)

- Les modules de haut niveau ne doivent pas dépendre de modules de bas niveau ; tous deux doivent dépendre d'abstractions.
- Exemple Java : injection de dépendances via interfaces.
## Séance 4 : Séparation des composants

**Durée :** 50 minutes

### Objectifs pédagogiques

- Savoir décomposer correctement une application en composants cohérents et indépendants.
### Contenus

#### Modularité et découplage

- L'importance du découplage pour faciliter les modifications et les tests.
- Exemple Java : utilisation de modules Java (JPMS) pour isoler les composants.
#### Gestion des dépendances entre composants

- Limiter les dépendances cycliques et privilégier les interfaces pour les échanges.
- Exemple C : utilisation de bibliothèques statiques ou dynamiques avec interfaces clairement définies.
## Séance 5 : Différencier l'essentiel de l'accessoire

**Durée :** 40 minutes

### Objectifs pédagogiques

- Apprendre à identifier les fonctionnalités essentielles à l'architecture et celles accessoires.
### Contenus

#### Analyse de la valeur métier

- Focaliser l'architecture sur les éléments apportant la plus grande valeur métier.
- Techniques pour évaluer l'impact des fonctionnalités sur les utilisateurs.
#### Gestion des compromis

- Savoir arbitrer entre complexité ajoutée et bénéfices réels.
## Séance 6 : Architecture multiservice

**Durée :** 50 minutes

### Objectifs pédagogiques

- Concevoir des architectures multiservices modernes intégrant microservices et serverless.
### Contenus

#### Microservices : principes et avantages

- Indépendance des services, évolutivité, déploiement autonome.
- Code Java simple illustrant un microservice REST.
@RestController
public class ClientController {
    @GetMapping("/clients")
    public List getClients() {
        return clientService.tousLesClients();
    }
}#### Architecture serverless

- Fonctionnement autour des fonctions cloud, déploiement facile, montée en charge automatique.
- Exemple conceptuel en pseudocode montrant un déclencheur cloud et traitement.
## Séance 7 : Identifier les erreurs de conception et les corriger

**Durée :** 50 minutes

### Objectifs pédagogiques

- Être capable de détecter les défauts d'architecture et proposer des solutions adaptées.
### Contenus

#### Erreurs fréquentes

- Couplage excessif, violation des principes SOLID, architecture monolithique rigide.
#### Techniques de refactoring architectural

- Utilisation des patterns de refactorisation pour réduire la dette technique.
- Exemple Java : extraction d'une interface pour découpler.
public interface ServiceClient {
    void traiterClient();
}
public class ServiceClientImpl implements ServiceClient {
    public void traiterClient() { /* implémentation */ }
}