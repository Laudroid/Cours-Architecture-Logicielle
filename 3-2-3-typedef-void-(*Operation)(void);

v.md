# Concepts SOLID

## 2. Open/Closed Principle (OCP)

### 3. Utilisation de pointeurs de fonction en C pour respecter l’OCP

Le principe **Open/Closed Principle (OCP)** est au cœur des bonnes pratiques de conception logicielle. Il stipule que :

> **Les entités doivent être ouvertes à l'extension, mais fermées à la modification.**

Cet article illustre comment, en langage C, on peut mettre en œuvre ce principe en utilisant des **pointeurs de fonction**, permettant d’étendre le comportement d’un programme sans modifier le code existant.

---

### Pourquoi utiliser des pointeurs de fonction ?

Contrairement aux langages orientés objet qui disposent de mécanismes comme l’héritage ou le polymorphisme, le C est un langage procédural. Pour respecter l’OCP, il faut donc exploiter d’autres outils. Les pointeurs de fonction offrent cette possibilité : ils permettent de remplacer une fonction par une autre sans toucher au code appelant.

---

### Exemple simple en C

#### Déclaration d'un pointeur de fonction

```c
typedef void (*Operation)(void);
```

Ici, `Operation` est un type défini comme un pointeur vers une fonction qui ne prend aucun argument et ne retourne rien (`void`).

#### Fonction initiale

```c
void operationInitiale() {
    // Code initial
    printf("Exécution de l'opération initiale.\n");
}
```

Cette fonction représente le comportement par défaut ou initial.

---

### Comment étendre le comportement ?

Au lieu d’appeler directement `operationInitiale`, on passe ce pointeur de fonction comme paramètre ou on le stocke dans une variable, ce qui permet de remplacer facilement la fonction appelée, respectant ainsi l’OCP :

```c
#include <stdio.h>

typedef void (*Operation)(void);

void operationInitiale() {
    printf("Exécution de l'opération initiale.\n");
}

void operationEtendue() {
    printf("Exécution de l'opération étendue.\n");
}

void executerOperation(Operation op) {
    op();  // Appel de la fonction pointée
}

int main() {
    Operation op = operationInitiale;

    executerOperation(op);  // Affiche : Exécution de l'opération initiale.

    // Extension : on remplace l’opération sans modifier executerOperation
    op = operationEtendue;

    executerOperation(op);  // Affiche : Exécution de l'opération étendue.

    return 0;
}
```

---

### Analyse

- La fonction `executerOperation` est **fermée à la modification** : son code ne change jamais.
- La fonction appelée est configurable via le pointeur `Operation`, ce qui rend le comportement **ouvert à l’extension**.
- Pour ajouter un nouveau comportement, il suffit de définir une nouvelle fonction et de l’assigner au pointeur sans toucher au code existant.

---

### Avantages pédagogiques de cette approche

- Facilite la maintenance du code.
- Réduit les risques d’introduire des bugs dans les fonctions déjà stables.
- Permet d’ajouter des fonctionnalités de façon modulaire.

---

### Références et ressources complémentaires

- [Function Pointers in C - Tutorialspoint](https://www.tutorialspoint.com/cprogramming/c_function_pointers.htm)  
- [Open/Closed Principle - GeeksforGeeks](https://www.geeksforgeeks.org/solid-principles-in-c/) — adaptation de SOLID en langage C  
- *Clean Architecture* de Robert C. Martin — une référence pour comprendre et appliquer les principes SOLID.

---

### En résumé

En résumé, le langage C, bien que procédural, peut respecter le **Open/Closed Principle** en utilisant des pointeurs de fonction. Cette technique permet d’**étendre** le comportement d’un programme sans modifier le code déjà testé, améliorant ainsi la robustesse, la modularité et la maintenabilité.

---

Ce tutoriel vous encourage à expérimenter avec les pointeurs de fonction pour créer des logiciels plus **évolutifs** et **flexibles**, même en C. Adopter l’OCP, c’est un pas important vers une conception logicielle professionnelle.