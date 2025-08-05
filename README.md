# symfony_react_docker_compose_deployment

Adapter les commandes suivantes avec vos images et repositories.

Se connecter au serveur distant et déployer le projet
```bash
ssh <utilisateur>@<IP_adresse>
curl https://raw.githubusercontent.com/fredericBui/symfony_react_docker_compose_deployment/refs/heads/main/compose.yaml -o compose.yaml
docker compose up -d
```

Entrer dans le container et réaliser les migrations
```bash
docker exec -it symfony_backend_container bash
rm -Rf migrations
mkdir migrations
php bin/console make:migration
php bin/console doctrine:migrations:migrate
```

http://<IP_Adresse>:8089/
http://<IP_Adresse>:3000/

Pour supprimer les déploiements
```bash
docker compose down
docker volume rm root_db_data
```