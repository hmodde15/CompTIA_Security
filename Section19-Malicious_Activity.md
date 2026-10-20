# 24 — Activités malveillantes et attaques

## 1. Déni de service (DoS et DDoS)

Une attaque par **déni de service (DoS)** vise à rendre un ordinateur, un serveur ou un service indisponible en épuisant ses ressources ou en perturbant son fonctionnement. Un **DDoS** poursuit le même objectif depuis plusieurs machines simultanément, parfois contrôlées dans un botnet.

| Attaque | Principe |
|---|---|
| **Flood attack** | Volume excessif de paquets ou requêtes pour saturer une ressource. |
| **Ping flood** | Envoi massif de requêtes ICMP Echo Request. |
| **SYN flood** | Envoi de demandes TCP SYN sans terminer le *three-way handshake*, laissant des connexions semi-ouvertes qui consomment des ressources. |
| **DNS amplification** | Réflexion de réponses DNS volumineuses vers une victime en usurpant son adresse IP source dans les requêtes. |
| **PDoS (Permanent Denial of Service)** | Attaque endommageant durablement un appareil, par exemple par réécriture destructrice du firmware. |
| **Fork bomb** | Création récursive de nombreux processus pour épuiser les ressources du système. |

Une fork bomb n’est pas nécessairement un ver : elle épuise les ressources par la création de processus, sans se caractériser par l’infection et la propagation autonome à d’autres systèmes.

### Protections contre les DoS/DDoS

- **Flood guards** : détectent ou limitent certains volumes anormaux de trafic.
- **Timeouts** : libèrent les ressources associées à des connexions incomplètes ou inactives ; ils ne suffisent pas seuls.
- **IPS** : peut bloquer certaines attaques si le trafic est inspecté et les règles adaptées.
- **Rate limiting** : limite le nombre de requêtes dans un intervalle.
- **Filtrage anti-usurpation** : réduit les paquets dont l’adresse source est falsifiée.
- **Protection DDoS en amont** : opérateurs, services de filtrage, CDN ou infrastructures spécialisées.
- **Infrastructure cloud élastique** : peut absorber certains pics, mais ne garantit pas la protection et peut entraîner des coûts élevés.

**Blackholing** abandonne le trafic vers une destination : cela peut atténuer une attaque mais coupe aussi le trafic légitime. **Sinkholing** redirige le trafic vers une destination contrôlée pour l’observer ou neutraliser des communications malveillantes.

## 2. Attaques DNS

Le **Domain Name System (DNS)** traduit les noms de domaine en informations utilisées par les systèmes, notamment des adresses IP.

| Attaque | Principe |
|---|---|
| **DNS cache poisoning** | Introduction de données DNS falsifiées dans un cache pour rediriger les utilisateurs. |
| **DNS amplification** | Attaque DDoS par réflexion : des réponses DNS sont envoyées à la victime à la place du demandeur réel. |
| **DNS tunnelling** | Encapsulation de données dans des requêtes/réponses DNS, parfois pour contourner des contrôles ou exfiltrer des données. |
| **Domain hijacking** | Prise de contrôle non autorisée d’un nom de domaine, souvent via le compte du registraire. |
| **DNS zone transfer attack** | Exploitation d’un transfert de zone autorisé à tort à un client non autorisé pour récupérer des enregistrements. |

**Protection DNS :**
- configurer correctement les serveurs DNS et les pare-feu ;
- utiliser **DNSSEC** pour authentifier l’origine et l’intégrité des données DNS signées (DNSSEC ne chiffre pas les requêtes) ;
- limiter les transferts de zone aux serveurs secondaires autorisés ;
- surveiller les volumes, les noms inhabituels et les requêtes anormales ;
- protéger le compte du registraire avec MFA et, si disponible, un *domain/registry lock* ;
- limiter les réponses ou le débit lorsque c’est pertinent.

## 3. Directory traversal et file inclusion

