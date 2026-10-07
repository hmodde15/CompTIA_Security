# Gouvernance, politiques, standards, procédures et conformité

## 1. Gouvernance

### Définition

La **gouvernance** désigne l'ensemble des structures, règles, responsabilités, processus et pratiques permettant de diriger et de superviser une organisation.

Dans le contexte informatique, la gouvernance IT vise notamment à garantir que :

- l'infrastructure IT est alignée avec les objectifs de l'organisation ;
- les ressources IT sont correctement gérées ;
- les responsabilités sont clairement définies ;
- les politiques et procédures sont cohérentes avec les objectifs stratégiques ;
- l'organisation respecte les exigences légales, réglementaires et contractuelles.

La gouvernance fait partie du modèle **GRC** :

> **GRC = Governance, Risk Management, Compliance**

### Gouvernance et alignement stratégique

La gouvernance permet de s'assurer que les activités IT soutiennent réellement les objectifs de l'organisation.

Elle ne concerne donc pas uniquement la technique : elle englobe également les décisions, les responsabilités, les règles et la manière dont l'organisation fonctionne.

### Monitoring et révision de la gouvernance

La gouvernance doit évoluer avec l'organisation et son environnement.

**Monitoring :**
- examiner régulièrement l'efficacité du framework de gouvernance ;
- identifier les forces et les faiblesses ;
- vérifier que les règles et pratiques restent adaptées.

**Revision :**
- mettre à jour le framework de gouvernance ;
- corriger les lacunes identifiées ;
- adapter les politiques et procédures aux nouveaux besoins.

### Exemple : télétravail

Lorsqu'une organisation met en place le télétravail, elle peut devoir revoir :

- ses politiques de sécurité ;
- ses procédures ;
- les règles d'accès aux ressources ;
- la gestion des équipements ;
- les contrôles de sécurité.

De la même manière, lorsqu'une réglementation concernant le traitement des données évolue, l'organisation doit revoir sa gouvernance afin de rester conforme.

---

# 2. Structures de gouvernance

## Board of Directors

Le **Board of Directors** est un groupe de personnes élu par les actionnaires afin de superviser la direction et la gestion de l'organisation.

Il joue un rôle important dans la supervision stratégique et la gouvernance.

## Committees

Les **committees** sont des sous-groupes du conseil d'administration ayant chacun un domaine d'intérêt particulier.

Ils peuvent par exemple se concentrer sur :

- la sécurité ;
- les risques ;
- l'audit ;
- la conformité.

## Government Entities

Les **government entities** établissent des lois et réglementations auxquelles les organisations doivent se conformer.

Ces exigences peuvent avoir un impact direct sur :

- les opérations ;
- la sécurité ;
- la protection des données ;
- les ressources humaines ;
- les contrats.

## Centralized vs Decentralized

### Centralized structure

Dans une structure **centralisée**, le pouvoir de décision est principalement concentré aux niveaux supérieurs de management.

### Decentralized structure

Dans une structure **décentralisée**, le pouvoir de décision est distribué entre différents niveaux ou différentes entités de l'organisation.

Le choix entre une structure centralisée ou décentralisée dépend notamment de la taille, des objectifs et du fonctionnement de l'organisation.

---

# 3. Policies — Politiques

Une **policy** définit les règles et orientations générales qu'une organisation souhaite appliquer.

Une policy indique principalement **ce qui doit être fait** et **pourquoi**.

## Acceptable Use Policy — AUP

La **politique d'utilisation acceptable** définit les règles concernant l'utilisation acceptable des ressources informatiques de l'organisation.

Elle peut notamment encadrer :

- l'utilisation d'Internet ;
- les systèmes informatiques ;
- les équipements professionnels ;
- les ressources réseau ;
- les comptes utilisateurs.

## Information Security Policy

La **politique de sécurité de l'information** définit les grandes orientations de sécurité de l'organisation.

Elle peut couvrir :

- la classification des données ;
- le contrôle d'accès ;
- le chiffrement des données ;
- la sécurité physique ;
- la protection des informations.

## Business Continuity Policy

La politique de **continuité des activités** définit les orientations permettant à l'organisation de maintenir ses activités malgré une perturbation.

## Disaster Recovery Policy

La politique de **reprise après sinistre** concerne la restauration des systèmes et des services après un événement perturbateur.

