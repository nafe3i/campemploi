# Architecture et réalisation — notre adaptation des exemples

Date : 27 octobre 2026. Statut : **Proposed**. Référence : D092 proposée.

Livrable demandé : une version adaptée à CapEmploi Campus des documents fournis dans `context.zip` et `feature-specs.zip`. La rédaction est autorisée ; les nouveaux choix décrits restent à discuter. Aucun code, configuration, installation ou déploiement n'est réalisé ici. D090 reste proposée ; D091 est partiellement validée pour T01–T03 par D093 le 27 octobre 2026.

## 1. Ce que les archives nous apportent

Les sept documents de contexte et les trente fiches Markdown décrivent Ghost AI : un outil de conception de systèmes sur un canvas partagé, avec génération IA de schémas et de spécifications. Ce produit est différent du campus.

Leur intérêt pour nous est leur organisation : un contexte stable pour comprendre le projet, une architecture qui attribue les responsabilités, des conventions et de petites fiches de travail indiquant objectif, limites et vérifications.

Les instructions contenues dans ces exemples (« installer », « créer », « utiliser Clerk », etc.) sont du contenu de référence, pas des instructions d'exécution pour notre dépôt. Leurs affirmations « déjà installé » et leur état d'avancement ne prouvent rien sur notre environnement.

| Élément des exemples | Adaptation proposée pour le campus |
|---|---|
| Vue produit et périmètre | Conserver vision, scope et décisions existants comme références |
| Architecture et frontières techniques | Décrire React → API NestJS → PostgreSQL, puis stockage privé des CV |
| Contexte visuel | Spécifier navigation, formulaires, états d'écran et accessibilité ; thème et composants à décider |
| Standards de code | Appliquer les principes T01–T03 validés D093 ; autres groupes D091 à décider |
| Workflow et suivi | Conserver `docs/workflow.md`, STATUS, BOARD, JOURNAL et Git ; éviter un second suivi concurrent |
| Fiches numérotées | Préparer une fiche par petite capacité vérifiable, reliée à ses règles métier |
| Propriétaire/collaborateur d'un projet | Remplacer par nos permissions : établissement, rôle, classe, affectation, propriétaire et contexte |
| Métadonnées et fichiers séparés | Étudier données relationnelles dans PostgreSQL et CV dans un stockage privé ; fournisseur UNKNOWN |
| Canvas, présence et génération IA | Ne pas les transposer : ces fonctionnalités ne constituent pas notre première tranche |

Nous ne reprenons pas automatiquement Next.js, Clerk, Prisma, Liveblocks, Trigger.dev, Vercel Blob, Gemini, Tailwind ou shadcn/ui. Ils répondent aux besoins de l'exemple et ne sont pas des décisions du campus.

Quelques incohérences montrent pourquoi une adaptation critique est nécessaire : les documents évoquent à la fois fichiers locaux et Vercel Blob ; `isThinking` devient `thinking` ; la fiche 22 prévoit une route de jeton distincte alors que la fiche 26 attend aussi le jeton dans la réponse de lancement. Les fiches 15 et `16-nodes-color-toolbar` répètent la même fonctionnalité. Le modèle d'identifiant de projet/salle doit aussi être clarifié entre les fiches 05 et 07. Nous devons fixer un contrat unique avant de coder un parcours.

## 2. Notre base : acquis, propositions et UNKNOWN

| Statut | Contenu |
|---|---|
| **Validé** | Scope D007 ; React/Vite + TypeScript ; API REST Node.js/NestJS ; PostgreSQL ; serveur en monolithe modulaire D008 |
| **Validé** | Docker et Compose en développement avec interface, API et base conteneurisées, rechargement automatique D088–D089 |
| **Validé** | Trois tranches D086 ; contrôles communs et spécifiques D060 ; accord avant nouvelle décision D064 ; suivi et synchronisation D062/D069/D074 |
| **Validé** | Principes T01–T03 : responsabilités, SOLID pragmatique et injection ciblée D093 ; mise en œuvre future à vérifier |
| **Proposé** | D090 : plan général ; D091 T04–T10 : auth, permissions, données et autres conventions ; D092 : présente adaptation globale |
| **UNKNOWN** | Organisation exacte du dépôt, versions, ORM, mécanisme/bibliothèque d'authentification, modèle détaillé d'isolation, outils UI/tests et hébergement |
| **UNKNOWN avant essais réels** | Responsabilités des données C11 et protocole de mesure C12 |

