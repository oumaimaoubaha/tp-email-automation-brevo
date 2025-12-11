# tp-email-automation-brevo
Objectif du projet

Ce projet illustre comment automatiser l’envoi d’emails de bienvenue grâce à l’API de Brevo (Sendinblue).

Il montre :

la connexion à une API marketing,

la lecture d’un fichier CSV contenant une liste de nouveaux inscrits,

l’envoi automatisé d’emails personnalisés,

la journalisation des retours API (succès / échecs).

 1. Contenu du repository
Fichier	Description
send_welcome.py	Script Python qui envoie un email de bienvenue à chaque inscrit
inscrits.csv	Exemple de fichier CSV contenant : email, prénom, date d'inscription
README.md	Documentation et instructions d'exécution
 2. Prérequis
✔️ Installer Python 3.8+
✔️ Installer les dépendances nécessaires :
pip install requests pandas

✔️ Créer une clé API Brevo

Aller sur : https://app.brevo.com/settings/keys/api

Cliquer sur Créer une clé API

Copier la clé → NE PAS la mettre dans un fichier public

 3. Sécurité : Comment utiliser votre clé API ?

Pour éviter d'exposer la clé API dans le code, utilisez une variable d’environnement.

➤ Sur Windows (PowerShell)
setx BREVO_API_KEY "votre_cle_api_ici"

➤ Sur Mac / Linux
export BREVO_API_KEY="votre_cle_api_ici"


Ensuite, le script récupère la clé automatiquement :

import os
API_KEY = os.getenv("BREVO_API_KEY")


⚠️ Ne jamais mettre la clé API directement dans le code, ni dans GitHub.

4. Format du fichier CSV (inscrits.csv)

Le fichier doit contenir les colonnes suivantes :

email,prenom,date_inscription
jean@email.com,Jean,2025-01-15
marie@email.com,Marie,2025-01-15
...

 5. Exécution du script

Dans le terminal :

python send_welcome.py


Le script :

Charge le fichier inscrits.csv

Envoie un email personnalisé à chaque utilisateur

Affiche le statut de l'envoi :

Exemple :

Email envoyé à Jean (jean@email.com) → Status 201
Email envoyé à Marie (marie@email.com) → Status 201
...

 6. Exemple d’email envoyé via l’API

Sujet :

Bienvenue {Prénom} !


HTML minimal :

<h1>Bienvenue !</h1>
<p>Merci de vous être inscrit à notre plateforme.</p>

 7. Journalisation (Logs)

Le script affiche pour chaque email :

destinataire

statut HTTP (201 = succès)

identifiant du message Brevo (messageId)

 8. Résultat attendu

Si tout fonctionne, vous obtiendrez une série de logs comme :

Email envoyé à Jean → Status 201
Email envoyé à Marie → Status 201
Email envoyé à Pierre → Status 201
...

 9. Auteur

Projet réalisé dans le cadre du TP Web Marketing & Automatisation – ENSA.