## Incident Response Policy

La politique de **réponse aux incidents** définit le cadre général permettant de répondre aux incidents de sécurité.

Une politique bien définie permet notamment de :

- réagir rapidement ;
- définir les responsabilités ;
- limiter les dommages ;
- réduire les temps d'arrêt.

## SDLC Policy

Une **SDLC Policy** encadre le cycle de développement logiciel.

Elle permet d'intégrer des exigences de qualité et de sécurité dans les différentes phases du développement.

## Change Management Policy

La politique de **gestion des changements** définit le cadre dans lequel les changements doivent être demandés, évalués, approuvés, réalisés et suivis.

---

# 4. Standards

Les **standards** fournissent un cadre plus précis pour mettre en œuvre les exigences définies par les politiques.

> **Policy = ce que l'organisation exige**
>
> **Standard = exigences précises à respecter**
>
> **Procedure = étapes à suivre pour réaliser une tâche**

Les standards font partie intégrante du framework de gouvernance.

## Password Standards

Les standards concernant les mots de passe peuvent définir :

- une longueur minimale ;
- les exigences de complexité ;
- la gestion du stockage ;
- l'utilisation de mots de passe uniques ;
- les règles de renouvellement lorsqu'elles sont requises par la politique de sécurité.

Les mots de passe doivent être stockés sous une forme protégée, notamment à l'aide de mécanismes de **hachage adaptés**.

## Access Control Standards

Les standards de contrôle d'accès peuvent définir les modèles utilisés par l'organisation.

### DAC — Discretionary Access Control

Le propriétaire d'une ressource peut déterminer qui peut y accéder.

### MAC — Mandatory Access Control

Les accès sont déterminés selon des règles et classifications imposées par une autorité centrale.

### RBAC — Role-Based Access Control

Les permissions sont attribuées en fonction du **rôle** de l'utilisateur.

## Physical Security Standards

Les standards de sécurité physique peuvent également couvrir les contrôles environnementaux :

- systèmes de suppression d'incendie ;
- HVAC ;
- alimentation électrique redondante ;
- protection des infrastructures.

## Encryption Standards

Les standards de chiffrement définissent les mécanismes cryptographiques à utiliser selon les besoins.

Le choix dépend notamment :

- du niveau de sécurité recherché ;
- du cas d'utilisation ;
- des performances ;
- des exigences réglementaires ou organisationnelles.

## Least Privilege et Separation of Duties

**Least Privilege :**
> Donner à un utilisateur uniquement les privilèges nécessaires à l'accomplissement de sa tâche.

**Separation of Duties :**
> Répartir une activité sensible entre plusieurs personnes afin qu'une seule personne ne puisse pas réaliser seule l'ensemble du processus.

---

# 5. Procedures — Procédures

Une **procedure** est une séquence systématique d'actions permettant d'obtenir un résultat précis.

Contrairement à une policy, une procédure décrit davantage **comment** réaliser une tâche.

## Emergency Evacuation Procedure

Une procédure d'évacuation d'urgence décrit les étapes à suivre en cas d'événement tel que :

- incendie ;
- catastrophe naturelle ;
- autre situation d'urgence.

## Data Backup Procedures

Les procédures de sauvegarde définissent notamment :

- quoi sauvegarder ;
- quand sauvegarder ;
- comment sauvegarder ;
- où stocker les sauvegardes ;
- comment vérifier les sauvegardes.

## Change Management Procedure

Une procédure de gestion des changements peut définir :

1. Demande de changement.
2. Analyse du changement.
3. Évaluation des risques.
4. Approbation.
5. Planification.
6. Mise en œuvre.
7. Vérification.
8. Documentation et clôture.

## Onboarding / Offboarding Procedures

Les procédures d'**onboarding** permettent de gérer l'arrivée d'un collaborateur :

- création du compte ;
- attribution des permissions ;
- fourniture du matériel ;
- accès aux applications.

Les procédures d'**offboarding** permettent de gérer son départ :

- désactivation des comptes ;
- retrait des accès ;
- récupération du matériel ;
- transfert des données ou responsabilités.

## Playbooks

Un **playbook** fournit des instructions opérationnelles permettant de gérer une situation ou une tâche particulière.

Les playbooks peuvent couvrir :

