## 1. Sécurité de l’infrastructure sans fil

La sécurité Wi-Fi dépend de la portée du signal, de la couverture, de la puissance d’émission, de l’emplacement des points d’accès et des mécanismes d’authentification et de chiffrement.

- **Portée (*range*)** : distance sur laquelle un signal reste exploitable.
- **Couverture (*coverage*)** : zones dans lesquelles le réseau sans fil est utilisable.
- **Puissance du signal (*signal strength*)** : niveau du signal reçu à un emplacement.
- **Emplacement des AP** : influe sur la couverture, les interférences et la possibilité que le signal soit capté depuis l’extérieur.

Placer les points d’accès de façon à couvrir les zones nécessaires tout en limitant autant que possible la propagation hors des locaux. Une installation en hauteur et dégagée peut améliorer la propagation, mais le meilleur emplacement doit être confirmé par une étude radio. Un emplacement central peut réduire la fuite du signal vers l’extérieur, selon la configuration du bâtiment.

### ESS et interférences

Un **Extended Service Set (ESS)** regroupe plusieurs points d’accès pour fournir une couverture étendue sous un même réseau, et facilite le déplacement des clients entre AP (*roaming*) si la configuration est cohérente.

- **Co-channel interference** : plusieurs AP utilisent le même canal et partagent le temps d’antenne ; cela peut réduire les performances dans un environnement dense.
- **Adjacent-channel interference** : des canaux qui se chevauchent partiellement perturbent les transmissions parce qu’ils sont trop proches.

Dans la bande **2,4 GHz**, les canaux **1, 6 et 11** sont souvent recommandés avec une largeur de 20 MHz, car ils ne se chevauchent pas entre eux. Le choix dépend toutefois des règles locales, de la largeur de canal et de l’environnement radio.

### Site survey et heat map

Une **site survey** (étude de site Wi-Fi) sert à planifier, concevoir et valider un réseau sans fil. Elle évalue notamment :
- **Couverture** : zones où le signal est suffisant.
- **Débits (*data rates*)** : débits réalistes dans différentes zones.
- **Capacité réseau** : nombre d’utilisateurs et volume de trafic pris en charge.
- **Roaming** : passage d’un AP à un autre sans interruption excessive.

Une **heat map** représente visuellement les mesures radio sur un plan : intensité du signal, couverture et parfois utilisation des canaux ou débit. Elle aide à repérer les zones mal couvertes et les problèmes d’interférences.

## 2. Paramètres et protocoles de sécurité Wi-Fi

| Standard | Caractéristiques | Évaluation |
|---|---|---|
| **WEP** | Ancien mécanisme de chiffrement, associé historiquement à des clés de 64 ou 128 bits. | Cassé et obsolète : ne pas l’utiliser. |
| **WPA** | Première transition conçue notamment pour remplacer WEP. | Obsolète pour les nouveaux déploiements. |
| **WPA2** | Utilise généralement AES-CCMP dans les configurations modernes. | Encore répandu ; la sécurité dépend du mode et de la configuration. |
| **WPA3** | Renforce l’authentification et la protection des réseaux Wi-Fi. WPA3-Personal utilise SAE. | À privilégier lorsque les appareils le prennent en charge. |

Un mot de passe robuste reste important. **SAE (Simultaneous Authentication of Equals)**, utilisé par WPA3-Personal, améliore la résistance aux attaques par dictionnaire hors ligne par rapport à l’ancienne méthode PSK de WPA2-Personal.

**Enhanced Open / OWE (Opportunistic Wireless Encryption)** permet de chiffrer individuellement la liaison Wi-Fi de certains réseaux ouverts, notamment publics, sans mot de passe partagé. Il améliore la confidentialité contre l’écoute passive, mais n’authentifie pas fortement le point d’accès.

**GCMP (Galois/Counter Mode Protocol)** est un protocole de protection Wi-Fi utilisant AES en mode Galois/Counter Mode ; il assure chiffrement et intégrité. Son utilisation dépend du standard et de la configuration.

Les **Protected Management Frames (PMF)** protègent certaines trames de gestion contre la falsification et certaines attaques de désassociation. Elles ne protègent pas contre toutes les attaques Wi-Fi et n’empêchent pas à elles seules toute récupération de clé.

Menaces courantes :
- **Eavesdropping** : écoute non autorisée du trafic.
- **Forging / usurpation** : création de messages ou trames falsifiés, ou usurpation d’identité.
- **Tampering** : modification non autorisée des données.
- **Attaque par dictionnaire hors ligne** : tentative de deviner un secret à partir de données capturées.

