# Séparation des composants

## 2. Gestion des dépendances entre composants

### 2. Exemple C : utilisation de bibliothèques statiques ou dynamiques avec interfaces clairement définies

La gestion des dépendances est une étape cruciale dans la construction de logiciels modulaires et maintenables. En langage C, cette gestion repose souvent sur l’utilisation de **bibliothèques statiques ou dynamiques**, avec des **interfaces bien définies**. Ces mécanismes permettent de découpler les composants, facilitant leur évolution, réutilisation et test.

---

## Bibliothèques statiques et dynamiques en C : rappels

- **Bibliothèque statique (.a sous Unix/Linux, .lib sous Windows)** : regroupe du code compilé lié statiquement à l’exécutable à la compilation, générant un binaire autonome.
- **Bibliothèque dynamique (.so sous Unix/Linux, .dll sous Windows)** : code compilé séparément chargé au moment de l’exécution, permettant un partage entre plusieurs programmes et une modularité accrue.

---

## Pourquoi des interfaces clairement définies ?

Une **interface** en C correspond à un ensemble de déclarations fonctionnelles (prototypes) contenus dans un fichier d’en-tête (`.h`). Elle définit **le contrat** que doivent respecter les différentes implémentations, sans révéler les détails internes.

- Permet un **encapsulation** stricte : le consommateur du module interagit uniquement via l’interface.
- Facilite les **remplacements d’implémentations** sans modifier le code client.
- Rend possible l’**évolution indépendante** des modules.

---

## Exemple pédagogique : gestion d’un module calcul mathématique

---

### Étape 1 : définition de l'interface (fichier `math_utils.h`)

```c
#ifndef MATH_UTILS_H
#define MATH_UTILS_H

// Fonction addition
int addition(int a, int b);

// Fonction multiplication
int multiplication(int a, int b);

#endif // MATH_UTILS_H
```

Ce fichier contient la déclaration des fonctions accessibles.

---

### Étape 2 : mise en œuvre dans la bibliothèque (fichier `math_utils.c`)

```c
#include "math_utils.h"

int addition(int a, int b) {
    return a + b;
}

int multiplication(int a, int b) {
    return a * b;
}
```

Ce fichier contient l’implémentation réelle, compilée en bibliothèque statique ou dynamique.

---

### Étape 3 : utilisation du module dans une application (fichier `main.c`)

```c
#include <stdio.h>
#include "math_utils.h"

int main() {
    int x = 5, y = 3;

    printf("Addition : %d\n", addition(x, y));
    printf("Multiplication : %d\n", multiplication(x, y));

    return 0;
}
```

---

## Compilation et liaison

### Avec une bibliothèque statique

```bash
gcc -c math_utils.c -o math_utils.o
ar rcs libmathutils.a math_utils.o

gcc main.c -L. -lmathutils -o app
```

### Avec une bibliothèque dynamique

```bash
gcc -fPIC -c math_utils.c -o math_utils.o
gcc -shared -o libmathutils.so math_utils.o

gcc main.c -L. -lmathutils -o app
export LD_LIBRARY_PATH=.
./app
```

---

## Bénéfices d’une telle organisation

- **Isolation** : Les fonctions de la bibliothèque peuvent évoluer indépendamment de l’application cliente.
- **Réutilisation** : La bibliothèque peut être partagée entre plusieurs programmes.
- **Réduction des erreurs** : Le contrat clair via le fichier header évite les erreurs d’utilisation.
- **Modularité** : Permet de remplacer facilement la bibliothèque par une autre qui respecte la même interface.

---

## Références pour approfondir

- [GNU C Library: Shared Libraries](https://www.gnu.org/software/libc/manual/html_node/Shared-Libraries.html)  
- [Linux Journal - Static vs Shared Libs](https://www.linuxjournal.com/article/2156)  
- [Tutorialspoint - C Dynamic Library](https://www.tutorialspoint.com/c_programming/c_dynamic_libraries.htm)  
- [Microsoft Docs - Using Static and Dynamic Libraries in C/C++](https://docs.microsoft.com/en-us/cpp/build/reference/create-static-and-dynamic-link-libraries)

---

## Conclusion

En langage C, l’organisation de votre code en bibliothèques statiques ou dynamiques, associée à une **interface bien définie via un fichier d’en-tête**, est essentielle pour gérer efficacement les dépendances. Elle favorise le découplage des composants, facilitant ainsi la maintenance, l’évolution et la réutilisation de votre code.

Maîtriser ces concepts est indispensable pour tout développeur C soucieux de construire des systèmes robustes, modulaires et évolutifs.

---

**N’hésitez pas à explorer ces techniques et à appliquer ces bonnes pratiques dans vos projets pour en améliorer la qualité et la modularité !**