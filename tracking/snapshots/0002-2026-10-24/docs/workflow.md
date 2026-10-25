# Workflow d'ingénierie

Adaptation du document JSM fourni par l'utilisateur. Les skills correspondants ne sont pas installés ; les noms ci-dessous désignent des phases de travail.

## Boucle

1. Scope : besoin, utilisateurs, limites et ordre de réalisation dans docs/scope/.
2. Architect : décisions et spécifications dans docs/specs/.
3. Setup puis audit : initialiser après choix de stack, inspecter le projet réel, actualiser AGENTS.md.
4. Develop : implémenter une petite tranche complète à partir de la spécification.
5. Check verify : exécuter l'application et vérifier les critères d'acceptation.
6. Test : couvrir les comportements importants, cas limites et erreurs.
7. Check review : revue séparée, constats dans docs/reviews/, sans modifier le code pendant la revue.
8. Document : résumer les changements réels ; changelog lorsque pertinent.
9. Sync : réaligner documentation, statuts et journal.

Debug peut intervenir à tout moment : comprendre, reproduire, vérifier les hypothèses, corriger au minimum et prévenir la régression.

## Spécifications

Historique temporel (D063) : tracking/HISTORY.md indexe des instantanés non réécrits du suivi et des documents concernés, avec identifiant, date, prédécesseur et motif. Créer une capture après changement significatif et en fin de session si le suivi a changé. Le journal décrit les changements ; seuls les fichiers capturés garantissent leur contenu à cet état. Pas de reconstruction inventée du passé ni d'état futur présenté comme réalisé.

Suivi du travail (D062) : tracking/BOARD.md regroupe tâches, statut et preuves. Conventions : À faire, En cours, À valider, Terminé, Reporté. Ce suivi est distinct du registre des décisions et des statuts des spécifications ci-dessous. Une tâche documentaire peut être terminée alors que la fonctionnalité est non développée. Actualiser après chaque avancée réelle et relier aux preuves, avec état/journal cohérents.

Chaque spécification indique : contexte, objectif, périmètre, règles, décisions, critères d'acceptation, vérifications et questions ouvertes.
Statuts : Proposed → In Progress → Accepted.
Accepted exige des critères vérifiés et les tests pertinents réussis ; le code seul ne suffit pas.
Toute modification d'une décision doit être explicite.
Accord avant application (D064) : présenter la nouvelle décision et ses conséquences concrètes, poser la question de validation et attendre un accord explicite avant l'action dépendante. Clarifier les réponses ambiguës. Une instruction explicite autorise l'action demandée ; ne pas redemander pour un périmètre déjà approuvé. Consigner l'accord avant application ; documentation de suivi et instantanés déjà autorisés restent à maintenir sans glisser de nouvelle décision.

## Vérifications communes et spécifiques — D060

Règle validée le 24 octobre 2026 : chaque fonctionnalité et chaque étape doivent avoir leurs contrôles explicités, avec un socle commun et des règles propres au métier. Appliquer les contrôles pertinents, sans créer de mécanisme ou dépendance inutile.

Socle commun à examiner : identité et état du compte, permissions côté serveur, établissement/classe/propriétaire concernés, validation des entrées, accès direct par identifiant, données exposées, erreurs compréhensibles, répétition d'une action et cohérence en cas d'échec.

Règles spécifiques à définir et valider avant implémentation : états et transitions autorisés, acteurs de chaque action, préconditions, expiration/révocation si applicable, modification/version, annulation, doublons et concurrence lorsque ces cas sont pertinents. Une durée d'expiration utile aux invitations n'est pas à imposer arbitrairement à toutes les données.

Pour chaque parcours, documenter : action → acteur autorisé → préconditions → résultat normal → refus/cas limite → preuve de vérification et test pertinent. Vérifier aussi l'absence d'effet non autorisé après un refus. Les permissions doivent être vérifiées à chaque requête concernée ; masquer un bouton n'est pas une protection suffisante.

Les mécanismes techniques communs pourront être mutualisés après choix d'architecture ; les responsabilités et règles métier restent explicites. Cette décision ne choisit aucune abstraction ni stack. Tests ciblés sur comportements importants, dont erreurs et isolation ; Accepted seulement après preuves selon les critères de la spécification.

Exemples à spécifier : invitation expirée/désactivée ; double avis sur le même contenu de CV et remplacement ; offre non publiée consultée par URL ; changement de classe sans exposition de documents. Les règles déjà validées sont des exigences ; les issues non tranchées restent ouvertes, pas inventées par les tests.

## Profondeur proposée

Beta pour le pilote avec utilisateurs réels : vérification de l'application et tests pertinents.
Revue renforcée des permissions, de l'authentification et de la séparation entre établissements.
Un autre modèle ou agent ne sera utilisé que si explicitement autorisé et disponible.

## Approche pédagogique

Expliquer le pourquoi avant le comment. Montrer des exemples petits.
Privilégier des tranches fonctionnelles complètes.
La documentation constitue la mémoire durable ; une proposition reste proposée jusqu'à validation.
