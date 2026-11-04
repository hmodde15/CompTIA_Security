## 1. Incident response process — Processus de réponse aux incidents

### 1.1 Définition

Un **incident de sécurité** (*security incident*) est un acte qui viole une politique de sécurité explicite ou implicite.

Les **incident response procedures** sont les consignes qui expliquent comment une organisation doit traiter un incident. L’objectif est de limiter ses conséquences, protéger les données et les activités, puis rétablir un fonctionnement normal.

### 1.2 Les étapes de la réponse aux incidents

| Étape | Rôle |
|---|---|
| **Preparation — Préparation** | Renforcer les systèmes et réseaux pour mieux résister aux attaques et préparer l’organisation. |
| **Detection — Détection** | Identifier qu’un incident se produit ou s’est produit. |
| **Analysis — Analyse** | Examiner les éléments disponibles pour comprendre l’incident, son étendue et sa gravité. |
| **Containment — Confinement** | Limiter l’impact, sécuriser les données et protéger les opérations. |
| **Eradication — Éradication** | Éliminer la menace, par exemple le malware ou son mécanisme de persistance. |
| **Recovery — Rétablissement** | Restaurer les systèmes et services dans un état sûr et opérationnel. |
| **Post-incident activity / Lessons learned** | Tirer des enseignements après le confinement, l’éradication et le rétablissement complet. |

**À retenir :** le confinement empêche l’incident de s’étendre ; l’éradication supprime la menace ; le rétablissement remet les services en fonctionnement.

### 1.3 Recovery — Rétablissement

Le rétablissement peut inclure :
- Restaurer les systèmes depuis une sauvegarde connue comme saine (*known-good backup*).
- Installer les correctifs de sécurité nécessaires.
- Appliquer des mises à jour de configuration.
- Surveiller les systèmes après leur remise en service pour détecter d’éventuelles menaces persistantes.
- Vérifier que le retour à la normale se déroule correctement.

Une sauvegarde doit être vérifiée : elle pourrait elle-même contenir le malware ou la configuration compromise.

### 1.4 Retour d’expérience et Root Cause Analysis

La **Root Cause Analysis (RCA)** est une démarche systématique visant à identifier la cause initiale de l’incident et les moyens d’empêcher sa répétition.

Étapes :
1. Définir le périmètre de l’incident.
2. Déterminer les relations de cause à effet (*causal relationships*).
3. Identifier une solution efficace.
4. Mettre en œuvre la solution et suivre son efficacité.

Il faut aussi examiner le réseau pour déterminer si d’autres machines ont pu être touchées. On recherche notamment les systèmes présentant des caractéristiques similaires à ceux déjà compromis.

**Approche no-blame :** éviter de chercher un coupable individuel. Une approche sans blâme encourage les personnes à rapporter honnêtement les faits et permet de rechercher les problèmes systémiques.

Les notes donnent l’exemple d’accidents aériens attribués à des problèmes du nouveau logiciel de commande de vol. Le NTSB est cité pour son approche qui considère que les erreurs humaines peuvent résulter de problèmes systémiques dans l’industrie aéronautique.

### 1.5 After Action Report (AAR)

L’**After Action Report** formalise les informations sur l’incident et la manière dont il a été traité. Il peut consigner :
- Ce qui s’est passé.
- Les actions réalisées pendant la réponse et le rétablissement.
- Les résultats obtenus.
- Les difficultés et lacunes identifiées.
- Les améliorations à mettre en œuvre.

Les acteurs possibles mentionnés dans les notes sont : responsable/leader, experts techniques (*subject matter experts*), support informatique, conseiller juridique, ressources humaines et relations publiques. Leur participation dépend de la nature de l’incident.

---

## 2. Threat hunting — Recherche proactive de menaces

### 2.1 Définition

Le **threat hunting** consiste à rechercher activement des menaces cachées que les mécanismes habituels de surveillance n’ont pas détectées.

La surveillance classique est souvent efficace pour repérer les menaces connues grâce à des signatures ou règles existantes. Le threat hunting cherche notamment ce qui échappe à ces règles.

- **Détection classique :** une règle ou un indicateur connu déclenche une alerte.
- **Threat hunting :** l’analyste formule une hypothèse et recherche proactivement des indices d’activité malveillante.

### 2.2 Déroulement

