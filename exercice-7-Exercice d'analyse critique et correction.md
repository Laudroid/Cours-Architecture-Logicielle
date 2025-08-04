---

# TP Architecture Logicielle : Analyse Critique et Refactorisation selon le DIP

## Objectif du TP
- Comprendre et identifier un couplage fort dans un code existant.
- Appliquer le principe d'inversion des dépendances (DIP) pour réaliser une refactorisation.
- Développer un regard critique sur la conception logicielle existante.
- Exploiter intelligemment un assistant d’IA pour aider à la compréhension et à la refactorisation du code.

---

## Contexte et mini-projet

Vous travaillez sur un mini-projet simple de gestion d’envoi de notifications dans une application. Cette application peut envoyer des notifications par email ou SMS.

Voici une version initiale, simpliste et fortement couplée de la classe `NotificationSender` :

```python
class EmailService:
    def send_email(self, recipient, message):
        print(f"Envoi d'un email à {recipient} : {message}")

class SmsService:
    def send_sms(self, phone_number, message):
        print(f"Envoi d'un SMS à {phone_number} : {message}")

class NotificationSender:
    def __init__(self):
        self.email_service = EmailService()
        self.sms_service = SmsService()

    def send_notification(self, contact_info, message, channel):
        if channel == 'email':
            self.email_service.send_email(contact_info, message)
        elif channel == 'sms':
            self.sms_service.send_sms(contact_info, message)
```

---

## Énoncé du TP

### 1. Analyse critique

- Identifiez et décrivez le ou les problèmes d’architecture et de couplage dans cet exemple.
- Expliquez pourquoi ce code ne respecte pas le **DIP (Dependency Inversion Principle)**.
- Quelles sont les conséquences possibles de ce couplage fort sur l’évolution future de l’application ?

### 2. Refactorisation

- Refactorez ce code pour que `NotificationSender` respecte le DIP.
- Introduisez des abstractions (interfaces ou classes abstraites) pour découpler `NotificationSender` des classes concrètes `EmailService` et `SmsService`.
- Permettez à `NotificationSender` de pouvoir utiliser n’importe quel service d’envoi de notification, sans modification du code source.

### 3. Extension (facultatif)

- Ajoutez un nouveau type de service de notification (par exemple, `PushNotificationService`).
- Montrez que vous pouvez facilement l’intégrer dans votre version refactorée sans modifier la classe `NotificationSender`.

---

## Conseils pour l’utilisation de l’IA dans ce TP

- Utilisez un assistant IA pour **comprendre** le sens du DIP et ses bonnes pratiques.
- Demandez-lui de vous aider à **identifier** les dépendances problématiques dans le code.
- Pour la refactorisation, sollicitez une proposition de code, mais **n’acceptez pas simplement la réponse :** expliquez, modifiez, adaptez en fonction de votre compréhension.
- Vérifiez que le code reste clair, maintenable et conforme aux principes SOLID.

---

## Livrables attendus

- Un rapport court (1-2 pages) présentant votre analyse critique.
- Le code source initial annoté avec vos remarques.
- Le code refactoré respectant DIP.
- (Facultatif) Le code extension avec un nouveau service.
- Captures ou transcripts de vos échanges avec l’IA (optionnel, pour montrer votre démarche).

---

## Barème indicatif

| Critère                          | Points |
|---------------------------------|--------|
| Analyse critique pertinente      | 4      |
| Refactorisation correcte & claire| 6      |
| Respect du DIP                   | 5      |
| Utilisation réfléchie de l’IA    | 3      |
| Extension fonctionnelle (option) | 2      |

---

Bon travail et n’hésitez pas à interagir avec votre assistant IA pour progresser efficacement !

---

# Annexes : rappel succinct du DIP

Le principe d’inversion des dépendances (DIP) affirme :

- Les modules de haut niveau ne doivent pas dépendre des modules de bas niveau. Tous deux doivent dépendre d’abstractions.
- Les abstractions ne doivent pas dépendre des détails. Les détails doivent dépendre des abstractions.

L’objectif est de réduire le couplage entre les composants et faciliter la maintenance et l’évolution du code.

---

Si besoin, je peux vous fournir un exemple de refactorisation une fois votre analyse terminée.