## 1. Ports et protocoles

### 1.1 Notions de base

Un **port réseau** est un point logique de communication associé à un service ou à une application sur un hôte. Les ports TCP et UDP vont de **0 à 65535**.

- **Port en écoute** : port sur lequel un service attend des connexions entrantes.
- **Connexion sortante** : connexion initiée par un client vers un service distant. Le client utilise généralement un port source éphémère et le serveur un port de destination connu.

Un port n'est pas intrinsèquement « entrant » ou « sortant » : cela dépend du point de vue et des règles réseau.

### 1.2 Catégories de ports

| Plage | Catégorie | Utilisation générale |
|---|---|---|
| 0–1023 | Ports bien connus | Services réseau courants |
| 1024–49151 | Ports enregistrés | Ports enregistrés auprès de l'IANA |
| 49152–65535 | Ports dynamiques/privés | Souvent utilisés temporairement comme ports source |

L'IANA attribue ou enregistre des numéros de ports, mais un numéro ne garantit pas à lui seul quel protocole fonctionne réellement sur ce port.

### 1.3 Ports courants

| Port(s) | Transport | Protocole / service | Fonction |
|---|---|---|---|
| 20/21 | TCP | FTP | Transfert de fichiers ; 21 sert au contrôle et 20 au canal de données en mode actif traditionnel |
| 22 | TCP | SSH, SCP, SFTP | Administration distante et transferts sécurisés via SSH |
| 23 | TCP | Telnet | Administration distante en clair ; à éviter sur un réseau non fiable |
| 25 | TCP | SMTP | Envoi et relais de courriels entre serveurs |
| 53 | TCP/UDP | DNS | Résolution de noms ; UDP est courant, TCP sert notamment aux transferts de zone et à certaines réponses |
| 69 | UDP | TFTP | Transfert simple de fichiers, notamment pour certains démarrages réseau |
| 80 | TCP | HTTP | Web sans chiffrement TLS |
| 88 | TCP/UDP | Kerberos | Authentification réseau |
| 110 | TCP | POP3 | Récupération des courriels, sans chiffrement natif |
| 119 | TCP | NNTP | Accès aux groupes de discussion |
| 135 | TCP | MS RPC Endpoint Mapper | Découverte des points de terminaison RPC Microsoft |
| 137–139 | UDP/TCP selon le service | NetBIOS | Résolution de noms, datagrammes et sessions NetBIOS |
| 143 | TCP | IMAP | Accès et gestion des courriels sur le serveur, sans chiffrement natif |
| 161 | UDP | SNMP | Requêtes de supervision et gestion des équipements |
| 162 | UDP | SNMP Trap/Inform | Notifications SNMP vers un gestionnaire |
| 389 | TCP/UDP | LDAP | Accès aux services d'annuaire |
| 443 | TCP, ou UDP avec QUIC | HTTPS | Web sécurisé ; HTTP/3 utilise QUIC sur UDP |
| 445 | TCP | SMB | Partage de fichiers, d'imprimantes et services Windows |
| 465 | TCP | SMTP sur TLS implicite | Soumission de courriels avec TLS dès la connexion |
| 514 | UDP traditionnellement | Syslog | Transmission de journaux ; le mode UDP traditionnel n'est pas chiffré |
| 587 | TCP | SMTP Submission | Soumission de courriels, généralement avec STARTTLS |
| 636 | TCP | LDAPS | LDAP sur TLS |
| 993 | TCP | IMAPS | IMAP sur TLS |
| 995 | TCP | POP3S | POP3 sur TLS |
| 1433 | TCP généralement | Microsoft SQL Server | Connexions à SQL Server |
| 1645/1646 | UDP historiquement | RADIUS (anciens ports) | Anciens ports ; les ports standard sont 1812/1813 |
| 1812/1813 | UDP | RADIUS | 1812 pour l'authentification/autorisation ; 1813 pour l'accounting |
| 3389 | TCP/UDP | RDP | Accès au Bureau à distance Windows |
| 6514 | TCP | Syslog sur TLS | Transmission sécurisée des journaux Syslog |

