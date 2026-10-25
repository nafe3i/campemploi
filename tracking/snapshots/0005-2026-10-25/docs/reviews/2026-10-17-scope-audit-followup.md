# Suite de l'audit critique du scope — 17 octobre 2026

Statut : propositions de travail, non validées. Source : audit fourni par l'utilisateur dans « Texte collé.txt » (pièce jointe 4054bc99-bc0e-406a-ad50-122ba91df1f3), comparé au scope et au registre D001–D046.
D007 reste en attente. Aucun choix de stack, suppression de fonctionnalité, nouveau blocage obligatoire ou démarrage de développement déduit de cet audit. Les notes chiffrées de l'audit sont des appréciations, pas des mesures observées.

## 1. Risques et arbitrages proposés

| Priorité proposée | Risque et état actuel | Prochaine preuve ou décision |
|---|---|---|
| P0 | Valeur de la découverte : sources repérées, volume utile non démontré | Examiner un échantillon réel par année, distinguer pertinent / à confirmer / incompatible / expiré ; comparer aux contributions humaines |
| P0 | Périmètre large malgré un petit nombre d'utilisateurs | Valider la frontière minimale de chaque tranche, sans retirer les fonctions déjà validées |
| P0 | Charge CME : 30 min/jour ou plus indiquées, capacité non mesurée | Chronométrer la validation d'un échantillon, relever entrées et stock en attente ; faire confirmer l'organisation opérationnelle |
| P0 | Responsabilité des données non identifiée | Identifier la personne/structure responsable du traitement ; vérifier les obligations applicables et les modalités avant tout essai avec données réelles |
| P1 | Offres : publication validée, cycle de vie incomplet | Arbitrer refus, correction, expiration, doublons et revalidation après modification |
| P1 | Permissions : principes validés, cas limites ouverts | Matrice rôle + établissement + propriétaire + demande + type de donnée ; annulation, réorientation et fin d'accès au CV |
| P1 | Suivi : états validés, transitions ouvertes | Définir transitions, correction d'erreur, sans réponse, retrait après entretien et signification d'acceptée |
| P1 | Rendez-vous et progression : nominal défini, exceptions ouvertes | Réorientation, absence de réponse, annulations répétées et responsabilité des prochaines actions |
| P1 | Évaluation : seuils validés, protocole ouvert | Définir tâche, aide admise, durée, participants effectivement évalués, absences et référence avant usage |
| P1 | Pilotage : indicateurs validés, calculs et visibilité ouverts | Réutiliser les événements des parcours, éviter une saisie parallèle et l'exposition des observations confidentielles |

Les P0/P1 ci-dessus sont des recommandations, pas une modification du workflow validée. L'audit ne prouve aucune non-conformité juridique. Les références légales du texte fourni doivent être vérifiées auprès de sources officielles avant d'en tirer des prescriptions ; aucune formalité précise n'est affirmée comme applicable ici.

## 2. Trois parcours de bout en bout à spécifier

Les scénarios relient les décisions existantes ; les comportements des exceptions ci-dessous restent des propositions à arbitrer.

### A — Apprenant : trouver une opportunité et suivre sa démarche

Nominal : inscription → rattachement validé → consultation d'une offre validée → préparation avec checklist/CV → envoi externe → enregistrement de l'état, date et prochaine action → suivi jusqu'au résultat. Demande d'accompagnement possible.

| Situation d'échec | Réponse proposée, à valider |
|---|---|
| Compte en attente | Expliquer l'attente sans exposer les données internes (principe D038 déjà validé) |
| Aucune offre adaptée | Expliquer l'absence de résultat ; proposer la recherche d'entreprise/candidature spontanée si ce parcours est disponible ; ne pas inventer d'offre |
| Offre expirée pendant la préparation | Signaler l'expiration et conserver le suivi déjà créé ; vérifier le canal source avant envoi |
| Candidature vers une entreprise absente de la liste | Permettre la démarche personnelle sans publication automatique de l'entreprise ; décision à prendre |

Preuve attendue : l'apprenant accomplit une tâche définie ; pertinence déclarée et compatibilité des conditions connues consignées séparément. Une information inconnue ne devient pas « compatible » par défaut.

### B — CME : publier une offre utile puis accompagner

Nominal : réception d'une proposition/collecte → examen de la source et des conditions → décision de publication → consultation du suivi des candidatures → traitement de l'accompagnement relevant de son rôle.

