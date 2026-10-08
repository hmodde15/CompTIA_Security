## 1. Acquisition et Procurement

**Acquisition** = processus permettant d'obtenir un bien ou un service.

**Procurement** = processus complet d'acquisition, incluant les étapes précédant l'achat : identification du besoin, demande, validation, sélection du fournisseur, achat, réception et suivi.

> Acquisition = obtenir le bien/service.  
> Procurement = gérer tout le processus d'acquisition.

### Types d'achat
- **Corporate credit card** : carte bancaire d'entreprise utilisée par les employés autorisés.
- **Individual purchase** : l'employé achète pour l'entreprise puis demande un remboursement.
- **Purchase order (PO)** : bon de commande formalisant une demande d'achat.

### Approval process
Le processus d'approbation vérifie que l'achat :
- répond à un besoin réel ;
- respecte le budget ;
- respecte les règles internes ;
- est aligné avec les objectifs de l'organisation ;
- présente un risque acceptable.

### ITPR
**ITPR (Information Technology Procurement Request)** : demande formalisée d'acquisition d'un produit ou service informatique.

L'acquisition et le procurement servent donc aussi à assurer la prudence financière, l'efficacité opérationnelle et un niveau de sécurité adapté.

---

## 2. Mobile Asset Deployment

### BYOD — Bring Your Own Device
L'employé utilise son appareil personnel pour accéder aux ressources de l'organisation.

**Avantages :**
- coût initial réduit ;
- liberté utilisateur.

**Risques :**
- sécurité plus difficile à contrôler ;
- compatibilité ;
- support ;
- coûts cachés.

### COPE — Corporate-Owned, Personally Enabled
L'organisation possède l'appareil mais autorise également son utilisation personnelle.

**Avantages :**
- gestion standardisée ;
- contrôle de sécurité élevé ;
- appareils homogènes.

**Inconvénient :**
- coût initial plus important.

### CYOD — Choose Your Own Device
L'organisation fournit une liste d'appareils approuvés parmi lesquels l'employé peut choisir.

**Avantages :**
- choix utilisateur ;
- appareils approuvés ;
- meilleur contrôle que BYOD ;
- gestion facilitée par MDM.

| Modèle | Propriété | Liberté utilisateur | Contrôle organisation |
|---|---|---|---|
| BYOD | Employé | Très élevée | Faible à moyenne |
| CYOD | Organisation | Élevée mais limitée | Élevé |
| COPE | Organisation | Moyenne | Très élevé |

> BYOD = liberté maximale  
> COPE = contrôle maximal  
> CYOD = compromis liberté/contrôle

---

## 3. Asset Management

L'**asset management** est l'approche systématique permettant de gérer les actifs d'une organisation et de maximiser leur valeur pendant leur cycle de vie.

Il comprend notamment :

### Assignment / Accountability
Chaque actif doit être attribué à un responsable ou à un groupe responsable.

### Classification
Les actifs peuvent être classifiés selon :
- fonction ;
- valeur ;
- criticité ;
- sensibilité ;
- type.

### Monitoring / Tracking
Le suivi permet de maintenir un inventaire précis comprenant par exemple :
- identifiant ;
- modèle ;
- numéro de série ;
- localisation ;
- utilisateur ;
- état ;
- date d'acquisition.

### Enumeration
L'**enumeration** consiste à identifier et compter les actifs, notamment lors :
- d'un inventaire ;
- d'une acquisition importante ;
- d'un retrait d'actifs.

Le suivi permet de détecter les appareils non autorisés, faciliter les mises à jour et identifier les vulnérabilités.

---

## 4. MDM — Mobile Device Management

Le **MDM** permet de gérer et sécuriser centralement les appareils mobiles.

Il peut permettre de :
- appliquer des politiques ;
- gérer les applications ;
- configurer les appareils ;
- maintenir une certaine homogénéité logicielle ;
- protéger les données ;
- vérifier la conformité ;
- verrouiller ou effacer certaines données à distance selon les capacités de la solution.

Le MDM réduit les risques liés aux appareils non sécurisés ou obsolètes.

---

## 5. Asset Disposal et Decommissioning

Le **decommissioning** correspond au retrait d'un actif ou d'un système de la production.

Le **disposal** correspond à sa mise au rebut ou à son élimination.

Avant de se débarrasser d'un équipement contenant des données, il faut appliquer une méthode de **sanitization** adaptée.

### NIST SP 800-88
La **NIST Special Publication 800-88** fournit des recommandations concernant la **media sanitization**.

La sanitization vise à rendre les données inaccessibles ou irrécupérables selon le niveau de sécurité requis.

