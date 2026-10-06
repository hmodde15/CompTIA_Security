# 14 - Risk Management — Synthèse

## 1. Risk Management

Le **risk management (gestion des risques)** est le processus permettant d'identifier, d'évaluer et de traiter les incertitudes pouvant avoir un impact sur les objectifs d'une organisation ou d'un projet.

L'objectif est notamment de comprendre quels risques existent, leur probabilité, leur impact, comment les traiter et qui est responsable de leur gestion.

---

## 2. Risk Assessment Frequency

La **risk assessment frequency** correspond à la régularité avec laquelle les évaluations des risques sont réalisées.

| Type | Principe |
|---|---|
| **Ad-Hoc** | Évaluation réalisée selon un besoin particulier, sans fréquence fixe. |
| **Recurring** | Évaluation réalisée régulièrement selon une fréquence définie. |
| **One-Time** | Évaluation réalisée une seule fois, par exemple lors d'un nouveau système, projet ou changement d'organisation. |
| **Continuous** | Évaluation ou surveillance réalisée de manière continue. |

---

## 3. Risk Identification

La **risk identification** consiste à reconnaître les risques potentiels pouvant avoir un impact négatif sur la capacité d'une organisation à fonctionner ou atteindre ses objectifs.

Méthodes mentionnées :
- **Brainstorming** : identifier collectivement les risques.
- **Checklists** : utiliser une liste de risques connus.
- **Interviews** : interroger les personnes connaissant le système ou processus.
- **Scenario Analysis** : analyser différents scénarios et leurs conséquences.

---

## 4. Business Impact Analysis

La **Business Impact Analysis (BIA)** évalue les effets potentiels d'une interruption sur les fonctions et processus métier d'une organisation.

Elle permet notamment d'identifier les fonctions critiques, les conséquences d'une interruption et les priorités de reprise.

---

## 5. RTO et RPO

### RTO

**RTO = Recovery Time Objective**

Le RTO correspond à la **durée maximale acceptable d'interruption** avant qu'un service ou système doive être restauré.

Exemple :

```text
RTO = 4 heures
```

### RPO

**RPO = Recovery Point Objective**

Le RPO correspond à la **quantité maximale de données que l'organisation accepte de perdre**, exprimée en temps.

Exemple :

```text
RPO = 1 heure
```

### RTO vs RPO

| RTO | RPO |
|---|---|
| Combien de temps peut-on rester indisponible ? | Combien de données peut-on accepter de perdre ? |
| Temps de reprise. | Point de reprise des données. |

> **RTO = temps ; RPO = données perdues.**

---

## 6. MTTR et MTBF

**MTTR = Mean Time To Repair** : temps moyen nécessaire pour réparer ou remettre en service un système après une panne.

**MTBF = Mean Time Between Failures** : temps moyen entre deux défaillances.

| Terme | Signification |
|---|---|
| **MTTR** | Temps moyen de réparation. |
| **MTBF** | Temps moyen entre deux pannes. |

---

## 7. Risk Register

Le **risk register (registre des risques)** centralise et permet de suivre les risques identifiés.

Il peut contenir :
- **Risk Description**
- **Risk Outcome**
- **Risk Impact**
- **Risk Level**
- **Risk Likelihood**
- **Cost**

### Risk Description
Description du risque identifié.

### Risk Impact
Conséquence potentielle du risque sur l'organisation.

### Risk Likelihood
Probabilité que le risque se produise.

### Risk Outcome
Résultat ou conséquence attendue si le risque se réalise.

### Risk Level / Threshold
Le niveau de risque est notamment déterminé en combinant l'impact et la probabilité.

```text
Risk Level ≈ Impact × Likelihood
```

Le **risk threshold** représente le niveau à partir duquel une action ou une attention particulière est nécessaire selon les règles de l'organisation.

### Cost
Coût potentiel associé au risque ou à son traitement.

---

## 8. Risk Appetite

Le **risk appetite** correspond au niveau de risque qu'une organisation est prête à accepter dans la poursuite de ses objectifs.

| Type | Attitude |
|---|---|
| **Expansionary** | Accepte davantage de risques pour rechercher davantage de gains. |
| **Neutral** | Cherche un équilibre entre risque et rendement. |
| **Conservative** | Privilégie une exposition plus faible au risque, même avec des rendements potentiellement plus faibles. |

---

## 9. Risk Tolerance et Risk Acceptance

### Risk Tolerance

La **risk tolerance** correspond aux limites de variation ou d'exposition au risque qu'une organisation est prête à supporter.

### Risk Acceptance

La **risk acceptance** consiste à décider consciemment d'accepter un risque particulier.

> **Risk appetite** = niveau global de risque accepté.  
> **Risk tolerance** = limites acceptables.  
> **Risk acceptance** = décision d'accepter un risque précis.

