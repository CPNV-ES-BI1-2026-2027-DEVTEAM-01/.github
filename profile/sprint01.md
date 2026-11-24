# Sprint Backlog

## Objectif de Sprint

- Avoir un fichier sql qui contient les informations de l'émetteur de la facture.

## Durée du sprint

- Jusqu'au 1 décembre

## DoD

- Respect de gitflow et conventionnal commit.
- Création d'issues dans le github project pour chaque tâches mais aussi si on a un problème (bug, incompréhension etc.)
- Création de classe de test fonctionnel pour chaque features.
- Utilisation de discord comme moyen de communication dans l'équipe de dev et mettre sur github toutes informations importante pour le projet.
- Chaque microservices doit maintenir à jour sa documentation OpenAPI (Swagger).

## Détails du sprint

- Push dans les repo correspondant chaque microservices.
- Les informations du fournisseurs sont l'adresse complète, le numéro de téléphone, l'email, et le site internet.
- Si le temps nous le permet nous allons commencer à mettre en place la pipeline CI/CD.

### Orchestrator

- Expose une route API pour recevoir l'état d'avancement des autres service avec en paramètre le nom du service, l'url.

### Extract
- Expose une route API pour le start.
- Récupérer la facture d'une source et de la copier dans une autre destination pour le transform.
- Retourner à l'orchestrator l'url de la copie du fichier.

### Transform
- Expose une route API pour le start avec en paramètre l'url.
- Extraire les informations du fournisseur de la facture et les mettres dans un fichier JSON pour le load.
- Mettre le fichier JSON dans un nouveau bucket.
- Retourner à l'orchestrator l'url du bucket qui contient le fichier JSON.

### Load
- Expose un route API pour le start avec un paramètre  l'url.
- Transformer les données du JSON en table et colonne SQL et les mettre dans un fichier sql.
- Mettre le fichier sql dans un nouveau bucket.
- Transmettre à l'orchestrator l'url du bucket avec le fichier sql et lui notifier que la tâche est finie.
