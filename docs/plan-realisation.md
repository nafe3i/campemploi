# Comment nous réaliserons CapEmploi Campus

Date : 26 octobre 2026.

**Statut : plan proposé, à valider ensemble.** La création de ce fichier est demandée par l'utilisateur ; elle ne vaut pas validation de toutes les propositions qu'il contient. Les décisions déjà validées restent applicables. Aucun code, installation ou déploiement réalisé par ce document.

## 1. Notre objectif et notre point de départ

Construire une plateforme utilisable par le campus : trouver des opportunités pertinentes et accessibles, préparer et suivre les candidatures, accompagner les apprenants et observer les résultats. Le projet répond à un besoin réel ; les explications techniques servent à permettre la participation du porteur aux décisions et à la réalisation.

| Déjà validé | Référence |
|---|---|
| Scope du pilote et vision multi-établissements | D007 ; [scope](scope/pilot.md) |
| Réalisation progressive, sans date fixe de livraison | D011 |
| React/Vite et TypeScript ; API REST Node.js/NestJS ; PostgreSQL ; serveur en monolithe modulaire | D008 |
| Docker Compose en développement : interface, API et base conteneurisées, rechargement automatique | D088–D089 |
| Tranche 1 : accès et offres ; tranche 2 : préparation/suivi et entreprises ; tranche 3 : accompagnement/pilotage | D086 ; [fonctionnalités](product/features-v1.md) |
| Accord avant toute nouvelle décision, contrôles métier, suivi documentaire et Git | D060, D062, D064–D065, D069, D074 |

État réel : cadrage global terminé, architecture en cours. Aucune application développée, aucun test applicatif exécuté et aucun environnement déployé.

## 2. Notre façon de travailler ensemble

Cette organisation reprend [notre workflow](workflow.md) et la [référence JSM](reference/jsm-workflow-source.txt).

- **Le porteur du projet** précise le besoin du campus, décide après comparaison des options, participe à la réalisation et donne ses retours sur le résultat visible. Son rôle ne se limite pas à approuver du code.
- **L'assistant** analyse les documents et le projet réel, recommande avec les compromis, aide à concevoir et implémenter dans le périmètre autorisé, vérifie et explique les résultats, puis tient les documents à jour.
- **La CME, les formateurs et les apprenants**, lorsque leur participation est organisée, pourront vérifier les usages et apporter leurs retours. Aucune disponibilité ni participation effective n'est présumée.

Avant une nouvelle décision, présenter le problème, les options, la recommandation, ses conséquences et les fichiers/actions concernés. Attendre l'accord explicite, puis consigner et appliquer ce périmètre. Ne pas redemander une validation déjà acquise et ne pas élargir un accord à une autre décision.

L'assistant ne délègue pas à un autre agent sans demande explicite. Les questions sont posées par petits groupes, au moment où leur réponse devient nécessaire.

## 3. Le parcours de réalisation proposé

Les étapes ci-dessous sont des repères de travail, sans dates imposées. Une étape franchie doit avoir une preuve ; la validation de ce plan ne rend pas automatiquement les futures décisions techniques validées.

| Étape | Ce que nous faisons | Livrable ou preuve permettant de poursuivre |
|---|---|---|
| A — Valider ce plan | Relire l'organisation du travail et ses limites | Accord consigné ; aucune nouvelle fonctionnalité ajoutée au scope |
| B — Concevoir le socle | Définir l'organisation du dépôt, les responsabilités interface/API/base, les premiers liens de données et permissions, les versions et le démarrage Docker | Spécification du socle dans docs/specs/, choix nécessaires validés, critères de démarrage écrits ; pas de génération de toute l'application |
| C — Initialiser puis auditer | Initialiser les outils retenus, configurer le développement Docker et inspecter les fichiers réellement créés | Démarrage interface/API/base vérifié, commandes reproductibles, configuration d'exemple sans secrets, conventions réelles dans AGENTS.md |
| D — Réaliser la tranche 1 | Spécifier puis développer les accès et les parcours d'offres par petites étapes complètes | Interface utilisable, règles serveur et données cohérentes ; vérifications, tests pertinents et revue de chaque parcours |
| E — Évaluer et préparer les essais | Vérifier l'ensemble disponible, corriger et préparer un environnement d'essai ; clarifier C11/C12 avant utilisateurs/données réels | Preuves techniques et conditions des essais établies ; retours mesurés lorsque les essais sont autorisés et effectués |
| F — Réaliser les tranches 2 et 3 | Reprendre la même boucle pour documents/candidatures/entreprises, puis accompagnement/pilotage | Preuves propres à chaque fonctionnalité, retours et documentation actualisés |
| G — Préparer et ouvrir la production pilote | Décider l'hébergement et l'exploitation, vérifier la version retenue, organiser l'ouverture autorisée | Déploiement réellement vérifié, accès contrôlés, sauvegarde/restauration et procédure de retour à la version précédente vérifiées selon le contexte |
| H — Observer et améliorer | Analyser les usages, incidents, temps et difficultés ; décider des corrections et évolutions | Résultats documentés et priorités validées, sans déclarer un gain non mesuré |

