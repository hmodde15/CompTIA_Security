# Chapitre 28 — Alerting et monitoring

## 1. Surveillance des ressources et baselines

Le **monitoring** consiste à observer un système, une application ou une infrastructure pour comprendre son état, sa disponibilité, ses performances et les événements qui s’y produisent.

### Trois catégories de monitoring

| Catégorie | Objet surveillé | Exemples |
|---|---|---|
| **System monitoring** | Ressources d’un système informatique | CPU, mémoire, stockage, processus, disponibilité. |
| **Application monitoring** | Performances et disponibilité des logiciels | Temps de réponse, erreurs, transactions, disponibilité d’un service. |
| **Infrastructure monitoring** | Infrastructure physique et virtuelle | Serveurs, machines virtuelles, équipements réseau, stockage, disponibilité des composants. |

### Baseline — référence de fonctionnement

Une **baseline** est un ensemble de mesures et de valeurs de référence décrivant le comportement habituel d’un système, d’un réseau ou d’une application.

Elle sert à :
- repérer les écarts par rapport au comportement attendu ;
- détecter des problèmes potentiels ;
- faciliter le dépannage proactif et la maintenance ;
- distinguer les variations normales des comportements inhabituels.

Une baseline doit être actualisée lorsque l’environnement ou les usages changent. Un écart est un signal à examiner, pas nécessairement la preuve d’un incident.

## 2. Activités de monitoring et d’alerting

### Agrégation des journaux (*log aggregation*)

L’agrégation des journaux rassemble des événements provenant de plusieurs systèmes en un emplacement commun pour faciliter la recherche, la corrélation et l’analyse.

Les journaux peuvent aider à :
- diagnostiquer les problèmes système ;
- analyser les incidents de sécurité ;
- étudier les problèmes de performance et les goulots d’étranglement ;
- fournir des éléments pour les audits et la conformité.

Exemples d’événements à surveiller :
- échecs répétés de connexion ;
- changements de privilèges utilisateurs ;
- connexions réseau suspectes ;
- changements de configuration ;
- interruptions ou ralentissements inhabituels.

### Alerting — génération d’alertes

L’**alerting** consiste à avertir les personnes ou systèmes concernés lorsqu’une condition définie est détectée. Les notifications peuvent être envoyées par e-mail, SMS, application mobile, système de ticketing ou autre canal.

L’alerting sert notamment à :
- accélérer la détection des incidents ;
- déclencher une intervention ;
- suivre les problèmes de performance ;
- soutenir les exigences de conformité et de traçabilité.

Des alertes trop nombreuses ou mal réglées provoquent une **fatigue d’alerte**. Il faut définir des seuils utiles, réduire les doublons, ajuster les règles et vérifier régulièrement la qualité des alertes.

### Scans et contrôles de sécurité

Des outils tels que **Nessus**, **OpenVAS/Greenbone** ou **Qualys** peuvent contribuer à détecter des vulnérabilités. Selon l’outil et le module utilisé, les contrôles peuvent inclure :
- scans de vulnérabilités ;
- audits de configuration ;
- inventaire logiciel ;
- vérification de paramètres par rapport à des référentiels ;
- certains tests de sécurité applicative.

Des tests applicatifs spécifiques peuvent rechercher, par exemple, des risques d’injection SQL, de cross-site scripting (XSS) ou des erreurs de codage. Il faut distinguer un scanner de vulnérabilités d’un outil de test de code : leurs objectifs et leur couverture ne sont pas identiques.

Les résultats peuvent révéler des ports ouverts inutilement, des contrôles d’accès faibles, des logiciels vulnérables ou des paramètres non conformes.

### Reporting et archivage

- **Reporting** : production de synthèses ou de rapports détaillés à partir des données collectées et analysées.
- **Archiving** : conservation à long terme des journaux, données de performance et informations d’incident, selon les besoins opérationnels, réglementaires et de sécurité.

Les données archivées doivent être protégées contre l’accès non autorisé et les modifications, et conservées pendant une durée adaptée. Il convient également de contrôler leur volume, leur coût et leur suppression à échéance.

## 3. Réponse aux alertes, remédiation et validation

Lorsqu’une alerte survient, l’équipe doit déterminer sa nature, sa gravité et la réponse appropriée.

### Étapes de réponse

- **Investiguer** : collecter le contexte et vérifier si l’alerte correspond à une activité réelle.
- **Escalader** : transmettre le cas à l’équipe ou au niveau de compétence approprié.
- **Initier une action** : ouvrir un ticket, déclencher un processus d’incident ou appliquer une mesure autorisée.
- **Documenter** : conserver les décisions, preuves et actions réalisées.

