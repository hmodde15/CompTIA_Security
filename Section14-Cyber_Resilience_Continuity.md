## 1. Cyber Resilience

La **cyber resilience** est la capacité d'une entité à continuer de fournir les résultats attendus malgré des événements cyber défavorables. Elle implique de maintenir les services essentiels, limiter l'impact d'une panne ou d'une attaque, puis récupérer les systèmes et les données.

## 2. Redundancy

La **redundancy** consiste à dupliquer des systèmes, équipements, connexions ou processus critiques afin de maintenir le fonctionnement si l'élément principal tombe en panne.

Exemples :
- alimentations électriques redondantes ;
- connexions réseau multiples ;
- serveurs redondants ;
- plusieurs fournisseurs ;
- stockage redondant.

La redondance doit être choisie selon la criticité du composant. Elle ne remplace pas nécessairement une sauvegarde : une réplication peut aussi reproduire une suppression ou une corruption.

## 3. High Availability, Uptime, Load Balancing et Clustering

### High Availability (HA)
La **high availability** désigne la capacité d'un service à rester disponible en réduisant les interruptions.

### Uptime
L'**uptime** est la durée pendant laquelle un système reste opérationnel sur une période donnée. Il est souvent exprimé en pourcentage.

Pour une année de 365 jours, les indisponibilités théoriques sont approximativement :

| Disponibilité | Downtime annuel |
|---|---:|
| 99 % | 3 jours et 15 heures |
| 99,9 % | 8 h 46 min |
| 99,99 % | 52 min 34 s |
| 99,999 % | 5 min 15 s |
| 99,9999 % | 31,5 secondes |

### Load Balancing
Le **load balancing** distribue la charge de travail entre plusieurs ressources pour éviter la surcharge d'une seule ressource, améliorer les performances et contribuer à la disponibilité.

### Clustering
Le **clustering** fait fonctionner plusieurs ordinateurs ou nœuds comme un système coordonné. Il peut améliorer la disponibilité, la fiabilité et l'évolutivité ; si un nœud tombe en panne, les autres peuvent maintenir le service selon la configuration.

## 4. Exemples de Redundancy

- **Power supplies** : deux blocs d'alimentation dans un serveur ou équipement réseau, si le matériel le permet.
- **Network connections** : plusieurs connexions ou chemins réseau pour éviter qu'une seule panne de liaison coupe le service.
- **Servers and services** : architectures load-balanced ou clustered.
- **Service providers** : plusieurs fournisseurs peuvent réduire la dépendance à un seul, à condition d'éviter les points de défaillance communs.
- **Multi-cloud** : répartir données, applications ou services entre plusieurs environnements cloud peut améliorer la flexibilité, la mise à l'échelle et parfois la résilience.

Une architecture multi-cloud doit prendre en compte la gestion des données, les menaces, l'application des policies et les dépendances communes.

## 5. Data Redundancy et RAID

Le **RAID (Redundant Array of Independent Disks)** combine plusieurs disques physiques en un ensemble logique.

| RAID | Fonctionnement | Tolérance à la panne |
|---|---|---|
| **RAID 0** | Striping : répartit les données pour améliorer les performances | Aucune ; la panne d'un disque peut faire perdre l'ensemble |
| **RAID 1** | Mirroring : duplique les données | Peut tolérer la panne d'un disque dans un miroir à deux disques |
| **RAID 5** | Striping avec parité distribuée | Tolère la panne d'un disque |
| **RAID 6** | Striping avec deux informations de parité | Tolère la panne de deux disques |
| **RAID 10** | Combine mirroring (RAID 1) et striping (RAID 0) | Dépend des disques touchés et de la configuration |

À retenir :
- RAID 0 privilégie la performance, pas la redondance.
- RAID 1 utilise le mirroring.
- RAID 5 utilise une parité.
- RAID 6 utilise deux parités.
- RAID 10 combine mirroring et striping.

**RAID ne remplace pas une sauvegarde** et ne protège pas à lui seul contre un sinistre affectant l'ensemble du système.

## 6. Capacity Planning

Le **capacity planning** est une démarche stratégique visant à garantir que l'organisation dispose des ressources nécessaires pour répondre aux besoins actuels et futurs, au meilleur coût possible.

### People
Analyser les compétences disponibles, prévoir les besoins futurs, planifier recrutement ou formation et disposer d'un nombre suffisant de personnes qualifiées.

### Technology
Mesurer l'utilisation des ressources actuelles, anticiper les besoins technologiques et déterminer si les solutions existantes peuvent absorber la croissance.

### Infrastructure
Prévoir l'espace physique, l'alimentation électrique, le refroidissement, les équipements et la connectivité.

