# 13 - Cryptography — Synthèse

## 1. Symmetric vs Asymmetric Encryption

### Symmetric Encryption
Le **chiffrement symétrique** utilise une **même clé secrète** pour chiffrer et déchiffrer les données.

```text
Plaintext → Chiffrement → Ciphertext
                         ↓
                   même clé secrète
                         ↓
Ciphertext → Déchiffrement → Plaintext
```

L'expéditeur et le destinataire doivent donc connaître le même secret.

### Asymmetric Encryption
Le **chiffrement asymétrique** utilise deux clés différentes :
- **clé publique** : peut être distribuée ;
- **clé privée** : doit rester secrète.

Dans le cas classique du chiffrement :

```text
Plaintext
   ↓
Clé publique de Mary
   ↓
Ciphertext
   ↓
Clé privée de Mary
   ↓
Plaintext
```

---

## 2. Symmetric Algorithms

| Algorithme | Type |
|---|---|
| **DES** | Symétrique |
| **3DES** | Symétrique |
| **IDEA** | Symétrique |
| **AES** | Symétrique |
| **Blowfish** | Symétrique |
| **Twofish** | Symétrique |
| **RC4** | Symétrique |
| **RC5** | Symétrique |
| **RC6** | Symétrique |

**AES = Advanced Encryption Standard**.

---

## 3. Asymmetric Algorithms

Les algorithmes/mécanismes mentionnés :
- **Diffie-Hellman (DH)**
- **RSA**
- **ECC**
- **ECDH**
- **ECDHE**
- **ECDSA**

### RSA
**RSA** vient de **Ron Rivest, Adi Shamir et Leonard Adleman**.

### ECC
**ECC = Elliptic Curve Cryptography** : cryptographie basée sur les courbes elliptiques.

### ECDH
**ECDH = Elliptic Curve Diffie-Hellman** : mécanisme d'échange de clé basé sur ECC.

### ECDHE
**ECDHE = Elliptic Curve Diffie-Hellman Ephemeral** : version utilisant des clés éphémères.

### ECDSA
**ECDSA = Elliptic Curve Digital Signature Algorithm** : algorithme de signature numérique basé sur ECC.

---

## 4. Diffie-Hellman

**Diffie-Hellman** permet à deux parties d'établir un **secret partagé** sur un canal qui n'est pas nécessairement sécurisé.

Le secret n'est pas directement transmis sur le réseau.

---

## 5. Hybrid Encryption

Une implémentation hybride combine les deux types de cryptographie :

1. l'asymétrique sert à établir ou protéger une clé secrète ;
2. cette clé est ensuite utilisée avec un algorithme symétrique ;
3. le symétrique chiffre efficacement les données.

```text
Asymmetric
    ↓
Établissement / protection de clé
    ↓
Symmetric
    ↓
Chiffrement des données
```

Le symétrique est adapté au chiffrement de grandes quantités de données, tandis que l'asymétrique est particulièrement utile pour l'échange de clés et l'authentification.

---

## 6. Stream Cipher vs Block Cipher

### Stream Cipher
Un **stream cipher** chiffre les données sous forme de flot à l'aide d'un **keystream**. Une opération **XOR** est notamment utilisée dans ce type de chiffrement.

```text
Plaintext
   XOR
Keystream
   ↓
Ciphertext
```

### Block Cipher
Un **block cipher** découpe les données en **blocs de taille fixe** puis chiffre chaque bloc.

| Stream Cipher | Block Cipher |
|---|---|
| Traite les données sous forme de flot. | Traite des blocs de taille fixe. |
| Utilise un keystream. | Travaille bloc par bloc. |
| XOR fréquemment utilisé. | Taille de bloc définie par l'algorithme. |

---

## 7. Hashing

Le **hashing** est une fonction cryptographique à sens unique qui transforme une entrée en **message digest**.

```text
Input → Hash Function → Digest
```

Il est notamment utilisé pour vérifier l'intégrité.

### Algorithmes mentionnés

- **MD5**
- **SHA-1**
- **SHA-2**
- **SHA-3**
- **SHA-224**
- **SHA-256**
- **SHA-384**
- **SHA-512**
- **RIPEMD**

### SHA-2
La famille SHA-2 comprend notamment SHA-224, SHA-256, SHA-384 et SHA-512.

---

## 8. HMAC

**HMAC = Hash-based Message Authentication Code**