1. **Establish a hypothesis — Établir une hypothèse :** formuler une hypothèse sur une activité malveillante possible, en s’appuyant notamment sur la modélisation des menaces (*threat modeling*) et les événements susceptibles d’avoir un impact important.
2. **Profiling threat actors and activities — Profiler les acteurs et leurs activités :** imaginer comment un attaquant pourrait pénétrer dans le système, quelles techniques il pourrait utiliser et quels objectifs il chercherait à atteindre.
3. **Analyze logs and data — Analyser les journaux et les données :** examiner les logs, les processus, les systèmes de fichiers, les changements sur les serveurs et les événements provenant de plusieurs machines.
4. **Seek undetected issues — Rechercher ce qui échappe aux règles :** chercher les activités qui contournent les détections existantes, les comportements suspects sans signature connue et les cas où les requêtes ne renvoient pas les données attendues.

### 2.3 Threat intelligence — Renseignement sur les menaces

Les **advisories and bulletins** sont des avis publiés par des éditeurs et chercheurs lorsqu’ils découvrent de nouvelles vulnérabilités ou techniques, tactiques et procédures (*TTPs*).

La **threat intelligence** peut être rapprochée des données internes afin de déterminer si une menace extérieure correspond à une activité observée dans l’organisation.

Exemple de démarche :
1. Un SIEM ou une plateforme d’analyse fait apparaître une activité suspecte.
2. L’analyste examine les autres hôtes pour rechercher des signes similaires.
3. Il identifie comment le processus malveillant a été exécuté sur les différentes machines.
4. Les indicateurs de compromission (*IoCs*) et les techniques observées sont documentés.
5. De nouvelles règles ou signatures peuvent être créées pour améliorer la détection future et, si pertinent, bloquer l’activité au niveau d’un IPS.

Le threat hunting améliore les capacités de détection en révélant des méthodes d’attaque qui n’étaient pas couvertes par les règles existantes. L’intégration avec la threat intelligence permet de confronter les menaces connues à l’extérieur aux journaux et données internes.

---

## 3. Incident training and testing — Formation et tests

### 3.1 Formation

La formation permet au personnel de comprendre les procédures, les responsabilités et les priorités en cas d’incident. Elle doit être adaptée aux différents rôles.

| Public | Contenu mentionné |
|---|---|
| **First responders — Premiers intervenants** | Procédures, réinstallation/recréation d’une image système (*machine re-image*), suppression d’un malware et modification des paramètres de configuration. |
| **Managers / Executives — Responsables et dirigeants** | Arbitrage risques/bénéfices, prise de décision, communication, relations avec les forces de l’ordre et les médias. |
| **End users — Utilisateurs finaux** | Reconnaître et signaler un incident suspect ; suivre une formation corrective si nécessaire. |

### 3.2 Tests et exercices

Les tests mettent en pratique les procédures de réponse aux incidents à travers des exercices ou simulations.

- **Tabletop exercise — Exercice sur table :** simulation guidée où les participants discutent d’un scénario et expliquent les actions qu’ils prendraient. Il teste les rôles, les décisions et la coordination.
- **Red team :** adopte le point de vue de l’attaquant et simule des techniques d’intrusion dans un cadre autorisé.
- **Blue team :** adopte le point de vue de la défense ; elle détecte, analyse et répond aux activités adverses.

Scénarios possibles :
- **Simple :** campagne de phishing ou infection par ransomware.
- **Complexe :** attaque en plusieurs étapes, compromission de données et coordination avec des parties externes.

Les exercices permettent de repérer les lacunes du plan de réponse, d’améliorer la coordination et de vérifier que chacun connaît son rôle.

Les notes citent Metasploit, Cobalt Strike, Kali Linux, Parrot OS et Commando OS. Ce sont des outils ou environnements associés aux activités de sécurité offensive et aux tests ; les notes ne précisent pas le rôle exact de chacun dans un exercice donné.

---

## 4. Digital forensics — Investigation numérique

### 4.1 Définition

La **digital forensics** (investigation numérique ou informatique légale) consiste à examiner des appareils et des données numériques afin de découvrir et préserver des éléments de preuve, notamment dans un contexte juridique.

Sources possibles : ordinateurs, serveurs, tablettes, smartphones, Smart TVs, supports de stockage, données réseau, journaux et archives.

### 4.2 Les étapes d’une investigation

| Étape | Objectif |
|---|---|
| **Identification** | Sécuriser la scène, éviter la contamination des preuves et déterminer quelles données collecter. |
| **Collection** | Acquérir les données de manière contrôlée et préserver leur intégrité. |
| **Analysis — Analyse** | Examiner les données pour rechercher des éléments pertinents : activité suspecte, fichiers cachés, horodatages et interactions utilisateur. |
| **Reporting — Rapport** | Documenter les résultats, les méthodes et les processus utilisés. |