Le chiffrement, une authentification robuste, une configuration à jour et la protection des trames de gestion réduisent certains risques sans éliminer toutes les menaces.

## 3. AAA, RADIUS, TACACS+ et EAP

**AAA** regroupe trois fonctions :
- **Authentication (authentification)** : vérifier l’identité.
- **Authorization (autorisation)** : déterminer les ressources et actions permises.
- **Accounting (traçabilité)** : enregistrer les connexions et activités pour le suivi et l’audit.

### RADIUS
**RADIUS** (*Remote Authentication Dial-In User Service*) est un protocole client-serveur couramment utilisé pour l’AAA, par exemple avec le Wi-Fi d’entreprise, les VPN ou les équipements réseau. Un équipement transmet la demande à un serveur central qui vérifie l’identité et renvoie une décision et, éventuellement, des attributs d’autorisation. RADIUS traditionnel utilise UDP et ne chiffre pas l’intégralité du paquet comme le ferait un tunnel chiffré moderne ; la protection dépend de l’architecture et de la méthode employée.

### TACACS+
**TACACS+** est utilisé notamment pour contrôler l’accès administratif aux équipements réseau. Il sépare plus clairement les fonctions AAA, ce qui permet un contrôle plus granulaire. Il utilise TCP et chiffre le corps des paquets, mais cela ne signifie pas que tous les éléments du trafic sont entièrement masqués.

| Élément | Usage courant | Transport | Particularité |
|---|---|---|---|
| **RADIUS** | Accès réseau utilisateur, Wi-Fi d’entreprise, VPN | UDP dans le protocole traditionnel | Centralise l’AAA ; souvent utilisé avec 802.1X/EAP. |
| **TACACS+** | Administration de routeurs, commutateurs et équipements | TCP | Sépare les fonctions AAA et permet une autorisation administrative plus granulaire. |

### EAP et IEEE 802.1X
**EAP (Extensible Authentication Protocol)** est un cadre d’authentification, pas une méthode unique.
- **PEAP** : établit un tunnel TLS, généralement authentifié par le certificat du serveur, puis utilise une méthode interne.
- **EAP-TTLS** : établit un tunnel TLS et permet une méthode d’authentification à l’intérieur.
- **EAP-FAST** : méthode conçue pour établir un tunnel protégé, historiquement associée aux *Protected Access Credentials*.

La sécurité dépend de la configuration et de la validation du certificat serveur. Accepter sans vérification un faux certificat peut exposer à une interception.

**IEEE 802.1X** est un cadre de contrôle d’accès au réseau basé sur les ports. Il permet de contrôler l’accès avant d’accorder un accès normal, souvent avec EAP entre le client et l’infrastructure et RADIUS entre l’équipement réseau et le serveur d’authentification.

## 4. Sécurité des applications

La **sécurité des applications** vise à concevoir, développer, tester et maintenir des logiciels résistants aux attaques.

### Validation des entrées (*input validation*)
La validation vérifie que les données reçues respectent les règles attendues : type, format, longueur, plage de valeurs et structure.

Bonnes pratiques :
- définir des règles précises pour les entrées acceptables ;
- valider les données aussi tôt que possible ;
- utiliser des formats autorisés lorsque c’est adapté ;
- appliquer un encodage de sortie adapté au contexte ;
- utiliser des requêtes paramétrées pour les requêtes SQL ;
- ne pas se fier uniquement à la validation côté client : valider aussi côté serveur.

La validation est importante, mais ne suffit pas à elle seule. Elle doit être complétée par une authentification et une autorisation adaptées, des communications sécurisées, une bonne gestion des erreurs et des audits de sécurité.

### Cookies et sécurité des sessions
Un **cookie** est une petite donnée stockée par le navigateur pour un site. Il peut maintenir une session ou mémoriser une préférence.

Pour les cookies de session :
- **Secure** : le navigateur n’envoie le cookie que sur HTTPS.
- **HttpOnly** : empêche l’accès au cookie via les API JavaScript habituelles, ce qui limite certains risques de vol via XSS.
- **SameSite** : limite certains envois de cookies intersites et aide à réduire le risque de CSRF selon le réglage.

Éviter d’utiliser un cookie persistant comme unique preuve d’une session durable sans contrôle adapté. Les identifiants de session doivent être aléatoires, protégés, renouvelés au moment opportun et invalidés à la déconnexion. `Secure` et `HttpOnly` ne corrigent pas à eux seuls les vulnérabilités de l’application.

