# Séparation des composants

## 1. Modularité et découplage

### 2. Exemple Java : utilisation de modules Java (JPMS) pour isoler les composants

Avec l’évolution rapide des applications, la gestion efficace de la modularité est devenue un enjeu majeur. Java a introduit à partir de la version 9 le **Java Platform Module System (JPMS)**, un système de modules natif qui permet d’isoler et d’organiser les composants logiciels pour mieux maîtriser leur couplage, faciliter la maintenance et améliorer la sécurité.

---

### Qu'est-ce que le JPMS ?

Le **Java Platform Module System** est une architecture modulaire intégrée dans la plateforme Java qui permet de :

- Diviser une application en modules distincts avec des frontières claires.
- Définir explicitement les dépendances entre modules.
- Contrôler la visibilité des packages entre modules.
- Faciliter la maintenance et l’évolution des applications.

---

### Pourquoi utiliser le JPMS ?

- **Isolation stricte** : chaque module définit ce qui est accessible à l’extérieur (via `exports`) et ce qui est caché.
- **Déclaration explicite des dépendances** : évite les surprises à l’exécution dues à des dépendances non déclarées.
- **Amélioration de la sécurité** : le module masque ses détails d’implémentation.
- **Réduction de la taille du runtime** : permet de construire des runtime customisés ne contenant que les modules nécessaires.

---

### Exemple simple d’utilisation du JPMS

Supposons un projet divisée en deux modules : un module `util` qui fournit des fonctionnalités utilitaires, et un module `app` qui utilise `util`.

---

#### Étape 1 : création du module `util`

- Arborescence :

```
util/
 ├── src/
 │    └── util/
 │         └── com.example.util/
 │              └── Calculatrice.java
 └── module-info.java
```

- Le contenu du fichier `module-info.java` :

```java
module com.example.util {
    exports com.example.util; // rend public le package util
}
```

- Exemple de classe dans `com.example.util.Calculatrice` :

```java
package com.example.util;

public class Calculatrice {
    public int additionner(int a, int b) {
        return a + b;
    }
}
```

---

#### Étape 2 : création du module `app`

- Arborescence :

```
app/
 ├── src/
 │    └── app/
 │         └── com.example.app/
 │              └── Main.java
 └── module-info.java
```

- Le fichier `module-info.java` :

```java
module com.example.app {
    requires com.example.util; // déclare la dépendance au module util
}
```

- Classe principale `Main.java` :

```java
package com.example.app;

import com.example.util.Calculatrice;

public class Main {
    public static void main(String[] args) {
        Calculatrice calc = new Calculatrice();
        System.out.println("2 + 3 = " + calc.additionner(2, 3));
    }
}
```

---

### Résultat et bénéfices

- Le module `app` ne peut utiliser que les packages explicitement exportés par `util`.
- Toute modification dans `util` nécessite une recompilation contrôlée des dépendances.
- Une séparation claire facilite la compréhension et la maintenance.
- Promotion de la responsabilité unique par module.

---

### Références et ressources complémentaires

- [Oracle - Introduction to the Java Module System](https://docs.oracle.com/javase/9/docs/api/java/lang/module/package-summary.html)  
- [Baeldung - Guide to the Java Module System](https://www.baeldung.com/java-9-modularity)  
- [Java 9 Modules Tutorial | Vogella](https://www.vogella.com/tutorials/JavaModules/article.html)  

---

### Conclusion

Le système de modules Java (JPMS) est une avancée majeure vers une modularité native et robuste. En définissant clairement les frontières et les dépendances des composants, JPMS facilite la séparation des composants, réduit le couplage, et donne aux développeurs un contrôle précis sur la visibilité et la gestion des composants.

Pour tout développeur Java souhaitant concevoir des applications modernes, bien structurées et maintenables, l’adoption du JPMS est une étape incontournable.

---

**Explorez le JPMS dès aujourd’hui pour améliorer la qualité et la modularité de vos projets Java !**