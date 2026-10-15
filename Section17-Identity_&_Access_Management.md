## 1. Gestion des identités et des accès

L’**Identity and Access Management (IAM)** regroupe les systèmes et processus permettant de gérer l’accès aux informations et aux ressources d’une organisation. L’objectif est que les bonnes personnes accèdent aux bonnes ressources, au bon moment et pour les bonnes raisons.

| Notion | Définition |
|---|---|
| **Identification** | L’utilisateur déclare l’identité qu’il souhaite utiliser, par exemple un nom d’utilisateur ou une adresse e-mail. |
| **Authentification** | Le système vérifie l’identité déclarée à l’aide de justificatifs ou de facteurs d’authentification. |
| **Autorisation** | Le système détermine les actions et ressources auxquelles l’identité authentifiée peut accéder. |
| **Accounting / traçabilité** | Enregistrement des activités pour permettre le suivi et l’audit. |
| **Provisioning** | Création des comptes et attribution des droits nécessaires. |
| **Deprovisioning** | Retrait des accès lorsqu’ils ne sont plus nécessaires. |
| **Identity proofing** | Vérification de l’identité réelle d’une personne avant la création du compte. |
| **Interopérabilité** | Capacité de systèmes différents à fonctionner ensemble et à échanger des informations. |
| **Attestation des accès** | Vérification périodique que les comptes et droits sont corrects, justifiés et à jour. |

À distinguer : identification = « Qui prétends-tu être ? » ; authentification = « Peux-tu le prouver ? » ; autorisation = « Que peux-tu faire ? » ; accounting = « Qu’as-tu fait ? ».

## 2. Authentification multifacteur (MFA)

La **MFA** exige au moins deux facteurs appartenant à des catégories différentes et indépendantes.

| Facteur | Principe | Exemples |
|---|---|---|
| Connaissance | Quelque chose que l’on sait | Mot de passe, code PIN |
| Possession | Quelque chose que l’on possède | Clé de sécurité, carte, application d’authentification |
| Inhérence | Quelque chose que l’on est | Empreinte digitale, reconnaissance faciale |
| Comportement | Quelque chose que l’on fait | Dynamique de frappe, habitudes de mouvement |
| Localisation | Un endroit où l’on se trouve | Connexion depuis une zone autorisée |

Le comportement et la localisation servent souvent de signaux contextuels de risque et ne constituent pas automatiquement un facteur MFA. Une authentification à un facteur utilise une seule catégorie. Deux éléments de la même catégorie, comme un mot de passe et un PIN, ne constituent pas nécessairement de la MFA.

## 3. Passkeys et authentification sans mot de passe

Une **passkey** est un justificatif fondé sur la cryptographie à clé publique. L’utilisateur valide généralement la connexion avec le déverrouillage de son appareil (PIN ou biométrie), tandis que le service vérifie une preuve cryptographique. Les passkeys résistent mieux au phishing que les mots de passe et les codes à usage unique classiques.

Autres méthodes :
- **Biométrie** : empreinte digitale ou reconnaissance faciale.
- **Jeton matériel** : clé de sécurité ou appareil dédié.
- **OTP (*One-Time Password*)** : code à usage unique ou à durée de validité courte.
- **Magic link** : lien de connexion envoyé à une adresse ou un canal enregistré.

Le niveau de sécurité dépend de l’implémentation. Un lien magique ou un code SMS n’offre pas les mêmes garanties qu’une passkey résistante au phishing.

## 4. Sécurité des mots de passe

- **Longueur** : privilégier des mots de passe longs et uniques, ou des phrases de passe.
- **Complexité** : la variété des caractères peut augmenter l’espace de recherche, mais ne compense pas un mot de passe court ou prévisible.
- **Réutilisation** : réutiliser un mot de passe permet à un attaquant de tenter de compromettre d’autres services après une fuite.
- **Expiration / âge** : imposer des changements périodiques sans raison peut encourager des variantes prévisibles. Changer un mot de passe en cas de compromission reste essentiel.
- **Stockage** : les services ne devraient pas stocker les mots de passe en clair ; ils doivent utiliser un hachage adapté, salé et configuré avec un coût approprié.