Méthodes possibles :
- effacement sécurisé ;
- écrasement lorsque approprié ;
- cryptographic erase ;
- degaussing pour certains supports ;
- destruction physique.

### Degaussing
Le **degaussing** utilise un champ magnétique puissant pour perturber ou supprimer les données de certains supports magnétiques.

### Secure Erase
Le **secure erase** vise à supprimer les données de manière à empêcher leur récupération par les méthodes classiques.

### Cryptographic Erase
Le **cryptographic erase** rend les données chiffrées irrécupérables en supprimant/détruisant la clé cryptographique permettant leur déchiffrement.

Son avantage majeur est sa rapidité par rapport à certains effacements physiques complets.

### Destruction
Lorsque nécessaire, le support peut être physiquement détruit :
- shredding ;
- pulverizing ;
- melting ;
- incinerating.

### Certification
Une certification ou preuve de destruction/sanitization documente que l'opération a été effectuée conformément aux exigences.

---

## 6. Data Retention

La **data retention** consiste à déterminer quelles données doivent être conservées et pendant combien de temps.

Certaines réglementations imposent des durées de conservation pour certaines données.

Exemples :
- données financières ;
- dossiers médicaux ;
- documents légaux.

Principe :

> **Plus une organisation conserve de données, plus elle doit les protéger.**

Une politique de rétention doit définir :
- quoi conserver ;
- combien de temps ;
- où stocker ;
- quand supprimer ;
- comment supprimer.

---

# 7. Change Management

Le **change management** est une stratégie organisée permettant de faire évoluer une organisation, son infrastructure ou ses processus d'un état existant vers un état souhaité.

Tout changement peut affecter :
- efficacité ;
- disponibilité ;
- sécurité ;
- opérations ;
- utilisateurs ;
- applications ;
- infrastructures.

L'objectif est d'intégrer les changements de manière contrôlée tout en limitant les perturbations.

---

## 8. Change Advisory Board — CAB

Le **CAB (Change Advisory Board)** est un groupe de représentants de différentes parties de l'organisation chargé d'évaluer les changements proposés.

Il peut examiner :
- impact ;
- risques ;
- dépendances ;
- planification ;
- ressources ;
- plan de retour arrière.

---

## 9. Change Owner

Le **change owner** est la personne ou l'équipe responsable du changement.

Il peut :
- initier la demande ;
- coordonner les actions ;
- suivre le changement ;
- maintenir la documentation ;
- suivre les résultats.

---

## 10. Stakeholders

Un **stakeholder** est une personne ou entité ayant un intérêt dans le changement ou pouvant être affectée par celui-ci.

### Technical stakeholders
- administrateurs systèmes ;
- réseau ;
- sécurité ;
- développeurs ;
- infrastructure.

### Business stakeholders
- management ;
- responsables métier ;
- finance ;
- direction.

### End users
Les utilisateurs finaux qui utiliseront ou subiront directement les conséquences du changement.

---

## 11. Impact Analysis

L'**impact analysis** consiste à déterminer les conséquences potentielles d'un changement.

Questions :
- Que pourrait-il se passer si le changement échoue ?
- Quels seraient les effets immédiats ?
- Quel serait l'impact à long terme ?
- Quelles dépendances seraient affectées ?
- Existe-t-il des conséquences imprévues ?
- Quels services pourraient devenir indisponibles ?

---

# 12. Change Management Process

## 1. Preparation
- rassembler les ressources ;
- identifier les stakeholders ;
- préparer les équipes ;
- évaluer les risques.

## 2. Vision of Change
- définir l'état futur ;
- expliquer pourquoi le changement est nécessaire ;
- définir les bénéfices attendus.

## 3. Implementation
- former les utilisateurs ;
- restructurer si nécessaire ;
- introduire les nouvelles technologies ;
- communiquer continuellement.

## 4. Verification
Vérifier les résultats grâce à :
- enquêtes ;
- métriques de performance ;
- entretiens avec les stakeholders ;
- vérifications techniques.

## 5. Documentation
Documenter :
- ce qui a été réalisé ;
- les décisions ;
- les problèmes ;
- les résultats ;
- les améliorations possibles.

---

# 13. Points à considérer pendant un changement

### Maintenance Window
Une **maintenance window** est une période planifiée pour réaliser des opérations de maintenance.

Elle réduit généralement l'impact sur les utilisateurs.

> Une maintenance window ne signifie pas qu'aucun changement urgent ne peut être effectué en dehors de cette période.

### Backout Plan
Un **backout plan** est une stratégie prédéfinie permettant de restaurer l'état précédent si le changement échoue.

```text
Changement
   |
   +-- Succès --> Continuer
   |
   +-- Échec --> Backout Plan --> État précédent
```

