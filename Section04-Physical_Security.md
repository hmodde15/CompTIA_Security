## 1. Physical Security — Sécurité physique

La **Physical Security** regroupe les mesures permettant de protéger les personnes, bâtiments, équipements, systèmes informatiques, infrastructures réseau, supports de stockage et données contre les menaces physiques.

Menaces : intrusion, vol, vandalisme, sabotage, destruction, incendie, inondation, accès non autorisé ou manipulation d'équipements.

> Objectif : empêcher les accès physiques non autorisés et limiter les conséquences d'un incident physique.

---

## 2. Fences — Clôtures

Les **fences** sont des barrières physiques autour d'un site.

Elles permettent de :
- empêcher ou ralentir les intrusions ;
- empêcher le trespassing ;
- limiter le vandalisme ;
- protéger contre le vol ;
- contrôler les points d'entrée.

> **Fence = première barrière physique.**

---

## 3. Bollards — Bornes anti-véhicules

Les **bollards** sont des poteaux ou bornes permettant de protéger un bâtiment contre des véhicules.

Ils réduisent notamment les risques de :
- collision accidentelle ;
- véhicule utilisé pour forcer une entrée ;
- attaque par véhicule ;
- intrusion dans une zone protégée.

> **Bollard = protection contre les véhicules.**

---

## 4. Surveillance Systems

Les systèmes de surveillance permettent de **détecter, observer et enregistrer** les activités physiques.

Exemples :
- caméras CCTV ;
- détecteurs de mouvement ;
- capteurs ;
- alarmes ;
- systèmes de contrôle d'accès ;
- agents de sécurité.

### CCTV

**CCTV = Closed-Circuit Television**

Les caméras permettent notamment :
- surveillance en temps réel ;
- enregistrement vidéo ;
- identification ;
- analyse d'incident ;
- dissuasion.

---

## 5. Attaques contre les systèmes de surveillance

Un attaquant peut tenter de contourner ou neutraliser la surveillance.

### Visual obstruction
Bloquer le champ de vision d'une caméra.

### Blinding
Perturber la vision d'une caméra, par exemple avec une lumière intense ou certaines sources infrarouges.

### Acoustic interference
Perturber certains systèmes utilisant des capteurs ou technologies basés sur le son.

### Electromagnetic interference
Perturber certains équipements électroniques ou communications avec des interférences électromagnétiques.

### Physical damage
Endommager :
- caméra ;
- capteur ;
- câble ;
- alimentation ;
- système d'enregistrement.

### Power disruption
Couper l'alimentation d'un système de surveillance.

### Environmental manipulation
Modifier les conditions physiques pouvant perturber certains capteurs.

### Incendie / sabotage
Un incident physique peut être provoqué pour détruire des équipements, créer une diversion ou faciliter un accès.

## Protection

- **Tamper alarms** → détectent la manipulation d'un équipement.
- **Backup power / UPS** → maintiennent l'alimentation en cas de coupure.
- **Redundancy** → plusieurs capteurs/caméras couvrent une même zone.
- **Cable protection** → conduits, câbles protégés ou enterrés.
- **Encryption** → protège certaines communications entre équipements.

---

## 6. Access Control Vestibule / Mantrap

Un **Access Control Vestibule**, aussi appelé **mantrap**, est un sas entre deux zones.

Fonctionnement :
1. la personne entre dans le vestibule ;
2. la première porte se ferme ;
3. l'identité ou le badge est vérifié ;
4. la seconde porte peut être déverrouillée ;
5. la personne accède à la zone sécurisée.

Les deux portes ne doivent normalement pas être ouvertes simultanément.

Utilisations :
- datacenters ;
- salles serveurs ;
- laboratoires ;
- zones militaires ;
- zones sensibles.

> **Vestibule / Mantrap = sas physique de sécurité.**

---

## 7. Tailgating vs Piggybacking

### Tailgating
Une personne suit une personne autorisée à travers une porte sécurisée **sans autorisation explicite**.

### Piggybacking
Une personne autorisée **laisse volontairement entrer** une autre personne.

> **Tailgating → entrée derrière quelqu'un sans autorisation explicite.**  
> **Piggybacking → une personne autorisée laisse entrer quelqu'un.**

