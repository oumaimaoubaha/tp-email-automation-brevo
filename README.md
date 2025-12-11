🎯 Objectif du projet

🎯 Objectif du projet

Ce projet montre comment automatiser l’envoi d’emails de bienvenue grâce à l’API Brevo (Sendinblue).
Il couvre les éléments suivants :

-Connexion à une API marketing

-Lecture d’un fichier CSV contenant de nouveaux inscrits

-Envoi automatisé d’emails personnalisés

-Journalisation des retours API (succès / erreurs)
📁 1. Contenu du repository
| Fichier           | Description                                                     |
| ----------------- | --------------------------------------------------------------- |
| `send_welcome.py` | Script Python qui envoie un email de bienvenue à chaque inscrit |
| `inscrits.csv`    | Exemple contenant email, prénom, date d'inscription             |
| `README.md`       | Documentation du projet                                         |
🛠️ 2. Prérequis
✔️ Installer Python 3.8+
✔️ Installer les dépendances :
pip install requests pandas

✔️ Créer une clé API Brevo

1-Se rendre sur : https://app.brevo.com/settings/keys/api

2-Cliquer sur Créer une clé API

3-Copier votre clé (❗ ne jamais la publier)
🔐 3. Sécurité : utilisation de la clé API
Pour éviter d’exposer votre clé API dans le code, configurez une variable d’environnement.

➤ Windows (PowerShell)
setx BREVO_API_KEY "votre_cle_api_ici"

➤ Mac / Linux
export BREVO_API_KEY="votre_cle_api_ici"


Dans le script Python :

import os
API_KEY = os.getenv("BREVO_API_KEY")


⚠️ Ne jamais mettre la clé API directement dans le script ni dans GitHub.
📄 4. Format du fichier CSV (inscrits.csv)

Le fichier doit contenir les colonnes suivantes :

email,prenom,date_inscription
jean@email.com,Jean,2025-01-15
marie@email.com,Marie,2025-01-15
...
▶️ 5. Exécution du script

Dans un terminal :

python send_welcome.py


Le script :

1-Charge les inscrits depuis inscrits.csv

2-Envoie un email personnalisé à chaque utilisateur

3-Affiche le statut de chaque envoi
6. Exemple d’email envoyé

Sujet :

Bienvenue {Prénom} !


Contenu HTML minimal :

<h1>Bienvenue !</h1>
<p>Merci de vous être inscrit à notre plateforme.</p>

📝 7. Journalisation (Logs)

Pour chaque email envoyé, le script affiche :

-Le prénom + email du destinataire

-Le code de réponse HTTP (201 = succès)

-L’identifiant unique du message Brevo (messageId)

🎉 8. Résultat attendu

En cas de succès, vous obtiendrez :

Email envoyé à Jean → Status 201
Email envoyé à Marie → Status 201
Email envoyé à Pierre → Status 201
...

✍️ 9. Auteur

Projet réalisé dans le cadre du TP Web Marketing & Automatisation – ENSA.
