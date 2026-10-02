## 1. Sécurité des systèmes d'information (SSI)

La **sécurité des systèmes d'information (SSI)** consiste à protéger les systèmes qui permettent de **stocker, traiter ou transmettre des informations**.

Cela concerne notamment :
- ordinateurs ;
- serveurs ;
- téléphones ;
- équipements réseau ;
- applications ;
- bases de données ;
- systèmes industriels ;
- services cloud ;
- systèmes de stockage.

> **Idée à retenir :** la SSI protège l'ensemble du système permettant de gérer l'information, pas uniquement les données.

### Sécurité de l'information

La **sécurité de l'information (Information Security / InfoSec)** consiste à protéger les **informations et les données** contre :
- l'accès non autorisé ;
- la modification non autorisée ;
- la divulgation ;
- l'interruption ;
- la corruption ;
- la destruction.

> **Différence simplifiée :**
> - **SSI** → protège les systèmes qui manipulent l'information.
> - **Sécurité de l'information** → protège l'information elle-même.

Les deux notions sont cependant très liées et sont souvent utilisées de manière interchangeable dans la pratique.

---

## 2. Threat — Menace

Une **menace (Threat)** est une situation, un événement ou un acteur susceptible de causer un dommage à un système d'information ou à ses données.

### Exemples

#### Menaces externes
- cyberattaque ;
- malware ;
- ransomware ;
- phishing ;
- attaque DDoS ;
- catastrophe naturelle ;
- incendie ;
- inondation.

#### Menaces internes
- employé malveillant ;
- erreur humaine ;
- mauvaise manipulation ;
- vol d'informations ;
- utilisation abusive des privilèges.

### Conséquences possibles

Une menace peut provoquer :
- une atteinte à la **confidentialité** ;
- une atteinte à l'**intégrité** ;
- une perte de **disponibilité** ;
- une divulgation d'informations confidentielles ;
- une destruction de données ;
- une interruption de service ;
- une perte financière.

---

## 3. Vulnerability — Vulnérabilité

Une **vulnérabilité** est une faiblesse qui peut être exploitée par une menace.

### Exemples
- bug logiciel ;
- logiciel obsolète ;
- correctif de sécurité manquant ;
- mauvaise configuration ;
- mot de passe faible ;
- mauvaise configuration réseau ;
- ports inutilement exposés ;
- droits utilisateurs excessifs ;
- absence de chiffrement ;
- sécurité physique insuffisante.

### Menace ≠ vulnérabilité

- **Menace** = ce qui peut causer le dommage.
- **Vulnérabilité** = faiblesse permettant à la menace de réussir.

Exemple :

> Un attaquant est une **menace**.  
> Un serveur non patché possède une **vulnérabilité**.  
> L'exploitation de cette vulnérabilité peut créer un **risque**.

### Risque

Une menace seule ne signifie pas nécessairement qu'il existe un risque important.

> **Sans vulnérabilité exploitable, une menace peut ne pas produire de risque significatif.**

Le risque dépend notamment de la **probabilité** et de l'**impact**.

**Risque ≈ Probabilité × Impact**

---

## 4. Les piliers de la sécurité — CIA Triad

Les trois piliers fondamentaux sont appelés **CIA Triad**.

### Confidentiality — Confidentialité

Garantir que les informations ne sont accessibles **qu'aux personnes ou systèmes autorisés**.

Exemples :
- chiffrement ;
- contrôle d'accès ;
- authentification ;
- gestion des permissions.

**Question :**  
> Qui a le droit de voir cette information ?

### Integrity — Intégrité

Garantir que les données restent **exactes, complètes et non modifiées de manière non autorisée**.

Exemples :
- hash ;
- signatures numériques ;
- contrôle d'intégrité ;
- permissions ;
- journalisation.

**Question :**  
> Est-ce que l'information a été modifiée sans autorisation ?

### Availability — Disponibilité

Garantir que les systèmes et données sont **accessibles lorsque les utilisateurs autorisés en ont besoin**.

Exemples :
- sauvegardes ;
- redondance ;
- haute disponibilité ;
- RAID ;
- systèmes de secours ;
- protection contre les DDoS.