La chaîne « aW3+ » dans les notes n’est pas expliquée : elle ne permet pas d’en déduire une règle précise.

### Gestionnaires de mots de passe

Ils peuvent générer des mots de passe uniques, conserver les identifiants dans un coffre chiffré, remplir automatiquement les formulaires, synchroniser les données et partager des secrets de manière contrôlée. Protéger le coffre par un mot de passe principal robuste et la MFA lorsqu’elle est disponible.

## 5. Attaques contre les mots de passe

| Attaque | Principe |
|---|---|
| **Force brute** | Tester de nombreuses combinaisons jusqu’à trouver la bonne. |
| **Dictionnaire** | Tester des mots et expressions courants ou des mots de passe connus. |
| **Password spraying** | Tester quelques mots de passe courants sur de nombreux comptes pour limiter les verrouillages. |
| **Hybride** | Combiner des mots connus avec des variantes, par exemple des chiffres ou symboles ajoutés. |

Mesures de défense : mots de passe longs et uniques, MFA (idéalement résistante au phishing), limitation du débit, détection des échecs répétés, délais progressifs, CAPTCHA lorsque pertinent et surveillance des connexions inhabituelles. Le CAPTCHA ne doit pas être la seule protection.

## 6. Single Sign-On (SSO)

Le **SSO** permet à un utilisateur de s’authentifier une fois puis d’accéder à plusieurs applications liées par une relation de confiance, sans ressaisir systématiquement ses identifiants.

- **Identity Provider (IdP)** : gère les informations d’identité et fournit les services d’authentification.
- **Service Provider (SP)** : application qui s’appuie sur l’IdP pour établir l’identité de l’utilisateur et appliquer ses règles d’accès.

Avantages : meilleure expérience, productivité accrue, réduction de certains tickets de support et politiques d’authentification plus cohérentes. Risques : un compte central compromis peut ouvrir l’accès à plusieurs applications ; l’IdP devient critique et doit être protégé par MFA, supervision et configuration robuste.

### LDAP, OAuth, OIDC et SAML

| Technologie | Rôle principal |
|---|---|
| **LDAP** | Protocole d’accès aux services d’annuaire ; ce n’est pas à lui seul un protocole SSO web complet. |
| **OAuth 2.0** | Cadre d’autorisation permettant un accès limité à une ressource. Ce n’est pas, à lui seul, un protocole d’authentification. |
| **OpenID Connect (OIDC)** | Couche d’identité et d’authentification construite au-dessus d’OAuth 2.0. |
| **SAML** | Standard fondé sur XML permettant notamment d’échanger des assertions d’authentification et des attributs entre IdP et SP. |

## 7. Fédération d’identités

La **fédération** permet à plusieurs domaines ou systèmes d’identité de se faire confiance et d’échanger des informations ou assertions, sans créer nécessairement un compte local distinct dans chaque service.

Déroulement général :
1. L’utilisateur demande l’accès à un service.
2. Le service le redirige vers l’IdP si nécessaire.
3. L’IdP authentifie l’utilisateur.
4. L’IdP génère une assertion ou un jeton.
5. Le client transmet cette preuve au service.
6. Le service vérifie l’émetteur, l’intégrité, la validité et les paramètres attendus, puis applique ses propres règles d’autorisation.

La séquence exacte dépend du protocole (SAML ou OpenID Connect, par exemple). Une assertion d’authentification ne donne pas automatiquement tous les droits dans l’application.

## 8. Privileged Access Management (PAM)

Le **PAM** regroupe les politiques, procédures et outils permettant de contrôler et surveiller les accès privilégiés : comptes administrateurs, comptes de service ou comptes d’urgence.

Mécanismes courants :
- **Just-in-time (JIT)** : accorder des privilèges pour une durée limitée, au moment où ils sont nécessaires.
- **Password vaulting** : stocker les identifiants privilégiés dans un coffre contrôlé et audité, avec rotation éventuelle.
- **Comptes temporaires** : créer des comptes limités dans le temps puis les désactiver ou supprimer.
- **Élévation contrôlée** : demander une approbation ou une justification pour certains droits.
- **Journalisation des sessions** : conserver une trace des actions sensibles.

