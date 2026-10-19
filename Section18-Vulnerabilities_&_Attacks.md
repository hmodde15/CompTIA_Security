# 23 — Vulnérabilités et attaques

## 1. Vulnérabilités matérielles et systèmes

Une **vulnérabilité** est une faiblesse pouvant être exploitée pour compromettre la confidentialité, l’intégrité ou la disponibilité d’un système ou de ses données.

Les appareils concernés peuvent inclure serveurs, postes de travail, portables, commutateurs, routeurs, appliances réseau, appareils mobiles et objets connectés (IoT).

### Firmware
Le **firmware** est un logiciel de bas niveau stocké dans un appareil matériel, par exemple un routeur ou un thermostat connecté. Il contrôle certaines fonctions de l’appareil.

Mesures : appliquer les mises à jour disponibles, auditer les paramètres, durcir les appareils et remplacer ceux qui ne peuvent plus être sécurisés.

### Catégories de systèmes vulnérables

| Notion | Définition | Risque |
|---|---|---|
| **End of Life (EOL)** | Produit arrivé à la fin de son cycle de vie selon le fournisseur | Fin ou réduction du support |
| **Legacy system** | Technologie ancienne encore utilisée | Dette technique et contrôles dépassés |
| **Unsupported system** | Produit ne recevant plus de support officiel ni de correctifs | Vulnérabilités susceptibles de rester non corrigées |
| **Unpatched system** | Système auquel des correctifs disponibles n’ont pas été appliqués | Exposition à des failles connues |
| **Hardware misconfiguration** | Paramètres d’un appareil incorrects ou non conformes | Accès inattendus ou comportement dangereux |

Ces catégories peuvent se recouper : un système ancien peut encore être pris en charge, tandis qu’un système récent peut être non corrigé ou mal configuré.

### Mesures de protection
- **Hardening** : réduire la surface d’attaque en désactivant les fonctions inutiles et en appliquant une configuration sécurisée.
- **Patching** : appliquer les correctifs de sécurité.
- **Configuration enforcement** : imposer et vérifier une configuration de référence.
- **Decommissioning** : retirer proprement un actif qui n’est plus nécessaire ou sécurisable.
- **Isolation** : limiter les communications d’un appareil.
- **Segmentation** : séparer le réseau en zones afin de limiter les flux et les mouvements latéraux.

Surveiller les mises à jour, évaluer leur impact, les déployer en temps utile, auditer les configurations, automatiser les contrôles lorsque possible et former le personnel.

## 2. Vulnérabilités Bluetooth

Le **Bluetooth** permet l’échange de données sans fil à courte portée entre appareils, sans nécessiter de connexion Internet.

| Attaque | Principe |
|---|---|
| **Appairage non sécurisé** | Connexion sans authentification ou protection suffisante |
| **Device spoofing** | Un attaquant imite un appareil légitime |
| **On-path attack** | Interception et éventuellement modification des communications |
| **Bluejacking** | Envoi de messages ou contenus non sollicités à proximité |
| **Bluesnarfing** | Accès non autorisé à certaines données, par exemple des contacts |
| **Bluebugging** | Exploitation de failles pouvant permettre de contrôler certaines fonctions |
| **BlueSmack** | Attaque par déni de service contre Bluetooth |
| **BlueBorne** | Famille de vulnérabilités Bluetooth divulguées en 2017, affectant plusieurs plateformes |

Selon la vulnérabilité et les permissions obtenues, un attaquant peut potentiellement accéder à des contacts, journaux d’appels ou messages, ou utiliser certaines fonctions. Cela dépend de l’appareil, de sa version et de ses protections.

**Bonnes pratiques :** désactiver Bluetooth lorsqu’il est inutile, désactiver la détectabilité hors appairage, installer les mises à jour, n’appairer que des appareils fiables, refuser les demandes inattendues et utiliser un mécanisme d’appairage robuste.

## 3. Vulnérabilités mobiles

- **Sideloading** : installation d’applications depuis une source autre que la boutique ou le mécanisme officiel. Cela peut contourner certaines vérifications. Privilégier les sources officielles et vérifier les autorisations demandées.
- **Rooting** : obtention de privilèges élevés, généralement sur Android.
- **Jailbreaking** : contournement de certaines restrictions de sécurité, généralement sur iOS.

