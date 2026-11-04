# 30 — Investigation à partir des données

## 1. Investigating with data — Investiguer à partir des données

L’investigation en cybersécurité s’appuie sur la collecte et l’analyse de données provenant des systèmes, des applications et du réseau. Ces données permettent de détecter des activités anormales, de comprendre un événement et de déterminer s’il s’agit d’une activité malveillante.

### 1.1 SIEM — Security Information and Event Management

Un **SIEM** centralise des événements et journaux provenant de différentes sources, puis les analyse afin d’identifier des activités suspectes ou malveillantes.

Il peut notamment :
- Collecter les journaux de plusieurs systèmes.
- Normaliser et corréler les événements.
- Déclencher des alertes à partir de règles.
- Présenter les informations dans des tableaux de bord.
- Produire des rapports.

Un SIEM peut nécessiter des ressources importantes. Les notes soulignent plusieurs contraintes à prendre en compte :

| Ressource | Pourquoi elle compte |
|---|---|
| **Processing power** — Puissance de calcul | Le traitement, la normalisation et la corrélation de nombreux événements demandent des ressources CPU. |
| **Network bandwidth** — Bande passante réseau | L’envoi continu des journaux et des données des capteurs vers une plateforme centrale consomme de la bande passante. |
| **Storage** — Stockage | Les journaux peuvent représenter un volume important et doivent être conservés pendant une durée définie. |

### 1.2 Sensors — Capteurs

Un **sensor** est un composant qui observe une activité et collecte des données. Il peut surveiller un réseau, un système ou une application.

Les notes mentionnent plusieurs éléments à considérer lors de l’utilisation de capteurs :

- **Sensitivity — Sensibilité :** capacité à détecter une activité ou un changement. Une sensibilité trop élevée peut générer davantage de faux positifs ; une sensibilité trop faible peut laisser passer des événements.
- **Trends — Tendances :** évolution des événements ou des comportements dans le temps.
- **Alerts — Alertes :** notifications déclenchées lorsqu’une condition ou une règle est satisfaite.
- **Correlation — Corrélation :** rapprochement de plusieurs événements afin de repérer une relation ou un comportement qui ne serait pas évident en examinant chaque événement isolément.

### 1.3 Log files — Fichiers journaux

Un **log file** est un fichier qui enregistre des événements survenus dans un système, une application ou un réseau. Les journaux peuvent aider à reconstituer une activité et à comprendre ce qui s’est passé.

Types de journaux cités dans les notes :

| Type de journal | Informations possibles |
|---|---|
| **Network logs** | Connexions, communications et événements réseau. |
| **System logs** | Événements du système d’exploitation et de ses composants. |
| **Application logs** | Événements produits par les applications. |
| **Security logs** | Authentifications, accès et événements liés à la sécurité. |
| **Web logs** | Requêtes et accès à un serveur ou service web. |
| **DNS logs** | Requêtes de résolution de noms et réponses DNS. |
| **Authentication logs** | Connexions réussies ou échouées et événements d’authentification. |
| **Dump files** | Contenu mémoire ou informations enregistrées lors d’un plantage ou d’un diagnostic. |
| **VoIP / call manager logs** | Événements liés à la téléphonie IP et à la gestion des appels. |

### 1.4 Centralisation des journaux : Syslog et ses variantes

**Syslog** est un standard/protocole de journalisation permettant de transmettre des messages de logs vers un système central. Les organisations peuvent ainsi regrouper les journaux de différents équipements et systèmes dans un dépôt central.

Les notes citent plusieurs implémentations ou solutions :

| Outil | Description issue des notes |
|---|---|
| **rsyslog** | Solution de journalisation courante sur Linux et Unix, notamment pour recevoir, traiter et transférer des logs. |
| **syslog-ng** | Autre solution de journalisation utilisée dans les environnements Linux et Unix. |
| **NXLog** | Agent de collecte et de transfert de journaux pouvant fonctionner sur Windows, Linux et Unix. |
| **journalctl** | Outil en ligne de commande permettant de consulter les journaux conservés par `systemd-journald` sur les systèmes utilisant systemd. |

**À retenir :** Syslog désigne le mécanisme/format de journalisation ; rsyslog, syslog-ng et NXLog sont des logiciels qui peuvent collecter ou transférer les journaux. `journalctl` sert principalement à consulter le journal systemd local.

---

## 2. Network flow data — Données de flux réseau

### 2.1 Qu’est-ce qu’un flow ?

Un **network flow** décrit un échange réseau à partir de métadonnées, plutôt que de conserver nécessairement le contenu complet des paquets.

Les informations associées à un flux peuvent inclure :
- L’adresse IP source et l’adresse IP destination.
- Les ports source et destination.
- Le protocole utilisé.
- Le volume de données échangées.
- Le nombre de paquets.
- La durée du flux.
- Le chemin ou les équipements réseau traversés, selon la solution.

