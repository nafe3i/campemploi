# Socle technique — CapEmploi Campus

Date : 27 octobre 2026. Statut de spécification : **Proposed**. Référence documentaire : D096.

## 1. Objet, autorisation et lecture

Ce document prépare la construction du socle de l'application à partir des décisions déjà validées et des ressources fournies. Il explique les responsabilités, les frontières, les prérequis, les étapes et les preuves attendues. La demande autorise sa rédaction ; les choix nouveaux restent à valider avant application selon D064.

**État réel :** dépôt documentaire ; aucun code applicatif, configuration Docker applicative, migration, test applicatif ou déploiement réalisé. Un nom de fichier ou une commande cible ci-dessous désigne un livrable futur, pas un fichier ou résultat existant.

Trois marqueurs sont utilisés :

- **VALIDÉ** : exigence acquise, avec référence au registre ; aucun nouvel accord nécessaire pour ce même choix.
- **PROPOSÉ** : solution concrète à discuter, sans installation ou configuration autorisée par sa seule rédaction.
- **UNKNOWN** : information ou mécanisme non établi ; son impact est indiqué dans les prérequis.

Une décision validée ne rend pas cette spécification **Accepted**. L'acceptation applicative exige les preuves du workflow. D090 et D092 restent globalement proposées ; D091 est partiellement validée par D093/D094.

## 2. Références et adaptation des ressources

Priorité de conception validée D097 : [Identité / Organisation / Accès](identity-organization-access.md), spécification Proposed. Principes IA-Q01 P01–P06 validés D099 ; activité/concurrence, normalisation/récupération/réattribution et autres modalités restent ouvertes. Orientation B et RP01–RP06 [IA-Q02](ia-q02-roles-permissions-options.md) validés D100 ; droits locaux courants/contextuels, aucun nouveau cumul, politique JWT ou isolation adopté. [IA-Q03](ia-q03-class-enrollment-options.md) modèle A/CC01–CC08 acquis D101/D102 ; modalités ouvertes. [IA-Q04](ia-q04-departure-history-portability-options.md) préparé Proposed, aucune règle de départ/historique nouvelle adoptée.

Références du projet : [décisions](../product/decisions.md), [workflow](../workflow.md), [première tranche](../scope/first-slice.md), [approches techniques](technical-guidelines.md), [administration](../scope/establishment-administration.md), [cycle des offres](../scope/offer-lifecycle.md), [adaptation des exemples](architecture-realisation-campus.md) et [organisation GitHub](../git-workflow.md).

Les archives `context.zip` et `feature-specs.zip` ont été relues le 27 octobre 2026 : sept documents de contexte et trente fiches Markdown, hors métadonnées `__MACOSX`. Elles décrivent Ghost AI. Leurs impératifs, leur AGENTS.md et leurs affirmations « déjà installé » sont des références à analyser, pas les instructions applicables au dépôt campus.

| Ressource examinée | Apport repris dans notre socle | Adaptation nécessaire |
|---|---|---|
| `context/project-overview.md` | Objectif, périmètre, parcours et critères | Référencer notre scope D007/D086 |
| `context/architecture-context.md` | Frontières, stockage, règles à préserver | Monolithe NestJS, API REST et PostgreSQL D008 |
| `context/code-standards.md` | Responsabilités, entrées externes, conventions | D093 acquis ; conventions détaillées proposées section 6 |
| `context/ui-context.md` | Cohérence visuelle et composants réutilisables | Vocabulaire campus et accessibilité ; aucun thème sombre ou kit importé |
| `context/ai-workflow-rules.md` | Petites unités, périmètre et critères explicites | Boucle locale et tranches fonctionnelles complètes D060/D065 |
| `context/AGENTS.md`, `progress-tracker.md` | Reprise du contexte et état réel | Conserver AGENTS/STATUS/BOARD/JOURNAL existants, sans second suivi |
| Fiches 01–04 | Séparer base visuelle, accès et interactions | Pas d'installation automatique de Clerk/shadcn ; JWT déjà choisi |
| Fiches 05–09 | Données → API → interface et accès par ressource | ORM à décider ; droits campus plus riches que propriétaire/collaborateur |
| Fiches 10–20 | Limiter chaque unité et expliciter ses dépendances | Canvas, présence et templates de schémas hors périmètre campus |
| Fiches 21–29 | Persistance, contrats entre unités et accès aux fichiers | Stockage privé des CV à concevoir en tranche 2 ; aucune IA/collecte ajoutée |