Rooting et jailbreaking peuvent affaiblir les protections intégrées et faciliter l’exécution de logiciels non autorisés. Les connexions non sécurisées et les appairages inconnus représentent également des risques.

### MDM (Mobile Device Management)
Un **MDM** gère les appareils mobiles de manière centralisée. Selon la solution, il peut imposer un code de verrouillage et le chiffrement, distribuer des configurations et certificats, gérer les applications autorisées, détecter certains signes de rooting/jailbreaking, imposer un VPN ou effacer un appareil à distance. Les capacités varient selon la plateforme et la configuration.

## 4. Vulnérabilités zero-day

- **Vulnérabilité** : faiblesse exploitable d’un système.
- **Exploit** : technique ou code qui exploite une vulnérabilité.
- **Malware** : logiciel malveillant.
- **Zero-day vulnerability** : vulnérabilité exploitée ou connue des attaquants avant qu’un correctif soit disponible, ou avant que le fournisseur ait eu le temps de la corriger.
- **Zero-day exploit** : exploit tirant parti d’une vulnérabilité zero-day.
- **Zero-day attack** : attaque utilisant une telle vulnérabilité.
- **Zero-day malware** : malware exploitant ou utilisant une vulnérabilité zero-day.

Les zero-days peuvent intéresser des criminels, des agences gouvernementales et des organismes d’application de la loi ; certaines vulnérabilités et certains exploits font l’objet d’un marché, y compris clandestin.

**Réduction du risque :** appliquer les mesures d’atténuation du fournisseur, réduire l’exposition, désactiver les fonctions vulnérables si possible, isoler les systèmes à risque, renforcer la surveillance et appliquer les correctifs dès qu’ils sont disponibles. Un antivirus à jour aide, mais ne garantit pas la détection d’un exploit zero-day.

## 5. Vulnérabilités des systèmes d’exploitation

Risques évoqués dans les notes :
- systèmes non corrigés ;
- vulnérabilités zero-day ;
- mauvaises configurations ;
- exfiltration de données ;
- mises à jour malveillantes ou mécanismes de mise à jour compromis.

L’**exfiltration de données** est plutôt un objectif ou un résultat d’attaque qu’une vulnérabilité en soi. Les mises à jour doivent provenir de sources authentiques et être vérifiées.

Mesures : gestion des correctifs, durcissement, contrôle des privilèges, vérification des configurations, surveillance et protection du mécanisme de mise à jour.


## 6. Injection SQL et XML

### Injection SQL
Une **injection SQL** survient lorsque des données utilisateur sont interprétées comme une partie de la commande SQL plutôt que comme de simples données. Selon les privilèges de l’application, elle peut permettre de contourner une authentification, lire ou modifier des données, ou les supprimer.

Commandes SQL courantes :
- `SELECT` : lire des données ;
- `INSERT` : ajouter des données ;
- `UPDATE` : modifier des données ;
- `DELETE` : supprimer des données.

Exemple pédagogique de requête vulnérable :

```sql
SELECT * FROM users
WHERE user_id = 'jason'
  AND password = 'pass1234';
```

Si l’application concatène directement les valeurs fournies par l’utilisateur, une entrée spécialement conçue peut modifier la logique de la requête. `OR 1=1` illustre une condition toujours vraie, mais l’exploitabilité dépend de la façon dont l’application construit et exécute la requête.

**Prévention :**
- utiliser des requêtes paramétrées (*prepared statements*) ;
- éviter la concaténation de données utilisateur dans les requêtes ;
- limiter les privilèges du compte de base de données ;
- valider les entrées selon le format attendu ;
- utiliser un WAF comme défense complémentaire, pas comme remplacement d’une correction applicative.

La validation et la sanitisation sont utiles, mais ne remplacent pas les requêtes paramétrées.

### XML et attaques associées
Le **XML (Extensible Markup Language)** est un format structuré utilisé pour représenter et échanger des données.

- **Injection XML** : insertion de données ou de structures inattendues dans un document XML.
- **XXE (XML External Entity)** : abus des entités externes XML si le parseur les autorise ; peut entraîner la lecture de fichiers locaux ou des requêtes vers des systèmes internes.
- **XML bomb** : document conçu pour provoquer une consommation excessive de mémoire ou de processeur, par exemple via une expansion massive d’entités.
- **Snooping** : observation non autorisée d’informations ou de communications ; terme général.
- **Spoofing** : usurpation d’identité ou d’origine ; terme général.
- **Request forgery** : fabrication de requêtes pour provoquer une action non souhaitée ; le sens précis dépend du contexte.

