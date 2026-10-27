# Approches et principes techniques de CapEmploi Campus

Statut de spécification : **Proposed**, sans preuve applicative. Mise à jour : 27 octobre 2026. D091 partiellement validée : principes T01–T03 retenus par D093 ; T04–T10 proposés.

## Contexte et objectif

À la demande du porteur, définir comment concevoir le logiciel avant d'implémenter ses fonctionnalités : responsabilités, SOLID, dependency injection, interfaces, authentification, permissions et accès à la base, avec les contrôles associés.

Ce document distingue les principes retenus et les recommandations restant à discuter par groupes. Accord « oui c est ça » du 27 octobre 2026 : T01–T03 validés dans le périmètre D093. Aucun choix de bibliothèque ni démarrage applicatif ; D090 reste proposée.

Acquis conservés : scope D007, React/Vite et TypeScript, Node.js/NestJS, API REST, PostgreSQL et serveur en monolithe modulaire D008 ; Docker Compose et conteneurisation complète en développement D088–D089. Les principes T01–T03 sont retenus par D093 ; les choix détaillés et T04–T10 restent proposés. Aucun code, installation ou configuration applicative créé.

## 1. Responsabilités et organisation du serveur — T01 validé, D093

Organiser le serveur par domaines métier, introduits progressivement : identité/organisation et offres en premier, puis domaines des tranches suivantes. À l'intérieur d'un domaine, distinguer les responsabilités utiles :

| Responsabilité | Ce qu'elle fait pour une publication d'offre |
|---|---|
| Controller et objets d'entrée/sortie | Recevoir la requête HTTP, vérifier sa forme, appeler l'action et construire la réponse |
| Mécanismes d'accès | Établir l'identité et vérifier les permissions pertinentes ; les contrôles dépendant de l'offre sont liés à l'action métier et aux données |
| Service ou cas d'utilisation | Appliquer les conditions de publication, coordonner les données et les changements d'état |
| Contrat de persistance et implémentation | Exécuter les accès PostgreSQL autorisés et les transactions nécessaires |
| Base de données | Garantir les contraintes d'intégrité définies : liens, unicité et autres contraintes pertinentes |

Principe retenu : contrôleurs courts, règles métier dans les services, accès SQL/ORM dans une responsabilité identifiée. Les noms et dossiers précis restent à décider dans le socle. La validation du format d'une entrée et la vérification métier de publication sont deux responsabilités distinctes.

Comparaison : appeler l'ORM directement depuis un contrôleur demande moins de fichiers au départ mais mêle transport, métier et données. Séparer ces responsabilités facilite nos règles de permissions, de transitions et leurs tests. Nous retenons cette séparation, en ajoutant une classe ou couche lorsqu'elle porte une responsabilité concrète.

## 2. SOLID, simplicité et composition — T02 validé, D093

SOLID est un ensemble de principes pour limiter les effets d'un changement et rendre le code testable. Principe retenu : les appliquer avec des exemples concrets pendant la conception et la revue.

| Principe | Application proposée au projet |
|---|---|
| S — Single Responsibility | Séparer la publication d'une offre, l'envoi d'un message et les requêtes SQL |
| O — Open/Closed | Prévoir un contrat de stockage ou de source d'offres lorsqu'un besoin de substitution apparaît, sans modifier tout le métier |
| L — Liskov Substitution | Une implémentation de dépôt respecte le même contrat, les mêmes garanties et les erreurs prévues que les autres |
| I — Interface Segregation | Un service dépend des opérations dont il a besoin, plutôt que d'une interface géante couvrant toute la plateforme |
| D — Dependency Inversion | Les règles métier s'appuient sur des contrats aux frontières techniques, dont persistance, stockage et messagerie |

Compléter par des fonctions lisibles, des noms métier, peu de duplication et une composition de petits composants. Une interface supplémentaire se justifie par une frontière, un contrat ou une substitution utile ; chaque classe n'exige pas sa propre interface. Les fonctions de calcul simples peuvent rester des fonctions. Éviter les dépôts génériques universels et les hiérarchies d'héritage sans besoin concret.

## 3. Dependency injection et interfaces — T03 validé, D093

**Concept :** une classe reçoit ses dépendances plutôt que de construire elle-même les outils dont elle a besoin. NestJS fournit ces objets à partir de sa configuration de providers.