Points corrigés dans notre méthode : une fiche backend et sa fiche frontend doivent partager le même contrat ; un build seul ne prouve pas les permissions. Les exemples divergent sur fichiers locaux/Blob, `isThinking`/`thinking`, et la réponse de lancement IA/route séparée de jeton. Les fiches 15 et `16-nodes-color-toolbar` se répètent. Nous maintiendrons une seule définition pour chaque contrat et un état de preuve réel.

## 3. Décisions et périmètre du socle

| Sujet | Statut et référence | Conséquence pour la construction |
|---|---|---|
| Produit et ordre | VALIDÉ D007/D086 | Tranche 1 : accès/organisation et offres humaines ; tranche 2 : documents/revues, candidatures/entreprises ; tranche 3 : accompagnement/pilotage |
| Interface | VALIDÉ D008 | React/Vite et TypeScript, distincts de l'API |
| Serveur | VALIDÉ D008 | Node.js/NestJS, API REST, un monolithe modulaire |
| Base | VALIDÉ D008 | PostgreSQL ; choix de driver/ORM et schéma détaillé ouverts |
| Développement Docker | VALIDÉ D088/D089 | Compose pour web, API et PostgreSQL, avec rechargement automatique |
| Responsabilités et SOLID | VALIDÉ D093 | Domaines progressifs, controllers courts, services métier et accès aux données séparés ; abstractions utiles seulement |
| Injection | VALIDÉ D093 | Dépendances fournies par constructeur ; contrats ciblés aux frontières utiles |
| Authentification | VALIDÉ D094 | JWT ; bibliothèque, cycle de vie, transport et stockage ouverts |
| Méthode et preuves | VALIDÉ D060/D062/D064/D065 | Contrôles communs/spécifiques, accords, petits parcours et preuves avant Accepted |
| Conservation et GitHub | VALIDÉ D069/D074/D095 | Commits/push vérifiés ; branches codex/… et PR pour développement ; BOARD référence, Project vue manuelle |

Le socle prépare l'exécution et les accès nécessaires au pilote. Il ne développe pas toutes les offres ni les tranches futures. La collecte automatique, le chat, l'envoi automatique de candidatures et les intégrations IA gardent leur périmètre futur. L'hébergement et l'ouverture à des utilisateurs réels ne sont pas autorisés par la rédaction du socle.

## 4. Vue d'ensemble et frontières

```text
Navigateur — interface React/Vite
    │ HTTP en développement local ; HTTPS sur environnement exposé
    │ API REST, contrats d'entrée/sortie limités
    ▼
API NestJS — un serveur métier modulaire
    ├── identité et authentification JWT
    ├── organisation et rattachements
    ├── offres et modération, ajoutées avec leur parcours
    └── accès PostgreSQL via dépendances identifiées
              │
              ▼
          PostgreSQL

Tranches suivantes : modules et stockage privé des CV au moment utile.
```

Le principe est VALIDÉ D008/D093 ; les noms et regroupements précis des modules sont PROPOSÉS. Le navigateur ne se connecte jamais directement à PostgreSQL. L'API porte l'autorité métier ; les éléments de configuration envoyés au navigateur doivent être publics. Les secrets de signature et de base restent côté serveur.

**Frontières PROPOSÉES :**

| Domaine | Possède et traite | Ce qu'il fournit aux autres domaines |
|---|---|---|
| Identité/authentification | Identité du compte, vérification de connexion, émission/validation JWT selon politique décidée | Identité vérifiée ; pas une permission universelle |
| Organisation | Établissements, classes, invitations, rattachements, rôles locaux et affectations | Contexte courant et opérations administratives autorisées |
| Offres | Propositions, qualification, modération, disponibilité, versions et signalements | Consultation/actions autorisées et références stables |
| Infrastructure PostgreSQL | Connexions, implémentations de persistance et migrations | Accès techniques utilisés par les services ; pas de règles métier cachées |

Proposition de dépendances : offres utilise les capacités d'identité/organisation nécessaires, sans modifier directement leurs données. Chaque domaine expose une petite API interne explicite ; éviter les dépendances circulaires et un dossier commun contenant tout le métier. Une modification impliquant plusieurs domaines demande de préciser coordination et transaction. Les exports/imports/providers des modules NestJS servent cette séparation ; ils ne nécessitent pas un service réseau par domaine. [Modules NestJS](https://docs.nestjs.com/modules)

## 5. Responsabilités et exemple de parcours — D093

