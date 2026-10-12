# Cloud, Virtualisation, Infrastructure et Technologies émergentes

## 1. On-Premises vs Cloud

**On-premises** : infrastructure informatique physiquement située dans les locaux de l'organisation ou dans un site qu'elle contrôle.

**Cloud** : ressources informatiques fournies par un prestataire, généralement à la demande, sans gestion directe de toute l'infrastructure physique.

| Critère | On-premises | Cloud |
|---|---|---|
| Availability | Dépend de l'infrastructure et des moyens internes | Peut bénéficier des capacités du fournisseur, selon l'architecture choisie |
| Resilience | À concevoir et financer par l'organisation | Des options existent mais doivent être configurées |
| Cost | Investissement matériel et coûts d'exploitation | Coûts à la consommation et récurrents ; attention aux transferts |
| Responsiveness | Évolution de capacité parfois lente | Ajustement souvent rapide |
| Scalability | Dépend du matériel et des délais d'approvisionnement | Mise à l'échelle généralement plus flexible |
| Ease of deployment | Installation physique et configuration possibles | Déploiement souvent plus rapide |
| Risk transference | L'organisation assume davantage de risques d'infrastructure | Certains risques sont transférés, pas toutes les responsabilités |
| Patch availability | L'organisation obtient et déploie les correctifs | Le fournisseur corrige les couches qu'il gère |
| Inability to patch | Compatibilité et contraintes opérationnelles possibles | Les systèmes et applications gérés par le client peuvent aussi être difficiles à corriger |
| Power | L'organisation prévoit alimentation et refroidissement | Le fournisseur gère l'alimentation des data centers |
| Compute | Capacité limitée au matériel disponible | Capacité ajustable selon l'offre et les limites du fournisseur |

**Notions à distinguer :**
- **Availability** : possibilité d'accéder au système quand on en a besoin.
- **Resilience** : capacité à récupérer après une panne et à continuer de fonctionner.
- **Responsiveness** : rapidité d'adaptation aux changements de demande.
- **Scalability** : capacité à gérer une hausse de charge.
- **Ease of recovery** : facilité de restauration après incident.
- **Compute** : ressources de calcul, par exemple CPU et mémoire.

Le cloud ne supprime pas automatiquement les risques : disponibilité, sauvegardes, sécurité et reprise doivent être conçues et vérifiées.

## 2. Compute et responsabilité partagée

Les ressources cloud peuvent inclure serveurs, stockage, bases de données, réseau, logiciels, analytics et services d'intelligence.

Une **responsibility matrix** indique la répartition des responsabilités entre le fournisseur et le client. Les couches peuvent inclure :
- infrastructure physique ;
- réseau ;
- serveurs ;
- système d'exploitation ;
- middleware et runtime ;
- applications ;
- données.

La répartition dépend du service utilisé. Plus le service est géré par le fournisseur, plus celui-ci prend en charge de couches techniques. Le client conserve généralement des responsabilités sur ses données, identités, accès et configurations.

Les **third-party vendors** fournissent des services spécialisés qui peuvent améliorer les fonctionnalités, la sécurité ou l'efficacité, mais ajoutent des dépendances à évaluer.

## 3. Hybrid Solutions

Une **hybrid solution** combine une infrastructure on-premises, un cloud privé et/ou un cloud public.

Points à évaluer :
- **Data security** : protéger les données sensibles ;
- **Compliance** : respecter les exigences réglementaires et contractuelles ;
- **Interoperability** : permettre aux systèmes de communiquer ;
- **Cost** : vérifier la pertinence économique.

Une architecture hybride exige une bonne gestion des identités, des réseaux, des données et des politiques de sécurité.

---

# 4. Cloud Security

### Shared Physical Server Vulnerabilities
Dans un environnement mutualisé, plusieurs clients peuvent utiliser une même infrastructure physique. Une mauvaise isolation peut exposer des ressources.

Mesures : appliquer les recommandations du fournisseur, maintenir les systèmes dont le client est responsable et surveiller les activités anormales.

### Inadequate Virtual Environment Security
Une sécurité insuffisante des environnements virtuels peut entraîner des accès non autorisés ou des fuites de données.

Mesures :
- utiliser des templates de VM sécurisés ;
- mettre à jour et corriger les VM ;
- surveiller les comportements inhabituels ;
- limiter les accès administratifs.

### User Access Management
Une mauvaise gestion des identités et permissions peut permettre des accès non autorisés.