- la réponse à un incident de cybersécurité ;
- l'analyse d'une alerte ;
- une procédure d'escalade ;
- le traitement d'une situation métier particulière.

---

# 6. Policy vs Standard vs Procedure vs Playbook

| Élément | Rôle | Question principale |
|---|---|---|
| **Policy** | Définit les règles et orientations | **What / Why ?** |
| **Standard** | Définit les exigences à respecter | **What exactly ?** |
| **Procedure** | Décrit les étapes d'une tâche | **How ?** |
| **Playbook** | Guide opérationnel pour une situation précise | **How do I respond to this situation ?** |

### Exemple

Une organisation veut sécuriser ses mots de passe :

**Policy :**
> Les mots de passe doivent être protégés.

**Standard :**
> Les mots de passe doivent respecter les exigences définies par le standard de sécurité de l'organisation.

**Procedure :**
> Étapes à suivre pour créer, modifier ou réinitialiser un mot de passe.

**Playbook :**
> Étapes à suivre lorsqu'un compte compromis est détecté.

---

# 7. Governance Considerations

La gouvernance doit prendre en compte plusieurs dimensions.

## Regulatory Considerations

Les organisations doivent respecter les réglementations applicables.

Le non-respect peut entraîner :

- des amendes ;
- des sanctions ;
- une atteinte à la réputation ;
- d'autres conséquences réglementaires.

## Legal Considerations

La gouvernance doit également prendre en compte les obligations légales.

Exemples :

- salaire minimum ;
- heures supplémentaires ;
- santé et sécurité ;
- discrimination ;
- avantages sociaux ;
- obligations contractuelles.

Les organisations peuvent également être confrontées à des risques juridiques, notamment à travers des litiges avec des clients, employés, fournisseurs ou autres entreprises.

## Industry Considerations

Les organisations doivent également tenir compte des standards et pratiques de leur secteur.

Ne pas respecter les attentes du secteur peut entraîner :

- une perte de confiance ;
- des critiques des parties prenantes ;
- un désavantage concurrentiel.

## Geographical Boundaries

Les exigences peuvent varier selon la localisation de l'organisation ou de ses activités.

Il faut donc prendre en compte les exigences :

- locales ;
- régionales ;
- nationales ;
- internationales.

---

# 8. Compliance

La **compliance** désigne le fait de respecter les exigences applicables à l'organisation.

Ces exigences peuvent provenir :

- de lois ;
- de réglementations ;
- de standards ;
- de contrats ;
- de politiques internes.

## Compliance Reporting

Le **compliance reporting** est le processus consistant à collecter et présenter des informations permettant de démontrer la conformité.

### Internal Compliance Reporting

Il consiste à collecter et analyser des données afin de vérifier que l'organisation respecte ses propres politiques et procédures.

### External Compliance Reporting

Il consiste à démontrer la conformité à des parties externes telles que :

- autorités réglementaires ;
- auditeurs ;
- clients.

Cette démarche peut être imposée par la loi ou par un contrat.

---

# 9. Compliance Monitoring

Le **compliance monitoring** consiste à examiner régulièrement les opérations de l'organisation afin de vérifier leur conformité avec :

- les lois ;
- les réglementations ;
- les politiques internes ;
- les exigences applicables.

L'objectif est d'identifier rapidement les écarts de conformité.

---

# 10. Due Diligence et Due Care

Ces deux notions sont importantes à distinguer.

## Due Diligence

La **due diligence** correspond à une évaluation approfondie permettant d'identifier les risques.

> **Due diligence = identifier et comprendre les risques.**

Exemples d'éléments pouvant être examinés :

- historique ;
- situation financière ;
- pratiques ;
- contrôles ;
- réputation ;
- risques de conformité.

## Due Care

Le **due care** correspond aux mesures prises pour réduire ou gérer les risques identifiés.

> **Due care = prendre les mesures appropriées pour traiter les risques.**

### Mémo

> **Due Diligence = chercher / identifier les risques**
>
> **Due Care = agir pour réduire ces risques**

---

# 11. Attestation et Acknowledgement

## Attestation

Une **attestation** est une déclaration formelle d'une partie responsable indiquant que les processus ou contrôles de l'organisation respectent certaines exigences.

## Acknowledgement

