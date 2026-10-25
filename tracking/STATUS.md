# État — 2026-10-25

Phase active : Scope. D007 (validation globale) toujours ouverte. Aucun code applicatif, stack, build, test applicatif ou déploiement.
D078 validée et documentée : un formateur référent par classe porte l'avis, plusieurs classes possibles par formateur, affectation CME dans son établissement avec permission locale. C08 en cours ; correspondance formateur/responsable technique UNKNOWN, clarification demandée séparément, sans fusion de rôles. Commit 957a2e309d2d5125317e587add5dcc424def5c09 publié et vérifié sur origin/main ; contrôles applicatifs non exécutés, sans snapshot D074.
Consolidation C09 documentaire terminée : parcours, matrice des droits et critères dans docs/scope/first-slice.md ; arbitrages D076/D077 publiés et vérifiés au commit a9ebfe0eddb335009b3a7cf01c1342c44e837746. Aucune preuve applicative ; D007 reste ouverte, C08 désormais en cours.

## Repères documentaires précédents

Les statuts C09 cités ci-dessous décrivent les étapes antérieures ; l'état courant de consolidation est indiqué ci-dessus et dans BOARD.md.
D075 validée et documentée : auteur demande retrait avant publication ; CME du même établissement rejette avec motif prévu, sans supprimer proposition/historique ni ajouter un état. Après publication, clôture D068. Contrôles attendus documentés, non exécutés ; C09 reste en cours. Commit fc6af0fc989bd73f05b5ae463272cb999bacff46 publié et vérifié sur origin/main selon D069, aucun nouveau snapshot selon D074.
D074 validée et appliquée à la documentation : nouveaux états par commits Git/push vérifié, sans nouveaux snapshots ; anciennes captures 0001–0018 conservées. STATUS, BOARD, JOURNAL et registre des décisions gardent leurs rôles. Consignes/workflow/index réalignés ; G06 terminée, commit dc6aeca0455c921c741771cbc19f80c6b7de3e65 publié et vérifié sur origin/main. Prochaine tâche produit C09 : consolidation de la première tranche, sans choix de stack.
D073 validée et documentée : réexamen d'un rejet autorisé par CME du même établissement avec motif si nouveaux éléments ; auteur corrige puis soumet en attente, rejet initial conservé. Aucun réexamen autonome par l'auteur ni publication automatique. C09 en cours ; bilan du scope demandé par l'utilisateur ajouté dans docs/scope/pilot.md, distinguant documentation réalisée et application non développée. Capture 0017 ; commit 492951a4a85daa2d7a96cbe845b324d93a9a75a3 publié et vérifié sur origin/main. Capture 0018 du résultat, suivi dans un commit distinct selon D069.
D072 validée et documentée : traitement manuel des propositions en doublon par CME, rejet « déjà présente », offre existante indiquée seulement si accès autorisé, aucun suivi supprimé/fusionné automatiquement. C09 reste en cours ; contrôles attendus documentés, non exécutés. Capture 0015 de cet accord. Commit 1b4ece250cae3e47ff71a349931933728212014d publié et vérifié sur origin/main ; capture 0016 du résultat, suivi dans un commit distinct selon D069.
D071 validée et documentée : auteur sur ses propres propositions, état et motifs de correction/rejet ; CME sur celles de son établissement ; autres membres après publication. Contrôles de propriété/rôle/établissement documentés, non exécutés dans une application. C09 reste en cours ; capture 0013 de cet accord. Commit 7fc20ee4b3bb6101e79b85403802c7cb78dc4c48 publié et vérifié sur origin/main ; capture 0014 du résultat, suivi dans un commit distinct selon D069.
D070 validée et documentée : informations minimales à la soumission, qualification CME avec inconnues explicites, moyen de candidature exploitable requis avant publication. C09 en cours ; contrôles attendus documentés, pas exécutés dans une application. Capture 0011 de cet accord ; commit 86d06eaf1d42d1063fc3ab7603ee64959a2bc87d envoyé et vérifié sur origin/main. Capture 0012 du résultat, suivi dans un commit distinct selon D069.
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
- D074 : nouveaux états dans Git, anciennes captures indexées dans tracking/HISTORY.md sans réécriture ; aucune nouvelle copie périodique. Migration de BOARD.md vers Projects non validée.
- Matrice complète des permissions, cas limites des classes/revues, protocoles de mesure et données réelles à spécifier.
- Prototype de collecte automatique prévu ultérieurement, pas une dépendance de la première tranche. Fonctions futures dans docs/product/roadmap.md.

Prochaine tâche produit proposée : C08, préciser les points de cadrage classes/revues puis relire le scope global C10/D007. C09 est terminée pour la consolidation documentaire ; détails de spécification encore à traiter avant développement. Aucun choix de stack ni démarrage applicatif autorisé par les deux arbitrages.