Mesures :
- authentification multifacteur (MFA) ;
- politiques d'authentification robustes ;
- principe du moindre privilège ;
- revue régulière des droits ;
- révocation des accès inutiles.

### Outdated Security Measures
Les systèmes non mis à jour peuvent rester vulnérables.

Mesures : appliquer les correctifs selon le risque, revoir les politiques et suivre les menaces connues.

### Single Point of Failure
Un **single point of failure** est un composant dont la panne peut interrompre un service entier : serveur unique, data center, fournisseur ou liaison réseau.

La redondance et les plans de reprise réduisent le risque, à condition d'éviter les dépendances communes.

### Weak Authentication and Encryption
Mesures : MFA, algorithmes de chiffrement robustes, gestion sécurisée des clés et contrôle des accès.

### Unclear Policies and Data Remnants
Les **data remnants** sont des données résiduelles après une suppression ou un effacement.

Mesures : définir les procédures de suppression, gérer les sauvegardes et rétentions, et vérifier l'effacement selon les capacités du service et les engagements du fournisseur.

---

# 5. Virtualization

La **virtualization** permet d'exécuter plusieurs environnements virtuels sur un même matériel physique. Une VM émule un environnement informatique et peut exécuter son propre système d'exploitation.

### Hypervisor Type 1 — Bare Metal
Fonctionne directement sur le matériel physique.

Exemples : VMware ESXi, Hyper-V dans son architecture hyperviseur, Xen.

### Hypervisor Type 2 — Hosted
Fonctionne au-dessus d'un système d'exploitation hôte comme Windows, macOS ou Linux. Souvent utilisé pour les postes de travail, tests et laboratoires.

### Sécuriser la virtualisation
- mettre à jour et sécuriser l'hyperviseur ;
- corriger les VM ;
- appliquer des protections adaptées ;
- utiliser une authentification robuste ;
- limiter les connexions entre VM et hôte ;
- désactiver les fonctions inutiles ;
- surveiller les activités anormales.

**Virtualization sprawl** : multiplication non contrôlée des VM, pouvant entraîner des coûts, des systèmes oubliés, des correctifs manquants et une visibilité réduite.

## Attaques liées à la virtualisation

- **VM escape** : sortir des limites d'isolation d'une VM et interagir avec l'hôte ou d'autres ressources.
- **Privilege escalation** : obtenir des privilèges supérieurs à ceux normalement autorisés.
- **Live VM migration** : déplacement d'une VM entre hôtes physiques avec une interruption limitée ; le processus et ses échanges doivent être sécurisés.
- **Resource reuse** : réutilisation de mémoire ou de stockage ; un nettoyage ou une isolation insuffisants peuvent exposer des données résiduelles.

---

# 6. Containerization

La **containerization** isole des applications dans des conteneurs légers. Contrairement à une VM classique, un conteneur partage généralement le noyau du système hôte.

### Avantages
- **Efficiency** : faible surcharge ;
- **Speed** : démarrage rapide ;
- **Portability** : déploiement uniforme dans les environnements compatibles ;
- **Scalability** : multiplication des instances ;
- **Isolation** : séparation logique des applications ;
- **Consistency** : environnement reproductible.

### Outils
- **Docker** : création et exécution de conteneurs ;
- **Kubernetes** : orchestration de conteneurs ;
- **Red Hat OpenShift** : plateforme Kubernetes avec des outils supplémentaires.

Les conteneurs ne sont pas sécurisés par défaut : sécuriser images, secrets, permissions, runtime et hôte.

---

# 7. Serverless Computing

Le **serverless** est un modèle où le fournisseur gère une grande partie de l'infrastructure sous-jacente. Les développeurs se concentrent sur le code ou les fonctions à exécuter.

Avantages possibles : mise à l'échelle automatique, moins de gestion serveur et facturation souvent liée à l'utilisation.

**Vendor lock-in** : dépendance à un fournisseur, ses API ou services propriétaires, rendant une migration coûteuse ou complexe.

---

# 8. Microservices

Les **microservices** décomposent une application en petits services relativement autonomes qui communiquent par des interfaces définies. Dans une architecture **monolithique**, les fonctions sont davantage regroupées dans une seule application.

### Avantages
- **Scalability** : faire évoluer séparément les services concernés ;
- **Flexibility** : adapter certaines technologies et cycles de développement ;
- **Resilience** : une panne peut être contenue si l'architecture le permet ;
- **Faster deployment and updates** : déployer un service sans redéployer toute l'application.