La suite expose une proposition concrète. Une phrase au futur décrit la cible proposée, pas une réalisation existante ni un accord implicite.

## 3. Comment l'application serait structurée

Un monolithe modulaire est un seul serveur métier, découpé en modules qui portent chacun un domaine. Cela permet de séparer les responsabilités sans exploiter un service indépendant pour chaque fonctionnalité. React constitue l'interface distincte déjà validée.

```text
Navigateur : React/Vite
          │ requêtes HTTPS / API REST
          ▼
Serveur : NestJS, un seul serveur métier
          ├── identité et accès
          ├── organisation : établissements, classes, rattachements
          ├── offres et modération
          ├── documents et revues                  [tranche 2]
          ├── candidatures et entreprises          [tranche 2]
          └── accompagnement, progression, suivi  [tranche 3]
          │
          ├── PostgreSQL : données et relations
          └── stockage privé : CV                 [tranche 2]
```

Les principes de séparation des responsabilités sont validés D093 ; le regroupement exact des modules est proposé. Les modules des tranches suivantes ne seraient créés qu'au moment utile. L'historique nécessaire à une offre ou à une revue reste rattaché au métier concerné ; un module d'audit universel n'est pas exigé.

| Partie | Responsabilité retenue D093 | Exemple |
|---|---|---|
| React | Afficher, recueillir les entrées, montrer chargement/erreurs/résultats | Formulaire de proposition d'offre |
| Identité et accès | Identifier le compte et établir son contexte autorisé | Compte connecté et rattachement actif |
| Controller | Recevoir HTTP, faire valider la forme des entrées, appeler l'action, répondre | Recevoir une demande de publication |
| Service métier | Vérifier les règles propres à l'action et coordonner les changements | Seule la CME autorisée publie une offre qualifiée |
| Accès aux données | Charger/enregistrer dans le périmètre autorisé ; réaliser les requêtes nécessaires | Chercher l'offre dans son établissement |
| PostgreSQL | Conserver les relations et garantir les contraintes retenues | Empêcher une référence incohérente |

Le navigateur ne décide pas des droits : retirer un bouton aide l'utilisateur, mais une requête directe doit être contrôlée par l'API. Les contrôles dépendant de la ressource restent liés à l'action métier, même si des mécanismes communs vérifient déjà la connexion.

### Exemple minimal : pourquoi séparer les responsabilités ?

Une demande « publier cette offre » traverse trois questions différentes :

1. La demande contient-elle un identifiant au format attendu ? C'est une validation d'entrée.
2. La personne peut-elle publier cette offre et les conditions sont-elles remplies ? Ce sont les permissions et règles métier.
3. Comment enregistrer ensemble l'état publié et son historique ? C'est la persistance et, selon le modèle retenu, une transaction.

Tout placer dans un controller paraît court au début, mais mélange ces trois raisons de changer. La séparation retenue D093 permet de tester la règle de publication sans construire une requête HTTP, puis de vérifier séparément l'API et les écritures PostgreSQL réelles.

Injection de dépendances : le service reçoit l'accès aux données dont il a besoin plutôt que de le construire lui-même. Un contrat ciblé peut exprimer ce besoin ; une interface par classe n'est pas obligatoire. D091 T01–T03 détaille ces principes, validés par D093. Les dossiers exacts et le mécanisme concret de liaison des contrats restent à préciser.

## 4. Organisation des fichiers proposée

```text
docs/
  product/                    références produit et décisions existantes
  scope/                      règles métier existantes
  specs/
    architecture-realisation-campus.md
    socle-technique.md        à rédiger après les choix nécessaires
    features/                 fiches à créer progressivement après accord
  reviews/                    constats de revue et preuves
tracking/                     suivi existant, sans duplication dans context/
apps/                         proposition ; non créé
  web/src/
    features/                 écrans et logique UI par fonctionnalité
    shared/                   composants et utilitaires réellement communs
  api/src/
    modules/                  domaines et leurs controllers/services/données
    common/                   mécanismes communs justifiés
```