Le PAM complète le principe du moindre privilège : il faut aussi réduire les droits permanents et surveiller les opérations.

## 9. Modèles de contrôle d’accès

| Modèle | Principe |
|---|---|
| **MAC (*Mandatory Access Control*)** | Politique centrale et étiquettes de sécurité ; l’utilisateur ne choisit pas librement les permissions. |
| **DAC (*Discretionary Access Control*)** | Le propriétaire d’une ressource peut généralement accorder ou retirer des permissions. |
| **RBAC (*Role-Based Access Control*)** | Les permissions sont liées à des rôles attribués aux utilisateurs selon leurs fonctions. |
| **Rule-Based Access Control** | L’accès dépend de règles prédéfinies, par exemple l’heure ou le réseau source. |
| **ABAC (*Attribute-Based Access Control*)** | La décision dépend d’attributs du sujet, de la ressource, de l’action et du contexte. |

Ces modèles peuvent être combinés.

### Moindre privilège et permission creep

Le **principe du moindre privilège** consiste à accorder uniquement les permissions nécessaires aux tâches de l’utilisateur ou du processus.

La **permission creep** (ou *privilege creep*) survient lorsqu’un utilisateur accumule des droits au fil de ses changements de poste, sans que les anciens droits soient retirés.

Prévention : revue périodique des droits, contrôle lors des changements de fonction, attestation des accès, rôles documentés et retrait automatisé des permissions devenues inutiles.

## 10. Attribution et gestion des comptes

- **Compte administrateur** : droits élevés ; usage à limiter aux tâches d’administration.
- **Compte utilisateur standard** : droits restreints pour les activités quotidiennes.
- **Compte local** : géré directement sur un poste ou serveur, sans nécessairement être synchronisé avec un annuaire central.
- **Compte Microsoft** : identité en ligne Microsoft utilisable pour ouvrir une session ou accéder à certains services, selon l’édition et la configuration.

### UAC sous Windows

Le **User Account Control (UAC)** aide à empêcher les modifications administratives non autorisées en demandant une élévation ou une confirmation lorsqu’une opération requiert des privilèges élevés, selon la configuration.

Bonnes pratiques : utiliser un compte standard au quotidien, n’élever les privilèges que lorsque nécessaire et ne pas approuver automatiquement les demandes UAC inattendues.

### Vérifier les permissions d’un fichier ou dossier

1. Cliquer avec le bouton droit sur le fichier ou dossier.
2. Choisir **Propriétés**.
3. Ouvrir l’onglet **Sécurité**.
4. Examiner les utilisateurs, groupes et autorisations.

Les permissions effectives dépendent aussi de l’appartenance aux groupes et de l’héritage des permissions NTFS.

## 11. Synthèse pour l’examen

- Identification = déclaration d’identité ; authentification = preuve ; autorisation = permissions ; accounting = traçabilité.
- Provisioning crée les comptes et attribue les droits ; deprovisioning retire les accès inutiles.
- Identity proofing vérifie l’identité avant la création ; l’attestation vérifie périodiquement les droits.
- La MFA exige au moins deux catégories de facteurs indépendantes.
- Une passkey repose sur la cryptographie à clé publique et peut résister au phishing.
- Force brute = nombreuses combinaisons ; dictionnaire = mots connus ; spraying = quelques mots de passe sur de nombreux comptes ; hybride = mots et variantes.
- SSO centralise l’authentification mais rend l’IdP critique.
- LDAP est un protocole d’annuaire ; OAuth 2.0 concerne surtout l’autorisation ; OIDC ajoute l’authentification ; SAML permet l’échange d’assertions.
- PAM contrôle les accès privilégiés ; JIT limite leur durée.
- MAC repose sur une politique centrale ; DAC sur le propriétaire ; RBAC sur les rôles ; ABAC sur les attributs.
- Permission creep = accumulation de droits devenus inutiles.
- UAC aide à contrôler les opérations administratives, mais ne remplace pas le moindre privilège.