### Défis
- **Complexity** : plus de composants à exploiter et surveiller ;
- **Data management** : cohérence et transactions entre services ;
- **Network latency** : délais et points de panne réseau ;
- **Security** : davantage d'API, d'identités et de communications à sécuriser.

---

# 9. Network Infrastructure

### Physical Separation / Air Gapping
L'**air gapping** isole un réseau en supprimant ses connexions directes avec d'autres réseaux. Cela réduit certaines voies d'accès, mais ne rend pas le réseau invulnérable : supports amovibles, accès physiques ou erreurs humaines restent des risques.

### Logical Separation
La **logical separation** crée des frontières logiques pour restreindre les accès.

Exemples : VLAN, sous-réseaux, règles de pare-feu et segmentation par identité ou application. L'efficacité dépend de la configuration.

---

# 10. Software-Defined Networking (SDN)

Le **SDN** permet de gérer le réseau de manière programmable, en séparant logiquement le contrôle du transfert des paquets.

- **Data plane / forwarding plane** : traite et transfère les paquets selon les règles installées.
- **Control plane** : détermine comment le trafic est acheminé ; le contrôle peut être centralisé dans un contrôleur logiciel.
- **Application plane** : contient les applications qui interagissent avec le contrôleur pour exprimer des politiques ou besoins réseau.

---

# 11. Infrastructure as Code (IaC)

L'**Infrastructure as Code (IaC)** consiste à définir et gérer l'infrastructure avec des fichiers de configuration ou du code. Ceux-ci peuvent être versionnés, testés, relus et audités.

### Formats et langages
- **YAML** : format de sérialisation lisible, souvent utilisé pour des configurations.
- **JSON** : format structuré de données.
- **HCL** : HashiCorp Configuration Language, utilisé notamment par Terraform.

### Snowflake Systems
Un **snowflake system** est configuré de manière unique et non standardisée, donc difficile à reproduire et maintenir. L'IaC peut réduire cette dérive.

### Idempotence
L'**idempotence** est la propriété d'une opération qui, répétée, produit le même état final attendu.

### Avantages
- rapidité et efficacité ;
- cohérence et standardisation ;
- scalabilité ;
- économies possibles ;
- auditabilité ;
- amélioration de la conformité.

### Défis
- courbe d'apprentissage ;
- complexité ;
- risque de diffuser une mauvaise configuration ;
- gestion des secrets ;
- contrôle des permissions et du code.

Les fichiers IaC doivent être relus, testés, versionnés et protégés comme du code sensible.

---

# 12. Centralized vs Decentralized Architecture

### Centralized
Les fonctions de calcul ou de gestion sont coordonnées depuis un point ou une autorité centrale.

**Avantages :** contrôle, cohérence, gestion uniforme, économies possibles.

**Risques :** point unique de défaillance selon l'architecture, difficultés de montée en charge, cible attractive pour un attaquant, dépendance à la connectivité.

### Decentralized
Les fonctions sont réparties entre plusieurs systèmes ou emplacements.

**Avantages :** résilience potentielle, évolutivité, flexibilité, répartition de charge.

**Risques :** gestion complexe, politiques difficiles à appliquer uniformément, incohérence des données, surveillance plus difficile.

Le choix dépend des besoins et risques. La décentralisation ne garantit pas automatiquement la résilience, et la centralisation n'implique pas nécessairement un point de panne unique.

---

# 13. Internet of Things (IoT)

L'**Internet of Things (IoT)** désigne un réseau d'objets physiques équipés de systèmes leur permettant de se connecter et d'échanger des données.

- **Hub** : point central de connexion ou de coordination pour des appareils.
- **Smart devices** : objets du quotidien dotés de capacités de calcul et de connectivité.
- **Wearables** : appareils connectés conçus pour être portés.
- **Sensors** : détectent des changements dans l'environnement et les transforment en données.

### Risques IoT
- mots de passe par défaut faibles ;
- services réseau mal configurés ;
- mises à jour insuffisantes ;
- segmentation inadéquate ;
- accès physiques ou distants non autorisés.

### Mesures
- changer les identifiants par défaut ;
- désactiver les services inutiles ;
- appliquer les mises à jour disponibles ;
- segmenter les réseaux IoT ;
- limiter les communications ;
- surveiller les comportements inhabituels.

---

# 14. ICS, DCS, PLC et SCADA

### ICS — Industrial Control Systems
Les **ICS** surveillent et contrôlent des processus industriels, de systèmes simples à des installations complexes.