| Situation d'échec | Réponse proposée, à valider |
|---|---|
| Offre incomplète | Demander une correction avec motif, plutôt que laisser une attente inexpliquée |
| Doublon ou offre manifestement inadaptée | Écarter avec motif et référence à l'offre existante si nécessaire |
| Stock dépassant la capacité | Prioriser et ajuster le volume de collecte après observation ; pas de publication sans validation |
| Modification d'une offre publiée | Définir les changements nécessitant revalidation et le sort des candidatures existantes |

Preuve attendue : mesurer temps de traitement, entrées, sorties et ancienneté du stock. Aucun engagement de délai n'est actuellement validé.

### C — Responsable technique : traiter une demande et assurer la continuité

Nominal : demande adressée par l'apprenant → acceptation → date convenue → rendez-vous saisi → réalisation/présence → bilan propre à l'accompagnant et retour propre à l'apprenant → prochaine action → revue de progression.

| Situation d'échec | Réponse proposée, à valider |
|---|---|
| Indisponibilité ou autre spécialité | Demande de réorientation (principe validé) ; préciser qui choisit le nouveau destinataire et les accès de l'ancien |
| Aucune réponse | Définir un délai indicatif et un recours sans attribuer automatiquement un retard sans échéance |
| Annulation ou absence | Conserver une trace et proposer un nouvel horaire ; préciser auteur du changement et absence de quel participant |
| Fin de l'accompagnement | Définir le retrait ou maintien limité de l'accès au CV, sans élargir l'accès aux autres bilans |

Preuve attendue : parcours complet et refus des accès par un autre responsable, un autre apprenant ou un autre établissement.

## 3. Découpage proposé en tranches testables

Ce découpage respecte l'ordre général D032. Le placement du tableau D045 et de la prospection reste à valider ; aucune fonction n'est retirée du pilote par ce document.

| Tranche proposée | Minimum utile proposé | Valeur / vérification |
|---|---|---|
| Exploration préalable, sans application | Échantillon d'offres réelles, conditions des sources et chronométrage de validation ; aucun CV réel nécessaire | Vérifier utilité et capacité ; décider des sources, pas seulement des interfaces techniques |
| 1 — Découvrir | Accès/rattachement et isolation nécessaires, contributions, collecte ciblée faisable, validation CME, consultation d'offres | Un apprenant trouve une opportunité adaptée ; seuls les comptes autorisés voient les offres publiées |
| 2 — Candidater | CV privé, portfolio par lien, checklist, brouillon, envoi externe, états et prochaine action | Démarche suivie sans exposer le CV ; distinguer offre et candidature spontanée |
| 3 — Être accompagné | Demande, choix du responsable, rendez-vous, observations séparées, actions de progression | Accompagnement jusqu'au bilan avec permissions vérifiées |
| 4 — Piloter | Tableau porteur D045 à partir des données existantes, filtre et échéances, sans contenu confidentiel | Repérer une action à traiter sans nouvelle saisie administrative ni ouverture des bilans |

Le statut opérationnel nécessaire à chaque tranche reste visible dès cette tranche ; la proposition de tranche 4 concerne le tableau transversal du porteur, pas la suppression des listes de travail CME/responsable.

Pour chaque tranche : spécification Proposed, règles/permissions arbitrées, architecture et stack décidées ensemble avant implémentation, vérification réelle, tests pertinents, revue et synchronisation. Aucun critère Accepted par ce document.

## 4. Évaluation et arbitrages à discuter

- D035 conservée : autonomie 80 %, utilité 70 %. Définir le dénominateur et documenter absences/abandons ; le petit échantillon guide le pilote, sans démontrer un taux identique pour tout l'établissement.
- Proposition : relever la méthode actuelle, le temps de recherche et les opportunités pertinentes avant expérimentation ; définir une observation comparable après.
- Proposition : commencer par la preuve de valeur de la découverte, priorité déjà exprimée mais non validée comme nouvelle gouvernance.
- Proposition de l'audit : distinguer cohérence de la vision et autorisation de construire une tranche. Ne pas adopter cette séparation sans validation utilisateur ; D007 inchangée.
- Question stratégique ouverte : si la collecte automatique ne fournit rien d'utile, continuer temporairement avec contributions humaines ou revoir le périmètre ? Ne pas abandonner l'automatisation sans décision explicite.

Prochain petit groupe de questions recommandé : priorité de la première preuve de valeur et responsable/structure portant les données du pilote. Les sources peuvent être étudiées en parallèle de ces réponses, sans utiliser de données personnelles réelles.
