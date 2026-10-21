## 1. Hardening : réduire la surface d’attaque

Le **hardening** (durcissement) consiste à configurer un système, un poste, un serveur ou une application afin de réduire les possibilités d’exploitation, tout en conservant les fonctions nécessaires.

### Modifier les configurations par défaut
- Remplacer les mots de passe par défaut.
- Désactiver les ports, protocoles et services inutiles.
- Fermer les ports qui ne sont pas nécessaires.
- Supprimer les applications superflues et appliquer des paramètres de sécurité adaptés.

### Least functionality — fonctionnalité minimale
Le principe de **least functionality** consiste à ne conserver que les applications, services et fonctions indispensables à l’usage du système. On peut restreindre les fonctions inutiles, désinstaller les logiciels superflus, désactiver les services inutiles et centraliser la gestion de configuration.

### Image de référence sécurisée
Une **secure baseline image** est une installation standardisée qui comprend le système d’exploitation, les applications essentielles et des paramètres de sécurité prédéfinis. Elle permet de déployer des postes et serveurs homogènes.

### Allowlisting et blocklisting

| Approche | Fonctionnement | Avantages et limites |
|---|---|---|
| **Allowlisting** (liste d’autorisation) | Seules les applications explicitement approuvées peuvent s’exécuter. | Généralement plus restrictive et plus sûre, mais demande une gestion rigoureuse. |
| **Blocklisting** (liste de blocage) | Les applications répertoriées sont interdites ; les autres peuvent généralement s’exécuter. | Plus simple à gérer, mais peut laisser passer des applications malveillantes inconnues. |

Une allowlist applique une logique d’autorisation explicite : ce qui n’est pas approuvé est bloqué. Le comportement réel dépend du mécanisme et de sa configuration.

## 2. Services et systèmes d’exploitation de confiance

### Services inutiles
Un **service** est un programme qui s’exécute en arrière-plan et fournit une fonction au système ou à une application. Un service inutile peut augmenter la surface d’attaque, notamment s’il écoute sur le réseau ou s’exécute avec des privilèges élevés. Vérifier ses dépendances avant de le désactiver.

### Trusted Operating System (TOS)
Un **système d’exploitation de confiance** est conçu pour appliquer des politiques de sécurité fortes et contrôler l’accès aux ressources. Certains utilisent le **Mandatory Access Control (MAC)**, dans lequel une politique centrale impose les décisions d’accès.

Exemples et notions :
- **INTEGRITY-178B** : système d’exploitation destiné aux systèmes embarqués, conçu pour des usages exigeants en matière de sûreté et de sécurité.
- **Trusted Solaris** : système Solaris renforcé historiquement associé au contrôle d’accès multiniveau, à l’audit et à la séparation des ressources.
- **SELinux** : mécanisme de contrôle d’accès obligatoire intégré notamment à Red Hat Enterprise Linux et CentOS.
- **Microkernel** : architecture qui déplace certaines fonctions hors du noyau privilégié. Cela peut réduire la quantité de code privilégié, mais ne garantit pas à lui seul la sécurité.

Les systèmes doivent également répondre à des contraintes d’**utilisabilité**, de **performance** et de **fonctionnalité**.

### Common Criteria et EAL
Les **Common Criteria** constituent un cadre d’évaluation de la sécurité des produits informatiques. Les **Evaluation Assurance Levels (EAL)** vont de **EAL1** à **EAL7** :
- **EAL1** : niveau d’assurance le plus bas.
- **EAL4** : produit conçu, testé et examiné méthodiquement dans le périmètre défini.
- **EAL6** : niveau d’assurance élevé, avec des méthodes d’ingénierie et de vérification plus rigoureuses.
- **EAL7** : niveau d’assurance le plus élevé.

Un EAL plus élevé indique une évaluation plus rigoureuse dans le cadre défini ; il ne garantit pas l’absence de vulnérabilités. L’évaluation porte sur une cible et un périmètre précis.

## 3. Gestion des mises à jour et des correctifs

### Termes à distinguer

| Terme | Définition |
|---|---|
| **Patch (correctif)** | Modification logicielle qui corrige un défaut, par exemple une vulnérabilité de sécurité. |
| **Hotfix** | Correctif ciblé pour un problème précis, parfois urgent. Il doit être testé selon le risque et les contraintes opérationnelles. |
| **Update (mise à jour)** | Terme général : elle peut inclure des correctifs de sécurité, des corrections de bugs ou de nouvelles fonctions. Une mise à jour peut donc corriger des vulnérabilités. |
| **Service pack** | Ensemble regroupé de correctifs et d’améliorations, surtout courant dans les anciennes générations de logiciels. |
| **Firmware** | Logiciel intégré à un équipement matériel, qui peut lui aussi nécessiter des mises à jour de sécurité. |

### Patch management — gestion des correctifs
La gestion des correctifs couvre la planification, les tests, le déploiement et la vérification.