**À retenir :**
- SSH (22) est à privilégier à Telnet (23).
- HTTP (80) ne fournit pas TLS ; HTTPS (443) le fait.
- DNS et Kerberos peuvent utiliser TCP et UDP.
- SNMP : 161 pour les requêtes, 162 pour les notifications.
- LDAP (389) et LDAPS (636) ; IMAP (143/993) ; POP3 (110/995).
- Un port indique un service probable, pas une certitude : vérifier le trafic et la configuration.

## 2. Pare-feu (firewalls)

Un **pare-feu** applique des règles afin d'autoriser, refuser ou inspecter des flux réseau entre des zones ou des hôtes. Il peut être matériel, logiciel ou virtuel.

### 2.1 Principales familles

| Type | Principe | Points forts / limites |
|---|---|---|
| Filtrage de paquets sans état (*stateless*) | Examine les en-têtes : IP, protocole et ports | Rapide et simple ; ne suit pas le contexte de connexion |
| Pare-feu à états (*stateful*) | Suit l'état des connexions et tient compte des sessions établies | Plus contextuel ; consomme davantage de ressources |
| Filtrage dynamique | Adapte temporairement les règles selon le contexte et les connexions | Plus flexible ; dépend de l'implémentation |
| Proxy / passerelle applicative | Relaye ou termine les connexions et comprend le protocole applicatif | Inspection fine ; peut ajouter latence et complexité |
| Proxy de circuit | Contrôle l'établissement des sessions sans forcément inspecter le contenu applicatif | Contrôle des connexions, inspection du contenu limitée |
| Proxy noyau (*kernel proxy*) | Traite ou relaie des flux au moyen de mécanismes du noyau | Terme dépendant du produit ; l'architecture varie |
| NGFW (*Next-Generation Firewall*) | Combine généralement filtrage à états, inspection approfondie, visibilité applicative et prévention d'intrusion | Visibilité plus riche ; débit dépendant du matériel, du trafic et des fonctions activées |
| UTM (*Unified Threat Management*) | Regroupe plusieurs fonctions : pare-feu, antivirus de passerelle, filtrage web, VPN, prévention d'intrusion, etc. | Administration intégrée ; peut créer un point unique de panne et une charge de traitement |
| WAF (*Web Application Firewall*) | Analyse les requêtes HTTP(S) pour protéger les applications web | Complète le pare-feu réseau ; ne le remplace pas |

L'**inspection approfondie des paquets (DPI)** analyse le contenu ou les couches supérieures du trafic, au-delà des seuls en-têtes. Elle peut améliorer la détection mais consommer des ressources et introduire de la latence. Un NGFW n'est donc pas automatiquement rapide dans toutes les conditions.

UTM et NGFW se recouvrent largement selon les fournisseurs. Il ne faut pas retenir comme règle absolue que tous les UTM utilisent des moteurs séparés ou que tous les NGFW utilisent un seul moteur.

### 2.2 WAF : en ligne ou hors bande

- **En ligne (*inline*)** : le WAF se trouve sur le chemin du trafic et peut bloquer une requête avant qu'elle n'atteigne le serveur.
- **Hors bande (*out-of-band*)** : il reçoit une copie du trafic, par exemple via un port miroir. Il peut analyser et alerter, mais ne bloque généralement pas directement la requête sur ce chemin.

### 2.3 DMZ et sous-réseau filtré

Une **DMZ** (zone démilitarisée) héberge souvent des services accessibles depuis l'extérieur : serveurs web, relais de messagerie ou DNS publics. Des règles séparent la DMZ du réseau interne afin qu'une compromission d'un serveur exposé ne donne pas directement accès aux ressources internes.

Un **hôte à double interface (*dual-homed host*)** est plus précisément un système doté de deux interfaces réseau. Ce n'est pas un synonyme universel de DMZ : une DMZ est une zone réseau qui peut être conçue de plusieurs façons.

### 2.4 Listes de contrôle d'accès (ACL)

Une **ACL** est une liste ordonnée de règles appliquées notamment sur des routeurs, commutateurs ou pare-feu. Une règle peut préciser le protocole, les adresses source et destination, les ports et l'action (autoriser/refuser).

Bonnes pratiques :
1. N'autoriser que les flux nécessaires (moindre privilège).
2. Vérifier l'ordre des règles.
3. Prévoir un refus final implicite ou explicite selon l'équipement.
4. Journaliser les refus importants sans générer un volume excessif de logs.
5. Tester et documenter les modifications.

## 3. IDS et IPS