### Remédiation

La **remédiation** correspond aux actions visant à résoudre le problème détecté. Exemples :
- appliquer un correctif à un logiciel obsolète ;
- reconfigurer un service ;
- modifier le code source d’une application ;
- corriger une règle de pare-feu ou une permission incorrecte.

### Quarantaine

La **quarantaine** consiste à isoler temporairement un appareil, un fichier, un compte ou un flux suspect afin de limiter la propagation ou les conséquences d’un incident, tout en permettant l’analyse. Elle doit être appliquée selon une procédure définie pour éviter une interruption non maîtrisée d’un service critique.

### Validation

La **validation** vérifie que la remédiation a réellement résolu le problème. Elle peut inclure :
- une nouvelle analyse ou un nouveau scan ;
- la vérification de la configuration ou de la version installée ;
- des tests fonctionnels ;
- l’observation des métriques après changement.

La résolution ne doit pas être considérée comme confirmée simplement parce qu’une action a été lancée.

### Tuning des alertes (*alert tuning*)

L’**alert tuning** consiste à ajuster les seuils, filtres, règles, fenêtres temporelles et conditions de déclenchement pour améliorer la pertinence des alertes. L’objectif est de réduire les faux positifs et le bruit sans manquer les événements réellement importants. Tout changement significatif des règles doit être documenté et testé.

## 4. SNMP — Simple Network Management Protocol

**SNMP** est un protocole de supervision et de gestion des équipements réseau. Il peut être utilisé pour surveiller des routeurs, commutateurs, pare-feu, imprimantes, serveurs et certains terminaux.

Les informations surveillées peuvent comprendre :
- disponibilité et temps de fonctionnement (*uptime*) ;
- utilisation d’interfaces et de ressources ;
- changements ou états de configuration, selon l’équipement ;
- événements et interruptions de service.

### Principaux composants et termes

- **Manager / système de supervision** : interroge les équipements et reçoit leurs notifications.
- **Agent SNMP** : composant de l’équipement qui expose les données de gestion.
- **MIB (Management Information Base)** : description structurée des données gérables par l’équipement.
- **OID (Object Identifier)** : identifiant hiérarchique unique d’un objet de gestion.
- **Trap** : notification envoyée par un équipement au système de supervision, généralement sans attendre une interrogation.
- **Get** : requête du système de supervision pour lire une valeur.
- **Granularité** : niveau de détail des données collectées.
- **Charge utile (*payload*)** : informations contenues dans un message ou une notification. Les détails d’un trap dépendent de l’implémentation et de la configuration.

Une **MIB** organise les objets de gestion dans un espace de noms hiérarchique, identifiés par des OID. Les traps peuvent signaler des événements sans que le système de supervision ait besoin d’interroger constamment l’équipement.

### Versions SNMP

| Version | Caractéristiques | Sécurité |
|---|---|---|
| **SNMPv1** | Version initiale, avec des fonctions de base de supervision. | Faible ; les chaînes de communauté ne fournissent pas un chiffrement moderne. |
| **SNMPv2c** | Améliore certaines fonctions et performances, tout en conservant le modèle de sécurité par communauté. | Pas de chiffrement ni d’authentification cryptographique robuste. |
| **SNMPv3** | Introduit des mécanismes de sécurité, dont l’authentification et, selon le mode, la confidentialité. | À privilégier lorsque correctement configuré, par exemple avec authentification et chiffrement. |

Les modes et capacités exacts dépendent de la configuration. Il faut limiter les équipements autorisés à interroger les agents, protéger les identifiants et éviter d’exposer SNMP inutilement.

## 5. SIEM — Security Information and Event Management

Un **SIEM** centralise et corrèle des événements et journaux provenant de sources variées pour détecter des comportements suspects et faciliter les investigations. Il fournit généralement des capacités d’analyse en temps réel ou quasi réel, d’alerting, de recherche et de reporting.

### Sources de données possibles

- serveurs et postes de travail ;
- pare-feu et équipements réseau ;
- bases de données et applications ;
- VPN ;
- solutions antivirus ou EDR ;
- systèmes de détection ou de prévention d’intrusion ;
- outils DLP (*Data Loss Prevention*) ;
- scanners de vulnérabilités ;
- systèmes de sécurité physique, si intégrés.

