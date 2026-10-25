# Fonctionnalités de la première version pilote

Synthèse mise à jour le 25 octobre 2026, fondée sur les décisions du registre jusqu'à D083. Besoins validés, règles encore ouvertes signalées. Pas de validation globale de D007, de stack ni de fonctionnalité Accepted.

| Bloc | Fonctions principales | Points ouverts |
|---|---|---|
| Administration générale | Premier établissement et CME pour le pilote ; écrans complets multi-établissements reportés, isolation dès la conception (D076) | Modalité de création initiale, procédures de désignation et récupération |
| Gestion locale | CME avec permission locale : classes, invitations formateurs/personnel, rattachements et rôles locaux | Catégories de personnel et délégations précises |
| Comptes apprenants | Inscription, rôle apprenant par défaut, validation du rattachement ; lien partagé par classe généré par CME, comptes individuels, expiration/désactivation/renouvellement (D059) | Authentification, durée d'expiration, demandes répétées et changements de classe à spécifier |
| Classes et profils | Référent par classe, plusieurs classes possibles (D078), rôle formateur/responsable commun (D079) ; remplacement CME, accès de l'ancienne affectation retirés, relais du nouveau et anciens avis attribués/conservés (D080) | Classe sans référent, transition, champs du profil et libellés d'interface |
| Offres | Contributions lien/texte ; modération motivée (D061), disponibilité/versions/suivis préservés (D068), compléments D070–D073/D075 ; doublon déjà publié clôturé par CME avec motif « doublon », suivis liés à l'offre d'origine sans fusion ni modification automatique (D077) | Modalités des demandes, formats/limites des champs, conservation/visibilité détaillée de l'historique et autres détails à spécifier |
| Entreprises | Liste enrichissable et propositions soumises à validation CME | Position dans les tranches et détails du parcours spontané |
| CV et portfolio | PDF/lien et double avis D057 ; classes/référent D058/D078–D081 ; retours partagés dans le périmètre D082 ; déclaration des changements portfolio avec date/résumé, deux avis à revalider et CV inchangé conservé D083 | Écriture/correction des commentaires, révision d'avis, autres statuts globaux, référence technique au contenu examiné et conservation |
| Candidatures | Checklist, brouillon, retours humains, envoi externe, six états, prochaine action/dates | Transitions, historique et partage du brouillon |
| Accompagnement | Demandes, choix du destinataire, acceptation/réorientation, simulations humaines | Réorientation, absence de réponse, règles de gestion des échéances |
| Rendez-vous et progression | Date/lieu/lien/participants/état, bilan, observations séparées, actions à faire/en cours/réalisées | Droits précis, changements et conservation |
| Tableau de suivi | Vue porteur sur apprenants, CME et responsables, filtre période et échéances, existence de bilans sans contenu | Calculs précis et position de la tranche |

## Ordre et limites

Construire progressivement : accès nécessaires et offres humaines/validation/consultation → préparation et suivi → accompagnement/progression. Affectations, revue des documents, entreprises et tableau à positionner précisément sans les supprimer. Organisation administrative D056 à intégrer au cadrage d'accès ; cela n'autorise pas à coder avant spécification et choix de stack.

Collecte automatique : étude/prototype indépendant et intégration ultérieure, non bloquante (D053–D054). Chat, envoi automatique, simulation automatique, matching complexe, espace recruteur et facturation prévus pour les versions futures (D040). Isolation des établissements anticipée dès la conception ; pas d'accès général aux documents sensibles via un rôle administratif.
