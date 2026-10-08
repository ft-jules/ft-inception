# Inception

Une petite infrastructure Docker, projet du cursus 42 Paris : trois
conteneurs construits à la main depuis Debian, sans image toute faite.

- **nginx**, seul point d'entrée, en HTTPS uniquement (TLS 1.2 et 1.3), sur le port 443
- **WordPress** avec php-fpm
- **MariaDB** pour la base de données

Chaque service a son Dockerfile dans `srcs/requirements/`. Les conteneurs
communiquent sur un réseau Docker dédié, et les données de WordPress et de
MariaDB sont gardées dans deux volumes, sur la machine hôte dans `/home/jules/data`.

## Lancement

Les mots de passe ne sont pas dans le repo. Il faut d'abord créer `srcs/.env` à
partir de l'exemple, et remplacer chaque `CHANGE_ME` :

```sh
cp srcs/.env.example srcs/.env
make
```

Le site répond ensuite sur https://jpointil.42.fr (le Makefile ajoute le domaine
à `/etc/hosts`). Le certificat est auto-signé, le navigateur affichera donc un
avertissement.

Le projet a été validé en 2025 sur Debian bullseye, l'avant-dernière version
stable de l'époque, comme le demandait le sujet.