**Question :**  
> Est-ce que le service est disponible quand j'en ai besoin ?

### À retenir

- **C = Confidentiality** → empêcher les personnes non autorisées de voir les données.
- **I = Integrity** → empêcher les modifications non autorisées.
- **A = Availability** → garantir l'accès au service.

---

## 5. Authentication / Authorization / Accounting — AAA

### Authentication — Authentification

L'authentification permet de **vérifier l'identité d'un utilisateur ou d'un système**.

> **« Qui es-tu ? »**

Exemples :
- mot de passe ;
- certificat ;
- empreinte digitale ;
- MFA ;
- token.

### Facteurs d'authentification

**Something you know**  
→ mot de passe, PIN.

**Something you have**  
→ téléphone, token, carte à puce.

**Something you are**  
→ empreinte digitale, reconnaissance faciale.

### Authorization — Autorisation

L'autorisation détermine **ce qu'un utilisateur authentifié a le droit de faire**.

> **« Qu'as-tu le droit de faire ? »**

Exemple :
Un utilisateur s'authentifie correctement puis est autorisé à lire certains fichiers, mais pas à modifier la configuration du serveur.

### Différence importante

- **Authentication → Qui es-tu ?**
- **Authorization → Qu'as-tu le droit de faire ?**

### Accounting — Comptabilisation / Traçabilité

L'**accounting** consiste à enregistrer et suivre les actions réalisées sur un système.

L'objectif est notamment de savoir :
- **qui** a effectué l'action ;
- **quoi** a été fait ;
- **quand** ;
- **où** ;
- éventuellement **comment**.

Exemples :
- connexion à un système ;
- accès à un fichier ;
- modification d'un fichier ;
- modification de configuration ;
- installation d'un logiciel ;
- téléchargement ;
- tentative d'accès non autorisé ;
- modification des permissions.

### Audit trail

Un **audit trail** est une trace chronologique des actions réalisées sur un système.

Il permet notamment :
- d'effectuer des investigations ;
- de réaliser des analyses forensiques ;
- de respecter des obligations réglementaires ;
- d'identifier les responsables d'une action ;
- de détecter des comportements suspects ;
- d'améliorer la sécurité ;
- d'analyser l'utilisation des ressources.

### Outils

On peut utiliser :
- Syslog ;
- Windows Event Logs ;
- logs réseau ;
- outils d'analyse réseau ;
- SIEM ;
- solutions de monitoring.

Exemple :

**Windows Event ID 4624** → connexion réussie à un système Windows.

---

## 6. Security Control Categories

Les contrôles de sécurité peuvent être classés selon leur **nature**.

### Technical Controls

Contrôles techniques mis en œuvre grâce à du matériel ou des logiciels.

Exemples :
- firewall ;
- antivirus / EDR ;
- IDS / IPS ;
- chiffrement ;
- MFA ;
- contrôle d'accès ;
- segmentation réseau ;
- systèmes de détection.

### Managerial Controls

Contrôles liés à la **gouvernance, la stratégie et la gestion des risques**.

Ils permettent notamment d'aligner la sécurité avec :
- les objectifs de l'entreprise ;
- les besoins métiers ;
- la tolérance au risque ;
- les exigences réglementaires.

Exemples :
- politiques de sécurité ;
- analyse des risques ;
- politique de gestion des mots de passe ;
- programme de sensibilisation ;
- stratégie de réponse aux incidents ;
- politiques de gestion des fournisseurs.

### Operational Controls

Contrôles liés aux **procédures et aux opérations quotidiennes**.

Exemples :
- procédure de sauvegarde ;
- revue périodique des comptes ;
- procédure de changement de mot de passe ;
- procédure d'onboarding/offboarding ;
- formation des utilisateurs ;
- procédures de réponse aux incidents.

### Physical Controls

Contrôles permettant de protéger physiquement les personnes, équipements et locaux.

Exemples :
- vidéosurveillance ;
- badge d'accès ;
- agents de sécurité ;
- verrouillage des salles serveurs ;
- portes sécurisées ;
- destruction sécurisée de documents ;
- contrôle d'accès physique.