Exemples d’événements pouvant être corrélés :
- échecs de connexion répétés suivis d’une connexion réussie ;
- transfert de données inhabituellement volumineux ;
- modification inattendue de permissions de fichiers ;
- activité inhabituelle provenant d’un compte ou d’un appareil.

Le SIEM peut aider à répondre à des questions telles que : d’où vient l’activité, quels systèmes ou données sont visés, et quelles méthodes semblent utilisées ?

### Collecte avec agent ou sans agent

- **Avec agent** : un logiciel est installé sur chaque système concerné pour collecter et transmettre les événements.
- **Sans agent (*agentless*)** : le SIEM ou un collecteur récupère les données au moyen de mécanismes et protocoles pris en charge, par exemple des API, des protocoles de journalisation ou des interfaces de gestion. SNMP et WMI peuvent être utiles pour certains types de données, mais ne constituent pas à eux seuls des méthodes universelles de collecte de journaux.

### Bonnes pratiques SIEM

1. Définir et documenter le périmètre et les événements à collecter.
2. Enregistrer les événements pertinents tout en filtrant les données réellement inutiles.
3. Développer des **cas d’usage** décrivant les menaces ou comportements à détecter.
4. Définir un processus de réponse aux alertes et incidents.
5. Utiliser un système de ticketing pour suivre les événements, les responsables et leur résolution.
6. Programmer des activités régulières de threat hunting.
7. Conserver une piste d’audit utile aux analystes et aux auditeurs.
8. Ajuster les règles et surveiller la qualité des données collectées.

Exemples de plateformes SIEM :
- **Splunk Enterprise Security** ;
- **Elastic Security** (dans l’écosystème Elastic) ;
- **ArcSight** ;
- **IBM QRadar**.

Le SIEM est un point central de consolidation et de corrélation, mais son efficacité dépend de la qualité des sources, des règles, du contexte et de la capacité des équipes à traiter les alertes.

## 6. SCAP — Security Content Automation Protocol

Le **SCAP** est un ensemble de standards ouverts qui aide à automatiser certaines tâches de gestion des vulnérabilités, de vérification de configuration et d’évaluation de conformité.

Il peut servir à comparer des configurations à des références reconnues, inventorier des logiciels et normaliser la représentation d’informations de sécurité.

### Éléments et standards associés

| Acronyme | Rôle général |
|---|---|
| **OVAL (Open Vulnerability and Assessment Language)** | Langage normalisé pour exprimer des vérifications de configuration ou d’état d’un système. |
| **XCCDF (Extensible Configuration Checklist Description Format)** | Format de description de listes de contrôle, profils et exigences de configuration. |
| **ARF (Asset Reporting Format)** | Format de représentation et d’échange de rapports d’évaluation d’actifs. |
| **CCE (Common Configuration Enumeration)** | Identifiants standardisés pour des problèmes ou paramètres de configuration. |
| **CPE (Common Platform Enumeration)** | Nomenclature standardisée pour identifier des produits, plateformes et systèmes. |
| **CVE (Common Vulnerabilities and Exposures)** | Identifiants publics pour les vulnérabilités connues. |
| **CVSS (Common Vulnerability Scoring System)** | Système de notation de la gravité technique d’une vulnérabilité. |

Un **benchmark** est une référence de configuration recommandée ou exigée à laquelle un système peut être comparé. Les CIS Benchmarks, par exemple, proposent des recommandations de configuration sécurisée. Le résultat d’un contrôle dépend du périmètre, de la version du benchmark et de l’outil employé.

SCAP n’est pas un scanner unique : il rassemble des standards qui peuvent être utilisés par des outils compatibles pour automatiser et uniformiser des évaluations.

## 7. NetFlow, IPFIX, analyse des flux et capture complète

### Capture complète des paquets (FPC)

La **Full Packet Capture (FPC)** enregistre les paquets réseau, y compris leurs en-têtes et, lorsque la capture le permet, leur contenu (*payload*). Elle fournit un niveau de détail élevé pour les investigations, mais peut demander beaucoup d’espace de stockage et soulever des enjeux de confidentialité.

### Analyse des flux (*flow analysis*)

L’analyse des flux enregistre principalement des métadonnées et statistiques de communication, plutôt que le contenu complet de chaque paquet. Elle peut représenter rapidement :
- les adresses IP source et destination ;
- les ports source et destination ;
- le protocole ou type de trafic ;
- les volumes et durées des sessions ;
- les interfaces ou autres attributs disponibles.

