## 1. Automation et orchestration : définitions

### 1.1 Automation — Automatisation

L’**automation** désigne l’exécution automatique d’une tâche sans intervention manuelle continue. Elle concerne généralement une tâche individuelle ou une action précise.

Exemple : créer automatiquement un ticket lorsqu’un utilisateur soumet un formulaire de support.

### 1.2 Orchestration

L’**orchestration** coordonne plusieurs tâches automatisées afin d’atteindre un résultat précis ou de réaliser un workflow complet.

Exemple : après la détection d’un poste infecté, un workflow peut isoler la machine, lancer une collecte forensique, réinstaller un système propre, vérifier le résultat puis autoriser sa reconnexion au réseau.

| Automation | Orchestration |
|---|---|
| Automatise une tâche ou une action. | Coordonne plusieurs tâches automatisées. |
| Périmètre généralement limité. | Périmètre plus large, organisé en workflow. |
| Exemple : créer un ticket. | Exemple : créer, catégoriser, prioriser et escalader un ticket. |

### 1.3 SOAR, playbook et runbook

- **SOAR (Security Orchestration, Automation and Response) :** plateforme qui combine l’orchestration, l’automatisation et les capacités de réponse aux incidents de sécurité. Elle peut coordonner des outils et exécuter des actions à partir d’alertes ou de scénarios.
- **Playbook :** liste structurée d’actions à suivre pour traiter un incident ou une situation précise.
- **Runbook :** procédure opérationnelle détaillée qui décrit comment réaliser une tâche. Elle peut être exécutée manuellement, partiellement automatisée ou automatisée, avec des points de validation humaine.

**Nuance importante :** un playbook n’est pas forcément manuel et un runbook n’est pas nécessairement entièrement automatisé. Les termes peuvent varier selon les organisations et les outils.

---

## 2. Quand utiliser l’automatisation et l’orchestration ?

Elles sont particulièrement utiles pour :
- Simplifier des processus complexes.
- Renforcer les mesures de sécurité.
- Améliorer l’efficacité opérationnelle.
- Réaliser de manière fiable des tâches stables et répétitives.

### 2.1 Exemple : traitement d’un poste infecté

Un workflow de réponse peut comporter plusieurs actions coordonnées :

1. Isoler le poste infecté du réseau.
2. Créer une image du support de stockage pour l’analyse forensique.
3. Analyser le disque.
4. Formater le poste lorsque les preuves nécessaires ont été préservées et que cela a été autorisé.
5. Installer une image propre du système d’exploitation.
6. Valider le bon fonctionnement et la sécurité du poste.
7. Reconnecter le poste au réseau lorsque les contrôles sont satisfaisants.

Cet exemple illustre l’orchestration : plusieurs tâches sont enchaînées pour atteindre un objectif global. Certaines étapes sensibles, comme la préservation des preuves ou la reconnexion, peuvent nécessiter une validation humaine.

### 2.2 Les éléments à évaluer avant d’automatiser

| Élément | Explication |
|---|---|
| **Complexity — Complexité** | Le processus est-il stable, connu et suffisamment documenté pour être automatisé ? |
| **Cost — Coût** | Prendre en compte le matériel, les logiciels, le personnel et les coûts de support continus. |
| **Single points of failure — Points uniques de défaillance** | Une automatisation mal conçue peut interrompre un processus métier critique si elle échoue. |
| **Redundancy — Redondance** | Prévoir des systèmes de secours ou des procédures manuelles pour assurer la continuité en cas de panne. |
| **Technical debt — Dette technique** | Les automatisations vieillissantes ou mal documentées deviennent difficiles à maintenir. Des révisions et mises à jour régulières limitent cette dette. |
| **Ongoing supportability — Maintenabilité et support continu** | Vérifier que l’organisation dispose des compétences et des ressources nécessaires pour maintenir les automatisations. |
| **Integrations — Intégrations** | Les automatisations dépendent souvent de connexions entre systèmes, notamment via des API et des webhooks. |