### Analyse statique et dynamique du code

| Technique | Fonctionnement | Utilité |
|---|---|---|
| **Static code analysis (SAST)** | Analyse le code ou les artefacts sans exécuter l’application ; outils automatisés et revue humaine peuvent être complémentaires. | Repérer tôt des défauts de code et des vulnérabilités potentielles. |
| **Dynamic analysis (DAST)** | Teste l’application pendant son exécution, souvent via ses interfaces. | Repérer des problèmes observables dans une application en fonctionnement. |
| **Fuzzing** | Envoie de nombreuses entrées inattendues, aléatoires ou malformées. | Découvrir plantages, défauts de validation et vulnérabilités. |
| **Stress testing** | Soumet le système à une charge élevée ou à des conditions extrêmes. | Évaluer la stabilité et la capacité sous forte charge ; ce n’est pas à lui seul un test de sécurité complet. |

### Signature de code et sandboxing
La **signature de code** aide à vérifier l’identité déclarée du signataire et à détecter si le contenu a changé depuis la signature, si la chaîne de confiance est valide. Une signature valide ne garantit pas que le programme est inoffensif.

Le **sandboxing** exécute du code dans un environnement isolé pour limiter son accès au système hôte. Il peut servir aux tests ou à l’analyse de fichiers suspects, mais son efficacité dépend de la configuration et de l’absence de failles dans l’isolation.

## 5. Network Access Control (NAC)

Le **NAC** contrôle l’accès au réseau selon l’identité et/ou l’état de sécurité d’un appareil. À la connexion, un appareil peut être placé dans un réseau restreint ou une zone de quarantaine pour évaluation. S’il satisfait aux exigences, son accès peut être autorisé ou élargi.

Selon la solution, les contrôles peuvent vérifier les mises à jour, la protection antimalware ou la configuration de sécurité. Le NAC peut être matériel, logiciel ou fourni comme service.

- **Agent persistant** : logiciel installé durablement sur le terminal, qui peut communiquer avec la solution NAC et fournir des informations de conformité.
- **Agent non persistant** : évaluation sans agent installé en permanence, par exemple via un portail captif ou un composant temporaire. Un simple portail web ne peut pas forcément vérifier tous les paramètres internes du terminal.

**802.1X** peut participer au contrôle d’accès avant l’accès normal au réseau. Les règles NAC peuvent également tenir compte :
- des **facteurs temporels** : accès autorisé pendant certaines plages horaires ;
- des **facteurs géographiques** : emplacement estimé à partir du réseau, de l’adresse IP ou, lorsque disponible, du GPS ;
- des **facteurs de rôle** : accès adapté au profil de l’utilisateur ou de l’appareil ;
- des **facteurs fondés sur des règles** : application d’une politique administrative à plusieurs conditions.

L’accès peut être réévalué pendant l’utilisation si l’état du terminal ou le contexte change.

## 6. Filtrage Web et DNS

### Filtrage Web
Le **filtrage Web** limite ou contrôle les contenus accessibles sur Internet. Les méthodes courantes comprennent :
- **Filtrage par agent** : un agent sur le terminal applique ou relaie les politiques.
- **Proxy centralisé** : les requêtes passent par un intermédiaire qui applique les règles, journalise et peut inspecter certains contenus.
- **Analyse d’URL** : évaluation des adresses demandées.
- **Catégorisation du contenu** : classement des sites par thème ou niveau de risque.
- **Règles de blocage** : interdiction de domaines, d’URL, de catégories ou de types de contenus.
- **Filtrage fondé sur la réputation** : décision à partir de la réputation connue d’un domaine ou d’une ressource.

Le filtrage doit être maintenu à jour. Il peut produire des faux positifs et ne remplace pas la protection des terminaux ni la sensibilisation des utilisateurs.

### Filtrage DNS
Le **DNS filtering** bloque ou autorise des domaines au moment de leur résolution DNS. Il peut empêcher la résolution de domaines associés à des logiciels malveillants, au phishing ou à des contenus interdits par la politique de l’organisation.

Il peut être contourné si les appareils utilisent un autre résolveur ou un autre mécanisme de résolution. Il doit donc être accompagné d’une politique réseau cohérente et d’une surveillance adaptée.

## 7. Sécurité des e-mails

### SPF, DKIM et DMARC