---

## 7. Security Control Types

Cette classification décrit **le rôle du contrôle**.

### Preventive Control — Contrôle préventif

Son objectif est d'**empêcher un incident de se produire**.

Exemples :
- firewall ;
- MFA ;
- contrôle d'accès ;
- antivirus ;
- segmentation réseau ;
- verrouillage d'une porte.

> **Avant l'incident → empêcher.**

### Deterrent Control — Contrôle dissuasif

Son objectif est de **décourager un attaquant ou un utilisateur de réaliser une action malveillante**.

Exemples :
- caméra de surveillance ;
- panneau indiquant que les locaux sont surveillés ;
- avertissement légal lors d'une connexion ;
- présence d'un agent de sécurité.

> **« Si tu essaies, tu risques d'être détecté. »**

### Detective Control — Contrôle détectif

Son objectif est de **détecter qu'un incident est en train de se produire ou s'est produit**.

Exemples :
- IDS ;
- SIEM ;
- monitoring ;
- logs ;
- caméra ;
- alertes EDR.

> **Pendant ou après l'incident → détecter.**

### Corrective Control — Contrôle correctif

Son objectif est de **corriger les conséquences d'un incident** et de remettre le système dans un état sécurisé.

Exemples :
- restauration d'une sauvegarde ;
- suppression d'un malware ;
- réinstallation d'un système compromis ;
- correction d'une mauvaise configuration.

> **Après l'incident → corriger.**

### Compensating Control — Contrôle compensatoire

Un contrôle compensatoire est une **mesure alternative** utilisée lorsqu'un contrôle de sécurité principal ne peut pas être mis en œuvre.

Exemple :

Une application ancienne ne supporte pas le MFA.

On peut mettre en place :
- segmentation réseau ;
- restrictions d'accès ;
- monitoring renforcé ;
- accès uniquement depuis un réseau spécifique ;
- comptes fortement restreints.

> **Le contrôle compensatoire réduit le risque autrement lorsque le contrôle initial n'est pas possible.**

### Directive Control — Contrôle directif

Un contrôle directif sert à **orienter ou imposer un comportement attendu**.

Exemples :
- politique de sécurité ;
- procédure de sécurité ;
- règles d'utilisation des systèmes ;
- consignes de sécurité ;
- formation et sensibilisation.

> **« Voici ce que vous devez faire. »**

---

## 8. Zero Trust

Le **Zero Trust** est un modèle de sécurité basé sur le principe :

> **« Never trust, always verify »**  
> **Ne jamais faire confiance par défaut, toujours vérifier.**

Contrairement à un modèle traditionnel où un utilisateur situé sur le réseau interne peut être considéré comme fiable, Zero Trust considère qu'aucun utilisateur, appareil ou connexion ne doit être automatiquement considéré comme fiable.

### Principes importants

- vérifier explicitement l'identité ;
- vérifier le contexte de la connexion ;
- appliquer le principe du moindre privilège ;
- limiter les accès ;
- segmenter les ressources ;
- surveiller les activités ;
- réévaluer régulièrement les autorisations.

### Exemple

Être connecté au réseau interne de l'entreprise ne signifie pas automatiquement :

> « J'ai accès à tous les serveurs. »

L'utilisateur doit être authentifié et autorisé à accéder à chaque ressource selon ses droits.

---

# 9. Gap Analysis

La **Gap Analysis** est un processus permettant d'identifier les différences entre :

- **l'état actuel** d'une organisation ;
- **l'état souhaité** ou les objectifs à atteindre.

L'objectif est d'identifier les **lacunes (gaps)** et de déterminer comment les corriger.

## Étapes

### Étape 1 — Définir le périmètre

Déterminer **ce qui doit être évalué**.

Exemples :
- réseau ;
- infrastructure ;
- processus ;
- conformité ;
- gestion des comptes ;
- sécurité des postes.

### Étape 2 — Collecter les données

Déterminer l'état actuel de l'organisation.