**À retenir :** l’automatisation et l’orchestration fonctionnent particulièrement bien avec des tâches répétitives, prévisibles et suffisamment stables. Elles doivent être mises en œuvre de manière stratégique.

---

## 3. Bénéfices de l’automatisation et de l’orchestration

Elles peuvent améliorer l’efficacité, la sécurité et la qualité des opérations.

Les bénéfices mentionnés dans les notes sont :

- **Efficiency and time savings :** exécuter plus rapidement les tâches répétitives et libérer du temps pour les activités à plus forte valeur.
- **Enforcing baselines :** appliquer automatiquement des configurations de référence (*security baselines*).
- **Standard infrastructure configuration :** maintenir des configurations d’infrastructure cohérentes.
- **Secure scaling :** déployer et gérer davantage de systèmes sans multiplier proportionnellement les tâches manuelles.
- **Employee retention :** réduire les tâches répétitives et pénibles, ce qui peut améliorer la satisfaction au travail.
- **Faster reaction times :** réduire le délai entre la détection d’un événement et l’action correspondante.
- **Workforce multiplier :** permettre à une équipe de traiter davantage de tâches sans augmenter dans les mêmes proportions ses effectifs.

L’automatisation ne remplace pas nécessairement les employés : elle leur permet de consacrer davantage de temps à l’analyse, aux décisions et aux situations complexes.

---

## 4. Automating support tickets — Automatisation des tickets de support

### 4.1 Pourquoi automatiser ?

Sans automatisation, un service de support peut rencontrer :
- Des retards dans la résolution des problèmes.
- Une charge de travail plus importante.
- Une baisse de la satisfaction des clients ou utilisateurs.

L’automatisation peut améliorer :
- **Efficiency :** efficacité du traitement.
- **Consistency :** cohérence des procédures.
- **Scalability :** capacité à traiter un volume plus important de demandes.
- **Transparency :** visibilité sur le traitement des demandes.
- **Accountability :** traçabilité des actions et des responsabilités.

### 4.2 Création automatique des tickets

1. Les utilisateurs ou clients soumettent des demandes via différents canaux.
2. Un outil surveille les demandes entrantes et crée des tickets selon des critères prédéfinis.
3. Le système récupère les informations essentielles fournies par l’utilisateur.
4. Il catégorise les tickets selon leur contenu ou leur source.
5. Il attribue une priorité selon des règles prédéfinies.
6. Des notifications sont envoyées à l’équipe ou au technicien concerné.

### 4.3 Escalade automatique des tickets

L’**escalation** consiste à transmettre un ticket à un niveau de support supérieur ou à une équipe plus spécialisée lorsque certains critères sont remplis.

1. L’organisation définit les critères d’escalade selon la nature et l’urgence du problème, ainsi que les engagements de service (*Service Level Agreement*, SLA).
2. Des règles sont configurées : niveau de priorité, délai de réponse ou statut non résolu.
3. Le système déclenche les actions prévues lorsque les critères sont atteints.
4. Il continue de suivre le ticket escaladé.
5. Lorsque le problème est résolu, le système peut déclencher la clôture du ticket et informer l’utilisateur.

---

## 5. Automating onboarding — Automatisation de l’intégration des employés

L’**onboarding** désigne le processus d’intégration d’un nouvel employé dans l’organisation. Son automatisation utilise des outils pour exécuter des tâches répétitives sans intervention humaine permanente.

### 5.1 Objectifs et bénéfices

- Améliorer la productivité globale.
- Améliorer la satisfaction des employés et potentiellement leur fidélisation.
- Éliminer des tâches manuelles répétitives.
- Réduire le risque d’erreur.
- Fournir une expérience d’intégration structurée et cohérente.
- Créer des traces documentaires des actions réalisées.