HMAC combine :
- une fonction de hachage ;
- une clé secrète.

Exemples :
- HMAC-MD5
- HMAC-SHA1
- HMAC-SHA256

HMAC permet notamment de vérifier l'intégrité et l'authenticité d'un message lorsqu'un secret partagé est connu.

---

## 9. Digital Signature

Une **signature numérique** permet notamment de vérifier l'origine et l'intégrité d'un message.

Principe simplifié :

```text
Message
   ↓
Hash
   ↓
Signature avec la clé privée
   ↓
Signature numérique
```

Le destinataire utilise la clé publique correspondante pour vérifier la signature.

La signature numérique n'est donc pas simplement un chiffrement du message : elle sert principalement à l'authentification et à l'intégrité, avec des propriétés de non-répudiation selon le système utilisé.

---

## 10. DSS

**DSS = Digital Signature Standard**.

DSS désigne un standard concernant les signatures numériques.

---

## 11. Password Attacks and Protection

### Dictionary Attack
Teste les mots de passe issus d'une liste prédéfinie.

### Brute Force Attack
Teste les combinaisons possibles selon l'espace de recherche.

### Rainbow Tables
Tables pré-calculées permettant d'accélérer la recherche de correspondances avec des hashes.

### Salting
Ajout d'une donnée aléatoire au secret avant le traitement cryptographique.

```text
Password + Salt → Hash
```

Le salt doit idéalement être unique pour chaque mot de passe.

### Key Stretching
Technique augmentant le coût de calcul nécessaire pour dériver un résultat cryptographique à partir d'un secret, afin de rendre les attaques par essais plus coûteuses.

### Limited Failed Login Attempts
Limiter les tentatives de connexion échouées permet de ralentir certaines attaques par force brute.

---

## 12. Collision et Birthday Attack

Une **collision** se produit lorsque deux entrées différentes produisent le même hash.

```text
Input A ─┐
         ├→ Hash → même digest
Input B ─┘
```

Une **birthday attack** exploite le **birthday paradox** pour rechercher une collision plus efficacement qu'une recherche naïve exhaustive.

---

## 13. Pass the Hash

Le **Pass the Hash** permet d'utiliser une valeur d'authentification dérivée d'un mot de passe, notamment un hash, afin de s'authentifier sans connaître nécessairement le mot de passe en clair.

Cette technique est particulièrement associée aux environnements Windows et NTLM.

### Mimikatz

**Mimikatz** est un outil connu pour l'extraction et l'exploitation de différents secrets d'authentification sous Windows.

---

## 14. Nonce

Un **nonce** est une valeur destinée à être utilisée une seule fois dans une opération ou un protocole cryptographique.

Le terme vient de **number used once**.

---

# 15. Public Key Infrastructure (PKI)

**PKI = Public Key Infrastructure**

Une PKI est un ensemble de :
- matériels ;
- logiciels ;
- politiques ;
- procédures ;
- personnes ;

permettant de gérer les clés cryptographiques et les certificats numériques.

Elle facilite notamment :
- l'authentification ;
- les communications chiffrées ;
- la gestion des certificats ;
- la confiance entre les entités.

La cryptographie à clé publique n'est qu'une partie de l'architecture PKI.

---

## 16. Certificate Authority

**CA = Certificate Authority**

La CA est l'autorité qui émet et signe les certificats numériques.

Elle participe à la création de la chaîne de confiance.

```text
Root CA
  ↓
CA
  ↓
Certificat du serveur
```

---

## 17. Registration Authority

**RA = Registration Authority**

La RA intervient dans le processus de demande de certificat.

Elle peut :
- recueillir les informations d'identification ;
- vérifier les informations ;
- transmettre la demande à la CA.

---

## 18. Certificate Signing Request

**CSR = Certificate Signing Request**

Un CSR est une demande de certificat contenant notamment des informations sur l'entité qui demande le certificat.

Exemples :
- organisation ;
- nom de domaine ;
- localité ;
- pays.

---

## 19. Digital Certificate

Un **certificat numérique** est un document électronique signé numériquement qui associe une **clé publique à une identité**.

---

## 20. Types de certificats

### Wildcard Certificate
Permet de couvrir plusieurs sous-domaines.

Exemple :

```text
*.example.com
```

### Single-sided Certificate
Dans une authentification classique, une seule partie présente son certificat.

### Dual-sided Certificate
Dans une authentification mutuelle, les deux parties présentent un certificat. On parle notamment de **mutual TLS (mTLS)**.