Les premières observations peuvent intervenir après une tranche utilisable, sans attendre toutes les fonctionnalités du produit. Le placement exact des essais et de l'ouverture pilote dépendra du cadre confirmé et des parcours disponibles. Préproduction, production et observation ne sont pas prouvées par un simple commit ou une release.

Sur un projet neuf, l'initialisation et l'audit interviennent après les choix nécessaires au socle. Les spécifications fonctionnelles détaillées sont produites avant chaque développement concerné ; nous n'avons pas à figer tous les détails des tranches suivantes avant le premier démarrage.

## 4. Comment nous découperons le développement

Nous suivons la réalisation par petites tranches fonctionnelles complètes : interface, traitement serveur, données et contrôles pour un besoin visible. Cela permet de constater rapidement si un parcours fonctionne et de corriger une erreur avant qu'elle se propage.

Découpage de travail proposé à préciser dans les spécifications de la tranche 1 :

1. Mettre en place les accès et l'organisation nécessaires au premier établissement et à sa CME.
2. Permettre la gestion des classes et le parcours apprenant par invitation, compte personnel et rattachement validé.
3. Permettre à un membre autorisé de proposer une offre et de retrouver sa proposition.
4. Permettre la qualification/modération CME et la consultation des offres publiées par les membres autorisés.
5. Compléter les corrections, retraits, clôtures, réouvertures, versions et doublons selon les règles déjà validées.

Cet ordre plus fin reste proposé. Les permissions et cas d'erreur propres à chaque parcours sont traités avec lui ; le point 5 ne reporte pas tous les contrôles à la fin. Une démonstration intermédiaire peut couvrir moins de règles que la tranche complète, à condition d'afficher ses limites. Aucun parcours n'est accepté avant ses propres vérifications.

Exemple : pour « proposer une offre », prévoir le formulaire, la réception par l'API, les champs requis, le rattachement à l'auteur et à l'établissement, le passage en attente et l'accès de l'auteur à sa proposition. Tester aussi une demande invalide et une tentative d'accès à la proposition d'un autre utilisateur. La publication reste soumise à ses règles CME.

Les détails des tranches 2 et 3 seront conçus à leur tour, en conservant les exigences déjà documentées. Les contraintes connues entre tranches doivent être anticipées : par exemple, les modifications d'offres ne devront pas casser les futurs liens de suivi des candidatures.

## 5. La boucle pour chaque petite fonctionnalité

1. **Comprendre** : objectif utilisateur, règles validées, acteurs et points ouverts.
2. **Spécifier** : parcours d'écran, données, échanges avec l'API, permissions, états, erreurs et critères d'acceptation dans docs/specs/.
3. **Décider** : soumettre les nouveaux choix nécessaires et consigner les accords ; ne pas inventer une règle pour débloquer du code.
4. **Implémenter progressivement** : expliquer la stratégie, inspecter les conventions, modifier uniquement les fichiers nécessaires et faire participer le porteur selon la tâche.
5. **Vérifier l'application réelle** : exécuter le parcours et relever les résultats, y compris refus d'accès et erreurs pertinents.
6. **Tester** : automatiser les comportements importants, les transitions et les protections qui doivent rester corrects après modification.
7. **Revoir** : relever les problèmes de sécurité, cohérence et maintenance ; corriger dans une étape distincte, puis refaire les contrôles concernés. Une revue par autre agent/modèle nécessite une autorisation explicite.
8. **Documenter et synchroniser** : preuves, limites et prochaine action ; diff et confidentialité contrôlés, commit descriptif et push vérifié selon D069.

Une difficulté peut demander un retour à la conception ou au diagnostic. Nous vérifions la cause avant de modifier au hasard. Nous n'ajoutons pas un outil ou une couche sans problème concret à résoudre.

## 6. Quand une étape est-elle réellement terminée ?