| Mécanisme | Rôle principal |
|---|---|
| **SPF (Sender Policy Framework)** | Le domaine publie les serveurs autorisés à envoyer des e-mails en son nom ; le serveur destinataire vérifie l’autorisation pour le domaine évalué. |
| **DKIM (DomainKeys Identified Mail)** | Ajoute une signature cryptographique au message ; le destinataire la vérifie à l’aide de la clé publique publiée dans le DNS. Cela aide à vérifier l’intégrité des parties signées et l’association au domaine signataire. |
| **DMARC (Domain-based Message Authentication, Reporting and Conformance)** | Définit une politique pour les messages qui échouent aux contrôles SPF/DKIM avec alignement du domaine visible dans `From`, et permet de recevoir des rapports. |

Ces mécanismes sont complémentaires et contribuent à limiter l’usurpation de domaine. Ils ne prouvent pas qu’un message est inoffensif et n’empêchent pas toutes les formes de phishing, notamment depuis un domaine légitime compromis. Ils peuvent contribuer à la réputation et à la délivrabilité, qui dépendent aussi d’autres facteurs.

### Passerelles de messagerie
Une **passerelle de messagerie (*email gateway*)** traite les messages entrants ou sortants et applique des contrôles de sécurité et de routage.

- **Sur site (*on-premises*)** : infrastructure hébergée et gérée par l’organisation.
- **Cloud** : service hébergé par un fournisseur.
- **Hybride** : combinaison d’éléments sur site et cloud.

Les fonctions possibles incluent le filtrage antispam, l’analyse des pièces jointes et des liens, l’application de politiques, la protection contre les malwares, le chiffrement et le routage.

Le **filtrage antispam** peut combiner l’analyse du contenu, les filtres bayésiens, les listes de réputation ou de blocage fondées notamment sur le DNS, et des règles générales de filtrage ou de quarantaine. Aucune méthode n’est parfaite.

## 8. EDR, XDR et surveillance de l’intégrité

### EDR — Endpoint Detection and Response
L’**EDR** collecte et analyse des données provenant des terminaux afin de détecter, investiguer et traiter des activités suspectes. Les données peuvent inclure :
- les processus et leur arborescence ;
- les modifications du registre Windows ;
- certains événements liés à la mémoire ;
- les connexions et modèles de trafic réseau ;
- les modifications de fichiers et autres événements système.

Un cycle EDR courant comprend :
1. collecte des données ;
2. centralisation et corrélation ;
3. détection ;
4. génération d’alertes ;
5. investigation ;
6. réponse et remédiation ;
7. rapport et suivi.

Les détections peuvent s’appuyer sur des **signatures**, des **comportements**, des règles ou des modèles analytiques. Les réponses peuvent inclure l’isolation d’un terminal, la suppression d’un fichier malveillant, l’arrêt d’un processus ou la restauration d’un état sain, selon l’outil et les procédures.

### FIM — File Integrity Monitoring
Le **FIM** surveille l’intégrité de fichiers importants du système ou des applications. Il compare leur état actuel à une référence connue comme saine (*known-good baseline*) et signale les modifications inattendues. Une modification n’est pas nécessairement malveillante : les mises à jour légitimes changent aussi les fichiers.

### XDR — Extended Detection and Response
Le **XDR** étend la détection et la réponse au-delà d’un seul type de terminal en corrélant plusieurs sources, selon le produit :
- terminaux ;
- e-mails ;
- serveurs ;
- réseaux ;
- ressources cloud et espaces de travail.

L’objectif est de consolider les signaux de solutions distinctes dans une plateforme plus intégrée afin de mieux détecter les attaques multi-étapes. La couverture dépend des connecteurs et des sources intégrées.

## 9. UBA et UEBA

### UBA — User Behavior Analytics
L’**UBA** analyse les activités des utilisateurs afin de repérer les écarts par rapport à leurs habitudes. Les outils collectent des données de différentes sources, établissent une référence de comportement normal et utilisent des analyses statistiques ou du machine learning pour signaler des anomalies.

Exemples possibles :
- connexions à des heures inhabituelles ;
- volumes de téléchargement ou d’accès anormaux ;
- accès inattendus à des ressources sensibles ;
- changements de comportement pouvant évoquer un compte compromis.

### UEBA — User and Entity Behavior Analytics
L’**UEBA** étend l’analyse aux autres entités, comme les appareils, les serveurs et les comptes de service.