Exemples :
- configurations ;
- procédures ;
- architecture ;
- outils de sécurité ;
- politiques ;
- niveau de patch ;
- résultats d'audit.

### Étape 3 — Analyser les écarts

Comparer :

**État actuel ↔ État souhaité**

Puis identifier les lacunes.

### Étape 4 — Élaborer un plan d'amélioration

Définir :
- les actions nécessaires ;
- les priorités ;
- les responsables ;
- les ressources nécessaires ;
- les délais ;
- les objectifs.

---

## 10. Technical Gap Analysis

La **Technical Gap Analysis** consiste à analyser les capacités techniques de l'infrastructure et à identifier les éléments qui ne permettent pas d'atteindre le niveau de sécurité souhaité.

Exemples :
- absence d'EDR ;
- systèmes non patchés ;
- absence de segmentation ;
- équipements obsolètes ;
- absence de MFA ;
- logs insuffisants ;
- infrastructure incapable de supporter une solution de sécurité.

---

## 11. Business Gap Analysis

La **Business Gap Analysis** cherche les écarts dans les processus et capacités métier.

Exemples :
- processus de gestion des données obsolète ;
- processus de budgétisation imprécis ;
- mauvaise gestion des fournisseurs ;
- processus d'approbation insuffisant ;
- manque de ressources ;
- procédures métiers qui ne correspondent plus aux besoins actuels.

---

# 12. POA&M

**POA&M = Plan of Action and Milestones**

Un POA&M est un **plan d'action permettant de corriger les vulnérabilités, faiblesses ou écarts identifiés**.

Il permet de transformer les résultats d'une analyse ou d'un audit en **actions concrètes et suivies dans le temps**.

### Pour chaque problème, on peut définir :

- le problème identifié ;
- la vulnérabilité ou le gap ;
- le risque ;
- l'action corrective ;
- la priorité ;
- le responsable ;
- les ressources nécessaires ;
- la date cible ;
- l'état d'avancement ;
- la date de résolution.

### Exemple

| Problème | Risque | Action | Priorité | Responsable | Échéance |
|---|---|---|---|---|---|
| Serveurs non patchés | Exploitation d'une vulnérabilité | Déployer les correctifs | Haute | Équipe système | 30 jours |
| Pas de MFA | Compromission de comptes | Déployer MFA | Haute | Équipe sécurité | 60 jours |
| Logs insuffisants | Difficulté de détection | Centraliser les logs dans un SIEM | Moyenne | SOC | 90 jours |

### Objectif

Le POA&M permet de :

> **Identifier → prioriser → corriger → suivre → atteindre le niveau de sécurité souhaité.**

Il ne s'agit donc pas forcément de tout corriger immédiatement, mais de **prioriser les actions selon le risque et les ressources disponibles**.

---

# 13. À retenir pour l'examen

### Menace / Vulnérabilité / Risque

**Threat**  
→ ce qui peut causer un dommage.

**Vulnerability**  
→ faiblesse exploitable.

**Risk**  
→ possibilité qu'une menace exploite une vulnérabilité et provoque un impact.

### CIA

**Confidentiality**  
→ empêcher l'accès non autorisé.

**Integrity**  
→ empêcher les modifications non autorisées.

**Availability**  
→ garantir l'accès aux ressources.

### AAA

**Authentication**  
→ Qui es-tu ?

**Authorization**  
→ Qu'as-tu le droit de faire ?

**Accounting**  
→ Qu'as-tu fait ?

### Security Controls

**Preventive**  
→ empêcher.

**Deterrent**  
→ dissuader.

**Detective**  
→ détecter.

**Corrective**  
→ corriger.

**Compensating**  
→ remplacer/compléter un contrôle impossible à mettre en œuvre.

**Directive**  
→ orienter/imposer un comportement.

### Control Categories

**Technical** → technologie.

**Managerial** → gouvernance et stratégie.

**Operational** → procédures et opérations.

**Physical** → sécurité physique.

### Gap Analysis

> **État actuel → identifier les écarts → état souhaité → plan d'amélioration**

### POA&M

> **Transformer les écarts/vulnérabilités en actions suivies, priorisées et datées.**