L’identification consiste notamment à assurer la sécurité de la scène, empêcher toute modification des preuves, déterminer le périmètre et identifier les appareils pertinents. Il faut éviter de manipuler inutilement un appareil : certaines actions peuvent modifier des données utiles à l’enquête.

### 4.3 Order of Volatility — Ordre de volatilité

L’**ordre de volatilité** indique dans quel ordre collecter les sources de données selon leur sensibilité à la perte ou à la modification. Le principe général est de collecter d’abord les informations les plus volatiles, qui peuvent disparaître rapidement, puis les données plus persistantes.

Les notes donnent la liste suivante :

1. Registres du processeur (*CPU registers*) et mémoire cache.
2. Mémoire système (RAM), tables de routage, caches ARP, table des processus et fichiers temporaires/swap.
3. Données sur les supports de stockage persistants (HDD, SSD, clés flash).
4. Données de journalisation et de supervision à distance.
5. Configuration physique et topologie réseau.
6. Supports d’archivage.

**Attention :** l’ordre exact peut dépendre du référentiel et du contexte. Le principe essentiel est de préserver en premier les données les plus susceptibles de disparaître.

Les notes signalent que certaines clés du registre Windows, comme `HKLM\HARDWARE`, sont liées à l’état en mémoire et nécessitent une acquisition de la mémoire pour être analysées correctement.

### 4.4 Collection et acquisition des données

La **data acquisition** est la méthode et l’ensemble des outils utilisés pour créer une copie fidèle et exploitable en investigation des données d’un appareil source (par exemple la mémoire vive ou un disque dur).

Les actions de collecte citées comprennent :
- Collecter les données présentes dans la mémoire du système.
- Capturer l’état du système.
- Acquérir les données des supports de stockage.
- Capturer le trafic réseau et les journaux.
- Collecter les données distantes ou archivées.

**Disk imaging — Image disque :** copie bit à bit d’un support de stockage. Elle permet d’examiner une copie plutôt que de travailler directement sur le support original.

**File carving — Récupération par signature :** recherche et reconstruction de fichiers à partir de leurs caractéristiques internes (par exemple leurs signatures), parfois sans s’appuyer sur les entrées du système de fichiers. Cette technique peut être utile lorsque des fichiers ont été supprimés ou que le système de fichiers est endommagé.

Outils cités :
- **FTK (Forensic Toolkit) :** suite d’outils d’investigation numérique.
- **EnCase :** solution utilisée pour l’acquisition et l’analyse forensiques.

Les notes mentionnent également la capture de captures d’écran (*screenshots*). Une capture d’écran peut documenter un état visible, mais elle ne remplace pas l’acquisition forensique des données sous-jacentes.

### 4.5 Contraintes liées à la collecte

- Les politiques **BYOD** (*Bring Your Own Device*) compliquent l’acquisition : l’organisation ne possède pas nécessairement le droit légal d’examiner ou de saisir l’appareil personnel.
- Certaines données ne peuvent être collectées qu’à un moment précis, notamment lorsque le système est encore allumé.
- Une extinction ou une coupure d’alimentation peut faire disparaître des données volatiles présentes en mémoire.
- Il faut examiner les licences et la documentation des systèmes concernés avant toute acquisition.

**Important :** les notes indiquent que certaines données peuvent nécessiter un système arrêté ou une coupure d’alimentation. Cela dépend des données recherchées ; pour les données volatiles en RAM, l’extinction entraîne généralement leur perte. Il faut donc décider de la méthode de collecte avant d’éteindre la machine.

### 4.6 Chain of Custody — Chaîne de conservation des preuves

La **chain of custody** est la documentation continue de la possession, du transfert, de l’accès et du traitement d’une preuve. Elle permet de démontrer qui a manipulé la preuve, quand, pourquoi et dans quelles conditions.

Pour chaque élément, il est utile de consigner :
- L’identifiant de la preuve.
- La date et l’heure.
- La personne ayant collecté ou transféré la preuve.
- Les actions réalisées.
- Le lieu ou le système de stockage.
- Les résultats des vérifications d’intégrité, lorsqu’elles sont effectuées.

### 4.7 Legal hold et eDiscovery

**Legal hold — Obligation de préservation :** notification formelle demandant aux employés et services concernés de préserver toutes les données électroniques, documents et enregistrements potentiellement pertinents pour une procédure juridique.

