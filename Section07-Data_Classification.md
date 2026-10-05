## 1. Data Classification

La **data classification (classification des données)** consiste à
catégoriser les données selon leur valeur pour l'organisation et leur
sensibilité en cas de divulgation.

L'objectif est d'appliquer différents niveaux de protection selon
l'importance des données.

### Entreprise commerciale

Une organisation peut utiliser : - **Public** - **Sensitive** -
**Private** - **Confidential** - **Critical** (si nécessaire)

### Gouvernement

On peut retrouver : - **Unclassified** - **Sensitive but
Unclassified** - **Confidential** - **Secret** - **Top Secret**

------------------------------------------------------------------------

## 2. Data Life Cycle

La gestion et la classification des données peuvent demander beaucoup de
temps et de ressources.

Le cycle de vie présenté dans les notes est :

``` text
Collect → Retain → Dispose
```

-   **Collect** : collecte des données.
-   **Retain** : conservation des données pendant la durée définie.
-   **Dispose** : suppression ou destruction des données lorsqu'elles ne
    doivent plus être conservées.

Le cycle de vie est défini par la politique de l'entreprise et dépend
notamment du pays, du gouvernement et des lois applicables concernant la
conservation des données.

------------------------------------------------------------------------

## 3. Data Ownership

Le **data ownership** consiste à identifier les personnes responsables
de la confidentialité, de l'intégrité, de la disponibilité et de la
protection des informations.

### Principaux rôles

  -----------------------------------------------------------------------
  Rôle                                Fonction
  ----------------------------------- -----------------------------------
  **Data Owner**                      Responsable métier des données.

  **Data Controller**                 Responsable de la détermination des
                                      finalités et moyens du traitement.

  **Data Processor**                  Traite les données pour le compte
                                      du Controller.

  **Data Custodian**                  Assure la gestion et la protection
                                      technique des données.

  **Data Steward**                    Participe à la gestion, à la
                                      qualité et à la gouvernance des
                                      données.

  **Data Privacy Officer**            Responsable des sujets liés à la
                                      protection des données et de la vie
                                      privée.
  -----------------------------------------------------------------------

### Data Owner

Le **Data Owner** est généralement une entité ou un responsable métier
connaissant le mieux les données et leur utilisation.

Les équipes IT ne sont donc pas nécessairement les Data Owners : elles
peuvent plutôt assurer leur gestion technique.

------------------------------------------------------------------------

## 4. Data States

Les données peuvent être dans trois états :

``` text
Data at Rest
Data in Transit
Data in Use
```

### Data at Rest

Les **données au repos** sont stockées sur un système.

Elles peuvent être protégées par chiffrement :

-   **Full Disk Encryption** : chiffrement du disque entier.
-   **Partition Encryption** : chiffrement d'une partition.
-   **File Encryption** : chiffrement de fichiers.
-   **Volume Encryption** : chiffrement d'un volume.
-   **Database Encryption** : chiffrement d'une base de données.
-   **Record Encryption** : chiffrement au niveau d'un enregistrement.

### Data in Transit

Les **données en transit** circulent entre plusieurs systèmes.

Exemples de technologies permettant de sécuriser leur transport : -
**SSL / TLS** - **VPN** - **IPsec**

### Data in Use

Les **données en cours d'utilisation** sont actuellement traitées par un
système ou une application.

Les notes mentionnent notamment : - **Application-level security** -
**Access Controls** - **Secure Enclaves** - **Intel Software Guard
Extensions (Intel SGX)**

------------------------------------------------------------------------

## 5. Data Types

Les notes distinguent notamment : - données réglementées ; - **PII** ; -
**PHI** ; - secrets commerciaux ; - propriété intellectuelle ; -
informations juridiques ; - informations financières ; - données
lisibles par l'humain ; - données non directement lisibles par l'humain.

### Regulated Data

Les **données réglementées** sont contrôlées par des lois,
réglementations ou normes industrielles.

Exemples : - **GDPR / RGPD** - **HIPAA**

### PII

**PII = Personally Identifiable Information**

Informations pouvant être utilisées pour identifier un individu.

### PHI

**PHI = Protected Health Information**

Informations concernant la santé, l'état de santé, la fourniture de
soins ou le paiement de soins lorsqu'elles peuvent être reliées à un
individu spécifique.

------------------------------------------------------------------------

## 6. Data Sovereignty

La **data sovereignty** désigne le principe selon lequel les
informations numériques sont soumises aux lois du pays dans lequel elles
sont situées ou traitées.

La localisation géographique des données peut donc avoir un impact
important sur une entreprise.

Il faut notamment connaître : - la localisation physique des datacenters
; - le lieu de stockage des données ; - le lieu de traitement des
données ; - les éventuels transferts internationaux.

Les notes citent notamment la Chine et la Russie comme exemples de pays
ayant des règles strictes pouvant imposer le stockage et le traitement
de certaines données à l'intérieur de leurs frontières.

> La localisation des données doit être connue afin d'éviter des
> transferts contraires aux exigences légales applicables.

------------------------------------------------------------------------

## 7. Techniques de sécurisation des données

Les principales techniques mentionnées sont :

### Geographic Restrictions

Limiter l'accès ou le traitement des données selon leur localisation
géographique.

### Encryption

Chiffrer les données afin d'empêcher leur lecture sans la clé
appropriée.

### Hashing

Transformer une donnée en une valeur permettant notamment de vérifier
son intégrité.

### Masking

Masquer tout ou partie d'une donnée sensible.

Exemple :

``` text
4532 1234 5678 9010
↓
**** **** **** 9010
```

