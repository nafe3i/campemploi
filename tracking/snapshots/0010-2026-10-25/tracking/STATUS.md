# État — 2026-10-25

Phase active : Scope. D007 (validation globale) toujours ouverte. Aucun code applicatif, stack, build, test applicatif ou déploiement.
Tâche C07 : règles de clôture/réouverture et modifications explicitement validées D068, documentées dans docs/scope/offer-lifecycle.md. C07 terminée pour le cadrage documentaire uniquement ; continuité des candidatures, versions et contrôles à implémenter/vérifier. Capture 0008 de cet accord. D068/D069 publiées au commit de732bdaca71bef05aaf62b372c9c052c1c4b870 ; concordance avec origin/main vérifiée après push normal. Capture 0010 du suivi de cette exécution ; publication de ce suivi traitée dans un commit distinct.

## Suivi Git et GitHub — D066

- Accord D067 obtenu le 25 octobre 2026 : premier commit et dépôt public acceptés. Exécution réalisée et vérifiée.
- D069 : commit descriptif et push après chaque validation explicite, sans nouvel accord pour le même périmètre ; contrôles de sélection, confidentialité et résultat distant obligatoires. Règle ajoutée à AGENTS.md, workflow et guide Git ; capture 0009 avant synchronisation.
- Application D069 réalisée : commit de732bd publié et vérifié ; diff contrôlé, recherche ciblée de secrets sans motif détecté, 30 fichiers de captures sélectionnés aux octets identiques. Aucun code applicatif ni déploiement.

- Organisation Git/GitHub validée ; dépôt local initialisé sur main.
- origin configuré : https://github.com/nafe3i/campemploi.git.
- Avant envoi : dépôt public et sans référence Git distante. Après accord : commit initial 2082f296e075c6f3a0b1d68a214f1de417c9d54b envoyé sur origin/main ; lecture distante confirmant exactement ce commit. Aucun changement de visibilité.
- Premier état documentaire publié. Aucun code applicatif, Issue, Project ou déploiement créé. Synchronisation documentaire de fin d'opération enregistrée séparément.
- .gitignore exclut secrets/configuration locale, répertoires de données utilisateur, dépendances et sorties générées. Recherche ciblée de secrets sans motif détecté, sans garantie absolue.
- Instantanés existants 0001–0003 préservés ; capture 0004 créée le 25 octobre 2026 pour la reprise Git. L'ancienne mention du 24 octobre annonçait une capture non présente sur disque et n'est pas une preuve de capture à cette date.
- Capture 0004 conservée dans une archive ZIP pour neutraliser la configuration Git imbriquée sans altérer ses octets ; copie décompressée locale exclue de Git, pas supprimée. Capture 0005 documentaire des contrôles finaux, sans configuration imbriquée.
- Prochaine action de suivi : proposer les Issues et le Project avant création externe. Première publication acquise ; capture 0006 de fin d'opération et mise à jour du suivi selon D063. Voir docs/git-workflow.md.

## Produit : décisions courantes

- Contributions humaines d'abord : proposition d'offre → validation CME → consultation (D053–D054).
- Modération nominale validée : en attente, à corriger, publiée, rejetée ; motifs et nouvelle soumission après correction (D061). Disponibilité distincte, clôture/réouverture et modifications par CME validées D068 ; signalements, versions, suivis préservés et retrait temporaire si doute sérieux. Détails de conservation et autres exceptions encore ouverts.
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

Prochaine tâche produit proposée : C09, consolider droits, champs et critères restants de la première tranche. C08 (classes/revues) reste à faire pour son périmètre. D007 toujours ouverte ; aucun choix de stack ni démarrage applicatif autorisé par D068.