- **IDS (*Intrusion Detection System*)** : détecte une activité suspecte et produit des alertes ou des journaux ; il ne bloque pas nécessairement le trafic.
- **IPS (*Intrusion Prevention System*)** : inspecte le trafic et peut bloquer ou limiter automatiquement une activité détectée.

### 3.1 Types de systèmes

| Type | Emplacement / portée | Exemple |
|---|---|---|
| NIDS | Segment réseau ou point d'observation du trafic | Détecter un balayage de ports |
| HIDS | Sur un hôte : système, fichiers et journaux selon l'agent | Détecter des modifications de fichiers suspectes |
| WIDS | Environnement Wi-Fi | Détecter des points d'accès non autorisés ou des attaques sans fil |

Un NIDS ne voit que le trafic auquel il a accès. L'emplacement du capteur et le chiffrement influencent sa visibilité.

### 3.2 Méthodes de détection

**Par signatures**
- Recherche des motifs ou règles associés à des attaques connues.
- Avantage : précise pour les menaces connues.
- Limite : peut manquer une attaque inconnue ou une variante différente.
- Le *pattern matching* recherche des motifs définis dans les données.

**Comportementale / par anomalie**
- Compare l'activité à une référence (*baseline*) ou à un comportement attendu.
- Peut utiliser des méthodes statistiques, l'analyse du trafic, la conformité aux protocoles, des règles/heuristiques ou l'analyse applicative.
- Peut détecter des écarts inconnus, mais générer des faux positifs lorsque le comportement légitime change.

La détection *stateful* tient compte de l'état ou de la séquence des échanges ; ce n'est pas simplement un synonyme universel de détection par baseline d'un HIDS.

## 4. Équipements réseau spécialisés

### 4.1 Répartiteur de charge (*load balancer*)

Un **load balancer** distribue les requêtes entre plusieurs serveurs selon une politique de répartition et l'état des services. Selon le produit, il peut effectuer des contrôles de santé (*health checks*), retirer un serveur indisponible, terminer TLS, compresser ou mettre en cache du contenu. Pour éviter un point unique de panne, le répartiteur lui-même peut devoir être redondé.

### 4.2 Serveur proxy

Un **proxy** sert d'intermédiaire entre un client et un serveur. Selon sa configuration, il peut filtrer les requêtes, mettre du contenu en cache, appliquer une authentification, masquer certaines adresses et journaliser les accès. Il ne garantit pas automatiquement la sécurité : il doit être configuré, maintenu et supervisé.

### 4.3 Capteurs réseau

Les **capteurs** collectent ou observent des données réseau pour détecter des anomalies, analyser des incidents ou surveiller les performances. Ils peuvent être passifs ou en ligne. La visibilité dépend du point de capture et de l'accès aux métadonnées ou au contenu déchiffré.

### 4.4 Serveur de rebond (*jump server / bastion*)

Un **jump server** est un point d'accès contrôlé permettant aux administrateurs d'atteindre des systèmes dans des zones sensibles. Bonnes pratiques : MFA, accès nominatif limité, journalisation, durcissement, mises à jour et interdiction des accès directs inutiles. C'est un actif critique à protéger.

## 5. Sécurité des ports de commutateur

### 5.1 Port security et table CAM

La **port security** limite les adresses MAC autorisées sur un port de commutateur, selon les capacités du modèle.

La **table CAM** associe des adresses MAC aux ports afin d'acheminer les trames. Elle n'est pas à elle seule un mécanisme de contrôle d'accès ; la port security peut s'appuyer sur les adresses MAC apprises ou configurées.

Le **sticky MAC learning** permet au commutateur d'apprendre automatiquement certaines adresses MAC et de les conserver comme adresses autorisées. Le comportement dépend de l'équipement.

Limite : une adresse MAC peut être usurpée. La port security réduit certains abus mais ne remplace pas une authentification forte.

### 5.2 IEEE 802.1X, RADIUS et TACACS+

**802.1X** fournit un cadre d'authentification au niveau du port, sur réseau filaire ou Wi-Fi.

- **Supplicant** : client qui demande l'accès.
- **Authenticator** : commutateur ou point d'accès qui contrôle le port.
- **Serveur d'authentification** : vérifie les identifiants, souvent via RADIUS.

**EAP (*Extensible Authentication Protocol*)** est un cadre permettant différentes méthodes :