### Tokenization

Remplacer une donnée sensible par un **token** qui peut être utilisé à
sa place.

### Obfuscation

Rendre une information ou un code plus difficile à comprendre ou à
analyser.

### Segmentation

Séparer les systèmes, réseaux ou données afin de limiter les accès et la
propagation d'une compromission.

### Permission Restrictions

Limiter l'accès aux données selon les droits et les besoins de
l'utilisateur.

------------------------------------------------------------------------

## 8. Data Loss Prevention (DLP)

Le **Data Loss Prevention (DLP)** permet de surveiller et contrôler les
données afin de détecter et prévenir les tentatives de fuite ou de vol.

Un DLP peut surveiller les données : - **at rest** ; - **in transit**
; - **in use**.

Il peut être implémenté au niveau logiciel ou matériel.

------------------------------------------------------------------------

## 9. Endpoint DLP

L'**Endpoint DLP** est un logiciel installé sur un poste de travail ou
un ordinateur portable.

Il surveille les données utilisées sur l'ordinateur.

``` text
Workstation / Laptop
        |
        v
   Endpoint DLP
        |
        v
  Données utilisées
```

------------------------------------------------------------------------

## 10. Network DLP

Le **Network DLP** est une solution logicielle ou matérielle placée au
niveau du réseau afin de détecter les fuites de données **en transit**.

``` text
Poste → Réseau → Network DLP → Internet
                     |
                  Inspection
```

------------------------------------------------------------------------

## 11. Storage DLP

Le **Storage DLP** est une solution installée sur un serveur ou dans un
environnement de stockage.

Il inspecte les données **au repos**.

------------------------------------------------------------------------

## 12. Cloud-based DLP

Le **Cloud-based DLP** est généralement proposé comme un service cloud,
souvent sous forme de **Software as a Service (SaaS)**.

Il permet de protéger les données utilisées dans les services et
stockages cloud.

------------------------------------------------------------------------

## 13. Exemple : DLP dans Google Workspace

Un DLP peut être configuré dans la console d'administration Google
Workspace.

Exemple :

``` text
Utilisateur
    ↓
Gmail
    ↓
Pièce jointe contenant des données sensibles
    ↓
Règle DLP
    ├── Blocage
    ├── Avertissement
    └── Alerte administrateur
```

------------------------------------------------------------------------

## 14. Tableau récapitulatif

  -----------------------------------------------------------------------
  Notion                              À retenir
  ----------------------------------- -----------------------------------
  **Data Classification**             Classe les données selon leur
                                      valeur et leur sensibilité.

  **Data Life Cycle**                 Collect → Retain → Dispose.

  **Data Ownership**                  Définit les responsabilités liées
                                      aux données.

  **Data Owner**                      Responsable métier des données.

  **Data Controller**                 Détermine les finalités et moyens
                                      du traitement.

  **Data Processor**                  Traite les données pour le compte
                                      du Controller.

  **Data Custodian**                  Assure la gestion/protection
                                      technique.

  **Data Steward**                    Participe à la gouvernance et à la
                                      qualité.

  **Data Privacy Officer**            Responsable de la protection des
                                      données et de la vie privée.

  **Data at Rest**                    Données stockées.

  **Data in Transit**                 Données en cours de transfert.

  **Data in Use**                     Données actuellement utilisées ou
                                      traitées.

  **PII**                             Informations permettant
                                      d'identifier un individu.

  **PHI**                             Informations de santé liées à un
                                      individu.

  **Regulated Data**                  Données soumises à des lois,
                                      réglementations ou normes.

  **Data Sovereignty**                Impact de la localisation des
                                      données sur les lois applicables.

  **Encryption**                      Protège les données par
                                      chiffrement.

  **Hashing**                         Produit une valeur permettant
                                      notamment de vérifier l'intégrité.

  **Masking**                         Masque les données sensibles.

  **Tokenization**                    Remplace une donnée sensible par un
                                      token.

  **Obfuscation**                     Rend une donnée ou un code plus
                                      difficile à comprendre.

  **Segmentation**                    Sépare les environnements ou
                                      données pour limiter les accès.

  **DLP**                             Détecte et prévient les fuites de
                                      données.

  **Endpoint DLP**                    DLP au niveau du poste.

  **Network DLP**                     DLP pour les données en transit.

  **Storage DLP**                     DLP pour les données stockées.

  **Cloud DLP**                       DLP appliqué aux environnements
                                      cloud.
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 15. À retenir pour les examens

-   **Data Classification** = classer les données selon leur valeur et
    leur sensibilité.
-   **Data Life Cycle** = Collect → Retain → Dispose.
-   **Data Owner** = responsable métier des données.
-   **Data at Rest** = données stockées.
-   **Data in Transit** = données qui circulent.
-   **Data in Use** = données en cours d'utilisation.
-   **PII** = données permettant d'identifier une personne.
-   **PHI** = données de santé associées à une personne.
-   **Regulated Data** = données soumises à des exigences
    légales/réglementaires.
-   **Data Sovereignty** = impact de la localisation géographique des
    données sur les lois applicables.
-   **Encryption** = protège la confidentialité.
-   **Hashing** = permet notamment de vérifier l'intégrité.
-   **Masking** = masque les informations sensibles.
-   **Tokenization** = remplace une donnée sensible par un token.
-   **DLP** = surveille et contrôle les données pour limiter les fuites.
-   **Endpoint DLP** = protection au niveau du poste.
-   **Network DLP** = protection des données en transit.
-   **Storage DLP** = protection des données stockées.
-   **Cloud DLP** = protection des données dans les services cloud.
