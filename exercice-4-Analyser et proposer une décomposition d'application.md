---

# TP : Analyse et décomposition d’une application – Amélioration du design

## Objectif du TP
- Comprendre les principes de la séparation des responsabilités dans une architecture logicielle.
- Analyser un design existant d’une mini-application.
- Proposer une refonte ou une décomposition pour améliorer la séparation des composants.
- S'initier à l’usage de l’IA (comme ChatGPT) pour assister l’analyse et la conception logicielle.

---

## Contexte et énoncé

Vous travaillez sur une mini-application de gestion de bibliothèque simple. L’application actuelle permet :

- d’ajouter des livres,
- de consulter la liste des livres,
- de gérer les emprunts (emprunter un livre, rendre un livre).

Le code à votre disposition centralise toutes ces fonctionnalités dans une seule classe/service, ce qui rend la maintenance et l’évolution difficiles.

**Votre tâche :**

1. Analyser le code fourni (voir annexe).
2. Identifier les responsabilités mélangées.
3. Proposer une nouvelle architecture décomposée en plusieurs composants/classes.
4. Justifier votre découpage en expliquant les bénéfices en termes de séparation des responsabilités et de modularité.
5. Optionnel : simuler une discussion avec une IA (ChatGPT, Copilot, etc.) pour obtenir des suggestions d’amélioration et les intégrer dans votre proposition.

---

## Étapes du TP

### Étape 1 : Analyse du code existant

- Étudiez le code fourni.
- Repérez les fonctions qui mélangent la gestion des livres, la logique métier, et les opérations utilisateurs.
- Notez les interactions difficiles à maintenir.

### Étape 2 : Identification des composants

- Listez les responsabilités qui pourraient être séparées.
- Par exemple : gestion des livres (catalogue), gestion des emprunts, interface utilisateur (simulée), gestion des données.

### Étape 3 : Proposition de refonte

- Dessinez un diagramme simple (UML ou diagramme de composants) représentant la nouvelle structure.
- Décrivez chaque composant et ses responsabilités.
- Expliquez pourquoi cette séparation est bénéfique (maintenabilité, testabilité, évolutivité).

### Étape 4 : Exploitation de l’IA

- Posez à une IA des questions précises sur le code initial, ou demandez-lui une proposition de découpage.
- Comparez les réponses de l’IA avec votre analyse.
- Intégrez éventuellement des suggestions utiles.

---

## Annexe : Exemple de code initial simplifié (Python)

```python
class LibraryApp:
    def __init__(self):
        self.books = []
        self.borrowed_books = {}

    def add_book(self, title, author):
        self.books.append({'title': title, 'author': author})

    def list_books(self):
        for i, book in enumerate(self.books):
            status = "Available" if book['title'] not in self.borrowed_books else "Borrowed"
            print(f"{i+1}. {book['title']} by {book['author']} - {status}")

    def borrow_book(self, title, user):
        if title in self.borrowed_books:
            print("Book already borrowed.")
        elif any(book['title'] == title for book in self.books):
            self.borrowed_books[title] = user
            print(f"{user} borrowed {title}.")
        else:
            print("Book not found.")

    def return_book(self, title):
        if title in self.borrowed_books:
            user = self.borrowed_books.pop(title)
            print(f"{user} returned {title}.")
        else:
            print("Book was not borrowed.")
```

---

## Autonomie et évaluation

- Vous êtes libre d’utiliser l’IA pour analyser ou proposer le découpage.
- Expliquez clairement votre processus de réflexion.
- Rédigez un bref rapport synthétique (1 page) présentant votre découpage et les raisons.
- Bonus : proposez une petite maquette de code pour la nouvelle architecture.

---

## Livrables

- Rapport d’analyse et proposition de décomposition.
- Diagramme architectural.
- Code (modifié ou refactoré) si possible.
- Captures ou transcriptions des échanges avec l’IA (facultatif mais recommandé).

---

**Bon travail !**  
Ce TP vous prépare à concevoir des architectures modulaires et à utiliser efficacement les outils basés sur l’IA dans vos projets.

---