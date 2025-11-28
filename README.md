# Firefly III Automatic Transaction Bot

> Automatisation de la création de transactions dans Firefly III à partir d'e-mails, avec validation et enrichissement via Telegram.

## Description

Ce projet automatise l’enregistrement des transactions dans Firefly III en traitant les e-mails reçus (notifications bancaires, paiements, etc.). Lorsqu’un e-mail contenant une transaction est détecté, le système extrait les informations pertinentes (montant, date, description, etc.). Avant d’enregistrer la transaction, un bot Telegram contacte l’utilisateur pour confirmer ou compléter les informations (catégorie, compte, notes, etc.). Après validation, la transaction est envoyée à Firefly III via son API.

## Fonctionnalités principales

- Surveillance d’une boîte mail pour détecter les e-mails de transaction
- Extraction automatique des données de transaction depuis les e-mails
- Interaction avec l’utilisateur via un bot Telegram pour confirmation ou ajout d’informations manquantes
- Création automatique de la transaction dans Firefly III après validation

## Structure du projet

```text
app/
	application/
		use_cases/           # Cas d'utilisation métier (logique applicative)
	core/                  # Logique centrale, entités et interfaces
	domain/                # Modèles de domaine (Transaction, Compte, etc.)
	infrastructure/
		email_listener/      # Gestion de la récupération et du parsing des e-mails
			email_client.py
			email_service.py
		http/                # Services HTTP (API Firefly III)
			http_service.py
		ml_model/            # (optionnel) Modèles ML pour classification ou extraction
		repositories/        # Accès aux données, implémentations des interfaces
		telegram_bot/        # Gestion du bot Telegram
			telegram_service.py
```

## Clean Architecture

Le projet suit les principes de la Clean Architecture :

- **Domain** : contient les entités métier et les interfaces abstraites.
- **Application** : regroupe les cas d’utilisation (use cases) qui orchestrent la logique métier.
- **Infrastructure** : implémente les interfaces (accès e-mail, API, bot Telegram, etc.).
- **Interface utilisateur** : interaction via Telegram (pas d’UI graphique).

Cette séparation permet une grande testabilité, une évolutivité et une indépendance vis-à-vis des frameworks ou services externes.

## Utilisation de devcontainer

Le projet inclut un fichier `.devcontainer` pour faciliter la configuration d’un environnement de développement reproductible sous VS Code (Docker). Cela permet à tous les contributeurs de disposer du même environnement (dépendances, outils, etc.) sans configuration manuelle.

## Licence

Ce projet est sous licence MIT. Vous pouvez l’utiliser, le modifier et y contribuer librement.

---

N’hésitez pas à ouvrir des issues ou des pull requests pour toute suggestion ou contribution !