### 5.2 Tâches pouvant être automatisées

- Planification des formations.
- Attribution du matériel.
- Gestion des droits d’accès.
- Distribution de listes de contrôle (*checklists*).
- Collecte des retours d’expérience (*feedback*).

### 5.3 User provisioning — Provisionnement des comptes

Le **user provisioning** consiste à créer et gérer les comptes utilisateurs et leurs droits d’accès aux systèmes internes.

Un workflow peut :
1. Créer le compte de l’utilisateur.
2. Lui attribuer les rôles et droits adaptés à son poste.
3. Envoyer les notifications et confirmations nécessaires.
4. Synchroniser et mettre à jour les informations de manière continue.

Les comptes peuvent notamment donner accès à :
- La messagerie électronique.
- Des plateformes de gestion du travail.
- Des outils de communication interne.

### 5.4 Resource provisioning — Attribution des ressources

Le **resource provisioning** consiste à attribuer les outils et ressources nécessaires au nouvel employé pour réaliser son travail.

Les étapes mentionnées sont :

1. **Requirements analysis :** identifier les besoins du poste.
2. **Resource allocation :** attribuer les ressources nécessaires.
3. **Configuration and customization :** configurer et adapter les ressources.
4. **Verification and auditing :** vérifier que l’attribution et la configuration sont correctes.
5. **Gathering feedback :** recueillir les retours de l’utilisateur.

La vérification permet de confirmer que l’automatisation s’est correctement déroulée.

Bénéfices : accélérer l’intégration, réduire les erreurs, assurer la conformité et économiser du temps et des ressources.

---

## 6. Automating security — Automatisation de la sécurité

La **security automation** utilise des technologies pour prendre en charge des tâches de sécurité répétitives et maintenir des défenses cohérentes.

### 6.1 Guardrails — Garde-fous de sécurité

Les **guardrails** sont des contrôles de sécurité automatisés destinés à empêcher ou corriger des configurations d’infrastructure non sécurisées.

Ils peuvent :
- Faire respecter les politiques de sécurité.
- Surveiller l’infrastructure.
- Détecter les violations de règles.
- Déclencher automatiquement une action corrective.

Exemples d’actions possibles :
- Révoquer des permissions.
- Reconfigurer des composants.
- Isoler un poste infecté.

### 6.2 Security groups — Groupes de sécurité

Dans le cloud, les **security groups** agissent comme des pare-feu virtuels associés à des ressources, par exemple des instances. Ils contrôlent le trafic réseau entrant et sortant selon des règles définies.

L’automatisation peut :
- Affecter automatiquement des instances à des groupes de sécurité.
- Appliquer des règles prédéfinies.
- Adapter les groupes de sécurité à l’évolution des besoins ou des menaces.
- Analyser le trafic pour vérifier le respect des règles.

### 6.3 Service access management — Gestion des accès aux services

La gestion des accès aux services est un domaine important de l’automatisation de la sécurité, car elle contribue à réduire les risques et à améliorer l’efficacité opérationnelle.

Exemples :
- Réaliser automatiquement des revues d’accès.
- Surveiller les activités inhabituelles pour accélérer la réaction.
- Restreindre automatiquement un accès lorsque cela est nécessaire.
- Activer ou désactiver automatiquement certains services pour des raisons de sécurité.

### 6.4 Role-Based Access Control (RBAC)

Le **RBAC** est un modèle de contrôle d’accès dans lequel les permissions sont attribuées selon les rôles des utilisateurs.

Il peut être automatisé pour :
- Gérer les permissions lors de l’arrivée d’un employé (*onboarding*).
- Adapter les permissions lors d’un changement de poste (*transfer*).
- Retirer les accès lors d’un départ (*offboarding*).
- Protéger les informations sensibles.
- Réaliser des contrôles et ajustements automatiques de conformité.