Les deux termes sont parfois utilisés comme synonymes selon les sources.

---

## 8. Types de serrures

### Padlock
**Cadenas**, serrure amovible utilisée pour portes, portails, armoires, etc.

### Pin-and-Tumbler Lock
Serrure mécanique classique utilisant un mécanisme de goupilles.

### Numeric / Combination Lock
Serrure utilisant un code ou une combinaison.

### Cipher Lock
Serrure utilisant un code pour autoriser l'accès.

### Wireless Lock
Serrure électronique contrôlée via une technologie sans fil.

### Biometric Lock
Serrure utilisant une caractéristique biométrique :
- empreinte digitale ;
- visage ;
- iris.

### Electronic Access Control System
Système électronique permettant de contrôler les accès via :
- badges ;
- cartes ;
- codes ;
- biométrie ;
- applications mobiles.

Il peut également enregistrer les événements d'accès.

---

## 9. Physical Security Threats

Exemples :
- forçage d'une serrure ;
- attaque contre un cadenas ;
- contournement du contrôle d'accès ;
- clonage de badge ;
- effraction ;
- tailgating ;
- piggybacking ;
- manipulation d'équipements ;
- sabotage ;
- vol ;
- vandalisme ;
- confrontation avec la sécurité ;
- véhicule contre une barrière ;
- destruction de caméras ;
- coupure de câbles ;
- incendie ;
- accès physique aux serveurs.

---

## 10. Security Guards

Les agents de sécurité jouent plusieurs rôles.

### Dissuasion
Leur présence peut décourager une intrusion.

### Identification
Vérification de l'identité, des badges, des autorisations et des visiteurs.

### Surveillance
Surveillance des entrées, sorties, zones sensibles et comportements suspects.

### Réponse
Intervention rapide en cas d'intrusion, d'alarme ou de comportement suspect.

> **Security Guard + Access Badge + Vestibule** constituent plusieurs couches complémentaires de sécurité.

---

## 11. Defense in Depth

La sécurité physique repose souvent sur plusieurs couches.

Exemple :

**Fence → Bollards → Security Guard → Badge → Vestibule → Biométrie → Salle serveur**

Si une couche est contournée, les autres continuent de protéger la ressource.

> **Defense in Depth = plusieurs couches de sécurité complémentaires.**

---

## 12. Access Badges

Un **access badge** permet à une personne d'accéder à certaines zones.

Le système peut :
- identifier l'utilisateur ;
- vérifier ses droits ;
- autoriser/refuser l'accès ;
- enregistrer l'accès dans les logs.

---

## 13. RFID

**RFID = Radio Frequency Identification**

La RFID utilise des **ondes radio** pour identifier un objet ou une personne équipée d'un tag ou badge.

Utilisations :
- contrôle d'accès ;
- identification ;
- suivi d'équipements ;
- gestion des stocks.

---

## 14. NFC

**NFC = Near Field Communication**

Technologie de communication sans fil à **très courte distance**.

Utilisée notamment dans :
- smartphones ;
- cartes sans contact ;
- badges ;
- paiements ;
- contrôle d'accès.

> **RFID = famille plus large de technologies radio d'identification.**  
> **NFC = technologie de communication à très courte portée utilisant notamment des principes issus de la RFID.**

---

## 15. Magnetic Stripe

Une **magnetic stripe** est une bande magnétique contenant des informations pouvant être lues par un lecteur.

On en trouve notamment sur certaines anciennes cartes d'accès ou cartes d'identification.

---

## 16. Access Badge Cloning

Le **badge cloning** consiste à copier les informations permettant à un badge d'être reconnu par un système de contrôle d'accès.

Un attaquant peut ensuite tenter d'utiliser le badge cloné pour obtenir un accès non autorisé.

### Risques
- accès à une zone sensible ;
- vol ;
- sabotage ;
- accès aux salles serveurs ;
- accès aux équipements.

### Protection
- badges utilisant des technologies sécurisées ;
- authentification multifactorielle ;
- biométrie ;
- vidéosurveillance ;
- vérification des accès ;
- détection des comportements inhabituels ;
- révocation rapide des badges perdus ;
- limitation des privilèges.