Elle est utile pour visualiser les connexions, les types de trafic, les volumes et les tendances. En revanche, elle ne donne généralement pas accès au contenu complet des communications.

### NetFlow et IPFIX

- **NetFlow** est une technologie d’exportation de métadonnées de flux, historiquement associée à Cisco et utilisée par de nombreux outils de supervision réseau.
- **IPFIX (IP Flow Information Export)** est un standard d’exportation d’informations de flux qui normalise l’échange de ces métadonnées.

Les champs réellement disponibles dépendent de l’équipement, de la version et de la configuration. Ils peuvent inclure le protocole, la version IP, les adresses et ports source/destination, le type de service, les compteurs de paquets et d’octets, ainsi que les horodatages.

### Zeek

**Zeek** est un outil de surveillance et d’analyse réseau qui observe passivement le trafic et génère des journaux structurés sur les activités réseau et applicatives. Il peut traiter les paquets pour extraire des informations pertinentes, normaliser certains éléments et les stocker sous forme de journaux texte délimités ou de JSON selon la configuration.

Zeek n’est pas simplement un outil qui archive uniquement les paquets complets : son rôle central est l’analyse du trafic et la production de journaux riches. La capture complète des paquets peut être utilisée séparément ou en complément.

### MRTG — Multi Router Traffic Grapher

**MRTG** est un outil historique de représentation graphique du trafic réseau, notamment à partir de données SNMP. Il affiche généralement l’évolution des compteurs de trafic d’interfaces dans le temps. Il est utile pour la tendance et la capacité, mais n’est pas un SIEM ni un outil d’analyse détaillée du contenu des paquets.

## 8. Single pane of glass

Une **single pane of glass** est une interface ou une vue unifiée permettant de consulter plusieurs outils, systèmes et sources de données depuis un point central.

Objectifs possibles :
1. simplifier la gestion de la sécurité en réunissant les informations utiles ;
2. surveiller des signaux suspects, tels que des connexions anormales ou des échecs d’authentification ;
3. suivre l’avancement des incidents et les actions restantes ;
4. améliorer l’efficacité des opérations d’un SOC ;
5. faciliter la collaboration et la communication entre équipes ;
6. aider à rassembler les preuves nécessaires aux audits et à la conformité.

Il peut s’agir d’une plateforme logicielle ou d’une interface qui agrège plusieurs produits. Une vue unifiée ne garantit toutefois pas que toutes les données sont complètes ou exactes : les intégrations et les processus doivent être maintenus.

### Mise en place

- **Définir les besoins** : quels rôles, décisions, alertes et indicateurs doivent être couverts ?
- **Identifier et intégrer les sources** : SIEM, supervision, tickets, outils de sécurité et autres données pertinentes.
- **Personnaliser l’interface** : tableaux de bord adaptés aux responsabilités des utilisateurs.
- **Documenter les procédures** : établir des procédures opératoires standard (*SOP*) et la documentation.
- **Surveiller et maintenir** : vérifier les intégrations, les permissions, la qualité des données et les besoins évolutifs.

Les intégrations peuvent s’appuyer sur des **API**, des **webhooks**, des **plugins** ou des **connecteurs**. Les accès doivent être contrôlés et les données présentées contextualisées.

## 9. Points à retenir pour l’examen

- Le monitoring observe l’état, la disponibilité et les performances ; l’alerting avertit lorsqu’une condition pertinente est détectée.
- Une baseline décrit le comportement habituel et permet de repérer les écarts.
- L’agrégation des journaux facilite la corrélation, le dépannage, l’investigation et l’audit.
- La remédiation résout ou atténue un problème ; la validation confirme que le traitement a fonctionné.
- SNMP utilise notamment des agents, des MIB, des OID, des requêtes et des traps. SNMPv3 est à privilégier avec authentification et confidentialité correctement configurées.
- Un SIEM centralise et corrèle des événements de sécurité ; il nécessite des sources fiables, des cas d’usage et un processus de réponse.
- SCAP regroupe des standards d’automatisation ; OVAL, XCCDF, ARF, CCE, CPE, CVE et CVSS ont des rôles distincts.
- La capture complète enregistre les paquets ; l’analyse des flux s’appuie surtout sur des métadonnées.
- NetFlow et IPFIX exportent des informations de flux ; Zeek analyse le trafic et génère des journaux structurés ; MRTG représente les tendances du trafic.
- Une single pane of glass fournit une vue unifiée, mais sa qualité dépend des intégrations, de la maintenance et des procédures.