Un dépôt commun avec interface et API dans `apps/` faciliterait leur évolution coordonnée ; il demanderait des commandes et conventions communes. Des dossiers racine `frontend/` et `backend/` seraient également possibles. La proposition `apps/` n'implique ni outil de monorepo ni paquet partagé. Aucun dossier applicatif n'est créé par ce document.

Nous conservons les documents existants comme sources de vérité plutôt que de copier les sept fichiers de `context.zip`. Le socle futur devrait référencer ces sources et décrire les conventions effectivement retenues.

## 5. Les données et la confidentialité

Avant le schéma SQL, dessiner les relations métier suivantes, puis vérifier chaque accès. Ce sont des concepts à modéliser, pas une liste de tables déjà décidée.

| Ensemble | Relations à préciser | Invariant déjà exigé |
|---|---|---|
| Comptes et organisation | Compte, rattachement, établissement, classe, rôle, affectation du référent, invitation | Une connexion ou un lien de classe ne remplace pas la validation du rattachement |
| Offres | Offre, auteur, établissement, état de modération, disponibilité, versions, motifs et signalements | Non publiée : auteur concerné/CME autorisée ; publiée : membres autorisés du même établissement |
| CV/portfolio et revues | Document, contenu/version examiné, avis CME et formateur, auteur d'avis, retours | Deux avis distincts ; modification de contenu entraîne nouvelle revue ; règles D057–D058/D078–D084 |
| Candidatures/entreprises | Apprenant, offre ou prospection, suivi ; entreprise et proposition d'ajout | Droits personnels et CME selon scope ; suivis conservés lors de clôture/doublon d'offre |
| Accompagnement | Demande, accompagnant, rendez-vous, observations et actions | Bilan réservé aux acteurs D025 ; affectation à une classe ne donne pas accès à tous les bilans |

Hypothèse D091 à comparer : base partagée et liens explicites vers l'établissement, avec contraintes et contrôles serveur. Des bases/schémas séparés renforceraient certaines frontières mais compliqueraient migrations et exploitation. Le mécanisme reste UNKNOWN ; aucun `tenant_id` ajouté mécaniquement partout.

Pour les CV, prévoir métadonnées et références en base, fichiers privés hors du dépôt et contrôle avant chaque téléchargement. Une URL difficile à deviner ne constitue pas une permission. L'outil de stockage, les limites de fichier et les durées de conservation restent à décider. Les liens de portfolio restent externes et suivent la déclaration D083 ; leur stabilité n'est pas garantie.

## 6. Notre catalogue de petites étapes

Les trois tranches sont validées D086 ; l'ordre fin et les identifiants ci-dessous sont **proposés**. Ces lignes sont un catalogue de futures fiches, pas des spécifications complètes ni une autorisation de démarrage. Une fiche dépend des décisions nécessaires à son propre parcours.