Les données de flux aident à répondre à des questions telles que : qui communique avec qui, à quel moment, avec quel volume de données et en utilisant quel protocole ?

### 2.2 NetFlow, sFlow et IPFIX

| Technologie | Description |
|---|---|
| **NetFlow** | Technologie de collecte et d’exportation de données décrivant les flux réseau. Elle permet notamment d’observer les sources, destinations et volumes de trafic. |
| **sFlow** | Technologie de surveillance qui s’appuie notamment sur l’échantillonnage (*sampling*) des paquets et des compteurs d’interfaces afin de fournir une vue du trafic. |
| **IPFIX** | Standard d’exportation des informations de flux IP. Il est issu des travaux de standardisation autour de l’export de flux et permet de transporter des enregistrements de flux. |

**Sampled flow / Sampling :** au lieu d’examiner systématiquement chaque paquet, un système peut en échantillonner une partie. Cela réduit la quantité de données à traiter, mais signifie que l’observation n’est pas nécessairement exhaustive.

### 2.3 Metadata — Métadonnées

Les **métadonnées** sont des informations qui décrivent une donnée ou une communication, sans nécessairement contenir son contenu.

Exemple pour une communication réseau :
- Adresse IP source et destination.
- Ports.
- Horodatage.
- Protocole.
- Durée.
- Volume de données.

**Différence importante :**
- Une capture complète de paquets (*packet capture*) peut contenir le contenu des communications.
- Les données de flux (*flow data*) décrivent principalement les caractéristiques des échanges.
- Les métadonnées donnent des informations contextuelles sur une activité.

---

## 3. Dashboards — Tableaux de bord

Un **dashboard** présente des informations de manière synthétique et visuelle afin de faciliter la surveillance et l’analyse.

Un tableau de bord de sécurité peut par exemple afficher :
- Le nombre d’alertes.
- Les événements les plus fréquents.
- Les hôtes qui génèrent le plus d’événements.
- Les tendances dans le temps.
- Les événements classés par niveau de gravité.
- Les résultats de recherches ou de corrélations.

Les notes citent **Splunk** comme exemple de plateforme pouvant être utilisée pour rechercher, analyser et visualiser des données de journaux.

---

## 4. Automated reports — Rapports automatisés

Un **automated report** est un rapport généré automatiquement à partir de données collectées et analysées par un outil.

Dans un contexte de sécurité, un rapport peut présenter des événements ou des éléments classés selon leur nature :

| Classification | Signification |
|---|---|
| **Malicious** — Malveillant | Activité identifiée comme malveillante. |
| **Suspicious** — Suspect | Activité inhabituelle ou potentiellement dangereuse qui nécessite une investigation. |
| **Benign** — Bénin | Activité considérée comme légitime ou sans danger dans le contexte analysé. |

Une classification automatisée n’est pas nécessairement une conclusion définitive : l’analyste doit examiner le contexte et valider les résultats.

---

## 5. Vulnerability scans — Analyses de vulnérabilités

### 5.1 Définition et rôle

Un **vulnerability scan** est une analyse automatisée qui recherche des vulnérabilités potentielles sur des systèmes, des applications ou des équipements.

Le scanner génère généralement un rapport présentant les vulnérabilités détectées et leur niveau de gravité.

Les notes indiquent les étapes suivantes :

1. Examiner les résultats du scan pour confirmer que les vulnérabilités détectées existent réellement sur le système.
2. Classer les vulnérabilités selon leur criticité.
3. Prioriser les hôtes vulnérables, en commençant par les plus critiques.
4. Corriger les vulnérabilités, par exemple en installant les correctifs de sécurité.
5. Si une mise à jour n’est pas possible, mettre en place des mesures compensatoires (*compensating controls*).

### 5.2 Niveaux de gravité

| Niveau | Sens général |
|---|---|
| **Critical — Critique** | Risque très élevé nécessitant généralement une priorité de traitement maximale. |
| **High — Élevé** | Risque important à traiter rapidement. |
| **Medium — Moyen** | Risque modéré à planifier selon le contexte. |
| **Low — Faible** | Risque plus limité, à traiter selon les priorités et les ressources. |

### 5.3 Ne pas se fier uniquement au score automatique

Les notes insistent sur le fait qu’il faut lire le rapport en détail et ne pas se baser uniquement sur les classements automatiques, les informations CVE ou les scores CVSS.

L’analyste doit tenir compte du contexte réel :
- La vulnérabilité est-elle réellement présente ?
- Le service vulnérable est-il activé et accessible ?
- Le système est-il exposé depuis Internet ou seulement depuis un réseau interne ?
- L’exploitation est-elle réaliste dans cet environnement ?
- Quel serait l’impact métier si le système était compromis ?

### 5.4 Exemple : RDP et Exchange Server

Les notes utilisent deux exemples pour illustrer l’importance du contexte :