| Élément | Responsabilité retenue | Exemple : soumettre une offre |
|---|---|---|
| Composant React | Affichage et interaction | Recueillir intitulé, entreprise et provenance |
| Appel API côté web | Transport et traitement des résultats | Envoyer les champs autorisés, afficher succès/erreur |
| Controller et validation d'entrée | Frontière HTTP | Vérifier la forme et appeler le service |
| Vérification d'identité | Authentification selon D094 | Valider le jeton et établir l'identité |
| Service métier | Permissions contextuelles, préconditions et coordination | Vérifier rattachement, déterminer auteur/établissement, état en attente |
| Contrat/implémentation de persistance | Requêtes et écritures nécessaires | Enregistrer les données autorisées et l'historique requis |
| PostgreSQL | Intégrité des données | Garantir les relations et contraintes définies |

Exemple minimal conceptuel : « soumettre une offre » reçoit une identité vérifiée et une entrée validée ; le service obtient son contexte autorisé, applique D070/D071 puis demande l'enregistrement. L'établissement, l'auteur et l'état publié ne sont pas attribués par confiance dans des champs transmis par le navigateur. Le résultat ne donne accès qu'aux informations autorisées.

Le format d'une URL est une question de validation ; le droit de publier et les conditions de publication sont des règles métier. Le controller ne contient pas les requêtes de données et le composant React n'attribue pas les permissions. Les contrôles de connexion communs ne remplacent pas la vérification de la ressource.

SOLID reste pragmatique : une responsabilité claire, contrats limités aux besoins et implémentations respectant leurs garanties. Pas de repository générique universel, interface par classe ou héritage systématique. Une fonction simple peut rester une fonction.