**Exemple conceptuel :** le service de publication demande un contrat « dépôt d'offres ». L'implémentation PostgreSQL lui est fournie en fonctionnement réel ; un double contrôlé peut servir pour certains tests métier. Le service exprime ce qu'il attend, tandis que l'implémentation réalise l'accès technique. Les tests d'intégration utilisent aussi PostgreSQL pour vérifier les vraies requêtes et contraintes.

Principe retenu : injection par constructeur pour les dépendances de services ; interfaces ciblées pour les frontières dont le métier doit rester indépendant. L'injection d'un service concret interne reste possible quand une abstraction supplémentaire n'apporte rien. Dependency injection et dependency inversion sont liées mais distinctes : recevoir un objet par constructeur ne suffit pas, à lui seul, à rendre le métier indépendant de l'outil.

**Particularité TypeScript :** les interfaces disparaissent à la compilation. NestJS a donc besoin d'un identifiant présent à l'exécution pour associer un contrat à une implémentation. Mécanisme à préciser dans le socle : interface TypeScript et token partagé de type Symbol aux frontières retenues est une option ; une classe abstraite est une alternative. D093 valide les principes de fourniture des dépendances et de contrats ciblés, sans figer ce mécanisme. [Source NestJS](https://docs.nestjs.com/fundamentals/custom-providers)

## 4. Authentification et sessions — proposition T04

Authentification : reconnaître le compte connecté. Autorisation : déterminer ce que ce compte peut faire sur une ressource. Le statut de rattachement de l'apprenant reste une condition métier même après une connexion réussie.

| Option | Intérêt | Contraintes |
|---|---|---|
| Session serveur et cookie contenant un identifiant opaque | Adaptée au navigateur ; révocation et déconnexion pilotées côté serveur | Stockage de sessions, expiration, protection CSRF et configuration des cookies à prévoir |
| Jetons d'accès JWT et mécanisme de renouvellement | Peut convenir à plusieurs types de clients | Renouvellement, révocation, vol de jeton et fraîcheur des permissions à concevoir |
| Fournisseur d'identité externe | Délègue une partie de la gestion des identités | Dépendance, conditions de service, coût éventuel et intégration à évaluer |

**Recommandation initiale à valider :** session côté serveur pour l'application web du pilote. L'API REST ne nécessite pas automatiquement des JWT. Bibliothèque de session/authentification et stockage précis à comparer ; ne pas inventer de protocole cryptographique.

Contrôles proposés : cookie HttpOnly, Secure en environnement HTTPS et SameSite adapté ; protection CSRF, renouvellement de session après connexion et révocation à la déconnexion. Définir les expirations et la réaction aux changements de compte ou de droits. L'attribut HttpOnly limite l'accès au cookie par JavaScript, sans éliminer les risques XSS et CSRF. [Source OWASP](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html)

Le parcours devra aussi spécifier : inscription/activation, première CME, vérification d'adresse si retenue, récupération du compte, hachage adapté des mots de passe, limitation des tentatives et absence de secrets dans les journaux. Ces modalités ne sont pas déjà validées par la proposition de session. Les liens de classe gardent les règles D059 et ne constituent pas des sessions de connexion.

## 5. Autorisations et séparation des établissements — proposition T05

Les exigences de confidentialité sont déjà validées ; leur mécanisme technique est à décider. Recommandation : combiner rôle, rattachement actif, établissement, classe/affectation, propriétaire, état de la ressource et contexte de l'action. Un simple rôle « formateur » ne suffit pas pour consulter n'importe quel CV.

Proposition : vérifications serveur réutilisables pour les conditions communes, règles métier explicites pour chaque action, refus par défaut. Les listes, accès directs, exports et fichiers doivent respecter les mêmes limites. Le contexte d'établissement est établi à partir des rattachements autorisés ; une valeur fournie par le navigateur ne crée aucun droit.

| Stratégie à comparer | Avantage | Contrepartie |
|---|---|---|
| Base et tables partagées, données rattachées à l'établissement | Exploitation et migrations centralisées pour un petit nombre d'établissements | Oubli d'un filtre dangereux ; contraintes, contrôles et tests systématiques nécessaires |
| Schémas ou bases distincts | Séparation technique plus marquée | Migrations, connexions et exploitation plus complexes |

Hypothèse proposée pour le pilote : base partagée avec rattachements explicites et protections côté serveur. À valider après le modèle des données et permissions. Les comptes peuvent relever d'un modèle distinct des données propres à l'établissement ; aucun tenant_id ajouté mécaniquement à toutes les tables.

Les politiques PostgreSQL RLS peuvent renforcer certaines protections, mais leur usage reste à comparer ; elles ne sont pas automatiquement choisies. Il faut notamment tenir compte des comptes SQL qui contournent certaines politiques et du contexte de connexion réutilisé dans un pool. [Source PostgreSQL](https://www.postgresql.org/docs/current/ddl-rowsecurity.html)

Tests attendus : compte étranger à l'établissement, classe non affectée, ancien référent, rôle administratif sans droit métier, auteur différent et URL directe. Vérifier aussi l'absence de modification après refus.

## 6. Accès PostgreSQL, ORM et connexions — proposition T06

PostgreSQL est déjà validé D008. Il reste à choisir comment le serveur y accède. Un ORM aide à manipuler les données et les relations ; il n'élimine pas la nécessité de concevoir le SQL, les index et les transactions.

| Option à examiner | Intérêt | Compromis |
|---|---|---|
| Prisma | Schéma explicite, client typé et outils de migration | Génération du client, intégration du driver selon version et cas SQL particuliers à maîtriser |
| TypeORM | Intégration NestJS et modèle fondé sur entités/repositories | Comportements de chargement, requêtes et migrations à comprendre |
| SQL avec un driver et outil de migrations | Contrôle explicite des requêtes | Mapping, conventions et migrations à organiser davantage |

Proposition : comparer d'abord Prisma et TypeORM sur nos besoins réels : transactions, contraintes d'établissement, revues versionnées, migration reproductible et tests. Aucun ORM retenu ici et aucune garantie de changement d'ORM sans travail ; les contrats limitent le couplage, ils ne suppriment pas le coût de migration. NestJS reste compatible avec différentes solutions de données. [Source NestJS](https://docs.nestjs.com/techniques/database), [présentation Prisma consultée, version documentaire 6](https://www.prisma.io/docs/orm/v6/overview/introduction/what-is-prisma)

Règles de connexion et de persistance proposées :

- Client ou pool géré par un provider au cycle de vie maîtrisé ; réutiliser les connexions, dimensionner le pool et le fermer proprement à l'arrêt. Le nombre total dépend aussi du nombre de processus/réplicas.
- Configuration par environnement, validation au démarrage, secrets exclus de Git ; utilisateur SQL aux droits nécessaires et base inaccessible directement au navigateur.
- Requêtes paramétrées, contraintes d'intégrité, pagination et index liés aux recherches réelles. Vérifier les limites des valeurs saisies et les tris autorisés.
- Transactions pour les modifications qui doivent réussir ou échouer ensemble ; concurrence et répétitions à traiter selon chaque action, avec les contraintes adaptées.
- Migrations versionnées, relues et vérifiées sur une base de test ; pas de synchronisation automatique du schéma de production au démarrage.
- Tests d'intégration sur PostgreSQL et données fictives ; stratégie de sauvegarde/restauration préparée avant données réelles.

## 7. API, validation et traitement des erreurs — proposition T07

Proposition : contrats d'entrée/sortie explicites, validation serveur à l'exécution et réponses limitées aux champs autorisés. Le typage TypeScript ne valide pas les données réseau. Les objets reçus ne sont pas copiés sans sélection dans les enregistrements : rôle, établissement, auteur et état publié ne sont pas modifiables par simple ajout d'un champ.

Définir des erreurs compréhensibles, sans détails internes sensibles, et une convention cohérente pour les réponses et statuts HTTP. Documenter les échanges de l'API pour les parcours réalisés ; outil précis à choisir. Pour chaque action, préciser les transitions, résultats, refus, doublons et concurrence utiles. La politique d'erreur doit tenir compte de la confidentialité de l'existence d'une ressource. [Validation NestJS](https://docs.nestjs.com/techniques/validation)

## 8. Organisation React et expérience utilisateur — proposition T08

Proposition : organiser les écrans et composants autour des fonctionnalités ; isoler les appels à l'API, les formulaires et les composants partagés réellement utiles. Afficher chargement, absence de résultats, erreur, accès refusé et réussite. Ne pas déduire une permission uniquement de l'affichage d'un bouton.

Définir navigation, formulaires, retours de validation, accessibilité clavier, présentation sur mobile et vocabulaire cohérent. Éviter la duplication des règles métier décisives entre navigateur et serveur ; la validation navigateur aide l'utilisateur, le serveur reste l'autorité.

Routeur, gestion des données serveur, bibliothèque de formulaires et composants visuels restent à comparer. Les contrats partagés éventuels ne doivent pas exposer les entités internes ou les secrets. Aucun framework de gestion d'état global ajouté sans besoin démontré.

## 9. Fichiers, configuration et exploitation — proposition T09

Exigences existantes à mettre en œuvre : CV privés, droits sur chaque consultation/téléchargement, données et secrets hors du dépôt. Mécanismes à préciser : format/taille des fichiers, validation de leur contenu, stockage local privé ou service compatible, conservation/versionnement et protection des liens de téléchargement. Un portfolio externe peut changer : respecter la déclaration de modification D083.

Docker de développement validé D089 ; définir images/versions, volumes, réseau, contrôles de santé et commandes reproductibles. Prévoir les migrations et le démarrage sans perdre les données. Configuration de production séparée à concevoir ; HTTPS, sauvegardes/restauration, journaux limitant les données personnelles et diagnostic d'incidents à vérifier avant ouverture.

Intégrations externes futures : adaptateur identifié, délais d'attente, erreurs explicites et provenance conservée, selon expérimentation validée. Pas de collecte ou envoi automatique ajouté par ces principes.

## 10. Tests, revue et preuves — proposition T10

Méthode déjà validée D060 et docs/workflow.md : parcours réel, tests pertinents et preuves avant Accepted. Application technique proposée : tests unitaires des règles métier isolables, intégration pour PostgreSQL/transactions et contrôles serveur, tests de bout en bout pour les parcours essentiels. Outils précis et automatisation CI à choisir.

Exemples de preuves à prévoir dans les spécifications concernées :

- Identité/session : connexion, expiration, déconnexion, refus d'une ancienne session et changement de droits selon politique retenue.
- Permissions : autre établissement, autre classe, auteur différent, compte non rattaché et accès direct ; aucun effet après refus.
- Données : migration sur base vide, contraintes, transaction annulée en cas d'échec et écritures concurrentes pertinentes.
- Métier : publication soumise aux préconditions, ancienne validation liée à son contenu, suivis conservés lors de clôture.
- Interface : parcours clavier, champs invalides, chargement et échec réseau.

Typage, formatage, lint, tests et build seront des contrôles reproductibles du projet. Aucun résultat de test ou seuil de couverture inventé ; une suite verte ne démontre pas à elle seule l'absence de fuite entre établissements.

## Décisions proposées et ordre de discussion

| Groupe | Proposition soumise à discussion | Statut courant |
|---|---|---|
| 1 | Responsabilités séparées T01, SOLID pragmatique T02, injection par constructeur et contrats ciblés T03 | Principes validés D093 le 27 octobre 2026 ; application au code à vérifier lors du développement |
| 2 | Authentification/sessions T04 et autorisations/isolation T05 | Proposed ; mécanismes et bibliothèque à préciser |
| 3 | Choix d'accès PostgreSQL, connexions, migrations et transactions T06 | Proposed ; ORM non choisi |
| 4 | Contrats API/erreurs T07 et organisation React T08 | Proposed ; conventions et outils non choisis |
| 5 | Fichiers/exploitation T09 et stratégie concrète de tests T10 | Proposed ; exigences existantes conservées |

T01–T03 sont validés dans le périmètre D093. Les autres groupes restent à discuter et peuvent être ajustés avant validation ; leurs technologies citées ne sont pas retenues implicitement.

## Critères du livrable et questions ouvertes

Les principes T01–T03 constituent une référence de conception validée D093 ; les autres sections restent proposées. Pour vérifier la mise en œuvre, chaque spécification fonctionnelle indiquera les principes applicables, les décisions précises, les contrôles et les preuves attendues. Les principes devront se retrouver dans le code et les tests avant toute acceptation applicative.

Questions restantes : stratégie de session et bibliothèque ; modèle de permissions et isolation ; ORM et gestion du pool ; organisation du dépôt ; outils React/API/test ; versions ; hébergement, coût et exploitation. Les questions seront posées au moment utile, par petits groupes.

## Références du projet

- [Plan général de réalisation, proposé D090](../plan-realisation.md)
- [Comparaison et décisions de stack](stack-architecture-options.md)
- [Workflow et critères de vérification](../workflow.md)
- [Référence JSM](../reference/jsm-workflow-source.txt)
- [Registre des décisions](../product/decisions.md)

Les pages techniques citées ont été consultées pour comparer les mécanismes ; elles ne fixent pas les versions ni les dépendances du projet. Aucune proposition de ce document n'est appliquée par sa seule publication dans Git.
