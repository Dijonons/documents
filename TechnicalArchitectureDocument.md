# Description de l'Architecture Technique (DAT)
![Logo](misc/owl.svg)

## 1. Description générale de l'infrastructure

- **Objectif de l'infrastructure :** L'infrastructure a pour objectif d'héberger et de mettre en ligne une application mobile pour les plateformes iOS et Android, tout en offrant une continuité de service aux utilisateurs.
- **Services ou applications hébergés :** L'infrastructure héberge une application mobile destinée aux utilisateurs sur les plateformes iOS et Android.

- **Taille de l'infrastructure :**
  - 15 machines virtuelles sont utilisées pour héberger les différents composants de l'infrastructure :
    - 2 sites internet pour fournir une interface utilisateur conviviale.
    - 1 backoffice pour la gestion administrative de l'application.
    - 5 micro-services pour assurer le fonctionnement des différentes fonctionnalités de l'application.
    - 4 bases de données pour stocker les données de l'application.
    - 1 service Gsm pour la communication avec les appareils mobiles.
    - 10 outils de logs, de monitoring et d'automatisation pour assurer la performance et la disponibilité de l'infrastructure.
    - 1 Runner de déploiement pour automatiser le processus de déploiement des mises à jour.
    - 1 pare-feu pfsense pour sécuriser l'accès à l'infrastructure.
    - 1 loadbalancer HAproxy pour répartir la charge entre les différents composants de l'infrastructure.

## 2. Topologie de l'infrastructure

- **Configuration réseau :** L'infrastructure utilise un réseau interne IPV4 avec l'adresse 10.4.169.0/16 dans le subnet 169. De plus, une adresse IP publique (192.214.203.196) est utilisée pour exposer l'application en ligne.
- **Composants principaux de l'infrastructure :**
  - 1 routeur est utilisé pour gérer la connectivité entre l'adresse IP publique et les réseaux LAN internes.
  - 1 pare-feu pfsense et VPN sont mis en place pour filtrer le trafic et assurer la sécurité de l'infrastructure.
  - 1 serveur Proxmox est utilisé comme plateforme d'hébergement pour les machines virtuelles.

## 3. Plateforme d'hébergement

- **Plateforme d'hébergement utilisée :** L'infrastructure est hébergée en interne, au CUCDB (Centre Universitaire de Calcul de Dijon-Bourgogne).
- **Fournisseur(s) cloud utilisé(s) :** Aucun fournisseur cloud externe n'est utilisé. Cependant, GitHub est utilisé pour l'hébergement du code source de l'application.

## 4. Système d'exploitation et logiciels

- **Systèmes d'exploitation utilisés sur les serveurs :** Les machines virtuelles utilisent le système d'exploitation Debian 10, réputé pour sa stabilité et sa compatibilité.
- **Logiciels ou services déployés sur l'infrastructure :** L'infrastructure déploie un ensemble de logiciels et de services essentiels, tels que :

    - MariaDB pour les bases de données relationnelles.
    - Redis pour la mise en cache des données.
    - Solr pour la recherche et l'indexation des données.
    - Haproxy pour le load balancing et la répartition de la charge.
    - Nginx pour le serveur web.
    - Docker pour la virtualisation des applications.
    - Hashicorp Vault pour la gestion des certificats et des secrets.
    - Neo4j pour la gestion des bases de données orientées graphe.
    - ElasticSearch pour la recherche et l'analyse de données.
    - Prometheus pour la surveillance des performances.
    - Ansible pour l'automatisation des tâches d'administration.
    - Jaeger pour la collecte et l'analyse des traces d'exécution.

## 5. Sécurité

- **Mesures de sécurité mises en place :** Plusieurs mesures de sécurité sont mises en place pour protéger l'infrastructure, notamment :
    - Un pare-feu pfsense est utilisé pour filtrer le trafic et prévenir les attaques indésirables.
    - Un VPN est configuré pour permettre un accès sécurisé aux outils internes.

- **Gestion des certificats et des connexions sécurisées :** La gestion des certificats et des connexions sécurisées est réalisée à l'aide de Hashicorp Vault, une solution de gestion des secrets et des certificats.

## 6. Surveillance et gestion

- **Surveillance de l'infrastructure :** L'infrastructure est surveillée en continu à l'aide de l'outil Uptime Kuma, qui fournit des informations sur la disponibilité et les performances des différents composants.
- **Alertes :** Des alertes sont envoyées via l'outil de notification Ntfy pour informer les administrateurs en cas de dysfonctionnement ou de situation critique.
- **Journalisation :** La journalisation des événements est effectuée à l'aide d'ElasticSearch et Kibana, permettant ainsi une analyse approfondie des logs.

## 7. Sauvegarde et récupération

- **Sauvegarde des données :** Les données de l'infrastructure sont sauvegardées à l'aide de la fonctionnalité de sauvegarde intégrée à Proxmox.
- **Plans de récupération en cas de sinistre ou de perte de données :** Des plans de reprise d'activité (PRA) sont mis en place en utilisant une approche d'infrastructure as code, permettant ainsi de déployer rapidement une nouvelle infrastructure en cas de sinistre ou de perte de données.

## 8. Évolutivité et redondance

- **Gestion de la croissance future et de la demande accrue :** L'infrastructure est conçue pour faire face à la croissance future et à la demande accrue en utilisant un équilibrage de charge et la possibilité d'ajouter des nœuds supplémentaires pour augmenter la capacité des micro-services en parallèle, si nécessaire.
- **Mécanismes de redondance pour assurer la disponibilité des services :** Le load balancer HAproxy est utilisé pour assurer la redondance et la haute disponibilité des services en répartissant la charge entre les différents composants de l'infrastructure.

## 9. Documentation et processus

- **Documentation de l'infrastructure :** Une instance de Bookstack est utilisée pour héberger la documentation détaillée de l'infrastructure, y compris la topologie, les configurations et les procédures.
- **Gestion des changements, incidents et problèmes :** En cas d'incident, une alerte est reçue, ce qui déclenche la création d'une réunion avec les parties concernées afin d'intervenir rapidement et de résoudre les problèmes de manière efficace.

## 10. Points de contact et support

- **Points de contact en cas de problèmes ou de demandes de support :** En cas de problèmes ou de demandes de support, les utilisateurs peuvent contacter directement le CEO Antoine GUYON ou le CTO Benoit Despierres.
- **Accords de niveau de service (SLA) :** Un accord de niveau de service (SLA) est en place pour garantir la disponibilité et la réactivité du support technique. Le SLA est basé sur les garanties fournies par le prestataire CUCDB (Centre Universitaire de Calcul de Dijon-Bourgogne).
- 