> Tous les badges RFID ne sont pas faciles à cloner : cela dépend fortement de la technologie et des mécanismes cryptographiques utilisés.

---

## 17. Biometrics

La biométrie utilise des caractéristiques physiques ou comportementales pour identifier une personne.

Exemples :
- empreinte digitale ;
- visage ;
- iris ;
- voix ;
- rétine.

---

## 18. False Acceptance Rate — FAR

**FAR = False Acceptance Rate**

Le FAR correspond au taux auquel un système biométrique **accepte à tort une personne qui ne devrait pas être autorisée**.

> **FAR → mauvaise personne acceptée.**

Un FAR élevé représente un risque de sécurité plus important.

---

## 19. False Rejection Rate — FRR

**FRR = False Rejection Rate**

Le FRR correspond au taux auquel un système biométrique **refuse à tort une personne qui devrait être autorisée**.

> **FRR → bonne personne refusée.**

Un FRR élevé représente davantage de problèmes d'utilisation.

---

## 20. FAR vs FRR

| Mesure | Signification | Conséquence |
|---|---|---|
| **FAR** | Personne non autorisée acceptée | Risque de sécurité |
| **FRR** | Personne autorisée refusée | Problème d'utilisation |

---

## 21. Equal Error Rate — EER

**EER = Equal Error Rate**

L'EER est le point auquel :

> **FAR = FRR**

Il sert à évaluer les performances d'un système biométrique.

En général :

> **Plus l'EER est faible, meilleur est le système biométrique.**

Il est aussi appelé **Crossover Error Rate (CER)** dans certaines ressources.

---

## 22. Seuil biométrique

Un système biométrique utilise un **threshold / seuil** pour décider si une correspondance est suffisamment bonne.

### Seuil plus permissif
Davantage de personnes peuvent être acceptées.

→ **FAR augmente généralement.**

### Seuil plus strict
Davantage de personnes légitimes peuvent être refusées.

→ **FRR augmente généralement.**

> Le réglage du seuil crée donc un compromis entre sécurité et facilité d'utilisation.

---

## 23. Exemple global

Une entreprise possède une salle serveur.

### Protection extérieure
**Fence** → protège le périmètre.  
**Bollards** → protègent contre les véhicules.

### Entrée du bâtiment
**Security Guard** → vérification des personnes.  
**Access Badge** → contrôle électronique.  
**CCTV** → surveillance et enregistrement.

### Salle serveur
**Access Control Vestibule** → sas sécurisé.  
**Biometric Lock** → vérification biométrique.

### Surveillance
**Tamper Alarm** → détection d'une manipulation.  
**UPS** → maintien de l'alimentation.  
**Redundant Camera** → surveillance même si une caméra est neutralisée.

### Journalisation
Le système peut enregistrer :
- utilisateur ;
- date ;
- heure ;
- porte ;
- résultat de l'accès.

---

# 24. À retenir pour l'examen

### Protection physique

**Fence** → protège le périmètre.

**Bollard** → protège contre les véhicules.

**CCTV** → surveille et enregistre.

**Security Guard** → dissuade, vérifie et intervient.

**Access Badge** → identifie et autorise.

**Vestibule / Mantrap** → crée un sas sécurisé.

**UPS** → alimentation de secours.

**Tamper Alarm** → détecte une manipulation.

### Accès

**Tailgating** → entrer derrière quelqu'un sans autorisation explicite.

**Piggybacking** → une personne autorisée laisse volontairement entrer quelqu'un.

### Badges

**RFID** → identification par radio.

**NFC** → communication sans fil à très courte portée.

**Magnetic Stripe** → données sur bande magnétique.

**Badge Cloning** → copie des informations d'un badge.

### Biométrie

**FAR** → mauvaise personne acceptée.

**FRR** → bonne personne refusée.

**EER** → point où FAR = FRR.

### Défense en profondeur

> **Fence → Guard → Badge → Vestibule → Biometric → CCTV → Logs**

Plusieurs contrôles complémentaires permettent de réduire le risque qu'une seule faille compromette toute la sécurité.