| Fiche proposée | Résultat attendu | Dépendances / preuves à préparer |
|---|---|---|
| F00 — Socle | Interface/API/base démarrent en développement Docker ; migration et configuration reproductibles | Choix techniques nécessaires validés ; preuve de démarrage et persistance après redémarrage |
| F01 — Première organisation | Premier établissement et CME préparés dans le périmètre administratif autorisé | Mode d'initialisation à décider ; pas d'accès métier implicite pour l'administration |
| F02 — Identité et session | Connexion/déconnexion et refus d'accès sans identité valable | Mécanisme choisi ; expiration/récupération et politiques à spécifier |
| F03 — Classes et personnel | Administration locale des classes, invitations du personnel et affectations nécessaires | D056/D078–D080 ; droits locaux et retrait des accès d'affectation à vérifier |
| F04 — Invitation apprenant | Compte individuel, demande et validation du rattachement par CME | D059 ; expiration/désactivation/renouvellement, répétition et absence d'accès avant accord |
| F05 — Proposer une offre | Soumission et consultation personnelle de sa proposition | D061/D070–D071 ; fiche détaillée illustrative ci-dessous |
| F06 — Modérer et consulter | CME qualifie, publie/corrige/rejette ; membres consultent les offres publiées autorisées | D061/D070 ; motifs, inconnues et moyen de candidature exploitable |
| F07 — Cycle des offres | Corrections, retrait demandé, signalements, clôture/réouverture, versions et doublons | D068/D072–D077 ; sous-fiches à découper, concurrence et historique à préciser |
| F08 — Documents personnels | CV PDF et lien portfolio avec accès privé | Tranche 2 ; format/limites, versions et déclaration de changement |
| F09 — Revues | Avis formateur/CME, retours et calcul de validation sur contenu examiné | D057–D058/D078–D084 ; référent remplacé/absent et accès historiques |
| F10 — Préparer/suivre | Candidature, préparation et suivi personnels avec visibilité CME prévue | D036–D037/D085 ; transitions et conservation des liens à spécifier |
| F11 — Entreprises | Liste commune et propositions modérées pour prospection | D046 ; champs et règles d'ajout à préciser ; aucune collecte activée par l'ajout |
| F12 — Accompagnement | Demandes adressées, acceptation/réorientation, simulations humaines | Tranche 3 ; D020–D023 ; cas sans réponse à arbitrer |
| F13 — Rendez-vous/progression | Rendez-vous tracés, observations propres aux auteurs et actions | D024–D027 ; confidentialité et changements d'état à vérifier |
| F14 — Tableau de suivi | Informations utiles selon les droits de chaque rôle | D043–D045 ; calculs et périmètres à spécifier, sans élargir l'accès aux bilans |
| F15 — Préproduction/pilote | Version réellement exécutée sur cible, accès/sauvegarde/restauration vérifiés | Hébergement et ouverture distincts ; C11/C12 avant personnes/données réelles |

F15 se prépare pendant les tranches et peut concerner une première version utilisable avant F14 ; son numéro n'impose pas d'attendre tout le produit. La collecte automatique est une évolution indépendante ultérieure, sans fournisseur ni fiche d'implémentation décidés ici.

Pour chaque capacité, on peut préparer séparément une maquette, une migration ou une route. Ces sous-tâches techniques ne prouvent pas à elles seules que le parcours complet fonctionne : il faut relier écran, API, données et contrôles avant de l'accepter.

## 7. Exemple concret de notre fiche : proposer une offre

**Statut : Proposed, illustration à compléter avant développement.** Sources métier : D061/D070/D071 et `docs/scope/first-slice.md`. Les noms de fichiers et la route sont des propositions.

**Objectif.** Un apprenant ou membre du personnel autorisé propose une opportunité à la CME et retrouve sa propre proposition en attente.

**Inclus.** Formulaire, validation serveur, rattachement à l'auteur et à son établissement, enregistrement en attente et affichage personnel du résultat. **Limites.** Aucune publication directe, modération, collecte automatique ou candidature envoyée.

**Entrées exigées par D070.** Intitulé, entreprise, type d'opportunité et lien source ou texte avec provenance. Formats, longueurs et valeurs permises restent à spécifier. Le moyen de candidature exploitable est exigé avant publication, pas nécessairement pour cette première soumission.

**Contrat HTTP illustratif.** `POST /api/offers`. Le navigateur transmet les champs autorisés du formulaire ; le serveur établit auteur, établissement et état initial depuis le contexte vérifié. Des champs ajoutés par le client ne doivent pas permettre d'usurper un auteur, un établissement ou l'état publié. Réponse limitée aux données accessibles à l'auteur ; contrat exact/statuts d'erreur à préciser.

**Fichiers envisagés après validation de la structure.** Dans `apps/web/src/features/offers/` : formulaire et appel API. Dans `apps/api/src/modules/offers/` : controller, entrée validée, service de soumission et persistance. Migration et tests dans les emplacements définis par le socle. Aucun de ces fichiers n'existe encore.

**Chemin de réalisation.** Définir contrat et droits → vérifier les règles métier → créer persistance/migration → réaliser API et contrôles → relier formulaire → exécuter le parcours → tests pertinents → revue et preuves. L'ordre technique peut être ajusté ; la fiche entière porte la preuve de bout en bout.