| Méthode | Principe général | Point d'attention |
|---|---|---|
| EAP-MD5 | Défi-réponse fondé sur MD5 | Pas d'authentification mutuelle ni de tunnel TLS ; à éviter dans un déploiement moderne |
| EAP-TLS | Authentification TLS par certificats client et serveur | Robuste si les certificats sont bien gérés |
| EAP-TTLS | Tunnel TLS puis authentification interne | Valider le certificat serveur et choisir une méthode interne adaptée |
| PEAP | Tunnel TLS avant authentification interne | Courant en entreprise ; valider le certificat serveur |
| EAP-FAST | Tunnel TLS et mécanismes de protection des identifiants selon la configuration | Dépend du déploiement |
| EAP-LEAP | Ancienne méthode propriétaire Cisco | Faible et obsolète ; ne pas la choisir pour un nouveau déploiement |

**RADIUS** centralise souvent l'authentification, l'autorisation et la comptabilisation (*AAA*) pour l'accès réseau. Les ports standards sont UDP 1812 (authentification) et UDP 1813 (accounting).

**TACACS+** est un protocole distinct, souvent utilisé pour contrôler l'accès administratif aux équipements réseau. Il utilise habituellement TCP 49. RADIUS et TACACS+ ne sont pas interchangeables dans tous les contextes.

## 6. Sécuriser les communications

### 6.1 VPN

Un **VPN** crée un chemin logique protégé sur un réseau qui n'est pas entièrement fiable. Selon le protocole et sa configuration, il peut assurer confidentialité, intégrité et authentification.

| Type | Description |
|---|---|
| Site-à-site | Relie les réseaux de sites différents au moyen de passerelles VPN |
| Client-à-site / accès distant | Connecte l'appareil d'un utilisateur distant au réseau de l'organisation |
| VPN sans client (*clientless*) | Fournit certains accès via un navigateur, généralement à des applications précises |

**Full tunnel** : tout ou presque tout le trafic IP prévu du client passe dans le VPN. Cela facilite la centralisation du filtrage et de la supervision, mais peut augmenter la charge et la latence.

**Split tunnel** : seul le trafic destiné aux réseaux ou services définis passe dans le VPN ; le reste emprunte une autre route, souvent directement vers Internet. Les performances peuvent être meilleures, mais le trafic hors VPN dépend des protections locales.

Un VPN ne rend pas automatiquement un poste sûr : la sécurité dépend aussi de l'authentification, de l'état des terminaux, des routes, des règles et de la supervision.

### 6.2 TLS et DTLS

- **TLS (*Transport Layer Security*)** protège les échanges par chiffrement, intégrité et authentification selon la configuration. HTTPS est HTTP protégé par TLS.
- TLS est couramment utilisé au-dessus de TCP.
- **DTLS** adapte des mécanismes similaires aux transports datagrammes, notamment UDP. Il n'est pas systématiquement plus rapide que TLS dans tous les scénarios.

### 6.3 IPsec

**IPsec** est une suite de protocoles permettant de protéger les communications IP. Les objectifs possibles comprennent confidentialité, intégrité, authentification de l'origine et protection contre le rejeu.

#### Établissement du tunnel

Dans le déroulement classique décrit par IKEv1 :
1. Un poste du site A envoie du trafic vers un poste du site B.
2. Les passerelles négocient les paramètres de sécurité et les associations de sécurité (*Security Associations*, SA) via IKE.
3. La phase 1 établit un canal de négociation sécurisé ; la phase 2 négocie les SA IPsec qui protègent les données.
4. Le trafic est transféré de manière sécurisée.
5. Les SA sont renouvelées ou supprimées selon les politiques.

IKEv2 utilise une séquence différente, souvent décrite par IKE_SA_INIT et IKE_AUTH.

#### Modes IPsec

| Mode | Fonctionnement | Utilisation typique |
|---|---|---|
| Transport | Protège principalement la charge utile du paquet IP original ; l'en-tête IP original reste visible | Souvent hôte-à-hôte |
| Tunnel | Encapsule le paquet IP original dans un nouveau paquet IP | Très courant entre passerelles VPN site-à-site |

Les modes ne sont pas strictement réservés à un seul type de VPN : le choix dépend de l'architecture.

#### AH et ESP