---

## 10. Key Risk Indicators

**KRI = Key Risk Indicator**

Les KRIs sont des indicateurs permettant de surveiller l'évolution du niveau de risque et de signaler une augmentation potentielle du risque.

Exemples :
- augmentation des incidents ;
- augmentation des tentatives de connexion échouées ;
- augmentation des vulnérabilités critiques ;
- augmentation des interruptions de service.

---

## 11. Risk Owner

Le **risk owner** est la personne ou le groupe responsable de la gestion d'un risque donné.

Il peut notamment surveiller le risque, coordonner les mesures de traitement et suivre son évolution.

---

## 12. Qualitative Risk Analysis

La **qualitative risk analysis** évalue les risques principalement selon :
- leur **impact potentiel** ;
- leur **probabilité d'occurrence**.

Elle utilise généralement des catégories plutôt que des valeurs financières précises.

Exemple :

```text
Likelihood : High
Impact     : High
Risk Level : High
```

---

## 13. Quantitative Risk Analysis

La **quantitative risk analysis** utilise des valeurs numériques, notamment financières.

Notions principales :
- **Asset Value (AV)**
- **Exposure Factor (EF)**
- **Single Loss Expectancy (SLE)**
- **Annualized Rate of Occurrence (ARO)**
- **Annualized Loss Expectancy (ALE)**

### Asset Value

L'**Asset Value (AV)** correspond à la valeur de l'actif concerné.

### Exposure Factor

**EF = Exposure Factor**

Pourcentage de perte de l'actif attendu dans un scénario.

```text
0 %   = aucune perte
100 % = perte totale
```

Exemple : perte estimée de 70 % → **EF = 70 %**.

### Single Loss Expectancy

**SLE = Single Loss Expectancy**

```text
SLE = Asset Value × Exposure Factor
```

Exemple :

```text
Asset Value = 10 000 $
EF = 50 %

SLE = 10 000 × 0,50
SLE = 5 000 $
```

Le SLE représente la perte attendue pour un seul événement.

### Annualized Rate of Occurrence

**ARO = Annualized Rate of Occurrence**

Nombre de fois qu'un événement est attendu sur une année.

Exemple :

```text
ARO = 0,5
```

signifie que l'événement est attendu en moyenne 0,5 fois par an.

### Annualized Loss Expectancy

**ALE = Annualized Loss Expectancy**

```text
ALE = SLE × ARO
```

Avec :

```text
SLE = 5 000 $
ARO = 0,5

ALE = 5 000 × 0,5
ALE = 2 500 $
```

L'ALE représente la perte annuelle attendue.

---

## 14. Exemple complet

```text
Asset Value = 10 000 $
Exposure Factor = 50 %
ARO = 0,5
```

### Étape 1

```text
SLE = AV × EF
SLE = 10 000 × 0,50
SLE = 5 000 $
```

### Étape 2

```text
ALE = SLE × ARO
ALE = 5 000 × 0,5
ALE = 2 500 $ / an
```

---

## 15. Risk Management Strategies

Les quatre stratégies principales sont :

1. **Risk Transfer / Transference**
2. **Risk Acceptance**
3. **Risk Avoidance**
4. **Risk Mitigation**

### Risk Transfer

Le **risk transfer** consiste à transférer une partie du risque ou de ses conséquences financières vers une autre partie.

Exemples :
- assurance ;
- contrat avec un prestataire ;
- clauses contractuelles.

Le transfert ne supprime pas le risque : il déplace principalement la responsabilité ou le poids financier de certaines conséquences.

### Contract Indemnity Clause

Une **indemnity clause** est une clause contractuelle par laquelle une partie accepte de couvrir certains dommages, responsabilités ou pertes de l'autre partie selon les conditions du contrat.

### Risk Acceptance

Consiste à accepter volontairement un risque après l'avoir évalué.

### Risk Avoidance

Consiste à supprimer l'activité ou la situation générant le risque.

### Risk Mitigation

Consiste à mettre en place des contrôles afin de réduire la probabilité ou l'impact du risque.

Exemples :
- sauvegardes ;
- MFA ;
- segmentation ;
- contrôles d'accès ;
- systèmes de sécurité.

### Comparaison

| Stratégie | Principe |
|---|---|
| **Avoidance** | Supprimer la source du risque. |
| **Mitigation** | Réduire la probabilité ou l'impact. |
| **Transfer** | Transférer une partie des conséquences à une autre partie. |
| **Acceptance** | Accepter le risque. |

```text
Avoid     → supprimer
Mitigate  → réduire
Transfer  → déplacer
Accept    → accepter
```

---

## 16. Risk Monitoring and Reporting

### Risk Monitoring

Le **risk monitoring** consiste à suivre l'évolution des risques dans le temps.