### Self-signed Certificate
Certificat signé par l'entité qui l'a créé plutôt que par une CA publique reconnue.

### Third-party Certificate
Certificat émis et signé par une autorité de certification tierce.

---

## 21. Root of Trust

Le **root of trust** représente une racine de confiance à partir de laquelle une chaîne de certificats peut être validée.

Les notes citent notamment :
- VeriSign ;
- Amazon ;
- Google Cloud ;
- Cloudflare.

---

## 22. SAN

**SAN = Subject Alternative Name**

Le champ SAN permet de spécifier des noms supplémentaires couverts par un certificat.

Il peut notamment contenir :
- plusieurs noms de domaine ;
- certaines adresses IP.

---

## 23. Certificate Revocation List

**CRL = Certificate Revocation List**

Une CRL est une liste publiée par une CA contenant les certificats qui ont été révoqués.

---

## 24. OCSP

**OCSP = Online Certificate Status Protocol**

OCSP permet de vérifier le statut de révocation d'un certificat, notamment à partir de son numéro de série.

### OCSP Stapling

Avec l'**OCSP stapling**, le serveur récupère périodiquement une preuve de statut auprès du service OCSP puis la fournit au client.

---

## 25. Public Key Pinning

Le **public key pinning** consiste à associer un service à une clé publique ou à une information cryptographique attendue afin de détecter certaines substitutions de certificats ou de clés.

---

## 26. Key Escrow

Le **key escrow** consiste à conserver une copie sécurisée d'une clé privée afin de permettre sa récupération dans certaines circonstances.

### Key Recovery Agent

Un **Key Recovery Agent (KRA)** est un mécanisme spécialisé permettant la récupération d'une clé protégée lorsqu'elle est perdue ou corrompue, selon les procédures prévues.

---

# 27. Blockchain

Une **blockchain** est un registre partagé et conçu pour être difficile à modifier.

Elle peut servir notamment à :
- enregistrer des transactions ;
- suivre des actifs ;
- établir de la confiance entre plusieurs participants.

Les blocs sont liés cryptographiquement entre eux, notamment grâce aux hashes.

```text
Block 1 → Block 2 → Block 3 → Block 4
```

Chaque bloc contient notamment une référence au bloc précédent.

### Public Ledger
Registre accessible selon les règles du réseau concerné.

### Smart Contracts
Programmes exécutés sur une blockchain permettant d'automatiser certaines règles ou transactions.

### Permissioned Blockchain
Blockchain dont l'accès ou certaines opérations sont réservés à des participants autorisés.

---

# 28. Cryptographic Hardware

### TPM

**TPM = Trusted Platform Module**

Composant matériel destiné notamment à fournir des fonctions de sécurité et à protéger certaines clés cryptographiques.

### HSM

**HSM = Hardware Security Module**

Matériel spécialisé dans la protection et la gestion des clés cryptographiques ainsi que dans certaines opérations cryptographiques.

### Key Management System

Un **KMS** permet de gérer le cycle de vie des clés :
- création ;
- stockage ;
- utilisation ;
- rotation ;
- révocation ;
- destruction.

### Secure Enclave

Une **Secure Enclave** est un environnement matériel isolé destiné à protéger certaines opérations ou données sensibles.

---

# 29. Obfuscation, Steganography, Tokenization, Masking

### Obfuscation
Rend un code ou une information plus difficile à comprendre ou analyser.

### Steganography
Dissimule une information dans un autre support.

```text
Image apparemment normale
          ↓
     Données cachées
```

Différence :
- **Encryption** = rend le contenu incompréhensible ;
- **Steganography** = cherche à cacher l'existence du message.

### Tokenization
Remplace une donnée sensible par une valeur de substitution appelée **token**.

### Data Masking
Masque une partie ou la totalité d'une donnée sensible.

```text
1234 5678 9012 3456
        ↓
**** **** **** 3456
```

---

# 30. Cryptographic Attacks

Les attaques cryptographiques cherchent à exploiter une faiblesse :
- d'un algorithme ;
- d'une implémentation ;
- d'une gestion de clé ;
- d'un protocole.

Exemples :
- downgrade attacks ;
- collision attacks ;
- birthday attacks ;
- attaques contre le stockage des mots de passe ;
- menaces liées au quantum computing.

## Downgrade Attack

