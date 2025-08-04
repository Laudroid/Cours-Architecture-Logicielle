# Architecture multiservice

## 2. Architecture serverless

### 1. Fonctionnement autour des fonctions cloud, déploiement facile, montée en charge automatique

L’architecture **serverless** s’impose de plus en plus comme une approche innovante pour concevoir des applications cloud modernes, en complément ou alternative aux architectures microservices classiques. Elle offre une gestion simplifiée des ressources informatiques en se basant sur des **fonctions cloud**, dont le déploiement est facile et la capacité de montée en charge automatique.

---

## Qu’est-ce que l’architecture serverless ?

- **Serverless** signifie littéralement « sans serveur », mais en réalité les serveurs existent, ils sont simplement **entièrement gérés** par le fournisseur cloud.
- Le développeur se concentre uniquement sur la logique métier sous forme de **fonctions**.
- Ces fonctions sont déclenchées automatiquement par des événements (appel HTTP, modification de données, files d’attente…).

---

## Fonctionnement autour des fonctions cloud

Une fonction cloud est un bloc de code autonome qui accomplit une tâche précise, par exemple :

- Traitement d’une requête HTTP,
- Analyse d’un fichier stocké,
- Envoi d’une notification.

Le fournisseur d’infrastructure (AWS Lambda, Azure Functions, Google Cloud Functions) prend en charge :

- Le **déploiement**,
- L’**exécution à la demande**,
- La **mise à l’échelle**.

---

## Déploiement facile

- Pas besoin de provisionner ou configurer des serveurs.
- Le développeur pousse directement son code (la fonction) dans le cloud.
- Intégration avec des outils CI/CD pour automatiser les mises à jour.
- Le modèle permet de réduire considérablement les délais entre développement et mise en production.

---

## Montée en charge automatique (Auto-scaling)

- Le fournisseur détecte automatiquement le nombre d’appels à la fonction.
- En cas de pic, plusieurs instances de la fonction sont lancées en parallèle.
- Lorsqu’il y a moins d’appels, le nombre d’instances diminue jusqu’à zéro.
- Ce modèle permet d’optimiser les coûts puisque l’on paie uniquement ce qui est consommé.

---

## Exemple concret

Imaginons un système de traitement d’images dans une application web :

- L’utilisateur télécharge une photo sur le cloud.
- Un événement déclenche une fonction serverless qui analyse l’image, applique des filtres et stocke le résultat.
- En période de forte activité (pics de téléchargements), plusieurs fonctions s’exécutent simultanément sans intervention humaine.
- Le coût est maîtrisé car on ne paye que le temps d’exécution réel des fonctions.

---

## Avantages de l’architecture serverless

| Avantages                    | Description                                             |
|-----------------------------|---------------------------------------------------------|
| Réduction de la charge opérationnelle | Pas de gestion de serveurs, sauvegardes ou sécurité.  |
| Déploiement rapide           | Mises à jour simplifiées avec déploiement ciblé.       |
| Adaptabilité                 | Auto-scalabilité automatique sans souci d’infra.       |
| Coût optimisé               | Facturation à l’usage réel et non à des ressources fixes. |

---

## Limites à considérer

- Limites de timeout (durée d’exécution maximale imposée).
- Moins adaptée aux tâches lourdes ou nécessitant un état persistant.
- Dépendance au fournisseur cloud (verrouillage).

---

## Références et ressources pour approfondir

- [AWS Lambda – Serverless computing](https://aws.amazon.com/lambda/)  
- [Azure Functions Documentation](https://learn.microsoft.com/en-us/azure/azure-functions/)  
- [Google Cloud Functions Overview](https://cloud.google.com/functions)  
- [Serverless Framework](https://www.serverless.com/)  
- [Martin Fowler – Serverless Architectures](https://martinfowler.com/articles/serverless.html)

---

## Conclusion

L’architecture serverless transforme la manière de concevoir et déployer des applications grâce à un concept innovant : les fonctions cloud autonomes. Ce modèle permet un déploiement simplifié, une montée en charge automatique et une gestion des ressources optimisée, offrant ainsi agilité, scalabilité et réduction des coûts.

**Adopter le serverless, c’est choisir une architecture adaptée aux environnements cloud modernes, où la rapidité et la flexibilité sont des facteurs clés de succès.**

---

**Intégrez dès aujourd’hui le serverless dans votre palette d’architectures pour répondre efficacement aux enjeux du développement moderne !**