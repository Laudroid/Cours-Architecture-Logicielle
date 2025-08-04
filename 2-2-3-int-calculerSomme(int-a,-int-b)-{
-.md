# Principes de conception

## 2. Principe DRY (Don't Repeat Yourself)

### 3. Exemple en C : fonction `calculerSomme` pour éviter la duplication de code

Le principe DRY (« Don't Repeat Yourself ») est une bonne pratique incontournable en développement. Il consiste à éviter la répétition inutile de blocs de code identiques ou similaires, en les centralisant dans des fonctions ou modules réutilisables. Cela simplifie la maintenance, réduit les erreurs et améliore la lisibilité du code.

---

### Présentation de la fonction `calculerSomme`

Voici un exemple simple en langage C d’une fonction qui calcule la somme de deux entiers :

```c
int calculerSomme(int a, int b) {
    return a + b;
}
```

Cette fonction contient la logique d'addition de deux nombres `a` et `b`. L'idée est de l'utiliser partout où cette opération est nécessaire, au lieu de répéter l'expression `a + b` directement dans plusieurs parties du code.

---

### Pourquoi utiliser une fonction comme `calculerSomme` ?

1. **Réutilisabilité**  
   Chaque fois que vous avez besoin d’ajouter deux nombres, vous appelez `calculerSomme` au lieu d’écrire `a + b` partout dans le code.

2. **Maintenance facilitée**  
   Si la logique d'addition devait évoluer (par exemple, avec une validation préalable), vous modifiez uniquement la fonction, et non chaque occurrence de l’opération.

3. **Lisibilité améliorée**  
   Le nom `calculerSomme` exprime clairement l’intention du code, rendant le programme plus compréhensible pour vous et vos collègues.

---

### Exemple d’utilisation de la fonction dans un programme C

```c
#include <stdio.h>

int calculerSomme(int a, int b) {
    return a + b;
}

int main() {
    int x = 10;
    int y = 20;

    int resultat = calculerSomme(x, y);
    printf("La somme de %d et %d est %d\n", x, y, resultat);

    return 0;
}
```

Ici, la fonction `calculerSomme` est appelée depuis la fonction `main` pour afficher la somme de deux nombres. Cela garantit que la logique d’addition est encapsulée et réutilisée.

---

### Références pour approfondir

- [Learn-C.org - Functions](https://www.learn-c.org/en/Functions) : Présentation des fonctions en C, un outil clé pour appliquer DRY.
- L'article [Don't Repeat Yourself (DRY) Principle](https://martinfowler.com/bliki/Don_tRepeatYourself.html) de Martin Fowler, un expert reconnu.
- Le livre *Clean Code* par Robert C. Martin qui illustre en profondeur l’importance des fonctions pour éviter la duplication.

---

### En résumé

Définir une fonction comme `calculerSomme` est un exemple classique et simple pour mettre en pratique le principe DRY en langage C. Cette approche évite le copier-coller du même calcul et facilite la gestion du code source.

Appliquer systématiquement des fonctions pour encapsuler les opérations répétitives est une bonne habitude, essentielle pour devenir un développeur efficace et produire du code durable.

---

Grâce à cette introduction au principe DRY en C via la fonction `calculerSomme`, vous êtes mieux armé pour écrire des programmes clairs, maintenables et sans redondance inutile.