| Étape | Objectif |
|---|---|
| **Planification** | Inventorier les actifs, surveiller les avis des éditeurs, évaluer la criticité et définir les priorités et fenêtres de maintenance. |
| **Tests** | Vérifier la compatibilité, le fonctionnement, les dépendances et les effets de bord dans un environnement représentatif. |
| **Implémentation / déploiement** | Déployer les correctifs approuvés par vagues ou groupes ; prévoir un retour arrière lorsque c’est possible. |
| **Audit et vérification** | Contrôler l’installation, la version attendue, le fonctionnement et les échecs ; documenter les exceptions. |

Un outil de gestion des correctifs doit suivre les appareils ciblés, le statut de déploiement, les échecs, les redémarrages éventuellement requis et les résultats de vérification.

### Bonnes pratiques
1. Désigner un responsable ou une équipe pour suivre les correctifs des éditeurs.
2. Automatiser, lorsque cela est approprié, le déploiement des correctifs des systèmes et applications.
3. Inclure les ressources cloud dans le processus.
4. Classer les correctifs selon leur urgence, leur importance et leur criticité métier.
5. Tester les correctifs critiques avant la production lorsque cela est possible, avec une procédure d’urgence documentée.
6. Conserver les journaux de déploiement et de vérification.
7. Définir une procédure de test et de déploiement des mises à jour de firmware.
8. Prévoir une procédure accélérée pour les correctifs urgents approuvés.
9. Réévaluer périodiquement les correctifs non critiques et les regrouper si cela est pertinent.

L’objectif est de réduire la période d’exposition aux vulnérabilités tout en maîtrisant le risque de régression.

## 4. Group Policy et modèles de sécurité Windows

### Group Policy (stratégie de groupe)
Une **GPO** est un ensemble de paramètres pouvant s’appliquer à des utilisateurs ou ordinateurs Windows, notamment dans un domaine Active Directory. Les GPO permettent de centraliser :
- les exigences de mots de passe et les stratégies de verrouillage de compte ;
- les droits utilisateurs et les paramètres d’audit ;
- les restrictions logicielles et règles d’exécution d’applications ;
- d’autres paramètres de sécurité et de configuration.

Sur une machine Windows compatible, ouvrir **Exécuter** (`Win + R`) et saisir `gpedit.msc` pour accéder à l’éditeur de stratégie de groupe locale. Sa disponibilité dépend de l’édition de Windows. Dans un domaine, les stratégies sont généralement administrées avec les outils de gestion des GPO.

### Exemples de paramètres
- **Password requirements** : longueur minimale, historique et autres règles définies par la politique.
- **Account lockout policies** : conditions de verrouillage après plusieurs échecs d’authentification et modalités de déverrouillage.
- **Software/application restrictions** : règles limitant les programmes autorisés à s’exécuter.

Un **security template** (modèle de sécurité) regroupe des paramètres pouvant être appliqués de façon cohérente.

### Baseline et baselining
- Une **secure baseline** est un ensemble de paramètres de sécurité de référence approuvés pour un type d’actif ou un usage.
- Le **baselining** consiste à établir une référence et à mesurer les changements ou écarts par rapport à celle-ci.

Les GPO peuvent déployer et maintenir une baseline Windows à l’échelle d’un domaine. La gestion de configuration doit aussi détecter les écarts et les changements non autorisés.

## 5. MAC, DAC, SELinux et AppArmor

### MAC et DAC

| Modèle | Principe | Exemple ou caractéristique |
|---|---|---|
| **MAC — Mandatory Access Control** | Le système impose les décisions d’accès selon une politique centrale, des étiquettes et/ou des niveaux de sécurité. | SELinux peut appliquer une politique MAC aux processus et ressources. |
| **DAC — Discretionary Access Control** | Le propriétaire d’un objet ou un mécanisme délégué peut déterminer quels utilisateurs ou groupes y accèdent, dans les limites des permissions. | Permissions classiques de fichiers Unix/Linux. |

### SELinux
**SELinux (Security-Enhanced Linux)** ajoute un contrôle d’accès obligatoire aux permissions Unix traditionnelles. Il permet de limiter les actions des processus sur les ressources, même si les permissions classiques semblent les autoriser.

Un contexte SELinux courant peut être représenté ainsi :

`utilisateur: rôle: type: niveau`

- **Utilisateur SELinux** : identité de sécurité SELinux ; elle n’est pas nécessairement le nom du compte Linux.
- **Rôle** : contribue à déterminer les domaines ou types dans lesquels un sujet peut opérer.
- **Type** : étiquette centrale des politiques *type enforcement*, utilisée pour associer des règles aux processus et objets.
- **Niveau** : information de sensibilité utilisée notamment par les politiques multiniveaux, lorsqu’elles sont configurées.

Exemples de noms pouvant apparaître dans les contextes : `unconfined_u`, `user_u`, `sysadm_u`, `object_r`. Leur disponibilité et leur signification dépendent de la politique installée. `object_r` apparaît couramment comme rôle de contexte d’objets, par exemple des fichiers ; ce n’est pas un rôle utilisateur ordinaire.