Force ou trompe un système afin qu'il utilise une version ou un mécanisme cryptographique plus faible.

---

# 31. Quantum Computing

L'**informatique quantique** utilise des principes de mécanique quantique pour effectuer certains calculs.

### Qubit

Le **qubit** est l'unité fondamentale d'information quantique.

Les ordinateurs quantiques pourraient à terme menacer certains algorithmes cryptographiques actuels.

---

# 32. Post-Quantum Cryptography

La **Post-Quantum Cryptography (PQC)** vise à développer des algorithmes résistants aux attaques réalisées avec de futurs ordinateurs quantiques.

Les algorithmes mentionnés dans les notes sont :
- **CRYSTALS-Dilithium**
- **FALCON**
- **SPHINCS+**

Ils sont notamment associés aux signatures numériques post-quantiques.

---

# 33. Tableau récapitulatif

| Notion | À retenir |
|---|---|
| **Symmetric** | Même clé pour chiffrer et déchiffrer. |
| **Asymmetric** | Clé publique + clé privée. |
| **Diffie-Hellman** | Établissement d'un secret partagé. |
| **RSA** | Cryptographie asymétrique. |
| **ECC** | Cryptographie sur courbes elliptiques. |
| **ECDH** | Diffie-Hellman basé sur ECC. |
| **ECDHE** | ECDH avec clés éphémères. |
| **ECDSA** | Signature numérique basée sur ECC. |
| **Hybrid Encryption** | Combine asymétrique et symétrique. |
| **Stream Cipher** | Chiffrement sous forme de flot. |
| **Block Cipher** | Chiffrement par blocs. |
| **Hashing** | Fonction à sens unique produisant un digest. |
| **HMAC** | Hash + clé secrète. |
| **Digital Signature** | Authentification et intégrité. |
| **Salt** | Donnée aléatoire ajoutée avant le hash du mot de passe. |
| **Key Stretching** | Augmente le coût des essais. |
| **PKI** | Infrastructure de gestion des clés et certificats. |
| **CA** | Émet et signe les certificats. |
| **CSR** | Demande de certificat. |
| **CRL** | Liste de certificats révoqués. |
| **OCSP** | Vérification du statut d'un certificat. |
| **SAN** | Noms supplémentaires couverts par un certificat. |
| **Key Escrow** | Conservation sécurisée d'une copie de clé. |
| **TPM** | Composant matériel de sécurité. |
| **HSM** | Matériel spécialisé pour les opérations et clés cryptographiques. |
| **KMS** | Gestion du cycle de vie des clés. |
| **Blockchain** | Registre partagé lié cryptographiquement. |
| **Steganography** | Cache l'existence d'une information. |
| **Tokenization** | Remplace une donnée par un token. |
| **Masking** | Masque une donnée sensible. |
| **Downgrade Attack** | Force une protection cryptographique plus faible. |
| **PQC** | Cryptographie conçue pour résister aux menaces quantiques. |

---

# 34. À retenir pour les examens

- **Symmetric = 1 clé secrète partagée.**
- **Asymmetric = clé publique + clé privée.**
- **Diffie-Hellman = établissement d'un secret partagé.**
- **RSA = algorithme asymétrique.**
- **ECC = cryptographie sur courbes elliptiques.**
- **ECDH = échange de clé basé sur ECC.**
- **ECDHE = ECDH avec clés éphémères.**
- **ECDSA = signature numérique basée sur ECC.**
- **Hybrid = asymétrique pour établir/protéger la clé, symétrique pour chiffrer les données.**
- **Stream cipher = chiffrement sous forme de flot.**
- **Block cipher = chiffrement par blocs.**
- **Hash = fonction à sens unique.**
- **HMAC = hash + clé secrète.**
- **Digital Signature = authentification + intégrité.**
- **Salt = rend les attaques pré-calculées plus difficiles.**
- **Key stretching = rend les essais de mots de passe plus coûteux.**
- **PKI = gestion des clés et certificats.**
- **CA = émet et signe les certificats.**
- **CSR = demande de certificat.**
- **CRL / OCSP = vérification de révocation.**
- **TPM / HSM = matériel de sécurité cryptographique.**
- **Steganography = cache l'existence du message.**
- **Tokenization = remplace la donnée par un token.**
- **Masking = masque la donnée.**
- **Downgrade attack = force un mécanisme plus faible.**
- **PQC = cryptographie adaptée aux menaces des ordinateurs quantiques.**