- **RDP (Remote Desktop Protocol) :** une vulnérabilité sur RDP peut concerner les postes de travail ou serveurs sur lesquels le service est activé et accessible.
- **Exchange Server :** une vulnérabilité sur un serveur Exchange peut affecter les services de messagerie de toute l’organisation.

Il faut donc considérer le périmètre et l’impact potentiel du système concerné, pas seulement le score technique de la vulnérabilité.

Les notes distinguent également :
- **Authenticated attacker :** attaquant disposant déjà d’un compte ou d’identifiants valides. Cela peut être un utilisateur interne, mais aussi un attaquant externe ayant volé des identifiants ; ce n’est donc pas automatiquement un *insider threat*.
- **Unauthenticated attacker :** attaquant qui n’a pas besoin de s’authentifier pour exploiter la vulnérabilité.

Si un correctif ne peut pas être installé, des mesures compensatoires peuvent réduire le risque : restreindre l’accès réseau, désactiver le service non essentiel, appliquer des règles de filtrage, renforcer la surveillance ou isoler le système.

---

## 6. Packet captures — Captures de paquets

Une **packet capture** consiste à capturer les paquets qui circulent sur une interface ou un segment réseau afin de les examiner.

Selon le point de capture et la configuration, elle peut permettre d’observer les communications entrantes et sortantes d’un équipement ou d’un réseau.

Elle peut être utilisée pour :
- Examiner les communications réseau.
- Identifier des connexions inhabituelles.
- Étudier les protocoles et les échanges.
- Reconstituer certaines étapes d’une communication.
- Rechercher des signes d’attaque.

### 6.1 Exemple : SYN scan et connexion semi-ouverte

Les notes évoquent un attaquant qui envoie un paquet **SYN** pour initier une connexion TCP, mais ne termine pas l’établissement de la connexion.

Dans une poignée de main TCP classique :
1. Le client envoie `SYN`.
2. Le serveur répond `SYN-ACK`.
3. Le client répond `ACK`.

Dans un **SYN scan** (scan TCP semi-ouvert), l’outil d’analyse peut ne pas envoyer le dernier `ACK` après avoir reçu `SYN-ACK`. Il obtient ainsi une indication sur l’état du port sans établir une connexion TCP complète.

Un tel comportement peut être observé dans des activités de reconnaissance réseau. Il n’est pas automatiquement malveillant : il faut examiner le contexte, la source, la fréquence et les autres événements associés.

---

## 7. Récapitulatif des notions à connaître

| Terme | Définition courte |
|---|---|
| SIEM | Plateforme centralisant et analysant les événements de sécurité. |
| Sensor | Composant qui observe une activité et collecte des données. |
| Correlation | Mise en relation de plusieurs événements pour identifier un comportement. |
| Log file | Fichier enregistrant des événements. |
| Syslog | Mécanisme standard de transmission de messages de journalisation. |
| rsyslog / syslog-ng | Solutions de collecte et de traitement de journaux. |
| NXLog | Agent de collecte et de transfert de logs multi-plateforme. |
| journalctl | Outil de consultation des journaux systemd. |
| NetFlow | Technologie d’exportation de données décrivant les flux réseau. |
| sFlow | Surveillance réseau utilisant notamment l’échantillonnage. |
| IPFIX | Standard d’exportation des informations de flux IP. |
| Metadata | Données décrivant une information ou une communication. |
| Dashboard | Tableau de bord présentant les données de façon synthétique. |
| Automated report | Rapport produit automatiquement par un outil. |
| Vulnerability scan | Analyse automatisée recherchant des vulnérabilités potentielles. |
| Compensating control | Mesure alternative réduisant le risque lorsqu’une correction directe est impossible. |
| Packet capture | Capture de paquets réseau pour analyse. |
| SYN scan | Technique de reconnaissance utilisant le début de la poignée de main TCP sans terminer la connexion. |

## 8. Points importants pour l’examen

- Un **SIEM** collecte et corrèle des événements provenant de nombreuses sources.
- La collecte centralisée peut consommer de la puissance de calcul, de la bande passante et du stockage.
- Les journaux réseau, système, application, sécurité, DNS et authentification apportent des perspectives différentes.
- **Syslog** est le mécanisme ; rsyslog et syslog-ng sont des solutions qui l’implémentent ou l’utilisent.
- **journalctl** permet de consulter les journaux de systemd.
- **NetFlow, sFlow et IPFIX** décrivent des flux ou des métadonnées réseau ; ils ne sont pas équivalents à une capture complète de paquets.
- Un dashboard facilite la visualisation ; un rapport automatisé présente des résultats générés par un outil.
- Un résultat de scan de vulnérabilités doit être validé et replacé dans son contexte.
- Ne pas se fier uniquement au score CVSS : l’exposition et l’impact métier comptent également.
- Si un correctif est impossible, utiliser des mesures compensatoires.
- Une capture de paquets peut aider à analyser une activité réseau ; un SYN scan n’établit pas une connexion TCP complète.