**Prévention :** désactiver les entités externes si elles ne sont pas nécessaires, utiliser des bibliothèques XML maintenues et configurées de manière sûre, limiter la taille et la complexité des documents, valider les données lorsque c’est approprié et surveiller les erreurs de parsing.

## 7. XSS et CSRF/XSRF

### Cross-Site Scripting (XSS)
Le **XSS** survient lorsqu’une application web inclut du contenu contrôlé par un attaquant dans une page sans le traiter correctement. Un script peut alors s’exécuter dans le navigateur de la victime avec l’origine du site vulnérable.

Scénario simplifié :
1. L’attaquant repère une entrée mal validée ou mal encodée.
2. Il prépare une entrée ou une URL contenant du contenu malveillant.
3. Le site renvoie une page qui incorpore ce contenu.
4. Le navigateur exécute le script dans le contexte du site vulnérable.

Impacts possibles : modification du contenu affiché, accès à des données accessibles au script, actions effectuées au nom de la victime ou redirection. L’impact réel dépend des protections du navigateur, des cookies et du code présent.

### Types de XSS
- **XSS réfléchi (reflected / non persistant)** : la charge est renvoyée dans la réponse à une requête, sans être nécessairement stockée.
- **XSS stocké (stored / persistant)** : la charge est enregistrée, par exemple dans un commentaire, puis servie à d’autres utilisateurs.
- **XSS basé sur le DOM** : le code côté client manipule dangereusement des données non fiables dans le DOM. Des sources comme `document.location` et des fonctions comme `document.write()` peuvent contribuer à une vulnérabilité si elles sont mal utilisées.

Prévention : encodage contextuel des sorties, éviter les fonctions DOM dangereuses, valider les données, appliquer une politique CSP adaptée et tester l’application. La validation seule ne suffit pas toujours.

### Sessions, cookies et détournement de session
La **gestion de session** permet à une application de reconnaître un utilisateur entre plusieurs requêtes. Un **cookie** est une petite donnée conservée par le navigateur et envoyée au site selon des règles définies ; un cookie de session peut contenir ou référencer un identifiant de session.

- **Session hijacking** : utilisation non autorisée d’un identifiant de session valide.
- **Session prediction** : tentative de deviner un jeton de session insuffisamment aléatoire.
- Le vol de jetons, les connexions non chiffrées et les faiblesses de gestion de session peuvent également être exploités.

Mesures de protection :
- générer des jetons longs, imprévisibles et cryptographiquement sûrs ;
- utiliser HTTPS ;
- configurer les attributs de cookies appropriés, notamment `Secure`, `HttpOnly` et `SameSite` selon le besoin ;
- renouveler l’identifiant après authentification et changement de privilèges ;
- invalider les sessions lors de la déconnexion et après certains événements sensibles.

### Cross-Site Request Forgery (CSRF/XSRF)
La **CSRF** consiste à faire envoyer par le navigateur d’un utilisateur authentifié une requête non souhaitée vers un site où il possède déjà une session. Le site peut croire que la requête est légitime si les protections sont absentes.

Prévention :
- utiliser des jetons CSRF uniques et imprévisibles dans les formulaires ou requêtes concernées ;
- vérifier l’origine de la requête lorsque c’est pertinent ;
- configurer correctement `SameSite` sur les cookies ;
- demander une confirmation ou une réauthentification pour les opérations sensibles ;
- éviter d’utiliser des requêtes GET pour modifier un état.

Les jetons CSRF sont distincts des jetons de session : ils protègent contre certains scénarios de requêtes forgées, sans remplacer une gestion de session robuste.

## 8. Débordement de tampon (buffer overflow)

Un **buffer** est une zone mémoire temporaire. Un **buffer overflow** se produit lorsque le programme écrit plus de données que le tampon ne peut en contenir. Cela peut corrompre la mémoire adjacente et, selon le contexte, provoquer un crash ou permettre l’exécution de code.

La **pile (stack)** sert notamment aux appels de fonctions, aux variables locales et aux informations de retour. Dans certains scénarios, un dépassement peut écraser une adresse de retour : on parle parfois de *stack smashing*.

