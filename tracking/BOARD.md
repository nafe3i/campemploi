# Tableau de suivi du projet

Dernière mise à jour : 25 octobre 2026. Phase active : Scope. Référence de méthode : docs/workflow.md ; D062.

Ce tableau suit notre réalisation du projet. Il est distinct du futur tableau d'activité des apprenants/CME/formateurs (D045).
Historique : nouveaux états de ce tableau dans les commits Git (D074), avec push vérifié selon D069. tracking/HISTORY.md conserve l'index des anciennes captures D063, inchangées ; aucune nouvelle copie périodique. Une version documentaire n'est pas une fonctionnalité applicative terminée.

## Lecture des statuts

- À faire : travail non commencé.
- En cours : travail commencé, incomplet.
- À valider : proposition concrète attendant une décision utilisateur.
- Terminé : livrable de la tâche produit et vérifié, avec preuve indiquée ; ne signifie pas qu'une fonctionnalité décrite est développée.
- Reporté : prévu pour plus tard.

Les décisions restent Validé/Proposé/UNKNOWN dans le registre. Les spécifications conservent Proposed → In Progress → Accepted ; Accepted exige les preuves définies par le workflow. Aucun pourcentage global sans base de calcul.

## Cadrage et décisions

| ID | Travail | Statut | Preuve / reste à faire |
|---|---|---|---|
| C01 | Créer la base documentaire et le workflow | Terminé | README.md, AGENTS.md, docs/workflow.md, tracking/JOURNAL.md |
| C02 | Documenter public, profils, objectifs et langues | Terminé | docs/product/vision.md ; D016–D018, D048–D051 ; détails individuels encore ouverts |
| C03 | Consigner organisation générale/locale et invitation par classe | Terminé | D056, D059 ; docs/scope/establishment-administration.md ; procédures techniques à spécifier |
| C04 | Consigner double validation CV/portfolio et accès par classe | Terminé | D057–D058 ; docs/scope/cv-portfolio-review.md ; cas limites encore ouverts |
| C05 | Consigner modération nominale des offres | Terminé | D061 ; docs/scope/offer-lifecycle.md ; complément clôture/modifications traité en C07/D068 |
| C06 | Étudier les sources et un échantillon documentaire initial | Terminé | docs/reference/offer-sources-study.md et opportunity-sample-2026-10-17.md ; aucune preuve de gain utilisateur ni de capacité CME |
| C07 | Définir clôture et modification d'une offre publiée | Terminé | Accord explicite du 25 octobre, D068 ; docs/scope/offer-lifecycle.md et synthèses alignées ; capture 0008. Décision/documentation terminée, aucun développement ni test applicatif |
| C08 | Préciser classes et revues de documents | En cours | D078–D080 documentées avec contrôles attendus ; D080 publiée/vérifiée au commit 316b654 ; docs/scope/cv-portfolio-review.md. Validation courante après remplacement, portfolio et commentaires à préciser |
| C09 | Consolider matrice d'accès et critères de la première tranche | Terminé | docs/scope/first-slice.md : parcours, matrice et critères ; arbitrages D076/D077 et documents publiés/vérifiés au commit a9ebfe0. Consolidation documentaire uniquement ; détails techniques à spécifier, aucune preuve applicative ni validation globale D007 |
| C10 | Valider globalement le scope et le découpage | À valider | D007 toujours ouverte ; synthèse docs/product/features-v1.md et docs/scope/pilot.md |
| C11 | Clarifier cadre des essais réels et responsabilité des données | À faire | Engagement institutionnel non confirmé ; aucune attribution juridique inventée |
| C12 | Mesurer utilité/effort humain et charge CME | À faire | Protocole proposé docs/scope/opportunity-experiment.md ; aucune mesure humaine ni D035 vérifiée |

## Architecture et réalisation

Chaque ligne sera découpée en tâches plus petites avant de coder ; cet inventaire n'autorise pas les décisions encore ouvertes.

| ID | Travail | Statut | Dépendance / validation attendue |
|---|---|---|---|
| R01 | Comparer et décider stack/architecture/hébergement | À faire | Cadrage de la tranche et décision documentée avec l'utilisateur |
| R02 | Spécifier accès, comptes, organisation et offres | À faire | R01 et règles métier pertinentes arbitrées ; critères/tests de permissions |
| R03 | Initialiser le projet et inspecter la structure réelle | À faire | Stack validée ; setup puis audit |
| R04 | Réaliser accès nécessaires et parcours d'offres humaines | À faire | Spécification ; développement → vérification → tests → revue → documentation |
| R05 | Réaliser CV/portfolio et suivi des candidatures | À faire | Spécifications propres ; tranche à positionner précisément |
| R06 | Réaliser accompagnement, rendez-vous et progression | À faire | Spécifications et accès propres |
| R07 | Réaliser entreprises et tableau de pilotage | À faire | Placement dans les tranches à préciser ; indicateurs et accès testés |
| R08 | Organiser le pilote puis l'élargissement | À faire | Cadre des données, vérifications, corrections et critères D035 |
| R09 | Prototype et intégration de collecte automatique | Reporté | D053–D054 ; source/faisabilité à choisir ; ne bloque pas R04 |
| R10 | Fonctions de la vision future | Reporté | docs/product/roadmap.md ; aucun calendrier imposé |

