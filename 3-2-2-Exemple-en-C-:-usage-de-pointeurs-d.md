# Concepts SOLID

## 2. Open/Closed Principle (OCP)

### 2. Exemple en C : usage de pointeurs de fonction pour étendre le comportement

Le **Open/Closed Principle (OCP)**, deuxième principe de SOLID, recommande que les entités (fonctions, modules, classes...) soient **ouvertes à l’extension** mais **fermées à la modification**. En pratique, cela signifie qu’il faut pouvoir ajouter de nouvelles fonctionnalités sans modifier le code existant.

En langage C, qui ne supporte pas l’orienté objet nativement, on peut respecter ce principe en utilisant des **pointeurs de fonction**. Cette technique permet d’étendre ou modifier le comportement d’une fonction sans toucher à son code source d’origine.

---

### Pourquoi utiliser des pointeurs de fonction ?

Dans des langages comme C, qui sont structurels, la flexibilité peut paraître limitée. Les pointeurs de fonction offrent un moyen d’implémenter des comportements modulaires, extensibles, avant la création de nouvelles versions ou le changement de fonctions.

---

### Exemple concret : calculs personnalisés avec des opérations paramétrables

Supposons que nous avons une fonction qui effectue une opération sur deux entiers :

```c
#include <stdio.h>

// Déclaration d'un type pointeur de fonction prenant deux int et retournant un int
typedef int (*Operation)(int, int);

// Fonctions concrètes pour différentes opérations
int addition(int a, int b) {
    return a + b;
}

int multiplication(int a, int b) {
    return a * b;
}

// Fonction générique qui utilise une opération passée en paramètre
int calculer(int a, int b, Operation op) {
    return op(a, b);
}

int main() {
    int x = 5, y = 3;

    printf("Addition : %d\n", calculer(x, y, addition));          // 8
    printf("Multiplication : %d\n", calculer(x, y, multiplication)); // 15

    return 0;
}
```

---

### Analyse et lien avec le principe OCP

Ici, `calculer` est **fermée à la modification** : on ne change pas son code pour ajouter des opérations. En revanche, elle est **ouverte à l'extension** car on peut lui passer n'importe quelle fonction correspondant à `Operation`.

Si vous voulez ajouter un nouveau comportement, par exemple la soustraction, il suffit de créer une nouvelle fonction et de la passer à `calculer` :

```c
int soustraction(int a, int b) {
    return a - b;
}

// Puis dans main ou ailleurs
printf("Soustraction : %d\n", calculer(x, y, soustraction));
```

Ainsi, on étend le système sans modifier la fonction principale `calculer`.

---

### Avantages

- **Modularité** : Le comportement est délégué à des fonctions spécifiques.
- **Flexibilité et extension** : Ajout facile de nouvelles fonctionnalités.
- **Respect de la stabilité du code** : Le cœur fonctionnel (ici `calculer`) n’est pas modifié.

---

### Références et ressources

- [Function Pointers in C - Tutorialspoint](https://www.tutorialspoint.com/cprogramming/c_function_pointers.htm)  
- [Open/Closed Principle - GeeksforGeeks](https://www.geeksforgeeks.org/solid-principles-in-c/) (adaptation des principes SOLID en C)  
- *Clean Architecture* par Robert C. Martin, expliquant l’importance des principes SOLID, même en programmation non orientée objet.

---

### En résumé

Le principe Open/Closed peut être appliqué en langage C grâce à des techniques telles que l’utilisation des pointeurs de fonction. Cette approche permet d’écrire un code qui ne nécessite pas d’être modifié pour intégrer de nouveaux comportements, ce qui encourage la robustesse et la maintenabilité.

Cet exemple montre que même dans les langages non orientés objet, il est possible d’adopter des pratiques de conception avancées en combinant créativité et bonnes habitudes.

---

Ce résumé pédagogique vous offre une manière concrète de comprendre et appliquer l’OCP en C, un pas important pour développer un code évolutif et propre.