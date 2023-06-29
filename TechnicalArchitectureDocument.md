# Description de l'Architecture Technique (DAT)
![Logo](misc/owl.svg)

## 1. Description générale de l'infrastructure
- **Objectif de l'infrastructure :** Héberger et mettre en ligne une application mobile IOS/Android et fournir une continuité de service aux utilisateurs.
- **Services ou applications hébergés :** Application mobile IOS/Android.
- **Taille de l'infrastructure :**
  - 15 machines virtuelles :
    - 2 sites internet.
    - 1 backoffice.
    - 5 micro-services.
    - 4 bases de données.
    - 1 service Gsm.
    - 10 outils de logs / monitoring / automatisation.
    - 1 Runner de déploiement.
    - 1 pare-feu pfsense.
    - 1 loadbalancer HAproxy, etc.

## 2. Topologie de l'infrastructure
- **Configuration réseau :**
  - Réseau interne IPV4 : 10.4.169.0/16 dans le subnet 169.
  - **1 adresse IP publique : 192.214.203.196 pour exposer l'application en ligne.**
- **Composants principaux de l'infrastructure :**
  - 1 routeur pour l'IP publique vers les réseaux LAN.
  - 1 pare-feu pfsense et VPN.
  - 1 serveur Proxmox pour héberger les machines virtuelles.
- **Interconnexion des composants :** Via des câbles RJ45 ou un commutateur virtuel sur Proxmox.

## 3. Plateforme d'hébergement
- **Plateforme d'hébergement utilisée :** On-premise au CUCDB (Diiage).
- **Fournisseur(s) cloud utilisé(s) :** GitHub pour l'hébergement du code uniquement.

## 4. Système d'exploitation et logiciels
- **Systèmes d'exploitation utilisés sur les serveurs :** Debian 10 (machines virtuelles).
- **Logiciels ou services déployés sur l'infrastructure :**
  - MariaDB.
  - Redis.
  - Solr.
  - HAproxy.
  - Nginx.
  - Docker.
  - Hashicorp Vault.
  - Neo4j.
  - ElasticSearch.
  - Prometheus.
  - Ansible.
  - Jaeger.

## 5. Sécurité
- **Mesures de sécurité mises en place :**
  - **Pare-feu pour filtrer le trafic.**
  - **VPN pour l'accès aux outils internes.**
- **Gestion des certificats et des connexions sécurisées :** Via une PKI Hashicorp Vault.

## 6. Surveillance et gestion
- **Surveillance de l'infrastructure :**
  - Outils de surveillance : Uptime Kuma.
  - **Alertes : Envoyées via Ntfy (sur les téléphones).**
- **Journalisation :** ElasticSearch Kibana.
- **Gestion des mises à jour et correctifs système :** Via le gestionnaire de paquets APT automatisé et pipeline.

## 7. Sauvegarde et récupération
- **Sauvegarde des données :** Via la sauvegarde de Proxmox.
- **Plans de récupération en cas de sinistre ou de perte de données :** Déploiement PRA (Plan de Reprise d'Activité) via une infrastructure as code.

## 8. Évolutivité et redondance
- **Gestion de la croissance future et de la demande accrue :** Équilibrage de charge et ajout de nœuds pour augmenter le nombre de micro-services en parallèle si nécessaire.
- **Mécanismes de redondance pour assurer la disponibilité des services :** HAproxy gère la redondance des services.

## 9. Documentation et processus
- **Documentation de l'infrastructure :** Instance Bookstack pour héberger la documentation. Organisation GitHub pour héberger la documentation liée aux services.
- **Processus de gestion des changements, incidents et problèmes :** Réception d'une alerte en cas d'incident, création d'une réunion avec les parties concernées pour intervenir rapidement.

## 10. Points de contact et support
- **Points de contact en cas de problèmes ou de demandes de support :** CEO Antoine GUYON ou CTO Benoit Despierres.
- **Accords de niveau de service (SLA) en place pour la disponibilité et la réactivité du support technique :** SLA basé sur les garanties fournies par le prestataire CUCDB (Diiage).