### Process
Optimiser les processus pour gérer les variations de demande grâce à l'amélioration des workflows, à l'automatisation ou à des prestataires.

**Exemple : télémédecine** — prévoir une capacité suffisante pour répondre à la demande, maintenir la qualité du service et accompagner le personnel et les patients.

## 7. Powering a Data Center

Les équipements informatiques sont sensibles aux perturbations électriques.

- **Surge** : augmentation de tension par rapport au niveau habituel.
- **Spike** : hausse de tension très brève et transitoire, parfois liée à la foudre ou à un événement électrique.
- **Sag** : baisse temporaire de tension.
- **Undervoltage** : tension inférieure au niveau attendu pendant une durée plus prolongée qu'un simple événement transitoire.
- **Full power loss** : perte complète d'alimentation pendant une période. Au rétablissement, une perturbation électrique peut aussi se produire.

## 8. Line Conditioners

Les **line conditioners** corrigent certaines variations de l'alimentation et fournissent une tension plus stable. Les capacités précises dépendent du modèle.

## 9. UPS — Uninterruptible Power Supply

Un **UPS** fournit une alimentation de secours lorsque la source électrique normale tombe en panne. Il permet de maintenir temporairement les équipements, d'assurer une courte continuité ou d'arrêter les systèmes proprement. Il ne remplace pas nécessairement un générateur lors d'une coupure prolongée.

## 10. Generators

Un **generator** convertit une autre forme d'énergie en énergie électrique.

Exemples :
- générateur portable à essence ;
- générateur installé de manière permanente ;
- solutions de secours utilisant batteries et onduleurs.

Le choix dépend de la puissance et de la durée de secours souhaitées, de la maintenance et des contraintes du site.

## 11. Power Distribution Center / PDU

Un **Power Distribution Center (PDC)** peut désigner un point central de distribution électrique. Une **Power Distribution Unit (PDU)** distribue l'alimentation vers plusieurs équipements, par exemple les serveurs d'une baie.

Un data center doit tenir compte de la charge, de la répartition électrique, de la capacité des circuits, de la redondance et de la surveillance. Une PDU standard ne fournit pas nécessairement de conditionnement de ligne.

## 12. Data Backups

Une **data backup** est une copie de données créée pour se protéger contre leur perte, corruption ou indisponibilité.

Une stratégie de sauvegarde doit considérer l'emplacement, la fréquence, le chiffrement, la rétention, les procédures de récupération et les tests de restauration.

### Onsite / Offsite / Offline
- **Onsite backup** : sauvegarde stockée sur le site principal ou à proximité.
- **Offsite backup** : sauvegarde conservée dans un autre emplacement physique, utile contre un sinistre local.
- **Offline backup** : sauvegarde déconnectée des systèmes ou réseaux habituels pendant tout ou partie du temps, ce qui peut protéger contre certains ransomwares.

**Offsite** décrit l'emplacement ; **offline** décrit l'état de connexion.

## 13. Backup Frequency et RPO

La fréquence des sauvegardes dépend de la quantité de données que l'organisation accepte de perdre et de la fréquence de modification des données.

Le **RPO (Recovery Point Objective)** est la quantité maximale de données, exprimée en durée, que l'organisation accepte de perdre après une interruption.

Exemple : un RPO de 4 heures signifie que l'organisation vise à récupérer des données jusqu'à un point situé au maximum 4 heures avant l'incident.

La fréquence des sauvegardes doit être cohérente avec le RPO, même si la stratégie peut également s'appuyer sur la réplication.

## 14. Encryption of Backups

Le chiffrement protège les sauvegardes contre les accès non autorisés.

- **Data at rest encryption** : protège les données stockées.
- **Data in transit encryption** : protège les données pendant leur transfert.

Il faut également protéger les clés de chiffrement et contrôler les accès aux sauvegardes.

## 15. Snapshots

Un **snapshot** est une copie représentant l'état d'un système ou de données à un instant donné. Il permet de revenir à un état antérieur selon la technologie utilisée.

Un snapshot n'est pas automatiquement une sauvegarde indépendante : il peut dépendre du stockage d'origine.

## 16. Recovery Process

La récupération peut comprendre :
1. sélectionner la sauvegarde appropriée ;
2. initier la restauration ;
3. restaurer les données ou systèmes ;
4. valider l'intégrité et la cohérence des données ;
5. tester le système restauré ;
6. documenter et rapporter les résultats ;
7. notifier les parties concernées.

## 17. Replication

La **replication** maintient des copies des données sur un autre système, en temps réel ou presque. Elle peut réduire le délai de récupération, mais elle peut aussi répliquer une suppression ou une corruption : elle ne remplace pas les sauvegardes historiques.