### Modes SELinux

| Mode | Comportement |
|---|---|
| **Enforcing** | La politique est appliquée : les actions interdites sont bloquées et peuvent être journalisées. |
| **Permissive** | Les violations sont généralement journalisées, mais SELinux ne les bloque pas. Utile pour diagnostiquer une politique. |
| **Disabled** | SELinux n’applique pas sa politique ; la protection qu’il fournit est donc absente. |

### Types de politiques
- **Targeted** : politique courante qui cible principalement certains services et processus.
- **Strict** : terme historiquement utilisé pour des politiques confinant plus largement les processus ; la disponibilité dépend de la distribution et de sa version.

Une **violation SELinux** survient lorsqu’une action ne respecte pas la politique active. Avant de désactiver SELinux pour résoudre un problème, examiner les journaux et corriger les permissions ou la politique concernée.

### AppArmor
**AppArmor** est un autre mécanisme de contrôle d’accès obligatoire sous Linux. Il utilise principalement des profils qui définissent les ressources et actions autorisées pour un programme. SELinux et AppArmor ont des objectifs proches, mais leurs modèles de politique et leurs configurations diffèrent.

## 6. Chiffrement des données selon leur portée

Le **chiffrement** transforme des données lisibles en données protégées à l’aide d’un algorithme et d’une clé. Son efficacité dépend notamment de la gestion des clés, des permissions et de la protection des données lorsqu’elles sont utilisées.

| Portée | Ce qui est chiffré | Exemples |
|---|---|---|
| **Disque complet (*full-disk encryption*)** | Le contenu du disque, à l’exception éventuelle de petites zones nécessaires au démarrage. | BitLocker, FileVault, LUKS. |
| **Partition** | Une partition déterminée, sans nécessairement chiffrer les autres partitions du disque. | Partition chiffrée avec LUKS. |
| **Volume / conteneur** | Un volume logique ou conteneur et les fichiers qu’il contient. | VeraCrypt. |
| **Fichier** | Un fichier spécifique, indépendamment du reste du disque. | GnuPG (`gpg`) pour chiffrer des fichiers ou archives. |
| **Base de données** | Les fichiers de base de données et journaux, selon le mécanisme utilisé. | Transparent Data Encryption (TDE) de SQL Server. |
| **Enregistrement (*record*)** | Des champs ou enregistrements précis, généralement au niveau applicatif ou de la base. | Chiffrement applicatif de champs sensibles. |

Ces niveaux ne sont pas interchangeables. Le chiffrement de disque protège notamment les données lorsque le support est hors ligne ; le chiffrement de fichier, de base ou d’enregistrement offre une granularité différente. Le chiffrement au repos ne remplace pas les contrôles d’accès, les sauvegardes sécurisées ni la gestion des clés.

## 7. Maintenir une baseline sécurisée

Une **secure baseline** est une configuration minimale et approuvée, adaptée au type d’actif, à son rôle et au risque. Elle peut couvrir les pare-feu, les permissions, l’audit, le chiffrement, les protections antimalware et les mises à jour.

### Cycle de vie
1. **Définir la référence** : choisir les paramètres exigés et documenter les exceptions autorisées.
2. **Déployer** : appliquer la configuration à tous les actifs concernés, par exemple avec des GPO pour Windows.
3. **Surveiller et valider** : comparer la configuration réelle à la référence et détecter les dérives.
4. **Maintenir** : réévaluer la référence lorsque les risques, systèmes, applications ou exigences changent.

Dans le cloud, des outils de gestion de configuration peuvent évaluer les ressources par rapport à des règles et détecter les écarts. **AWS Config** permet notamment d’enregistrer et d’évaluer la configuration de ressources AWS ; les possibilités de remédiation dépendent des règles et automatisations mises en place.

Une baseline n’est pas figée : elle doit évoluer avec les correctifs, les changements d’architecture et les exigences de sécurité.

## 8. Points à retenir pour l’examen

- Le **hardening** réduit la surface d’attaque en sécurisant les paramètres et en supprimant les fonctions inutiles.
- **Least functionality** signifie ne conserver que ce qui est nécessaire.
- Une **allowlist** n’autorise que les applications approuvées ; une **blocklist** bloque les applications répertoriées.
- Un EAL élevé correspond à une évaluation plus rigoureuse, pas à une garantie d’invulnérabilité.
- La gestion des correctifs comprend la planification, les tests, le déploiement et la vérification.
- Les GPO centralisent de nombreux paramètres Windows ; `gpedit.msc` ouvre l’éditeur local lorsqu’il est disponible.
- **MAC** impose une politique centrale ; **DAC** laisse une part de contrôle au propriétaire de l’objet.
- SELinux fonctionne en modes **Enforcing**, **Permissive** ou **Disabled**.
- Le chiffrement peut s’appliquer au disque, à une partition, à un volume, à un fichier, à une base de données ou à un enregistrement.
- Une baseline doit être définie, déployée, surveillée et maintenue.