Les données peuvent être modifiées, supprimées ou écrasées (*overwritten*). L’organisation doit prendre des mesures adaptées pour empêcher leur destruction ou leur modification, par exemple :
- Réaliser des copies de sauvegarde appropriées.
- Isoler certains systèmes critiques lorsque cela est nécessaire.
- Mettre en place des contrôles d’accès.
- Suspendre les mécanismes de suppression automatique concernés.

**Electronic Discovery (eDiscovery) :** processus d’identification, de collecte et de production des informations stockées électroniquement (*Electronically Stored Information*, ESI) dans le cadre d’éventuelles procédures judiciaires.

**Différence :** le legal hold impose de préserver les informations pertinentes ; l’eDiscovery organise leur identification, leur collecte, leur examen et leur production dans le cadre juridique.

### 4.8 Éthique et qualité d’une investigation

Un analyste forensique doit respecter un code d’éthique et suivre une méthode rigoureuse.

Principes :
- **Avoiding bias :** éviter les biais et les conclusions prédéterminées.
- **Repeatable actions :** réaliser des actions documentées et reproductibles.
- **Preservation of evidence :** préserver l’intégrité des preuves.
- **Independence :** faire appel, lorsque nécessaire, à un analyste indépendant de la situation afin de réduire les risques de conflit d’intérêts ou de biais.

Le rapport doit permettre de comprendre :
- **Time :** quand l’action a eu lieu.
- **Actions :** ce qui a été fait.
- **Results :** ce qui a été obtenu.

Toute preuve collectée doit être protégée contre les modifications ou manipulations non autorisées.

---

## 5. Récapitulatif des notions à connaître

| Terme | Définition courte |
|---|---|
| Incident response | Processus de gestion d’un incident de sécurité. |
| Preparation | Préparer et renforcer les systèmes avant un incident. |
| Detection | Identifier un incident. |
| Containment | Limiter sa propagation et son impact. |
| Eradication | Éliminer la menace et ses mécanismes. |
| Recovery | Restaurer les systèmes dans un état sûr. |
| Lessons learned | Tirer des enseignements après l’incident. |
| Root Cause Analysis (RCA) | Identifier la cause profonde et éviter une récidive. |
| After Action Report (AAR) | Rapport formalisant l’incident et les actions menées. |
| Threat hunting | Recherche proactive de menaces non détectées par les outils habituels. |
| TTPs | Tactics, Techniques and Procedures : tactiques, techniques et procédures des attaquants. |
| IoC | Indicator of Compromise : indice technique pouvant signaler une compromission. |
| Tabletop exercise | Exercice de simulation discuté par les participants. |
| Red team | Équipe simulant l’adversaire dans un cadre autorisé. |
| Blue team | Équipe chargée de la défense et de la réponse. |
| Digital forensics | Investigation et préservation de preuves numériques. |
| Order of volatility | Ordre de collecte des données selon leur volatilité. |
| Data acquisition | Acquisition contrôlée des données d’un support ou d’un système. |
| Disk imaging | Copie bit à bit d’un support de stockage. |
| File carving | Reconstruction de fichiers à partir de leurs signatures ou structures. |
| Chain of custody | Traçabilité de la collecte, des transferts et de la conservation des preuves. |
| Legal hold | Instruction de préserver les données pertinentes pour une procédure juridique. |
| eDiscovery | Identification, collecte et production de données électroniques à des fins juridiques. |

## 6. Points importants pour l’examen

- Le **confinement** limite l’impact ; l’**éradication** élimine la menace ; le **rétablissement** remet les systèmes en service.
- Le **retour d’expérience** intervient après la résolution de l’incident.
- La **Root Cause Analysis** cherche la cause profonde, pas seulement le symptôme visible.
- Une approche **no-blame** favorise le signalement honnête et la recherche de problèmes systémiques.
- Le **threat hunting** recherche activement les menaces qui échappent aux détections classiques.
- Une hypothèse de threat hunting peut être construite à partir de la threat intelligence et du threat modeling.
- Les exercices **tabletop**, Red Team et Blue Team permettent de tester et d’améliorer la réponse aux incidents.
- En investigation numérique, préserver les preuves et respecter l’**ordre de volatilité** est essentiel.
- Une **image disque** est une copie du support ; l’analyse doit préserver autant que possible l’original.
- La **chain of custody** assure la traçabilité des preuves.
- Le **legal hold** préserve les données ; l’**eDiscovery** organise leur collecte et leur production dans un contexte juridique.
- L’acquisition de données sur un appareil **BYOD** doit tenir compte des limites légales et des règles de l’organisation.