- **AH (*Authentication Header*)** apporte intégrité, authentification de l'origine et protection anti-rejeu selon la configuration, mais ne chiffre pas les données.
- **ESP (*Encapsulating Security Payload*)** peut fournir chiffrement, intégrité, authentification de l'origine et protection anti-rejeu selon les algorithmes et paramètres.

Les notes évoquent AH et ESP ensemble, mais ce n'est pas une obligation générale : ESP suffit souvent à fournir les protections recherchées. AH peut aussi être difficile à combiner avec la traduction d'adresses (NAT).

#### MTU et fragmentation

La **MTU** est la taille maximale d'un paquet transporté sur une liaison sans fragmentation au niveau considéré. Une MTU Ethernet courante est de 1500 octets, mais ce n'est pas universel.

L'encapsulation VPN ajoute des en-têtes et réduit la place disponible pour les données. Cela peut provoquer fragmentation, baisse de performance ou problèmes de connectivité. Il faut diagnostiquer MTU/MSS et ajuster la configuration ; 1400 octets peut être un point de départ dans certains environnements, pas une règle universelle. Les *jumbo frames* ne sont utilisables que si le chemin les prend en charge de bout en bout.

## 7. SD-WAN et SASE

### 7.1 SD-WAN

Le **SD-WAN (*Software-Defined Wide Area Network*)** est une approche logicielle de gestion d'un réseau étendu. Elle permet d'optimiser les chemins entre sites, centres de données et services cloud en fonction de politiques et de mesures telles que latence, perte et disponibilité.

Les connexions sous-jacentes peuvent comprendre Internet haut débit, liens cellulaires, liaisons micro-ondes et MPLS.

**MPLS** est une technologie de transfert utilisant des labels pour acheminer le trafic au sein d'un réseau opérateur. Elle peut fournir des caractéristiques de service prévisibles, mais n'est pas automatiquement chiffrée de bout en bout.

Le SD-WAN centralise la gestion et peut combiner plusieurs types de liens. Il ne remplace pas à lui seul les contrôles de sécurité.

### 7.2 SASE

**SASE (*Secure Access Service Edge*)** regroupe des fonctions réseau et de sécurité fournies principalement comme services cloud. Selon l'offre, il peut intégrer :
- SD-WAN ;
- pare-feu en tant que service (FWaaS) ;
- accès réseau Zero Trust (ZTNA) ;
- passerelle web sécurisée (SWG) ;
- courtier de sécurité d'accès au cloud (CASB) ;
- protection contre les menaces et prévention des pertes de données.

SASE vise à fournir un accès sécurisé aux utilisateurs distants, utilisateurs mobiles, agences et applications cloud. Les composants précis varient selon le fournisseur.

**ZTNA** donne un accès basé sur l'identité, le contexte et les politiques, plutôt qu'un accès réseau large par défaut. Un **CASB** applique des contrôles de sécurité à l'utilisation des services cloud : visibilité, politiques d'accès et protection des données, par exemple.

## 8. Conception de l'infrastructure

### 8.1 Placement et zones de sécurité

Les équipements doivent être placés selon les flux autorisés et les niveaux de confiance. On peut distinguer :
- services accessibles depuis Internet ;
- ressources internes des employés ;
- DMZ ;
- stockage de données sensibles ;
- zones d'administration.

Le cloisonnement réduit les communications inutiles et limite les mouvements latéraux en cas de compromission.

### 8.2 Surface d'attaque

La **surface d'attaque** regroupe les points d'entrée et interfaces par lesquels un attaquant pourrait accéder à un environnement, y introduire des données ou en extraire.

Pour la comprendre, il faut inventorier les services exposés, appareils, comptes, interfaces d'administration, connexions externes et flux entre zones.

### 8.3 Méthodes de connectivité

Le réseau peut utiliser des connexions filaires, Wi-Fi, cellulaires, satellites ou des liaisons micro-ondes. Chaque méthode présente des contraintes de disponibilité, latence, portée et sécurité. La protection doit tenir compte du support, des équipements et du chemin complet.

### 8.4 Équipements actifs, passifs et en ligne

- **Équipement actif** : traite ou transmet les signaux et participe au fonctionnement du réseau, par exemple un commutateur ou un routeur.
- **Équipement passif d'observation** : collecte une copie du trafic sans être sur le chemin de transfert, par exemple un TAP ou une capture via port miroir.
- **Équipement en ligne (*inline*)** : placé directement dans le chemin du trafic ; il peut le laisser passer ou le bloquer selon sa fonction.