Il permet de vérifier :
- si le niveau de risque augmente ;
- si les contrôles fonctionnent ;
- si de nouveaux risques apparaissent ;
- si le traitement reste adapté.

### Residual Risk

Le **residual risk (risque résiduel)** est le risque qui reste après la mise en place des mesures de traitement ou des contrôles.

```text
Risque initial
     ↓
Contrôles
     ↓
Risque résiduel
```

Un contrôle réduit généralement un risque mais ne le fait pas nécessairement disparaître.

### Control Risk

Le **control risk** correspond au risque qu'un contrôle ne permette pas de prévenir ou détecter correctement un problème.

Un contrôle peut :
- échouer ;
- être mal configuré ;
- être contourné ;
- ne plus être adapté.

### Risk Reporting

Le **risk reporting** consiste à communiquer les informations importantes concernant les risques aux personnes concernées.

Il peut inclure :
- risques identifiés ;
- niveau de risque ;
- évolution ;
- mesures mises en place ;
- risques résiduels ;
- actions à réaliser.

---

## 17. Importance du Risk Management

### Informed Decision Making
Fournit aux responsables des informations permettant de prendre des décisions plus éclairées.

### Risk Mitigation
Permet de réduire les risques importants grâce à des contrôles adaptés.

### Stakeholder Communication
Permet d'informer les parties prenantes du niveau de risque et des actions entreprises.

### Regulatory Compliance
Contribue au respect des exigences légales, réglementaires et internes.

---

## 18. Tableau récapitulatif

| Notion | À retenir |
|---|---|
| **Risk Management** | Identifier, évaluer et traiter les risques. |
| **Risk Assessment** | Évaluer les risques. |
| **Ad-Hoc** | Selon le besoin. |
| **Recurring** | Régulièrement. |
| **One-Time** | Une seule fois. |
| **Continuous** | En continu. |
| **Risk Identification** | Identifier les risques potentiels. |
| **BIA** | Évaluer l'impact d'une interruption sur le métier. |
| **RTO** | Temps maximal acceptable avant reprise. |
| **RPO** | Quantité maximale de données que l'on accepte de perdre. |
| **MTTR** | Temps moyen de réparation. |
| **MTBF** | Temps moyen entre deux pannes. |
| **Risk Register** | Registre centralisant les risques. |
| **Risk Appetite** | Niveau global de risque accepté. |
| **Risk Tolerance** | Limites acceptables d'exposition au risque. |
| **Risk Acceptance** | Décision d'accepter un risque particulier. |
| **KRI** | Indicateur permettant de surveiller l'évolution du risque. |
| **Risk Owner** | Responsable d'un risque. |
| **Qualitative Analysis** | Analyse basée notamment sur impact/probabilité. |
| **Quantitative Analysis** | Analyse utilisant des valeurs numériques. |
| **SLE** | Perte attendue pour un événement. |
| **ARO** | Nombre annuel attendu d'occurrences. |
| **ALE** | Perte annuelle attendue. |
| **Avoidance** | Supprimer la source du risque. |
| **Mitigation** | Réduire le risque. |
| **Transfer** | Transférer une partie des conséquences. |
| **Acceptance** | Accepter le risque. |
| **Residual Risk** | Risque restant après les contrôles. |
| **Risk Monitoring** | Suivre les risques dans le temps. |
| **Risk Reporting** | Communiquer les informations sur les risques. |

---

## 19. À retenir pour les examens

- **Risk Management** = identifier, évaluer et traiter les risques.
- **Risk Identification** = trouver les risques potentiels.
- **BIA** = mesurer les conséquences d'une interruption sur le métier.
- **RTO** = combien de temps le service peut rester indisponible.
- **RPO** = combien de données l'organisation accepte de perdre.
- **MTTR** = temps moyen pour réparer.
- **MTBF** = temps moyen entre deux pannes.
- **Risk Register** = registre des risques.
- **Risk Appetite** = niveau global de risque accepté.
- **Risk Tolerance** = limites d'exposition acceptables.
- **Risk Owner** = responsable du risque.
- **KRI** = indicateur de niveau ou d'évolution du risque.
- **Qualitative** = impact + probabilité avec des catégories.
- **Quantitative** = valeurs numériques et financières.
- **SLE = Asset Value × Exposure Factor**
- **ALE = SLE × ARO**
- **Exposure Factor** = pourcentage de perte de l'actif.
- **Avoidance** = supprimer.
- **Mitigation** = réduire.
- **Transfer** = déplacer les conséquences vers une autre partie.
- **Acceptance** = accepter.
- **Residual Risk** = risque restant après les contrôles.
- **Risk Monitoring** = surveiller l'évolution du risque.
- **Risk Reporting** = communiquer le risque aux parties prenantes.