**À retenir :** le RBAC attribue les permissions selon le rôle, et l’automatisation permet de maintenir ces permissions à jour tout au long du cycle de vie de l’utilisateur.

---

## 7. Automating application development — Automatisation du développement logiciel

L’automatisation du développement permet de tester, préparer et déployer des applications ou de nouvelles fonctionnalités avec moins d’interventions manuelles.

Elle peut améliorer la qualité du logiciel et accélérer la livraison des fonctionnalités.

### 7.1 Continuous Integration (CI) — Intégration continue

La **CI** est une pratique de développement dans laquelle les développeurs fusionnent fréquemment leurs changements de code dans un dépôt ou une branche partagée.

Après l’intégration, des tests automatisés sont exécutés afin de détecter rapidement les erreurs.

### 7.2 Release et deployment

- **Release — Livraison/version :** processus de finalisation et de préparation d’une nouvelle version du logiciel ou d’une mise à jour afin qu’elle puisse être mise à disposition.
- **Deployment — Déploiement :** installation ou mise en place de cette version dans un environnement donné, par exemple un environnement de test ou de production.

### 7.3 CI/CD : Continuous Integration et Continuous Delivery

La **Continuous Delivery** prolonge l’intégration continue : le code est automatiquement construit, testé et préparé pour être déployé. Une étape de validation ou d’approbation peut rester nécessaire avant le déploiement en production.

### 7.4 Continuous Deployment — Déploiement continu

La **Continuous Deployment** automatise également le déploiement des changements en production après la réussite des étapes de construction et de test, sans approbation manuelle systématique à chaque livraison.

| Notion | Idée principale |
|---|---|
| **CI — Continuous Integration** | Intégrer fréquemment le code et exécuter automatiquement des tests. |
| **Continuous Delivery** | Garder le logiciel prêt à être déployé ; une validation humaine peut précéder la production. |
| **Continuous Deployment** | Déployer automatiquement en production les changements qui passent les contrôles. |

### 7.5 Rollback — Retour à une version précédente

La capacité de **rollback** permet de revenir à une version antérieure si un déploiement provoque un problème. Elle est importante pour maintenir la continuité du service dans un modèle de déploiement continu.

Dans une démarche CI/CD, les développeurs prennent davantage de responsabilités sur les tests et le déploiement du code, plutôt que de transmettre simplement le travail à une autre équipe selon un modèle de transfert traditionnel (*hand-off*).

---

## 8. Integrations and APIs — Intégrations et interfaces de programmation

### 8.1 API — Application Programming Interface

Une **API** est un ensemble de règles et de protocoles permettant à des applications de communiquer, d’échanger des données et d’intégrer leurs fonctionnalités.

Les API sont utilisées pour automatiser notamment :
- L’administration.
- La gestion.
- La supervision (*monitoring*).
- Le provisionnement.
- La configuration.
- Le déprovisionnement (*deprovisioning*).

Elles permettent de connecter des services et des outils différents afin de construire un workflow automatisé.

### 8.2 REST

**REST (Representational State Transfer)** est un style architectural utilisé pour concevoir des API. Il s’appuie couramment sur :
- Les méthodes HTTP standard, comme `GET`, `POST`, `PUT`, `PATCH` et `DELETE`.
- Les codes de statut HTTP.
- Des identifiants de ressources, souvent sous forme d’URI.
- Des formats de représentation des données, par exemple JSON.

REST est un style architectural, et non un protocole strictement défini de la même manière que SOAP.

### 8.3 SOAP

**SOAP (Simple Object Access Protocol)** est un protocole de communication qui définit une structure de message standardisée, généralement exprimée en XML.

Il dispose de règles formelles pour les messages et peut s’intégrer à des mécanismes de sécurité et de fiabilité des échanges. Les notes le décrivent comme offrant un niveau élevé de sécurité et d’intégrité transactionnelle ; en pratique, ces propriétés dépendent des extensions, des mécanismes et de la configuration utilisés.