L'**acknowledgement** correspond à la reconnaissance et à l'acceptation des exigences de conformité par les parties concernées.

Exemple :

> Un employé reconnaît avoir lu et accepté la politique de sécurité de l'organisation.

---

# 12. Internal vs External Compliance

## Internal Compliance

La conformité interne consiste à vérifier régulièrement que l'organisation respecte ses propres politiques et procédures.

## External Compliance

La conformité externe implique une vérification par une partie externe ou par rapport à des exigences externes.

Exemples :

- audit par un tiers ;
- contrôle d'un organisme réglementaire ;
- certification ;
- audit client.

---

# 13. Automation in Compliance

L'automatisation peut faciliter la conformité.

Les systèmes automatisés peuvent notamment :

- collecter les données ;
- vérifier automatiquement certains contrôles ;
- améliorer la précision ;
- générer des rapports ;
- fournir une visibilité en temps réel ;
- détecter des écarts de conformité.

---

# 14. Conséquences de la Non-Compliance

Le non-respect des exigences peut avoir différentes conséquences :

### Fines
Des **amendes** peuvent être imposées par les autorités.

### Sanctions
L'organisation peut subir différentes **sanctions réglementaires ou administratives**.

### Reputational Damage
Une violation de conformité peut entraîner une **atteinte à la réputation** et une perte de confiance des clients, partenaires ou investisseurs.

### Loss of License
Dans certains secteurs, une organisation peut perdre une **licence ou une autorisation d'exercer**.

### Contractual Impacts
Le non-respect d'une obligation contractuelle peut entraîner :

- pénalités ;
- rupture du contrat ;
- perte d'un client ;
- litiges.

---

# 15. Vue d'ensemble : GRC

Le **GRC** regroupe trois dimensions complémentaires :

| Domaine | Objectif |
|---|---|
| **Governance** | Diriger l'organisation et aligner ses activités avec ses objectifs |
| **Risk Management** | Identifier, analyser et traiter les risques |
| **Compliance** | Respecter les lois, réglementations, contrats et politiques |

### Exemple : mise en place du télétravail

**Governance :**
- définir les responsabilités ;
- définir les politiques ;
- aligner le télétravail avec les objectifs de l'organisation.

**Risk Management :**
- identifier les risques liés au télétravail ;
- évaluer les risques ;
- mettre en place des contrôles.

**Compliance :**
- vérifier le respect des lois ;
- respecter les exigences contractuelles ;
- documenter la conformité.

---

# 16. À retenir pour l'examen

## Les distinctions essentielles

**Governance**
> Cadre global permettant de diriger, superviser et aligner l'organisation avec ses objectifs.

**Policy**
> Règle ou orientation générale : **ce que l'organisation exige**.

**Standard**
> Exigence précise permettant d'appliquer une policy.

**Procedure**
> Étapes détaillées pour réaliser une tâche.

**Playbook**
> Guide opérationnel pour gérer une situation précise.

**Compliance**
> Respect des exigences internes et externes.

**Due Diligence**
> Identifier et évaluer les risques.

**Due Care**
> Prendre les mesures nécessaires pour traiter les risques.

**Attestation**
> Déclaration formelle de conformité.

**Acknowledgement**
> Reconnaissance et acceptation d'une exigence.

## Chaîne logique

```text
Governance
    |
    +-- Policies
    |      |
    |      +-- Standards
    |             |
    |             +-- Procedures
    |                    |
    |                    +-- Playbooks
    |
    +-- Risk Management
    |
    +-- Compliance
```

## Les points à savoir absolument

- **GRC = Governance, Risk Management, Compliance**
- La gouvernance doit rester alignée avec les objectifs de l'organisation.
- La gouvernance doit être revue lorsque l'environnement change.
- Une nouvelle réglementation peut nécessiter une modification des policies et procedures.
- **Policy ≠ Procedure** : la policy définit les règles, la procédure explique comment les appliquer.
- **Due Diligence ≠ Due Care** :
  - Due Diligence = identifier/évaluer les risques.
  - Due Care = prendre des mesures pour les réduire.
- Le compliance monitoring permet de vérifier régulièrement la conformité.
- La conformité peut être **interne** ou **externe**.
- Le non-respect des exigences peut entraîner des amendes, sanctions, perte de licence, dommages réputationnels ou conséquences contractuelles.
