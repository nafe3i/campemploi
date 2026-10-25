# Fonctionnalités de la première version pilote

Synthèse mise à jour le 25 octobre 2026, fondée sur les décisions du registre jusqu'à D073. Besoins validés, règles encore ouvertes signalées. Pas de validation globale de D007, de stack ni de fonctionnalité Accepted.

| Bloc | Fonctions principales | Points ouverts |
|---|---|---|
| Administration générale | Création d'établissement et désignation CME/administrateur local par le porteur | Étendue des écrans multi-établissements au pilote, procédures de désignation et récupération |
| Gestion locale | CME avec permission locale : classes, invitations formateurs/personnel, rattachements et rôles locaux | Catégories de personnel et délégations précises |
| Comptes apprenants | Inscription, rôle apprenant par défaut, validation du rattachement ; lien partagé par classe généré par CME, comptes individuels, expiration/désactivation/renouvellement (D059) | Authentification, durée d'expiration, demandes répétées et changements de classe à spécifier |
| Classes et profils | Affectations des formateurs, vue CME établissement, tri/filtres classe/année/formateur | Équivalence formateur/responsable technique, nombre de formateurs par classe, champs du profil |
| Offres | Contributions lien/texte ; modération motivée (D061), disponibilité/versions/suivis préservés (D068), informations/qualification (D070), consultation auteur/CME avant publication (D071), doublons vérifiés manuellement (D072) ; réexamen après rejet autorisé par CME avec motif, correction puis retour en attente et rejet initial conservé (D073) | Retrait par auteur, formats/limites des champs, doublons déjà publiés, conservation/visibilité détaillée de l'historique et autres exceptions à préciser |
| Entreprises | Liste enrichissable et propositions soumises à validation CME | Position dans les tranches et détails du parcours spontané |
| CV et portfolio | CV PDF privé remplaçable, portfolio par lien ; avis CME/formateur séparés, double validation, nouvelle revue après modification et historique (D057). Accès formateur par classe sans demande ; CME pour son établissement (D058) | Changements d'affectation, plusieurs formateurs, autres statuts globaux, version examinée et signalement des changements du portfolio externe |
| Candidatures | Checklist, brouillon, retours humains, envoi externe, six états, prochaine action/dates | Transitions, historique et partage du brouillon |
| Accompagnement | Demandes, choix du destinataire, acceptation/réorientation, simulations humaines | Réorientation, absence de réponse, règles de gestion des échéances |
| Rendez-vous et progression | Date/lieu/lien/participants/état, bilan, observations séparées, actions à faire/en cours/réalisées | Droits précis, changements et conservation |
| Tableau de suivi | Vue porteur sur apprenants, CME et responsables, filtre période et échéances, existence de bilans sans contenu | Calculs précis et position de la tranche |

## Ordre et limites

Construire progressivement : accès nécessaires et offres humaines/validation/consultation → préparation et suivi → accompagnement/progression. Affectations, revue des documents, entreprises et tableau à positionner précisément sans les supprimer. Organisation administrative D056 à intégrer au cadrage d'accès ; cela n'autorise pas à coder avant spécification et choix de stack.

Collecte automatique : étude/prototype indépendant et intégration ultérieure, non bloquante (D053–D054). Chat, envoi automatique, simulation automatique, matching complexe, espace recruteur et facturation prévus pour les versions futures (D040). Isolation des établissements anticipée dès la conception ; pas d'accès général aux documents sensibles via un rôle administratif.