**Mécanisme DI PROPOSÉ :** interfaces ciblées et tokens partagés de type Symbol aux frontières retenues. Une classe abstraite reste une alternative ; le choix est ouvert. Les interfaces TypeScript n'existent pas à l'exécution ; le conteneur a besoin d'une référence concrète pour fournir l'implémentation. L'injection d'un service interne concret reste possible. [Providers NestJS](https://docs.nestjs.com/fundamentals/custom-providers)

## 6. Structure du dépôt et conventions — PROPOSÉ

La structure suivante illustre l'application de D093 ; elle n'est pas encore créée ni validée comme arborescence exacte.

```text
apps/
  web/
    src/
      features/              écrans, formulaires et appels API par capacité
      shared/                composants et outils réellement communs
  api/
    src/
      modules/
        identity/            à créer avec son parcours
        organization/        à créer avec son parcours
        offers/              à créer au début du parcours offres
      infrastructure/        configuration et accès techniques
    test/                    tests d'intégration/parcours selon outil retenu
docs/
  specs/socle-technique.md   présent document
  specs/features/           futures fiches, pas toutes générées dès le départ
  reviews/                  constats et preuves
tracking/                   suivi existant
compose.yaml                configuration future de développement
```

Alternative : `frontend/` et `backend/` à la racine, plus directs à nommer mais sans avantage fonctionnel décisif. Recommandation : retenir `apps/web` et `apps/api` dans le dépôt existant ; cela coordonne les évolutions sans ajouter nécessairement un outil de monorepo. Gestionnaire de paquets, workspaces, scripts et fichiers de verrouillage restent à choisir. Aucun paquet partagé n'est requis par principe.

Conventions PROPOSÉES : TypeScript strict ; éviter `any` et valider les données externes à l'exécution ; noms métier explicites ; fichiers proches de leur fonctionnalité ; objets d'entrée/sortie distincts des enregistrements internes. Partager seulement ce qui a une utilité démontrée. Formatage, lint, organisation des tests et outils précis seront fixés avec le setup, puis documentés après audit. Ces recommandations ne rendent pas T07/T08/T10 validés.

## 7. Authentification JWT — D094 et modalités ouvertes

**VALIDÉ :** JWT pour authentifier les requêtes de l'API. JWT ne définit ni l'inscription, ni la récupération du compte, ni la durée de connexion, ni les autorisations. Connexion réussie et rattachement validé sont deux conditions différentes.

Parcours à spécifier : vérifier les identifiants → émettre le jeton → le présenter à l'API → vérifier le jeton → contrôler compte/rattachement et action. Une simple lecture du contenu ne valide pas un jeton. Une signature n'en chiffre pas les informations. La validation doit fixer les algorithmes acceptés, clés, émetteur/destinataire et conditions temporelles attendus ; ces paramètres restent à décider. Aucune donnée confidentielle ou clé dans le contenu ou les journaux. [Bonnes pratiques JWT, RFC 8725](https://www.rfc-editor.org/rfc/rfc8725.txt)

| Point à décider | Pourquoi il est nécessaire | Statut |
|---|---|---|
| Connexion, activation, récupération et première identité administrative | Garantir un parcours utilisable et maîtrisé | UNKNOWN |
| Bibliothèque/version, signature et gestion des clés | Éviter une implémentation cryptographique artisanale | UNKNOWN |
| Claims et contrôle de l'identité courante | Déterminer ce que le serveur vérifie et quand | UNKNOWN |
| Transport et stockage navigateur | Définir les compromis entre mémoire, cookies, persistance, XSS/CSRF et rechargement | UNKNOWN ; aucun localStorage/cookie choisi |
| Expiration et renouvellement éventuel | Fixer durée de connexion et comportement à l'expiration | UNKNOWN ; aucune durée ou refresh token retenu |
| Déconnexion, révocation, multi-appareils | Définir l'effet sur les jetons existants, y compris leurs copies | UNKNOWN |
| Changement de compte/rattachement/affectation | Appliquer les retraits de droits métier malgré un jeton encore valable | Politique technique UNKNOWN, exigences métier conservées |

Écrire ensuite une fiche d'accès complète avec résultats et refus attendus, avant développement. La spécification devra distinguer déconnexion locale et invalidation serveur, et définir les cas de répétition/concurrence si un renouvellement est choisi. Aucun service externe ou envoi de mail n'est ajouté par défaut.

## 8. Autorisations, organisation et séparation des établissements

Les exigences ci-dessous sont VALIDÉES ; le mécanisme technique T05 reste PROPOSÉ.

| Cas | Règle métier à préserver | Référence |
|---|---|---|
| Apprenant connecté mais rattachement non approuvé | Pas d'accès interne ; un lien de classe ne vaut pas approbation | D038/D059 |
| Administration générale/locale | Périmètres distincts ; rôle administratif sans accès confidentiel automatique | D056/D076 |
| Offre non publiée | Auteur concerné et CME autorisée ; la classe ne donne pas à un formateur l'accès aux propositions d'autrui | D061/D071 |
| Offre publiée | Consultation selon rattachement et établissement autorisés ; publication par CME dans son périmètre | D029/D061/D071 |
| Référent remplacé | Fin des accès de l'ancienne affectation ; autres permissions indépendantes selon leur contexte | D078–D082 |
| CV/portfolio et avis, en tranche 2 | Apprenant concerné, CME locale et référent autorisé ; avis distincts liés au contenu examiné | D057/D058/D081–D084 |
| Bilans d'accompagnement, en tranche 3 | Apprenant concerné, accompagnant du rendez-vous et CME locale ; pas d'ouverture par simple appartenance à une classe | D025/D080 |

Principe contextuel acquis D100, mécanismes ouverts : composer identité, état du compte, rattachement courant/approuvé/autorisé, attributions locales explicites, permissions administratives distinctes, établissement, propriétaire, classe/affectation, état et action. Catalogue limité/extensible sans éditeur libre ni moteur adopté ; aucune action sensible autorisée par simple union de permissions, aucun nouveau cumul. Retrait des nouveaux accès malgré JWT valide ; point d’effet et concurrence IA-Q08 ouverts. Les listes, accès par identifiant, exports et fichiers doivent employer les mêmes limites. Un identifiant d'établissement reçu ne crée aucun droit. Vérifier le refus sans lecture/écriture non autorisée.

Classes D101 : demande sans droit cible, changement/réentrée approuvés, relais des droits après effet, pas de double inscription effective ; effet/concurrence ouverts. D102, règle métier distincte de D081 : changement local seul sans remise à revalider du contenu inchangé ; auteur réel/type/version préservés, aucun avis positif créé, ancien avis sans maintien d’accès, D057/D083 conservées. Aucun transfert inter-établissements ni révision libre/rétention illimitée.

Isolation UNKNOWN : base/tables partagées avec périmètre explicite, schémas séparés ou bases séparées. L'hypothèse de base partagée D091 reste proposée ; elle demanderait contraintes, requêtes bornées et tests avec deux établissements fictifs. RLS éventuelle à comparer, pas requise par défaut. Aucun `tenant_id` ajouté mécaniquement à toutes les tables et aucun droit « staff » global inventé.

## 9. Modèle conceptuel et persistance

Les principes IA-Q01 D099 sont acquis : identité globale stable, rattachements distincts, au plus un actif au pilote et email vérifié/unique indépendant de l'identifiant. IA-Q02 B/RP01–RP06 acquis D100 : rôles et permissions séparés des relations, attributions locales explicites ; auto-attribution/délégations IA-Q05/07 ouvertes. D101 fixe au plus une inscription de classe courante au pilote dans le rattachement autorisé, historique/demandes distincts et garantie concurrente requise ; D102 valide CC06/V1 pour contenu inchangé au seul changement local. Le modèle détaillé reste proposé : aucune table, valeur d'enum ou suppression en cascade fixée ; demande en attente/activité/historique distincts, garantie concurrente à définir.

```text
Compte ── rattachement et rôles locaux ── Établissement
Classe ── appartient à ── Établissement
Apprenant ── rattachement de classe ── Classe
Formateur ── affectation de référent ── Classe
Invitation ── cible une classe ou un parcours de personnel selon sa règle
Offre ── auteur, établissement, modération, disponibilité et versions
```

Points à figer avant migration : unicité utile, statuts du compte/rattachement, possibilité et limites des rattachements multiples, changements d'établissement/classe, historique d'affectation, relations inter-établissements interdites et conservation. Ne pas inventer une règle de cardinalité pour simplifier le schéma.

PostgreSQL est VALIDÉ. Prisma, TypeORM ou SQL explicite restent à comparer sur migrations, transactions, intégrité des périmètres et facilité de test ; aucun ORM sélectionné par la fiche 05 des exemples.

Persistance PROPOSÉE : un provider gère le client/pool et son arrêt ; requêtes paramétrées, contraintes utiles et migrations versionnées ; configuration validée au démarrage ; base de test distincte ; données fictives et nettoyage borné à cet environnement. Préciser les index à partir des requêtes réelles, puis pagination et tris des listes concernées.

Une transaction regroupe les écritures devant réussir ou échouer ensemble. Exemple à spécifier : changement d'état d'offre et trace associée ; concurrence à traiter pour éviter un écrasement silencieux. Le mécanisme précis dépend de l'accès retenu. [Transactions PostgreSQL](https://www.postgresql.org/docs/current/tutorial-transactions.html)

## 10. API, interface et contrats — PROPOSÉ

API REST acquise D008 ; contrats détaillés T07 ouverts. Chaque future fiche devra définir méthode/chemin, entrée, réponse autorisée, erreurs, acteurs et effets. Noms de routes, préfixe, versionnement et outil de documentation à décider ; aucun endpoint métier n'est créé ici.

Proposition : entrée validée à l'exécution ; sélection explicite des champs modifiables ; réponse sans détails internes ni données superflues ; erreurs compréhensibles et cohérentes. La politique de refus doit tenir compte de la confidentialité de l'existence d'une ressource. Une validation TypeScript seule n'est pas une validation réseau.

Interface T08 proposée : organisation par fonctionnalités, navigation selon parcours, chargement, liste vide, erreur, accès refusé et réussite. Prévoir clavier, mobile, libellés compréhensibles et erreurs près des champs. Couleurs, typographie, bibliothèque UI, routeur, formulaires et gestion des données serveur restent ouverts. Les règles Next.js Server Components, Clerk et le thème Ghost AI ne sont pas applicables par copie.

Un premier écran technique pourra interroger une route de diagnostic minimale : chemin, contenu public/protégé et effet de l'indisponibilité de la base à décider en fiche S02. Pas de faux écran « connecté » ou de données simulées présentées comme une authentification réelle.

## 11. Environnement Docker et configuration

**VALIDÉ D089 :** trois composants conteneurisés en développement, Compose et rechargement automatique. Production distincte ; aucune image/version, aucun port, volume ou outil installé par ce document.

| Composant cible | Responsabilité | Modalités PROPOSÉES, à préciser avant configuration |
|---|---|---|
| Web | Servir React/Vite au navigateur | Rechargement, adresse API accessible depuis le navigateur, configuration publique seulement |
| API | Exécuter NestJS | Configuration serveur, connexion PostgreSQL, redémarrage propre et diagnostic minimal |
| PostgreSQL | Persister les données | Volume persistant ; pas d'exposition réseau plus large que nécessaire ; accès local de diagnostic à décider |

Différencier adresses entre conteneurs et adresses du navigateur ; définir origine web/API, CORS et protections liées au transport JWT retenu. Ne pas utiliser un nom de service Compose comme URL navigateur sans vérifier qu'il est résolu dans ce contexte.

Proposition : vérifier la disponibilité effective de PostgreSQL avant les opérations qui en dépendent, et traiter ses pannes après démarrage. Compose distingue lancement et disponibilité ; un healthcheck peut servir de précondition de démarrage. Son résultat ne remplace ni migrations ni gestion des erreurs applicatives. [Ordre de démarrage Docker Compose](https://docs.docker.com/compose/how-tos/startup-order/)

Livrables futurs proposés : fichier Compose, instructions de configuration, exemples sans secrets, gestion du volume, commandes reproductibles et registre des versions. Leurs chemins précis et les scripts seront figés après arbitrage ; aucun copier-coller de commandes non vérifiées.

| Opération à documenter | Résultat vérifiable attendu |
|---|---|
| Préparer la configuration | Variables requises identifiées ; absence/invalidité signalée sans secret exposé |
| Construire et démarrer | Web/API/base joignables selon exposition décidée |
| Appliquer une migration | Base vide créée puis réexécution maîtrisée, sans perte des données conservées |
| Modifier le code | Rechargement observé côté web et API |
| Arrêter/redémarrer sans suppression de volume | Données fictives conservées |
| Exécuter typage/lint/tests/build | Commandes et résultats effectivement reproductibles |

Aucune suppression de volume présentée comme un arrêt ordinaire. Séparer développement et test avant toute opération de réinitialisation. Un volume Docker n'est pas une sauvegarde ; sauvegarde/restauration à préparer avant données réelles.

## 12. Confidentialité, fichiers et exploitation future

Secrets, CV, coordonnées et candidatures réels hors Git ; exemples et jeux de test fictifs. Limiter les journaux aux informations utiles, sans mots de passe, jetons, clés ou contenu privé. La configuration frontend publiée n'est pas un emplacement pour secrets.

CV PDF/portfolio et revues en tranche 2 D086 : stockage privé, autorisation à chaque lecture/téléchargement, référence au contenu examiné et versions à préciser alors. Une URL de fichier ne vaut pas droit d'accès ; une URL de portfolio inchangée ne prouve pas un contenu inchangé, déclaration D083 conservée. Aucun fournisseur de stockage, taille, durée de conservation ou scanner choisi ici.

Avant utilisateurs/données réels : responsabilités C11 et protocole C12, hébergement/coût, HTTPS, configuration de production, migrations, sauvegarde/restauration, diagnostic et retour à une version précédente. Ces points ne bloquent pas la seule rédaction ou les essais locaux fictifs ; ils conditionnent l'ouverture concernée. Aucun déploiement déduit d'un commit, d'une fusion ou d'un build.

## 13. Découpage de construction et prérequis — PROPOSÉ

Le socle est réalisé en petites unités techniques, puis les fonctions en parcours complets. Un livrable partiel doit afficher sa limite et ne devient pas une fonctionnalité acceptée.

| Unité | Objectif / inclus | Hors de cette unité | Préconditions et preuve de sortie |
|---|---|---|---|
| S01 — Structure et outillage | Initialiser web/API, scripts et configuration d'exemple | Comptes/offres et exposition réelle | Structure, versions, paquets et conventions nécessaires décidés ; audit des fichiers générés et build de chaque composant |
| S02 — Exécution Compose | Web/API/PostgreSQL et diagnostic minimal, rechargement | Authentification prétendue ou parcours métier | Modalités réseau/configuration décidées ; démarrage et indisponibilité base observés, secrets absents des réponses |
| S03 — Persistance initiale | Client/pool, migration et données fictives minimales | Schéma de toutes les tranches | Accès PostgreSQL et modèle des données nécessaires décidés, avec arbitrages IA-Q applicables de la spécification D097 ; migration/base vide, réexécution, persistance au redémarrage et échec contrôlé |
| S04 — Identité/JWT | Parcours de connexion et contrôle d'une requête protégée | Toute permission de classe/offre par défaut | Politique JWT et identité décidées après arbitrages IA-Q applicables D097 ; succès et jetons invalides/expiration/déconnexion vérifiés selon politique |
| S05 — Organisation et accès nécessaires | Première organisation, rôles/rattachements utiles et contrôles de périmètre | Écrans complets multi-établissements | Procédures d'initialisation et droits concernés spécifiés selon matrice/scénarios D097 ; deux établissements fictifs, refus sans effet, parcours des accès requis vérifiés |
| S06 — Revue du socle et passage aux offres | Consolider preuves, limites, conventions réelles et prochaine fiche | Déclaration de production ou produit complet | Critères applicables ci-dessous, corrections et revue ; préparation de la première fiche d'offre |

S04/S05 sont à découper en fiches plus petites si elles ne peuvent pas être vérifiées rapidement. S05 ne doit pas dissimuler la gestion des invitations et rattachements : chaque procédure nécessaire aura sa fiche et ses erreurs avant implémentation. Prévoir des données de test via le mécanisme retenu, sans endpoint public de contournement.

**Socle exécutable** : S01–S03 vérifiés sur leur périmètre, sans prétendre que l'accès métier existe. **Socle d'accès** : S04–S05 vérifiés avant parcours interne exposé. Ce découpage est proposé ; il ne permet pas d'ouvrir un parcours dont les décisions de sécurité manquent. L'hébergement de production et les détails des tranches suivantes se décident au moment nécessaire, sans bloquer artificiellement le premier démarrage local.

## 14. Contrôles, critères et preuves attendues — D060

Toutes les preuves ci-dessous sont **À produire**. Outils de test et conventions T10 restent proposés. Il faut vérifier aussi l'absence de données exposées ou d'effets après refus.

| ID | Action / contexte | Critère attendu | Preuve à produire et périmètre |
|---|---|---|---|
| C-S01 | Installer/construire depuis le dépôt | Versions/configuration documentées, pas de secret requis dans Git | Commandes, versions et résultats de typage/lint/build ; S01 |
| C-S02 | Exécuter les trois composants | Interface appelle réellement l'API, connexion base vérifiée selon contrat | Parcours exécuté et réponse minimale ; S02 |
| C-S03 | Configuration absente ou base indisponible | Échec explicite, sans réponse de succès trompeuse ni détails sensibles | Cas d'erreur exécutés ; S02/S03 |
| C-S04 | Arrêter/redémarrer sans effacer le volume | Donnée fictive conservée | Lecture avant/après ; S03 |
| C-S05 | Migration et écritures liées | Schéma reproductible ; échec sans écriture partielle sur opération retenue | Test PostgreSQL réel et résultat de migration ; S03 |
| C-S06 | Connexion/requête protégée | Identité authentifiée selon politique ; requête invalide refusée | API réelle et tests jeton absent/altéré/expiré/mauvaise signature/usage ; S04 |
| C-S07 | Déconnexion ou changement de droits | Effet des jetons existants conforme aux règles décidées | Scénarios de révocation/renouvellement retenus, pas de résultat inventé ; S04/S05 |
| C-S08 | Compte sans rattachement validé ou invitation invalide | Aucun accès interne ; expiration/désactivation/reprise selon fiche | Tests API, URL directe et absence d'écriture illégitime ; S05 |
| C-S09 | Administrateur local/autre établissement/identifiant connu | Aucun élargissement de rôle ou accès métier implicite | Tests avec deux établissements fictifs, listes et accès directs ; S05 |
| C-S10 | Entrée falsifiant rôle/auteur/établissement/état | Champ non autorisé sans pouvoir de modifier les droits | API et base vérifiées, selon contrat ; S05 puis offres |
| C-S11 | Ancien référent/autre classe/bilan | Respect des droits contextuels lors de la tranche concernée | Tests distincts D080/D082/D025 à produire avec documents/accompagnement ; pas une preuve exigible d'un module non encore développé |
| C-S12 | Offre humaine soumise/publiée | Auteur/CME/autres membres selon D061/D070/D071 ; inconnues explicites | Fiche d'offre et tests de publication/refus ; après le socle d'accès |

Pour chaque exécution, enregistrer version/commit, environnement, commande ou parcours, résultat observé, limites et constats de revue dans `docs/reviews/`, puis reporter les liens dans BOARD/Issue/PR. Les tests unitaires visent les règles isolables ; l'intégration vérifie les vrais contrôles et PostgreSQL ; les parcours de bout en bout prouvent l'usage. Un mock de base ne démontre pas l'intégrité SQL ou l'isolation.

## 15. Fiche de travail commune et GitHub — D095

Format adapté des exemples, à utiliser dans les futures fiches sans recopier leurs exigences :

1. Identifiant, titre, statut et décision(s) de référence.
2. Besoin, acteur, objectif et résultat visible.
3. Inclus, exclus, dépendances et UNKNOWN bloquant le périmètre.
4. Parcours et contrats UI/API/données ; responsabilités et fichiers concernés.
5. Règles acquises ; nouvelles propositions explicitement séparées.
6. Matrice action → acteur autorisé → préconditions → résultat → refus/cas limite → preuve.
7. Petites étapes de réalisation, tests pertinents, critères et résultats réels.
8. Revue, limites, prochaine action et liens Issue/branche/PR/commit réellement existants.

BOARD reste la référence. Project en est une vue synchronisée manuellement. Développement : Issue → branche `codex/…` depuis `main` → commits/push → PR liée → vérifications/revue → fusion. Pas de branche `develop` permanente ; les commits documentaires suivent D069. Aucun numéro de ressource inventé et aucun passage automatique à Terminé sur la seule fusion si les critères restent non prouvés.

La création distante de Project/Issues/milestones est autorisée D095 mais pas réalisée. Le plugin a été constaté installé/activé, ses outils et la connexion du compte n'étaient pas confirmés dans cette conversation au dernier contrôle. Ce constat n'est pas une preuve d'absence de capacité future. La présente rédaction ne réessaie pas une interface interrompue ; elle conserve le travail préparatoire.

## 16. Registre des choix restants et passage au setup

| ID | Choix à valider / préciser | Quand il est nécessaire | État |
|---|---|---|---|
| Q01 | Arborescence et échanges internes des premiers modules | Avant S01 | PROPOSÉ : section 4/6 |
| Q02 | Versions compatibles, gestionnaire de paquets, verrouillage, scripts et outils de base | Avant S01 | UNKNOWN |
| Q03 | TypeScript strict, conventions/API/UI/test nécessaires | Au setup et avant parcours concerné | PROPOSÉ T07/T08/T10 ; D093 conservée |
| Q04 | Images, réseau, ports, rechargement, volumes et configuration Compose | Avant S02 | UNKNOWN ; périmètre D089 acquis |
| Q05 | Accès PostgreSQL, migration, modèle minimal et contraintes de périmètre | Avant S03 | UNKNOWN / modèle proposé section 9 |
| Q06 | Identité, bibliothèque JWT, clés, claims, transport/stockage, durées, renouvellement/révocation | Avant S04 | UNKNOWN ; JWT D094 acquis |
| Q07 | Mécanisme d'autorisation/isolation, procédures initiales et rattachements | Avant S05 et parcours concerné | PROPOSÉ T05 / modalités UNKNOWN |
| Q08 | Contrat d'injection interface/provider | Avant frontière nécessitant ce contrat | PROPOSÉ Symbol ; alternative classe abstraite |
| Q09 | Hébergement, données réelles, sauvegarde/restauration, exploitation et essais | Avant ouverture concernée | UNKNOWN C11/C12 ; pas requis pour la seule rédaction |

Priorité de conception validée D097 : traiter Identité / Organisation / Accès et ses arbitrages IA-Q avant les décisions dépendantes de JWT et des migrations métier. Principes IA-Q01/02/03 D099/D100/D101/D102 acquis ; prochaine discussion IA-Q04 et ses choix liés ; Q01/Q02/Q04 du présent socle restent ouverts pour le setup. Les préparations techniques indépendantes ne confèrent aucun accès métier et aucun démarrage n'est autorisé par la seule rédaction de D096/D097. Les fiches S01–S06 ne sont pas renumérotées.

**Critère de préparation avant une unité :** son périmètre et ses dépendances sont décrits, les décisions dont dépend son code sont validées, les erreurs/permissions applicables sont explicites et les vérifications réalisables sont définies. Une question ouverte indépendante peut rester ouverte ; une question dont dépend l'action ne se résout pas par une hypothèse cachée.

**Critère d'acceptation du socle réalisé :** les unités du périmètre retenu ont leurs preuves, tests pertinents et revue traitée ; les limites restent visibles. Le document demeure Proposed tant que les critères d'application ne sont pas vérifiés. Sa relecture documentaire ou son approbation de conception ne suffit pas à le passer Accepted.

## 17. Résultat de cette rédaction et prochaine action

Livrable : spécification préparatoire du socle, liée aux décisions D007/D008/D086/D088/D089/D093/D094/D095 et inspirée des deux archives relues. Vérification documentaire : cohérence des références/statuts, liens locaux et distinction entre prérequis, propositions et preuves ; résultat consigné dans le suivi.

Prochaine action : examiner la [comparaison IA-Q04](ia-q04-departure-history-portability-options.md) et HP01–HP08 avant nouvelle décision. IA-Q03 modèle A/CC01–CC08 validés D101/D102 ; modalités et IA-Q04–IA-Q12 ouverts. Les principes [IA-Q01](ia-q01-account-membership-options.md) sont validés D099, leurs modalités non résolues restent ouvertes dans [Identité / Organisation / Accès](identity-organization-access.md). Compléter ensuite politique JWT et modèle relationnel minimal avant leurs implémentations ; versions/outillage/configuration du socle restent à décider au moment nécessaire. Aucune option ouverte, aucun fichier applicatif, installation ou test applicatif produit par cette rédaction.