### Testing
Les tests permettent de :
- détecter les problèmes ;
- vérifier la compatibilité ;
- valider le fonctionnement ;
- réduire les risques.

### SOP — Standard Operating Procedure
Une **SOP** est une procédure standardisée décrivant étape par étape comment réaliser une tâche.

Objectifs :
- cohérence ;
- réduction des erreurs ;
- efficacité ;
- standardisation.

---

# 14. Technical Implications

Avant un changement, il faut analyser les conséquences techniques.

### Allow List / Deny List

**Allow list** = éléments explicitement autorisés.

**Deny list** = éléments explicitement interdits.

Il faut vérifier qu'un changement ne bloque pas involontairement un élément nécessaire au fonctionnement du système.

### Restricted Activities
Certaines activités peuvent être interdites ou limitées. Les connaître permet d'éviter :
- problèmes opérationnels ;
- violations de sécurité ;
- problèmes de conformité ;
- interruptions.

### Downtime
Le **downtime** correspond à une période d'indisponibilité d'un système ou service.

Il faut évaluer :
- durée ;
- utilisateurs concernés ;
- dépendances ;
- conséquences métier ;
- possibilité de réduire l'interruption.

### Services et Applications Restarts
Certains changements nécessitent des redémarrages. Ils peuvent provoquer :
- indisponibilité temporaire ;
- perte de données en transit ;
- backlog ;
- problèmes utilisateurs.

### Legacy Applications
Une **legacy application** est une application ancienne toujours utilisée car elle répond aux besoins de l'organisation.

Elle peut être très sensible aux changements et dépendances modernes.

### Dependencies
Les **dependencies** doivent être cartographiées avant un changement.

Exemple :

```text
Application
   |
   +-- Database
   +-- API
   +-- Authentication
   +-- Network
   +-- External Service
```

Une modification apparemment mineure peut avoir des conséquences importantes si elle affecte une dépendance critique.

---

# 15. Documenting Changes

Chaque changement doit être correctement documenté.

La documentation doit permettre de savoir :
- **quoi** a changé ;
- **quand** ;
- **pourquoi** ;
- **par qui** ;
- **avec quel résultat**.

Elle améliore :
- traçabilité ;
- accountability ;
- dépannage ;
- audit ;
- continuité opérationnelle.

### Version Control

Le **version control** permet de suivre et gérer les différentes versions de documents, configurations ou logiciels.

Il permet :
- de connaître les modifications ;
- de collaborer ;
- de conserver un historique ;
- de revenir à une version précédente.

### Records à maintenir
Après un changement, vérifier que :
- la documentation est à jour ;
- les diagrammes sont actualisés ;
- les policies et procedures sont révisées si nécessaire ;
- les change requests sont complètes ;
- les tickets associés sont correctement documentés ;
- les autres enregistrements liés sont conservés.

---

# 16. À retenir pour l'examen

## Acquisition / Procurement
- **Acquisition** = obtenir un bien ou service.
- **Procurement** = processus complet d'acquisition.
- Les achats doivent être contrôlés et approuvés.
- Méthodes : carte d'entreprise, achat individuel, purchase order.

## Mobile Assets
- **BYOD** = appareil personnel.
- **COPE** = appareil appartenant à l'entreprise avec usage personnel autorisé.
- **CYOD** = choix parmi des appareils approuvés.
- **MDM** = gestion centralisée des appareils mobiles.

## Asset Management
- identifier ;
- attribuer ;
- classifier ;
- suivre ;
- maintenir l'inventaire ;
- retirer correctement les actifs.

## Asset Disposal
- **Sanitization** = rendre les données inaccessibles/inrécupérables selon les exigences.
- **Degaussing** = champ magnétique, notamment pour certains supports magnétiques.
- **Cryptographic erase** = suppression/destruction de la clé cryptographique.
- **Destruction** = rendre physiquement le support inutilisable.
- **Certification** = preuve de l'opération.

## Change Management
- **CAB** = évalue les changements.
- **Change owner** = responsable du changement.
- **Stakeholder** = partie intéressée ou affectée.
- **Impact analysis** = analyse des conséquences.
- **Maintenance window** = période planifiée.
- **Backout plan** = retour à l'état précédent.
- **SOP** = procédure standardisée.
- Tester avant production lorsque possible.
- Identifier les dépendances et legacy applications.
- Documenter chaque changement.

## Chaîne simplifiée

```text
Preparation
     |
Vision of Change
     |
Impact Analysis
     |
Testing
     |
Approval / CAB
     |
Maintenance Window
     |
Implementation
     |
     +---- Échec ----> Backout Plan
     |
Verification
     |
Documentation
```