## 18. Journaling

Le **journaling** consiste à enregistrer les modifications apportées aux données ou à un système.

Il faut gérer :
- le niveau de détail des changements ;
- la taille du journal ;
- la durée de rétention ;
- la sécurité contre les modifications non autorisées.

## 19. Continuity of Operations

Un plan de continuité des opérations vise à maintenir ou rétablir les activités essentielles pendant une perturbation.

### BCP — Business Continuity Plan
Le **BCP** décrit comment l'organisation continuera ses fonctions essentielles pendant et après une perturbation. Il couvre des événements qui ne sont pas nécessairement des catastrophes techniques.

Exemples :
- basculer vers un autre processeur de paiement ;
- permettre le télétravail si un site est inaccessible ;
- maintenir des activités métier essentielles ;
- prévoir des solutions de remplacement pour les fonctions critiques.

Le BCP peut inclure des actions préventives et des mesures de continuité.

### DRP — Disaster Recovery Plan
Le **DRP** se concentre sur la récupération des systèmes, données et infrastructures après un sinistre.

Il peut inclure :
- restauration depuis des sauvegardes ;
- bascule vers des systèmes de secours ;
- solutions cloud de récupération ;
- récupération des infrastructures ;
- dispositions géographiques face aux catastrophes.

> **BCP = maintenir les activités essentielles.**  
> **DRP = récupérer les systèmes et l'infrastructure après un sinistre.**

Le DRP est souvent considéré comme une partie du dispositif global de continuité des activités.

## 20. BCP/DRP Governance and Scope

### Senior Management
La direction générale sponsorise ou prend en charge le développement des plans, car ils concernent les priorités et les ressources de l'organisation.

### Business Continuity Committee
Le comité doit inclure des représentants de différents départements, car la continuité concerne l'ensemble de l'organisation.

### Define the Scope
Définir le périmètre du BCP/DRP pour éviter le **scope creep**, c'est-à-dire l'élargissement progressif et non maîtrisé du périmètre.

### Risk Appetite and Risk Tolerance
- **Risk appetite** : niveau de risque que l'organisation est disposée à poursuivre ou accepter pour atteindre ses objectifs.
- **Risk tolerance** : variation ou niveau de risque que l'organisation peut tolérer dans un contexte donné.

### Organize the Plan
Le plan peut être structuré par fonction métier, système/service, zone géographique ou scénario de perturbation.

## 21. Comparaison des concepts clés

| Concept | Objectif |
|---|---|
| **Cyber resilience** | Continuer à fournir les résultats attendus malgré des événements cyber |
| **Redundancy** | Dupliquer des composants pour limiter les points de défaillance |
| **High availability** | Réduire l'indisponibilité |
| **Load balancing** | Distribuer la charge |
| **Clustering** | Faire coopérer plusieurs nœuds |
| **RAID** | Combiner des disques pour performance et/ou tolérance aux pannes |
| **Backup** | Conserver des copies récupérables |
| **Replication** | Maintenir des copies synchronisées ou presque |
| **BCP** | Maintenir les fonctions métier essentielles |
| **DRP** | Récupérer les systèmes et l'infrastructure après un sinistre |

## 22. À retenir pour l'examen

- **Redundancy** = duplication d'éléments critiques.
- **High availability** = minimiser le downtime.
- **Load balancing** répartit la charge ; le **clustering** fait coopérer plusieurs nœuds.
- **RAID 0** = striping sans tolérance aux pannes.
- **RAID 1** = mirroring.
- **RAID 5** = parité simple, tolère la panne d'un disque.
- **RAID 6** = double parité, tolère la panne de deux disques.
- **RAID 10** = mirroring + striping.
- RAID ne remplace pas une sauvegarde.
- **Capacity planning** couvre les personnes, la technologie, l'infrastructure et les processus.
- **Surge/spike** = hausse de tension ; **sag** = baisse temporaire ; **undervoltage** = tension basse prolongée ; **full power loss** = coupure complète.
- **UPS** fournit une alimentation de secours temporaire ; un générateur peut prendre le relais plus longtemps.
- **Offsite** = emplacement distinct ; **offline** = déconnecté.
- **RPO** = perte de données maximale acceptable exprimée en durée.
- **Snapshot** = état à un instant donné ; ce n'est pas automatiquement une sauvegarde indépendante.
- **Replication** peut aussi répliquer une suppression ou une corruption.
- **BCP** vise la continuité métier ; **DRP** vise la récupération après sinistre.
- Les plans BCP/DRP doivent être soutenus par la direction, impliquer plusieurs métiers et avoir un périmètre clair.
