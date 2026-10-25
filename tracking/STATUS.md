# État — 2026-10-25

Phase active : Scope. D007 (validation globale) toujours ouverte. Aucun code applicatif, stack, build, test applicatif ou déploiement.

## Suivi Git et GitHub — D066

- Accord D067 obtenu le 25 octobre 2026 : réaliser le premier commit et envoyer le contenu documentaire sur le dépôt public accepté. Exécution en cours ; aucun résultat de publication encore déclaré par cette entrée.

- Organisation Git/GitHub validée ; dépôt local initialisé sur main.
- origin configuré : https://github.com/nafe3i/campemploi.git.
- Contrôle renouvelé le 25 octobre 2026 : aucune référence distante annoncée ; API GitHub indiquant private=false et taille 0. Dépôt public, contrairement au choix privé prévu ; aucun envoi effectué.
- Premier contenu documentaire préparé et contrôlé pour présentation avant accord. Aucun commit, push, Issue ou Project créé.
- .gitignore exclut secrets/configuration locale, répertoires de données utilisateur, dépendances et sorties générées. Recherche ciblée de secrets sans motif détecté, sans garantie absolue.
- Instantanés existants 0001–0003 préservés ; capture 0004 créée le 25 octobre 2026 pour la reprise Git. L'ancienne mention du 24 octobre annonçait une capture non présente sur disque et n'est pas une preuve de capture à cette date.
- Capture 0004 conservée dans une archive ZIP pour neutraliser la configuration Git imbriquée sans altérer ses octets ; copie décompressée locale exclue de Git, pas supprimée. Capture 0005 documentaire des contrôles finaux, sans configuration imbriquée.
- Prochaine action de suivi : accord sur premier commit et clarification du dépôt public avant tout envoi. Voir docs/git-workflow.md et revue docs/reviews/2026-10-24-initial-git-review.md.

## Produit : décisions courantes

- Contributions humaines d'abord : proposition d'offre → validation CME → consultation (D053–D054).
- Modération nominale validée : en attente, à corriger, publiée, rejetée ; motifs et nouvelle soumission après correction (D061). Clôture et modifications publiées encore proposées.
- Portage officiel de l'établissement non confirmé ; responsabilités des données réelles encore à préciser.
- Public full stack Java/Angular, MERN, PHP/Laravel ; bac+2/bac+3 ; français et anglais, niveaux individuels inconnus.
- Première année : deux mois de stage, début flexible avril/mai 2027 ; limites exactes de fin à confirmer. Deuxième année : préembauche et premiers emplois.
- Offres bac+5 conservables avec écart mentionné ; accessibilité inconnue explicitement signalée, sans garantie d'éligibilité.

## Comptes et accompagnement : validé, non développé

- Portage de l'administration générale par le porteur ; CME avec permission d'administration locale, classes, personnel invité, rôles et rattachements (D056).
- Lien partagé par classe : comptes individuels, validation CME avant accès, expiration/désactivation/renouvellement (D059).
- CV PDF et portfolio par lien ; avis formateur et CME distincts, deux validations positives par document, nouvelle revue après modification et historique (D057).
- Accès de revue formateur limité à ses classes sans demande préalable, CME à son établissement (D058). Les bilans confidentiels gardent leurs propres restrictions.
- Préparation et suivi des candidatures, demandes d'accompagnement, rendez-vous, actions de progression et tableau de suivi restent prévus.
- Groupe pilote 8 à 12 apprenants, CME et 1 à 2 responsables ; critères D035 non encore vérifiés.

## Méthode et points ouverts

- Accord explicite avant application d'une nouvelle décision (D064), contrôles communs/spécifiques (D060).
- Tâches et preuves dans tracking/BOARD.md ; suivi global et par fonctionnalité de conception à production (D062/D065).
- Historique des captures dans tracking/HISTORY.md. Ne pas remplacer les captures par Git ni migrer BOARD.md vers Projects sans décision précise.
- Matrice complète des permissions, cas limites des classes/revues, protocoles de mesure et données réelles à spécifier.
- Prototype de collecte automatique prévu ultérieurement, pas une dépendance de la première tranche. Fonctions futures dans docs/product/roadmap.md.

Prochaine tâche produit : C07, arbitrer clôture des offres puis modifications après publication. L'initialisation de Git ne tranche aucune règle produit et n'autorise pas le choix d'une stack ou un démarrage applicatif.
