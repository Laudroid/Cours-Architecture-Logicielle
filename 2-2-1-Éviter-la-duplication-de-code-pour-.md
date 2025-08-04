# Principes de conception

## 2. Principe DRY (Don't Repeat Yourself)

### 1. Éviter la duplication de code pour faciliter la maintenance et réduire les erreurs

Le principe DRY, qui signifie « Don't Repeat Yourself » (Ne vous répétez pas), est un principe fondamental en développement logiciel. Il encourage les développeurs à éviter la duplication de code afin de simplifier la maintenance, d’améliorer la lisibilité et de réduire les risques d’erreurs.

---

### Pourquoi éviter la duplication de code ?

La duplication se manifeste lorsque des morceaux de code identiques ou très similaires apparaissent à plusieurs endroits dans une application. Cela entraîne plusieurs problèmes :

- **Maintenance complexe** : Lorsqu’un changement est nécessaire, il doit être répercuté manuellement à chaque occurrence du code dupliqué, ce qui est long et source d’erreurs.
- **Incohérence** : Si une modification est oubliée dans un endroit, cela peut provoquer des comportements inattendus ou des bugs.
- **Lisibilité réduite** : Un code dupliqué encombre le codebase, rendant la compréhension plus difficile.

Le principe DRY invite donc à centraliser toute logique ou tout morceau de code répétitif dans un seul endroit, appelé souvent « abstraction », ce qui assure un point unique de modification.

---

### Comment appliquer le principe DRY ?

- **Fonctions et méthodes** : Extraire les morceaux de code répétitifs dans des fonctions réutilisables.
- **Classes et objets** : Regrouper dans des classes les responsabilités communes.
- **Héritage et interfaces** : Exploiter la programmation orientée objet pour partager du comportement commun.
- **Modèles ou templates** : Pour les interfaces utilisateur, éviter de réécrire la même structure.
- **Outils et bibliothèques** : Réutiliser du code éprouvé existant plutôt que de réinventer la roue.

---

### Exemple simple en Java

Supposons qu’un développeur code à deux endroits différents une fonction pour valider une adresse email. Sans DRY, il pourrait avoir :

```java
public boolean isValidEmail1(String email) {
    return email != null && email.contains("@");
}

public boolean isValidEmail2(String email) {
    return email != null && email.contains("@");
}
```

En appliquant le principe DRY, on centralise la validation dans une seule méthode :

```java
public boolean isValidEmail(String email) {
    return email != null && email.contains("@");
}
```

Ainsi, toutes les parties du programme utilisent cette méthode unique, facilitant la maintenance et garantissant la cohérence.

---

### Références pour approfondir

- Le site [Martin Fowler](https://martinfowler.com/bliki/Don_tRepeatYourself.html) décrit en détail le principe DRY et ses bénéfices.
- [Microsoft Docs](https://learn.microsoft.com/fr-fr/dotnet/standard/design-guidelines/general-design-guidelines) recommande DRY dans ses bonnes pratiques pour la conception logicielle.
- Le livre *Clean Code* de Robert C. Martin, un ouvrage de référence qui consacre un chapitre au principe DRY et à la qualité du code.

---

### En résumé

Le principe DRY (Don't Repeat Yourself) est un pilier de la bonne conception logicielle. En évitant la duplication de code, il améliore la maintenabilité, réduit les erreurs, et augmente la qualité globale d’un système. Appliquer ce principe systématiquement est une marque de professionnalisme pour tout développeur.

---

Cet article vous a présenté de manière simple et illustrée le principe DRY, essentiel pour structurer un logiciel robuste et facile à faire évoluer.