### ASLR
L’**Address Space Layout Randomization (ASLR)** randomise certaines adresses mémoire pour rendre plus difficile la prédiction des emplacements utiles à une exploitation. Elle réduit le risque, mais ne corrige pas la vulnérabilité elle-même.

D’autres protections comprennent les contrôles de limites mémoire, les langages sûrs en mémoire, les protections de pile et la prévention de l’exécution de données.

Les notes indiquent que les buffer overflows seraient le vecteur initial de 85 % des violations de données. Cette statistique n’est pas étayée par les éléments fournis et ne doit pas être considérée comme vérifiée.

## 9. Conditions de concurrence (race conditions)

Une **race condition** survient lorsque le résultat dépend de l’ordre ou du moment d’exécution d’événements concurrents, d’une façon non prévue par le développeur. Elle peut apparaître lorsque plusieurs threads ou processus accèdent à une ressource partagée sans synchronisation correcte.

### TOCTOU, TOC, TOU et TOE
- **TOCTOU (Time of Check to Time of Use)** : un programme vérifie l’état ou les permissions d’une ressource, puis l’utilise plus tard. Un attaquant peut modifier la ressource entre la vérification et l’utilisation.
- **TOC (Time of Check)** : moment de la vérification.
- **TOU (Time of Use)** : moment où la ressource est utilisée.
- **TOE (Time of Evaluation)** : expression parfois utilisée pour décrire une fenêtre où des données ou ressources sont évaluées ; son sens précis dépend du contexte. Le terme central à retenir est TOCTOU.

La **déréférence** consiste à accéder à l’objet ou à la valeur pointée par un pointeur ou une référence. Une mauvaise gestion de la durée de vie ou des accès concurrents peut contribuer à des vulnérabilités.

### Dirty COW
**Dirty COW** est une vulnérabilité Linux divulguée en 2016, liée à une condition de concurrence dans le mécanisme **Copy-on-Write (COW)**. Dans certaines circonstances, elle pouvait permettre à un utilisateur local d’obtenir une capacité d’écriture non prévue.

### Mutex, verrous et deadlock
- **Verrou (lock)** : mécanisme de synchronisation protégeant l’accès à une ressource partagée.
- **Mutex (mutual exclusion)** : mécanisme qui permet à un seul thread à la fois d’entrer dans une section critique protégée.
- **Deadlock / interblocage** : situation où plusieurs processus ou threads attendent indéfiniment des ressources détenues les uns par les autres.

Les verrous et mutex réduisent les race conditions s’ils sont utilisés correctement. Une mauvaise synchronisation peut toutefois créer des interblocages ou des problèmes de performance.

## 10. Synthèse pour l’examen

- Firmware = logiciel de bas niveau embarqué dans un appareil.
- EOL = fin du cycle de vie ; legacy = technologie ancienne ; unsupported = absence de support officiel ; unpatched = correctifs disponibles non appliqués.
- Hardening réduit la surface d’attaque ; patching applique les correctifs ; segmentation sépare les zones ; isolation limite les communications ; decommissioning retire un actif.
- Bluejacking = messages non sollicités ; bluesnarfing = accès non autorisé à des données ; bluebugging = contrôle via certaines failles ; BlueSmack = déni de service ; BlueBorne = famille de vulnérabilités Bluetooth.
- Sideloading installe des applications depuis des sources alternatives ; rooting/jailbreaking contourne certaines protections mobiles.
- Vulnérabilité = faiblesse ; exploit = moyen de l’exploiter ; malware = logiciel malveillant ; zero-day = vulnérabilité exploitée avant qu’un correctif ne soit disponible ou avant que le fournisseur puisse la corriger.
- SQLi exploite une construction SQL vulnérable ; les requêtes paramétrées sont une défense clé.
- XXE concerne les entités externes XML ; une XML bomb vise notamment l’épuisement des ressources.
- XSS exécute un script dans le contexte du site vulnérable ; CSRF pousse le navigateur authentifié à envoyer une requête non souhaitée.
- Un buffer overflow écrit au-delà d’un tampon ; ASLR rend les adresses moins prévisibles mais ne corrige pas le défaut.
- Une race condition dépend du timing ; TOCTOU est la fenêtre entre vérification et utilisation.
- Les verrous et mutex protègent les accès concurrents, mais une mauvaise synchronisation peut créer un deadlock.