Un capteur passif peut observer sans interrompre le trafic, mais ne bloque généralement pas lui-même les paquets observés.

### 8.5 Modes de panne

- **Fail-open** : en cas de panne, le trafic continue de passer. Cela favorise la disponibilité, mais peut supprimer une protection.
- **Fail-closed** : en cas de panne, le trafic est bloqué. Cela favorise l'application de la politique de sécurité, mais peut interrompre le service.

Le choix dépend du risque, de la criticité du service, de la fonction de l'équipement et des exigences de continuité.

## 9. Contrôles d'infrastructure

Un **contrôle de sécurité** est une mesure technique, organisationnelle ou physique destinée à réduire un risque et à protéger les actifs.

### 9.1 Principes clés

- **Moindre privilège** : accorder uniquement les droits nécessaires, pour la durée nécessaire.
- **Défense en profondeur** : combiner plusieurs couches de protection afin qu'une défaillance ne suffise pas à compromettre l'ensemble.
- **Gestion du cycle de vie fondée sur le risque** : sélectionner, déployer, maintenir, surveiller et retirer les équipements en tenant compte de leur criticité.
- **Principe de conception ouverte** : la sécurité ne doit pas dépendre du secret de la conception ou de l'algorithme ; les secrets doivent rester les clés, identifiants et autres éléments prévus à cet effet.

### 9.2 Méthodologie de mise en place des contrôles

1. **Évaluer l'état actuel** : inventorier les actifs, règles, flux et mesures existantes.
2. **Réaliser une analyse des écarts (*gap analysis*)** : comparer la situation actuelle aux exigences ou à l'état cible.
3. **Définir des objectifs mesurables** : préciser le risque à réduire et le résultat attendu.
4. **Comparer aux références pertinentes (*benchmarking*)** : utiliser des standards, référentiels ou environnements comparables.
5. **Analyser les coûts et bénéfices** : considérer les coûts de déploiement, d'exploitation et de maintenance ainsi que la réduction du risque.
6. **Impliquer les parties prenantes** : associer sécurité, réseau, systèmes, métiers et responsables de service.
7. **Mettre en place une supervision et des boucles de retour** : mesurer l'efficacité, examiner les alertes et ajuster les contrôles.

## 10. Synthèse pour l'examen

- Un port identifie un point logique de communication ; les ports bien connus vont de 0 à 1023.
- Un pare-feu applique des règles ; un IDS détecte et alerte, tandis qu'un IPS peut bloquer.
- Une DMZ héberge des services exposés et les isole du réseau interne.
- Une ACL décrit les flux autorisés ou refusés ; l'ordre des règles est important.
- Un WAF protège spécifiquement les applications web ; un NGFW fournit des fonctions réseau et applicatives plus larges.
- NIDS = observation réseau ; HIDS = observation sur l'hôte ; WIDS = détection dans l'environnement Wi-Fi.
- 802.1X contrôle l'accès au port ; le supplicant est le client, l'authenticator le commutateur ou point d'accès, et le serveur d'authentification vérifie les identifiants.
- RADIUS est fréquent pour l'accès réseau ; TACACS+ est souvent employé pour l'administration des équipements.
- Un VPN site-à-site relie des réseaux ; un VPN client-à-site relie un utilisateur distant à l'organisation.
- Full tunnel envoie le trafic prévu dans le VPN ; split tunnel ne fait passer dans le VPN que les routes définies.
- TLS protège les échanges ; DTLS adapte des mécanismes similaires aux transports datagrammes.
- IPsec peut fournir confidentialité, intégrité, authentification et protection anti-rejeu. AH ne chiffre pas ; ESP peut chiffrer.
- Le mode tunnel encapsule le paquet IP original ; le mode transport conserve l'en-tête IP original.
- Le SD-WAN optimise les chemins WAN ; SASE combine des fonctions réseau et de sécurité, souvent dans le cloud.
- Fail-open privilégie la continuité du trafic en cas de panne ; fail-closed privilégie le blocage.
- Le moindre privilège, la défense en profondeur, le cloisonnement et la supervision sont des principes fondamentaux.
