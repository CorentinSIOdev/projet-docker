# Containerisation de cette Application

Ce projet provient d'une source externe confier par un formateur via ce lien ci-dessous : [https://github.com/tasmer/exemple-wp-docker](https://github.com/tasmer/exemple-wp-docker).

## Configuration des Services

Nous avons besoin de 4 services orchestrés avec un fichier `docker-compose.yml` :

1. Un service avec **MariaDB 10.3** pour la gestion de notre base de données.
2. Un service avec **Adminer** pour nous connecter sur la base de données.
3. Un service qui va utiliser notre **Dockerfile**.
4. Un service pour exécuter **Nginx**.

## Installation du Projet

1. Clonez le dépôt sur la machine locale.
2. Exécutez la commande `docker-compose up --build` afin de construire les conteneurs et le démarrer.
3. Exécutez la commande afin d'installer les dépendances nécessaire au fonctionnement du projet avec Composer :

```bash
docker-compose exec wp composer install
```

Copiez le fichier .env.example vers un nouveau fichier .env et configurez les accès à la base de données utilisée :

```bash
docker-compose exec wp cp .env.example .env
```

Éditez le fichier .env créer précedemment afin d'y ajouter les informations de la base de données comme ceci :

```bash
DB_NAME=wp
DB_USER=root
DB_PASSWORD=R00t
DB_HOST=mariadb
WP_HOME=http://localhost
```

Pour voir l'application WordPress fonctionnel, y accéder depuis l'URL : http://localhost à fournir dans un navigateur.

## Les commandes plus ou moins utiles

```bash
Va servir à construire un ou des conteneur(s) et le démarrer
    docker-compose up --build

Va servir à arrêter et supprimer les conteneurs construits
    docker-compose down

Va servir à installer les dépendances du projet via Composer directement.   
    docker-compose exec wp composer install
```
