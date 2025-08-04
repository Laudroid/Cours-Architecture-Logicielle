# Principes de conception

## 2. Principe DRY (Don't Repeat Yourself)

### 2. Exemple en langage C : fonction unique de calcul réutilisable au lieu de copier-coller le code

Le principe DRY (Don't Repeat Yourself) invite à éviter la duplication de code dans un programme. En langage C, comme dans tout autre langage, il est conseillé de regrouper les opérations répétitives dans des fonctions réutilisables. Cela facilite la maintenance, améliore la clarté du code, et réduit le risque d’erreurs.

---

### Pourquoi préférer une fonction unique à du code dupliqué ?

Imaginons que vous ayez à réaliser plusieurs fois le même calcul dans différentes parties de votre programme. Copier-coller ce calcul à chaque fois introduit plusieurs risques :

- Si la formule évolue, vous devez modifier tous les morceaux de code dupliqués, ce qui est fastidieux et source d’erreur.
- Le code devient encombré et moins lisible.
- Tester et valider le calcul devient moins fiable.

La solution est donc d’implémenter la logique dans une fonction dédiée, puis de l’appeler à chaque fois que cela est nécessaire.

---

### Exemple concret en C

Sans appliquer DRY, un programme pourrait contenir du code répétitif comme ceci :

```c
#include <stdio.h>

int main() {
    int a = 5, b = 10;
    // Calcul 1
    int result1 = a * b + 2;
    printf("Resultat 1: %d\n", result1);

    int c = 7, d = 3;
    // Calcul 2 identique
    int result2 = c * d + 2;
    printf("Resultat 2: %d\n", result2);

    return 0;
}
```

Le calcul `x * y + 2` est copié-collé. En appliquant le principe DRY, on crée une fonction qui encapsule ce calcul :

```c
#include <stdio.h>

// Fonction qui réalise le calcul x * y + 2
int calcul(int x, int y) {
    return x * y + 2;
}

int main() {
    int a = 5, b = 10;
    int c = 7, d = 3;

    int result1 = calcul(a, b);
    int result2 = calcul(c, d);

    printf("Resultat 1: %d\n", result1);
    printf("Resultat 2: %d\n", result2);

    return 0;
}
```

---

### Bénéfices de cette approche

- **Maintenance simplifiée** : Pour modifier la formule, il suffit d’éditer la fonction `calcul` une seule fois.
- **Code plus lisible** : On comprend directement la signification du calcul à travers le nom clair de la fonction.
- **Réutilisation facile** : La fonction peut être utilisée partout dans le programme, voire dans d’autres projets.

---

### Références et ressources complémentaires

- [Learn-C.org](https://www.learn-c.org/en/Functions) : Introduction aux fonctions en C pour organiser votre code efficacement.
- [GeeksforGeeks - DRY Principle](https://www.geeksforgeeks.org/dry-dont-repeat-yourself-principle-in-software-engineering/) : Explications du principe DRY avec des exemples pratiques.
- Le livre *Clean Code* de Robert C. Martin, une référence incontournable en qualité de code et principes de conception.

---

### En résumé

En programmation C, encapsuler les calculs répétitifs dans des fonctions permet d’appliquer efficacement le principe DRY. Cette démarche améliore la qualité, la robustesse et la maintenabilité de vos programmes.

---

Cet article vous a montré concrètement comment éviter la duplication en regroupant une opération de calcul dans une fonction unique, un réflexe essentiel pour tout développeur soucieux de bien structurer son code.