### DCS — Distributed Control System
Un **DCS** contrôle des processus industriels de manière distribuée entre plusieurs contrôleurs ou zones.

### PLC — Programmable Logic Controller
Un **PLC** est un automate programmable industriel contrôlant des machines ou étapes de processus selon une logique programmée.

### SCADA — Supervisory Control and Data Acquisition
Le **SCADA** supervise et collecte des données de processus, souvent géographiquement dispersés.

Exemples :
- production, transmission et distribution d'électricité ;
- traitement et distribution de l'eau ;
- pipelines pétroliers ou gaziers.

### Risques ICS/SCADA
- accès non autorisé ;
- malware ;
- systèmes non mis à jour ;
- menaces physiques ;
- perturbation des processus industriels.

### Mesures
- contrôles d'accès robustes ;
- mises à jour planifiées et testées ;
- pare-feu et détection d'intrusion adaptés ;
- audits réguliers ;
- formation ;
- segmentation entre réseaux IT et OT.

Dans les environnements industriels, les mises à jour doivent être planifiées et testées pour ne pas compromettre la sûreté ou la disponibilité.

---

# 15. Embedded Systems

Un **embedded system** est un système informatique spécialisé intégré à un équipement plus large pour réaliser des fonctions déterminées.

### RTOS — Real-Time Operating System
Un **RTOS** est conçu pour traiter des tâches dans des contraintes temporelles définies, ce qui est important pour les applications sensibles au temps.

### Risques
- panne matérielle ;
- bugs logiciels ;
- vulnérabilités ;
- systèmes ou firmwares obsolètes ;
- difficulté ou impossibilité de patcher.

### Stratégies de sécurisation

**Network segmentation** : isoler les équipements selon leur fonction et limiter les communications.

**Wrappers** : couche logicielle enveloppant un composant ou une interface pour ajouter ou adapter certaines fonctions. Elle peut aider à contrôler l'accès à un composant ancien, mais ne corrige pas automatiquement ses vulnérabilités internes.

**Firmware code control** : contrôler l'intégrité, l'origine et les mises à jour du firmware ; n'autoriser que des firmwares approuvés lorsque possible.

**Inability to patch** : certains équipements ne peuvent pas être corrigés facilement en raison de contraintes matérielles, de certification, de compatibilité ou d'indisponibilité du fournisseur.

Mesures compensatoires :
- isoler l'équipement ;
- restreindre les accès ;
- filtrer les communications ;
- surveiller les activités ;
- prévoir un remplacement lorsque le risque devient inacceptable.

---

# 16. À retenir pour l'examen

## Cloud
- On-premises : l'organisation gère l'infrastructure physique dans un environnement qu'elle contrôle.
- Cloud : le fournisseur gère une partie de l'infrastructure, selon le service.
- La **responsibility matrix** définit qui est responsable de chaque couche.
- Les responsabilités du client sur les données, identités, accès et configurations ne disparaissent pas automatiquement.
- Une solution hybride combine on-premises et cloud.
- Availability = accès au service ; resilience = récupération et continuité.

## Virtualisation et conteneurs
- Hypervisor **Type 1** : directement sur le matériel.
- Hypervisor **Type 2** : au-dessus d'un OS hôte.
- **VM escape** = sortir de l'isolation d'une VM.
- **Privilege escalation** = obtenir des privilèges plus élevés.
- Containerization = conteneurs légers partageant généralement le noyau de l'hôte.
- Docker exécute des conteneurs ; Kubernetes les orchestre.
- Virtualization sprawl = multiplication non maîtrisée de VM.

## Architectures
- Serverless réduit la gestion de l'infrastructure, mais peut entraîner du vendor lock-in.
- Microservices : avantages de déploiement et d'évolutivité, mais complexité accrue.
- Air gap = isolation physique ; logical separation = segmentation logique.
- SDN : data plane transfère, control plane décide, application plane exprime les besoins via les applications.
- IaC : infrastructure décrite en code ; idempotence = répétition sans modifier l'état final attendu.
- Snowflake system = configuration unique difficile à reproduire.

## IoT / ICS / Embedded
- IoT = objets connectés et échange de données.
- ICS = famille de systèmes de contrôle industriel.
- DCS = contrôle distribué ; PLC = automate programmable ; SCADA = supervision/acquisition de données.
- RTOS = système conçu pour respecter des contraintes temporelles.
- Pour les équipements non patchables : segmentation, restriction des accès, surveillance et remplacement si nécessaire.