| Ce que nous affirmons | Preuve attendue |
|---|---|
| Décision validée | Accord explicite et entrée du registre des décisions |
| Document produit | Fichier relu, points ouverts indiqués et suivi actualisé |
| Fonctionnalité développée | Code correspondant au périmètre décrit ; cela seul ne suffit pas à l'accepter |
| Fonctionnalité Accepted | Critères vérifiés sur l'application réelle, tests pertinents réussis, preuves et limites consignées selon le workflow |
| État enregistré/publié | Commit existant et concordance distante vérifiée après push |
| Version en production | Déploiement et contrôles sur l'environnement cible réellement effectués |
| Bénéfice utilisateur démontré | Mesures réelles suivant le protocole retenu, pas le nombre de fonctionnalités codées |

Pour les contrôles D060, examiner à chaque parcours : identité/compte, rôle et rattachement, établissement/classe/propriétaire, accès direct par identifiant, entrées, informations exposées, transitions et absence d'effets après refus. Répétitions, concurrence, expiration et autres cas limites sont traités lorsqu'ils s'appliquent au métier concerné.

Les statuts de spécification restent **Proposed → In Progress → Accepted**. L'accord sur une décision technique ne marque pas sa mise en œuvre Accepted.

## 7. Préparer un pilote réel et exploitable

Le groupe initial validé reste de 8 à 12 apprenants des deux années, avec la CME et 1 à 2 responsables techniques (D034). Leur recrutement effectif et le déroulement précis restent à organiser.

Avant les essais avec des personnes ou données réelles, clarifier le portage et les responsabilités sur les données (C11), puis le protocole (C12). Les données de développement et de démonstration seront fictives ; CV, coordonnées, secrets et données réelles ne vont pas dans le dépôt public.

La mesure doit porter sur pertinence/accessibilité des opportunités, effort de recherche, utilité des parcours disponibles et charge CME. Les critères D035 restent la référence à opérationnaliser ; ne pas les modifier implicitement ni exiger d'un parcours non encore livré une preuve qu'il ne peut fournir.

Pour la préproduction et la production, préciser avant ouverture : hébergement et coût, configuration sécurisée, stockage privé, migrations, sauvegardes et restauration, journaux utiles sans exposition de données, traitement des incidents et retour à une version précédente. Docker de développement ne fixe pas automatiquement la configuration de production. L'ouverture reste une action distincte à autoriser dans son périmètre concret.

## 8. Suivre le travail et les changements dans le temps

| Document | Ce qu'il garde |
|---|---|
| [Ce plan](plan-realisation.md) | Vue d'ensemble de la réalisation proposée, puis de l'organisation retenue après validation |
| [Scope](scope/pilot.md) et [fonctionnalités](product/features-v1.md) | Besoins, limites et ordre des tranches |
| [Décisions](product/decisions.md) | Accords, propositions et inconnues, avec leurs raisons |
| docs/specs/ | Contrat de réalisation de chaque sujet technique ou fonctionnel |
| [BOARD](../tracking/BOARD.md) | Tâches, étapes, preuves et prochaine action |
| [STATUS](../tracking/STATUS.md) | Point de reprise courant |
| [JOURNAL](../tracking/JOURNAL.md) | Avancées réelles et décisions dans le temps |
| Git et GitHub | Versions réellement enregistrées et publiées, comparables entre elles |

Nous conservons les anciennes captures 0001–0018 sans créer de nouveaux snapshots (D074). Les Issues et le Project GitHub restent à proposer avant création ; ce plan n'en crée pas et ne remplace pas automatiquement BOARD.md.

## 9. Ce qui reste à décider, dans le bon ordre

**Première discussion : valider l'organisation de réalisation proposée dans ce fichier**, notamment les étapes et les conditions de passage. Cette validation n'autorise pas toute la feuille de route d'un seul accord.

Ensuite, recommander et arbitrer les choix nécessaires au socle : organisation du dépôt, versions, environnement Docker et commandes de démarrage. Concevoir les relations et limites d'accès principales, puis choisir les mécanismes adaptés : accès aux données, authentification, séparation des établissements et configuration du stockage au moment concerné. Les bibliothèques, fournisseurs et détails d'interface restent ouverts tant qu'ils ne sont pas explicitement retenus.

La collecte automatique est une évolution ultérieure indépendante, fondée sur l'étude existante et une expérimentation à décider (D053–D054). Elle ne bloque pas les trois tranches validées. Chat, envoi automatique de candidatures, simulations automatiques, matching complexe, espace recruteur et facturation restent dans la vision future D040.

Ce plan ne choisit ni nouvelle stack, ni hébergeur, ni durée d'itération, ni calendrier de livraison. Les propositions nouvelles attendent l'accord de l'utilisateur.