| REST | SOAP |
|---|---|
| Style architectural. | Protocole de messagerie. |
| Utilise couramment HTTP et des ressources identifiées par URI. | Définit une structure de message XML. |
| Souvent utilisé avec JSON. | Messages généralement en XML. |
| Souvent plus léger et flexible. | Plus formel et encadré par des standards. |

### 8.4 APIs et automatisation

Les API permettent à plusieurs services de s’intégrer. Une plateforme d’automatisation peut par exemple :
1. Recevoir un événement depuis un outil.
2. Interroger un autre service via une API.
3. Créer ou modifier un compte.
4. Appliquer une configuration.
5. Retirer un accès lorsqu’il n’est plus nécessaire.

Les **webhooks** sont également utiles : ils permettent à une application d’envoyer automatiquement une notification à une autre application lorsqu’un événement se produit.

---

## 9. Récapitulatif des notions à connaître

| Terme | Définition courte |
|---|---|
| Automation | Exécution automatique d’une tâche. |
| Orchestration | Coordination de plusieurs tâches automatisées dans un workflow. |
| SOAR | Plateforme d’orchestration, d’automatisation et de réponse en sécurité. |
| Playbook | Ensemble structuré d’actions à suivre pour un scénario. |
| Runbook | Procédure opérationnelle détaillée pour exécuter une tâche. |
| Single point of failure | Élément unique dont la panne peut interrompre un service ou processus. |
| Redundancy | Mécanismes de secours permettant d’assurer la continuité. |
| Technical debt | Coût futur créé par des choix techniques difficiles à maintenir. |
| Guardrails | Contrôles automatisés empêchant ou corrigeant des configurations non sécurisées. |
| Security group | Pare-feu virtuel contrôlant le trafic d’une ressource cloud. |
| Provisioning | Création et attribution de comptes, accès ou ressources. |
| Deprovisioning | Retrait ou désactivation des comptes, accès ou ressources. |
| RBAC | Attribution des permissions selon les rôles. |
| CI | Intégration fréquente du code avec tests automatisés. |
| Continuous Delivery | Préparation automatisée du logiciel pour livraison, avec approbation possible avant production. |
| Continuous Deployment | Déploiement automatique en production après validation des contrôles. |
| Rollback | Retour à une version précédente. |
| API | Interface permettant à des applications de communiquer. |
| REST | Style architectural courant pour les API. |
| SOAP | Protocole de messagerie structuré, généralement en XML. |
| Webhook | Notification envoyée automatiquement à une autre application lors d’un événement. |

## 10. Points importants pour l’examen

- **Automation = une tâche automatisée ; orchestration = plusieurs tâches coordonnées.**
- **SOAR** combine l’orchestration, l’automatisation et la réponse aux incidents de sécurité.
- Un playbook décrit les actions à suivre ; un runbook décrit comment réaliser une procédure opérationnelle.
- Avant d’automatiser, évaluer le coût, la complexité, les dépendances, la maintenance et les points uniques de défaillance.
- Prévoir une redondance ou une procédure manuelle de secours pour les processus critiques.
- L’automatisation est particulièrement adaptée aux tâches répétitives, stables et prévisibles.
- L’automatisation des tickets permet la création, la catégorisation, la priorisation, l’escalade et le suivi.
- Le provisioning gère la création et l’attribution des accès ; le deprovisioning retire les accès qui ne sont plus nécessaires.
- Les guardrails appliquent automatiquement des règles de sécurité.
- Le RBAC attribue les permissions en fonction des rôles.
- **CI** intègre fréquemment le code et lance des tests ; **Continuous Delivery** prépare le déploiement ; **Continuous Deployment** déploie automatiquement en production.
- Le rollback permet de revenir à une version antérieure en cas de problème.
- Une API permet à des applications de communiquer ; REST est un style architectural et SOAP un protocole de messagerie.