| Action / acteur | Préconditions | Résultat ou refus attendu | Preuve à produire |
|---|---|---|---|
| Membre autorisé soumet | Identité et rattachement valables ; informations minimales | Proposition en attente liée au bon auteur/établissement | Parcours réel formulaire → API → PostgreSQL → consultation personnelle |
| Compte sans accès interne soumet | Compte non rattaché ou identité absente | Refus sans nouvelle proposition | Test API et contrôle de l'absence d'écriture |
| Auteur consulte sa proposition | Auteur reconnu dans son périmètre | État et motifs autorisés visibles | Test de lecture directe |
| Autre membre consulte avant publication | Aucun droit CME sur cette proposition | Refus sans contenu exposé | Test par identifiant connu, même établissement puis autre établissement |
| Client falsifie rôle/auteur/établissement/état | Requête modifiée manuellement | Aucun droit ou changement d'état obtenu | Test API, résultat et base contrôlés |
| Entrée requise absente/invalide | Formulaire incomplet | Erreur compréhensible, aucune écriture partielle | Tests de validation et de persistance |
| Échec réseau, double clic ou requêtes répétées | Résultat du premier envoi éventuellement inconnu | Comportement explicite à définir avant code ; pas de promesse « exactement une fois » | Tests selon stratégie validée, sans confondre répétition réseau et doublon métier D072 |

**Questions ouvertes bloquant les parties concernées.** Modèle d'identité/rattachement, formats/limites, comportement en cas de changement de rattachement, stratégie de répétition et confidentialité des erreurs. Ne pas les inventer dans les tests.

**Acceptation.** Tous les critères du périmètre sont réellement vérifiés, tests pertinents réussis et revue traitée ; résultats/limites inscrits dans le suivi. Un build réussi seul ne valide ni les permissions ni l'isolation.

## 8. Comment nous vérifierions chaque étape

| Niveau | Ce qu'il prouve | Exemple campus |
|---|---|---|
| Vérification statique et build | Le code respecte les vérifications configurées et peut être construit | Types d'entrée/sortie cohérents |
| Test unitaire métier | Une règle isolée produit le résultat attendu | Publication refusée sans précondition métier |
| Intégration API/PostgreSQL | Les vrais contrôles, requêtes, contraintes et transactions fonctionnent ensemble | Échec d'écriture sans état partiellement modifié |
| Parcours de bout en bout | L'utilisateur accomplit réellement l'action | Soumission puis lecture de sa proposition |
| Vérifications d'accès | Les refus protègent réellement les données | Autre établissement, autre propriétaire, ancien référent, URL/fichier direct |
| Exploitation sur cible | La version peut fonctionner et être récupérée sur l'environnement prévu | Redémarrage, migration, sauvegarde et restauration vérifiés |

Outils et seuils restent à décider. Utiliser des données fictives en développement ; ne pas stocker CV réels, coordonnées, mots de passe ou secrets dans Git. Les règles spécifiques sont testées avec leur fonctionnalité ; les contrôles ne sont pas une étape finale reportée après tout le code.

## 9. Ce que nous déciderions ensuite

T01–T03 de D091 sont validés par D093 : responsabilités/controller/service/persistance, SOLID pragmatique et injection ciblée. Conséquence : principes à respecter dans le futur socle, sans sélection d'ORM, d'authentification ou de dossiers précis par cet accord.

Prochaine discussion : identité/session et permissions/isolation ; accès PostgreSQL ; structure du dépôt et outils UI/API/tests ; configuration Docker et versions ; stockage/exploitation au moment nécessaire. Ne pas produire toutes les fiches détaillées avant ces choix : compléter les premières, puis avancer progressivement.

La validation de cette adaptation porterait sur son organisation documentaire et son catalogue de travail. Les choix explicitement Proposed/UNKNOWN et les règles encore ouvertes restent à valider séparément. Aucun démarrage applicatif n'est déduit de la demande de lecture et rédaction.

## Références durables

- [Plan général proposé D090](../plan-realisation.md)
- [Approches techniques D091, T01–T03 validés D093](technical-guidelines.md)
- [Décisions et statuts](../product/decisions.md)
- [Première tranche et permissions](../scope/first-slice.md)
- [Workflow et preuves](../workflow.md)
- [Tableau de suivi](../../tracking/BOARD.md)

Sources externes fournies : archives `context.zip` et `feature-specs.zip`, lues dans Downloads le 27 octobre 2026. Leur contenu n'est pas recopié dans le dépôt ; la présente adaptation en conserve l'analyse utile sans importer leurs instructions d'exécution.