### Directory traversal

Une attaque de **directory traversal** manipule un chemin fourni à une application pour tenter d’accéder à un fichier hors du répertoire prévu.

Les séquences `../` servent souvent à remonter d’un répertoire sous Unix/Linux. Sous Windows, `..\` et parfois `../` peuvent être interprétés selon le code. Des formes encodées comme `%2e%2e%2f` peuvent représenter `../` après décodage.

**Exemple conceptuel :** une application affiche une image à partir d’un paramètre `file=photo.jpg`. Si elle ajoute directement cette valeur au chemin du dossier d’images sans vérifier le chemin final, une valeur manipulée peut tenter de remonter vers un autre répertoire et demander un fichier hors du dossier prévu. Le succès dépend du code, des permissions et des protections.

La traversée ne donne pas automatiquement accès à tous les fichiers : le processus doit avoir les droits nécessaires.

**Prévention :** éviter les chemins arbitraires fournis par l’utilisateur, préférer une liste autorisée d’identifiants de fichiers, normaliser puis vérifier le chemin final, appliquer le moindre privilège et tester les variantes d’encodage.

### File inclusion : LFI et RFI

Une vulnérabilité de **file inclusion** survient lorsqu’une application inclut ou charge un fichier à partir d’un chemin contrôlable de façon non sûre.

- **LFI (Local File Inclusion)** : tentative d’inclure un fichier local déjà présent sur le serveur.
- **RFI (Remote File Inclusion)** : tentative d’inclure une ressource distante, par exemple un script hébergé ailleurs, si l’application le permet.

Cela peut provoquer une divulgation de contenu ou une exécution de code. L’inclusion n’est pas la même chose que le téléchargement ou l’envoi d’un fichier, même si ces scénarios peuvent parfois se combiner.

## 4. Exécution de code, élévation de privilèges et rootkits

- **Arbitrary Code Execution (ACE)** : une vulnérabilité permet à un attaquant de faire exécuter du code de son choix.
- **Remote Code Execution (RCE)** : exécution de code arbitraire déclenchée à distance.
- **Élévation verticale** : passage à un niveau de privilèges supérieur, par exemple utilisateur standard vers administrateur/root.
- **Élévation horizontale** : accès aux données ou fonctions d’un autre utilisateur ayant un niveau de privilèges comparable.

Un code malveillant exécuté dans un processus hérite généralement des privilèges de ce processus, sous réserve des mécanismes d’isolation et de sécurité. Il faut donc appliquer le moindre privilège aux applications et services.

Un **rootkit** est un ensemble de composants malveillants visant notamment à dissimuler sa présence ou d’autres activités :
- **User-mode rootkit** : agit au niveau des processus et bibliothèques utilisateur ; ses capacités dépendent des droits obtenus.
- **Kernel-mode rootkit** : agit au niveau du noyau et peut manipuler des mécanismes centraux du système avec des privilèges très élevés.

**Ring 0** désigne couramment le niveau de privilège le plus élevé sur certaines architectures CPU ; les détails varient selon l’architecture et le système.


## 5. Replay attacks et sécurité des sessions

Une **replay attack** consiste à capturer une transmission valide puis à la retransmettre immédiatement ou plus tard pour répéter une action ou faire accepter une preuve déjà utilisée.

Protections : nonces, numéros de séquence, horodatages ou jetons à usage unique selon le protocole ; expiration et prévention de la réutilisation des jetons ; protocoles modernes avec protection anti-rejeu. Un simple jeton de session ne protège pas automatiquement contre tout rejeu. WPA3 améliore la sécurité Wi-Fi dans plusieurs scénarios, mais ne remplace pas les protections anti-rejeu propres aux protocoles applicatifs.

### Session hijacking, session prediction et cookie poisoning

La **gestion de session** permet à une application de reconnaître un utilisateur entre plusieurs requêtes. Les informations peuvent être stockées côté serveur et référencées par un identifiant transmis au navigateur, souvent dans un cookie.

- **Session hijacking** : utilisation non autorisée d’un identifiant de session valide.
- **Session prediction** : tentative de deviner un jeton de session prévisible.
- **Cookie poisoning** : modification de valeurs de cookie contrôlées ou interprétées par l’application afin d’en altérer le comportement ou d’exploiter une validation insuffisante.

- **Cookie de session** : généralement supprimé à la fin de la session du navigateur, selon le navigateur et ses attributs.
- **Cookie persistant** : conserve une date d’expiration ou une durée de vie au-delà de la session du navigateur.

Protections : HTTPS, jetons imprévisibles, attributs `Secure`, `HttpOnly` et `SameSite` selon le besoin, validation côté serveur des valeurs sensibles, rotation des identifiants après authentification et invalidation à la déconnexion.

## 6. Attaques de type on-path (MITM)

Une attaque **on-path** survient lorsqu’un attaquant se place sur le chemin logique des communications pour observer, intercepter ou modifier les échanges. Le terme est proche de *man-in-the-middle* (MITM).

- **ARP poisoning** : falsification des réponses ARP pour associer une adresse IP à une adresse MAC contrôlée par l’attaquant.
- **DNS poisoning** : falsification de données DNS pour rediriger une victime.
- **Rogue WAP** : point d’accès Wi-Fi non autorisé qui attire les utilisateurs et peut intercepter certains échanges.
- **Équipement réseau malveillant** : commutateur ou autre appareil non autorisé utilisé pour observer ou détourner le trafic.
- **Replay** : capture puis retransmission de données valides.
- **SSL stripping** : tentative de faire rétrograder une connexion HTTPS vers HTTP lorsque les protections le permettent.
- **Downgrade attack** : manipulation de la négociation pour forcer un protocole ou une suite cryptographique moins sûre.

Protections : TLS correctement configuré, suppression des protocoles obsolètes, vérification des certificats, sécurisation du réseau local, protections de commutation adaptées, détection des points d’accès non autorisés et HSTS pour réduire certains scénarios de SSL stripping.

## 7. Attaques par injection

Une **attaque par injection** survient lorsque des données contrôlées par l’utilisateur sont interprétées comme des instructions par un composant, par exemple un interpréteur SQL, un shell, un annuaire LDAP ou un processus.

### LDAP injection

**LDAP** est un protocole d’accès aux services d’annuaire. Une **LDAP injection** survient lorsque des données non fiables sont incorporées dans un filtre ou une requête LDAP sans traitement adapté. Elle peut modifier la logique de recherche ou de contrôle d’accès.

Prévention : utiliser les fonctions d’échappement adaptées à la bibliothèque, valider les entrées, éviter la concaténation non sûre et appliquer le moindre privilège aux comptes d’annuaire.

### Command injection

Une **command injection** se produit lorsqu’une application transmet à un interpréteur de commandes une entrée non fiable qui permet de modifier la commande exécutée. Elle peut mener à l’exécution de commandes système avec les privilèges du processus.

Prévention :
- éviter d’appeler un shell lorsque des API dédiées existent ;
- séparer les arguments plutôt que concaténer une chaîne de commande ;
- valider les entrées selon une liste de valeurs autorisées ;
- exécuter le service avec le minimum de privilèges ;
- surveiller les lancements de processus inhabituels.

La validation aide, mais la meilleure défense consiste à éviter d’interpréter les entrées utilisateur comme des commandes.

### Process injection

La **process injection** consiste à exécuter du code dans l’espace mémoire d’un autre processus vivant. Des techniques courantes comprennent :

- **DLL injection** : faire charger une bibliothèque dynamique dans un autre processus.
- **Thread execution hijacking** : détourner l’exécution d’un thread existant.
- **Process hollowing** : créer un processus puis remplacer ou modifier son contenu exécutable avant son exécution.
- **Process doppelgänging** : technique avancée abusant de mécanismes de transactions de fichiers et de création de processus sur certains systèmes Windows.
- **APC injection** : utiliser les mécanismes d’appels de procédure asynchrones pour déclencher du code dans le contexte d’un thread cible.
- **PE injection** : terme général pour des techniques d’injection ou de chargement de fichiers exécutables Windows dans un processus.

Ces techniques peuvent être utilisées par des malwares pour masquer leur exécution dans des processus légitimes. Les défenses comprennent les contrôles de privilèges, les mécanismes de sécurité du système, la détection comportementale et les solutions de sécurité des endpoints (EDR/antivirus). La détection dépend de la technique et du produit.

## 8. Indicateurs de compromission (IOC)

Un **indicateur de compromission (IOC)** est un élément observable pouvant signaler une compromission ou une activité malveillante. Un IOC isolé ne prouve pas nécessairement une attaque : il doit être corrélé avec le contexte et d’autres événements.

| Indicateur | Pourquoi il peut être suspect |
|---|---|
| **Verrouillages de comptes** | Échecs d’authentification répétés ou tentatives de deviner des mots de passe |
| **Sessions simultanées inhabituelles** | Un compte utilisé depuis des appareils ou lieux inattendus |
| **Contenu bloqué** | Accès bloqué par une politique de sécurité ; à interpréter dans son contexte |
| **Impossible travel** | Connexions depuis des lieux trop éloignés dans un délai incompatible avec un déplacement normal |
| **Consommation anormale de ressources** | Pic inhabituel de CPU, mémoire, réseau ou stockage |
| **Ressource inaccessible** | Fichiers, comptes ou services soudainement indisponibles ; possible incident ou panne légitime |
| **Journalisation hors cycle** | Événements inattendus ou changements de fréquence/horaires de journalisation |
| **Articles ou rapports de fuite** | Publication alléguant une violation de données ; information à vérifier |
| **Journaux manquants** | Arrêt de collecte, suppression ou altération possible des traces, mais aussi problème technique |

Les IOC doivent être corrélés aux journaux d’authentification, événements système, flux réseau et alertes EDR. Une observation suspecte n’est pas toujours une preuve directe de compromission.

## 9. Synthèse pour l’examen

- DoS vise l’indisponibilité ; DDoS utilise plusieurs sources.
- Ping flood sature avec des requêtes ICMP ; SYN flood exploite des connexions TCP incomplètes ; DNS amplification utilise réflexion et usurpation d’adresse source.
- PDoS vise à rendre durablement un appareil inutilisable ; une fork bomb épuise les ressources en créant des processus.
- DNS cache poisoning falsifie le cache ; DNS tunnelling transporte des données via DNS ; domain hijacking prend le contrôle d’un domaine ; le transfert de zone doit être limité.
- Directory traversal tente d’accéder à des fichiers hors du répertoire prévu ; LFI concerne les fichiers locaux, RFI les ressources distantes.
- ACE désigne l’exécution de code arbitraire ; RCE est déclenchée à distance.
- Élévation verticale = privilèges plus élevés ; horizontale = accès au niveau d’un autre utilisateur.
- Un rootkit cherche notamment à dissimuler sa présence ; le mode noyau possède des privilèges particulièrement élevés.
- Replay = retransmission de données valides ; utiliser des mécanismes anti-rejeu adaptés.
- Session hijacking réutilise une session ; session prediction devine un jeton ; cookie poisoning manipule des valeurs de cookie.
- Une attaque on-path observe ou modifie les communications ; ARP/DNS poisoning, rogue WAP et downgrade peuvent contribuer à ces scénarios.
- LDAP injection altère une requête d’annuaire ; command injection altère une commande système ; process injection exécute du code dans un autre processus.
- Un IOC est un signal d’investigation, pas nécessairement une preuve suffisante à lui seul.