Avantages possibles :
1. détection plus précoce de certaines menaces ;
2. identification de comportements potentiellement liés à une menace interne ou à un compte compromis ;
3. amélioration de l’investigation et de la réponse aux incidents.

Une anomalie n’est pas une preuve de compromission. Les alertes nécessitent une investigation et leur qualité dépend des données, des modèles et du contexte métier.

## 10. Choisir des protocoles et ports sécurisés

Le choix d’un protocole doit tenir compte de l’authentification, du chiffrement, de l’intégrité, des mises à jour et du contexte d’utilisation.

### Exemples de protocoles

| Usage | À privilégier | À éviter lorsque possible |
|---|---|---|
| Web | **HTTPS** (HTTP sur TLS) | HTTP en clair pour les échanges sensibles |
| Administration distante | **SSH** | Telnet |
| Transfert de fichiers sécurisé | **SFTP** (via SSH) | FTP en clair |
| Consultation du courrier | **IMAPS** ou **POP3S** | IMAP ou POP3 sans chiffrement |
| Envoi du courrier | SMTP avec **STARTTLS** correctement configuré ou soumission SMTP sur TLS | SMTP en clair |
| Supervision réseau | **SNMPv3** avec authentification et confidentialité configurées | SNMPv1/v2c lorsque la protection est requise |

**SFTP** et **FTPS** sont différents : SFTP fonctionne au-dessus de SSH ; FTPS est FTP protégé par TLS. Le suffixe « S » n’est pas une règle universelle pour tous les protocoles.

### Réduire les ports exposés
- N’ouvrir que les ports nécessaires aux applications et aux flux autorisés.
- Bloquer les ports inutiles à l’aide des pare-feu et des contrôles réseau.
- Ne pas se fier uniquement aux ports par défaut : changer un port peut réduire le bruit de certains scans, mais ne remplace pas l’authentification forte, le chiffrement ni les mises à jour.
- Maintenir les protocoles et services à jour.
- Limiter les accès administratifs et journaliser les connexions pertinentes.

### TCP et UDP
- **TCP** est orienté connexion et fournit une livraison fiable et ordonnée, avec contrôle de flux et de congestion.
- **UDP** est sans connexion et ne garantit pas à lui seul la livraison ou l’ordre des données ; il convient à certains usages sensibles à la latence ou à des protocoles qui gèrent eux-mêmes la fiabilité.

Le choix de TCP ou UDP ne détermine pas à lui seul si un service est sécurisé : cela dépend aussi du protocole applicatif et de sa configuration.

### Plages de ports
Selon la classification courante de l’IANA :
- **Ports système / bien connus** : `0–1023`.
- **Ports enregistrés** : `1024–49151`.
- **Ports dynamiques ou privés** : `49152–65535`.

Un service peut utiliser un port non standard, mais cela ne constitue pas une protection suffisante. Contrôle d’accès, chiffrement, authentification et maintenance restent essentiels.

## 11. Points à retenir pour l’examen

- L’emplacement des AP, la couverture, la puissance et les interférences influencent la sécurité et la performance Wi-Fi.
- En 2,4 GHz, les canaux 1, 6 et 11 sont souvent utilisés pour limiter le chevauchement avec des canaux de 20 MHz.
- WEP et WPA sont obsolètes ; privilégier WPA3 si compatible, ou WPA2 correctement configuré.
- SAE est utilisé par WPA3-Personal ; OWE protège la confidentialité de certains réseaux ouverts, mais n’authentifie pas fortement le point d’accès.
- AAA signifie authentification, autorisation et traçabilité. RADIUS et TACACS+ ont des usages et caractéristiques différents.
- EAP est un cadre d’authentification ; PEAP, EAP-TTLS et EAP-FAST sont des méthodes distinctes.
- Validation des entrées, cookies sécurisés, analyses statiques/dynamiques, fuzzing, signature de code et sandboxing sont complémentaires.
- Le NAC évalue l’identité et/ou la conformité d’un terminal avant ou pendant son accès réseau.
- Le filtrage Web agit sur les requêtes ou contenus Web ; le filtrage DNS agit sur la résolution des noms.
- SPF, DKIM et DMARC sont complémentaires pour lutter contre l’usurpation d’e-mail.
- EDR se concentre sur les terminaux ; XDR corrèle plusieurs domaines ; FIM surveille l’intégrité des fichiers.
- UBA analyse le comportement des utilisateurs ; UEBA inclut aussi d’autres entités.
- Préférer les protocoles chiffrés, n’exposer que les ports nécessaires et maintenir les systèmes à jour.