## Point de reprise

## Suivi par fonctionnalité — D065

État observé au 25 octobre 2026 : aucun développement, test applicatif ou déploiement. Versions livrées : aucune. Les références ci-dessous sont des preuves documentaires uniquement.

| Fonctionnalité | Étape actuelle | Prochaine action / décision attendue | Preuve | Difficulté / point ouvert | Version |
|---|---|---|---|---|---|
| Comptes, établissements et invitations | Conception métier partielle | Spécifier activation, expiration, rôles locaux et cas de rattachement après cadrage | D056, D059, D076 ; docs/scope/establishment-administration.md | Modalité initiale et procédures | Aucune |
| Offres | Cadrage de tranche consolidé | Relire le périmètre global et préparer les spécifications après décisions nécessaires | D061, D068, D070–D073, D075, D077 ; docs/scope/first-slice.md et offer-lifecycle.md | Modalités des demandes, formats/limites et conservation à spécifier | Aucune |
| CV et portfolio | Conception métier partielle | Arbitrer validation courante après remplacement, puis commentaires/portfolio | D057–D058, D078–D080 ; docs/scope/cv-portfolio-review.md | Validation au changement, commentaires et modifications externes | Aucune |
| Candidatures | Cadrage documenté | Spécifier transitions et historique | D036–D037 | Cas limites et partage des brouillons | Aucune |
| Accompagnement et progression | Cadrage documenté | Spécifier réorientation et mise à jour des actions | D020–D027 | Délais, absence de réponse, droits précis | Aucune |
| Entreprises et tableau de suivi | Cadrage documenté | Positionner les tranches et préciser calculs/permissions | D043–D046 | Champs et événements des indicateurs | Aucune |
| Collecte automatique | Reportée, étude exploratoire disponible | Choisir une expérimentation après accord | D053–D054 ; docs/reference/offer-sources-study.md | Source utile et collecte autorisée non démontrées | Aucune |

## Reprise courante

## Mise en place de Git et GitHub — D066

| ID | Travail | Statut | Preuve / reste à faire |
|---|---|---|---|
| G01 | Initialiser Git local et configurer origin fourni | Terminé | main, origin configuré ; dépôt distant sans références lors du contrôle |
| G02 | Préparer premier contenu et contrôles | Terminé | .gitignore/.gitattributes, docs/git-workflow.md et revue docs/reviews/2026-10-24-initial-git-review.md ; contenu documentaire sélectionné, contrôles avant accord commit |
| G03 | Créer le premier commit et envoyer le premier état | Terminé | D067 ; commit initial 2082f296e075c6f3a0b1d68a214f1de417c9d54b envoyé et vérifié sur origin/main le 25 octobre 2026 ; dépôt public accepté |
| G04 | Préparer tâches et Project GitHub | À faire | Modèle à relier au tableau existant avant création externe |
| G05 | Consigner et appliquer commit/push après chaque validation | Terminé | D069 et consignes alignées ; lot D068/D069 publié au commit de732bdaca71bef05aaf62b372c9c052c1c4b870 ; concordance origin/main vérifiée, contrôles documentaires et captures ; capture 0010 du résultat |
| G06 | Remplacer les nouvelles copies snapshots par Git | Terminé | D074 ; consignes, workflow et index historique alignés ; commit dc6aeca0455c921c741771cbc19f80c6b7de3e65 publié et vérifié sur origin/main ; anciennes captures inchangées, aucune nouvelle copie créée |

## Prochaine action immédiate

Consolidation documentaire C09 terminée après accord D076/D077 ; aucune réalisation applicative. Prochaine tâche produit proposée C08 (classes/revues), puis relecture globale C10/D007. Proposer le contenu des Issues/Project avant création externe.

Prochaine tâche proposée : C08, clarifier les points de cadrage des classes et revues, sans détailler prématurément la technique. D007 reste ouverte. Aucune fonctionnalité applicative développée ou Accepted ; mise à jour après chaque avancée réelle avec preuve.
