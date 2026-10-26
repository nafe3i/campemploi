# Première tranche — proposer, valider et consulter des offres

Mise à jour : 26 octobre 2026. Statut : règles référencées D053–D054, D061, D068, D070–D073 et D075–D077 validées ; consolidation documentaire C09 terminée et scope global D007 validé. Détails restant à spécifier signalés ci-dessous. Stack et architecture générale validées D008, Docker retenu D088 ; détails techniques à préciser, aucun code.

## Résultat utilisateur

Un membre rattaché propose une offre ; la CME de son établissement l'examine et, si elle la valide, les apprenants rattachés peuvent la consulter avec les exigences et incertitudes clairement indiquées. Cette tranche mutualise et qualifie la recherche humaine, sans promettre un gain de collecte automatique.

## Éléments déjà validés à inclure

- Invitation par classe (D059) : lien partagé généré par CME, compte individuel ou connexion existante, demande de rattachement puis validation CME avant accès interne ; lien expirant, désactivable et renouvelable, aucun rôle privilégié ni changement de classe automatique.

- Inscription ouverte, rôle apprenant par défaut, attente du rattachement validé par l'administrateur ; changement de rôle sur demande par ce dernier (D038–D039).
- Proposition d'offre par apprenants et personnel, lien ou texte avec provenance, entreprise, intitulé, type (D031–D032).
- D070 : soumission avec intitulé, entreprise, type et lien source ou texte accompagné de sa provenance. Avant publication, qualification CME du lieu/mode, compétences/niveau et durée/début des stages selon les informations disponibles ; inconnues explicites. Moyen exploitable de candidature requis avant publication, sinon correction demandée selon D061.
- Validation par CME avant visibilité collective aux apprenants de l'établissement (D028) ; consultation individuelle de l'auteur précisée par D071.
- Mention explicite des conditions inconnues d'accessibilité et du niveau demandé, y compris bac+5, sans prétendre l'apprenant éligible (D029, D052).
- Permissions et séparation des établissements ; administration des comptes distincte de l'accès aux contenus confidentiels.
- Consultation D071 : auteur rattaché sur ses propres propositions, état et motifs de correction/rejet ; CME sur les propositions de son établissement. Autres membres : attendre publication, sans droit supplémentaire lié à la classe.

## Règles validées et propositions à trancher avant spécification

Approfondissement du cycle, des transitions, de la disponibilité et des vérifications dans docs/scope/offer-lifecycle.md. La demande initiale d'explication ne valait pas validation.
Proposition finale C07 explicitement validée le 25 octobre (D068) : clôture/réouverture par CME, modifications contrôlées, versions et suivis préservés, retrait temporaire si doute sérieux et contrôles spécifiques. Voir section finale de offer-lifecycle.md. Décision documentée, fonctionnalité non développée.

| Sujet | Proposition | État |
|---|---|---|
| États de modération | En attente, à corriger, publiée, rejetée ; décision par CME | Validé D061 |
| Visibilité avant publication | Auteur sur ses propositions, état et motifs ; CME sur celles de son établissement ; autres membres attendent publication | Validé D071 ; pas de droit de publication déduit |
| Correction / rejet | Motif communiqué à l'auteur ; correction par l'auteur puis retour en attente de validation | Validé D061 |
| Modification après publication | CME seule modifie/confirme ; signalement par contributeur, version des conditions et mention dans les suivis ; retrait temporaire si doute sérieux | Validé D068 ; conservation détaillée à spécifier |
| Fin de recrutement | Disponibilité distincte ; CME clôture/rouvre avec trace ; retrait de la recherche courante, suivis existants conservés, sans refus automatique | Validé D068 ; échéance dépassée à vérifier par CME |
| Informations de soumission | Intitulé, entreprise, type et lien source ou texte avec provenance | Validé D070 ; formats et limites à spécifier |
| Qualification et informations absentes | CME renseigne les conditions disponibles ; absences explicites « non précisé » ou « à confirmer », sans invention | Validé D070 ; géographie D029 et niveau D052 conservés |
| Moyen de candidature | Page, adresse professionnelle publiée ou instructions exploitables nécessaires avant publication ; correction si absent | Validé D070 ; présence du seul lien source insuffisante |
| Proposition en doublon | Vérification manuelle CME ; une seule offre au catalogue, proposition répétée rejetée avec motif « déjà présente » ; référence existante seulement si consultable par l'auteur | Validé D072 ; aucun suivi supprimé/fusionné automatiquement |
| Réexamen après rejet | CME seule remet à corriger avec motif si nouveaux éléments ; auteur corrige puis retour en attente ; rejet initial conservé | Validé D073 ; aucune réouverture autonome ni publication automatique |
| Retrait demandé avant publication | Auteur demande à CME ; CME rejette avec motif « retrait demandé par l'auteur », proposition et historique conservés | Validé D075 ; pas de suppression ni nouvel état ; après publication, clôture D068 |
| Administration pilote | Premier établissement/CME et gestion locale nécessaire ; écrans complets multi-établissements ultérieurs | Validé D076 ; isolation dès conception |
| Doublon déjà publié | CME clôture la répétition avec motif « doublon », garde la référence et les suivis à leur offre d'origine | Validé D077 ; aucune fusion/suppression/modification automatique |

Les quatre états et le cycle correction/rejet ont été validés explicitement par D061, puis clôture/modifications D068 et compléments D070–D073/D075. Les autres propositions restent ouvertes ; autres droits, formats/limites des champs et transitions restantes à préciser.

## Synthèse de consolidation C09 — 25 octobre 2026

Synthèse préparée à la demande de poursuivre le travail, puis deux arbitrages explicitement validés (« je valides les deux propositions »), enregistrés D076/D077. Les références ci-dessous identifient les exigences validées. Consolidation C09 documentaire terminée ; aucune fonctionnalité développée ou Accepted. D007 reste ouverte.

### Parcours à couvrir selon les décisions acquises

1. Préparer le premier établissement, sa CME, les classes, invitations/rattachements et rôles nécessaires au pilote selon D056/D059/D076 ; écrans complets multi-établissements reportés, isolation requise dès la conception.
2. Permettre une contribution humaine avec les informations de D070 ; l'auteur suit sa proposition selon D071.
3. Faire examiner la proposition par CME : publier, demander correction ou rejeter avec motif (D061), qualifier les conditions et le moyen de candidature (D070).
4. Consulter les offres publiées de son établissement avec exigences et inconnues explicites (D029/D052/D071).
5. Traiter signalements, modifications, versions, disponibilité, clôture/réouverture et retrait temporaire (D068).
6. Traiter propositions répétées, réexamen après rejet et retrait demandé avant publication (D072/D073/D075).

D086 fixe leur placement : CV/portfolio, revues, préparation/suivi et liste d'entreprises en tranche 2 ; accompagnement, rendez-vous/progression et tableau transversal en tranche 3. Ces blocs ne deviennent pas des écrans de la tranche 1. La conservation des liens de candidatures D068 est une contrainte d'intégration, pas une annonce que leur parcours est développé ou inclus maintenant.

### Matrice de consultation et d'action — synthèse des droits acquis

| Acteur | Consulter | Agir | Limites |
|---|---|---|---|
| Compte en attente de rattachement | Aucune donnée interne | Demande de rattachement selon D059 | Lien de classe seul insuffisant |
| Apprenant/personnel rattaché | Offres publiées de son établissement ; ses propositions/états/motifs | Soumettre, corriger après retour, signaler, demander retrait de sa proposition | Ni modération directe, ni propositions non publiées d'autrui |
| CME du même établissement | Propositions et offres de son établissement | Modérer, qualifier, modifier, clôturer/rouvrir, autoriser réexamen et traiter retrait | Motifs et règles D061/D068/D070–D075 ; pas de droit inter-établissements |
| Formateur affecté à une classe | Droits de contribution ci-dessus ; aucun accès supplémentaire aux propositions de la classe | Contribuer sans modérer par son seul rôle formateur | Revue CV/portfolio D058 distincte de modération des offres |
| Administrateur général/local | Aucun accès métier supplémentaire déduit du rôle administratif | Administration dans son périmètre D056 | CME/administration locale distinctes, cumul possible |

La matrice résume les décisions ; elle ne règle pas les effets des changements de classe/établissement ou des comptes désactivés. Ces cas devront être spécifiés avant exposition du parcours concerné, sans ouverture d'accès implicite.

### Critères vérifiables issus des règles validées — preuves à produire

| Critère | Vérification attendue avant acceptation |
|---|---|
| Accès limité | Compte en attente, autre établissement, URL directe et changement d'identifiant : refus sans contenu interne exposé ni modification |
| Contribution exploitable | Champs minimaux exigés ; lien source ou texte/provenance ; auteur voit état et motifs, autres membres attendent publication |
| Qualification CME | Publication impossible sans moyen de candidature exploitable ; inconnues explicites, bac+5 et écart affichés sans éligibilité inventée |
| Modération correcte | Motif de correction/rejet, correction puis nouvelle attente ; auteur ne publie ni ne rouvre seul ; CME respecte son établissement |
| Exceptions tracées | Doublon de proposition, réexamen et retrait demandé suivent D072/D073/D075 ; motifs et historique conservés |
| Disponibilité et versions | Clôture sort de la recherche courante ; réouverture vérifiée ; conditions modifiées confirmées et retrait temporaire selon D068 |
| Échec et répétition | Actions répétées/concurrentes ne produisent ni publication multiple ni écrasement silencieux ; modalités à spécifier selon D060 |

Ces critères sont des exigences de vérification, pas des tests exécutés ni une spécification technique Accepted. Le plan de tests précis, formats/limites des entrées, activation/récupération des comptes, expiration et changements de rattachement seront définis en spécification avant développement des parcours concernés. Les critères de réussite du pilote D035 (autonomie, utilité, charge, accompagnement) restent à mesurer sur leur périmètre ; ils ne sont pas tous des critères de sortie de cette seule tranche.

### Deux arbitrages de périmètre — Validés D076/D077

**A — Étendue de l'administration du pilote, D076.** Inclure la mise en place du premier établissement et de sa CME par l'administrateur général, puis classes, invitations/rattachements et rôles nécessaires par la CME avec permission locale. Reporter les écrans complets de gestion simultanée de plusieurs établissements ; isolation et séparation des rôles exigées dès la conception. D056 n'est pas supprimée. Modalité de création initiale à comparer en architecture, sans choix technique à ce stade.

**B — Doublons découverts après publication, D077.** La CME conserve l'offre de référence et clôture l'offre répétée avec un motif explicite « doublon », sans prétendre que le recrutement est terminé. Les suivis restent liés à leur offre d'origine ; aucune fusion, suppression ou modification automatique de candidature. Référence vers l'offre conservée seulement si consultation autorisée. D077 complète D072 pour le cas déjà publié et D068 pour le motif de clôture.

Deux décisions enregistrées, périmètre et synthèses réalignés ; détails techniques à spécifier avant développement. Vérifications spécifiques à prévoir : administration locale sans accès inter-établissements ou confidentiel automatique ; doublon publié clôturé avec motif exact, sorti de la recherche courante, suivis inchangés et référence visible seulement si autorisée. Aucune preuve applicative. D007, cadre des données réelles et protocole du pilote demeurent ouverts ; cet accord ne vaut pas leur validation.

## Limites de cette première tranche

D086 : CV/portfolio et revues, préparation/suivi et liste d'entreprises en tranche 2 ; accompagnement, rendez-vous/progression et tableau en tranche 3. Ces fonctions restent à réaliser et ne sont pas déjà disponibles. Prototype de collecte séparé, sans fournisseur ni langage choisis, indépendant de la première tranche.

## Vérifications à prévoir, preuves applicatives absentes

- Compte en attente : aucune offre interne accessible ; compte rattaché : offres publiées de son établissement, plus ses propres propositions selon D071 ; CME avec ses droits de modération.
- Un contributeur ne peut pas publier directement ni usurper le rôle CME.
- Aucune proposition non validée visible par les autres membres non auteurs et sans droit CME, même par URL directe ou affectation à la même classe (D071).
- Refus de tout accès inter-établissements avec un identifiant connu.
- Cycle de correction et motif selon D061 ; clôture/réouverture, versions, retrait temporaire et continuité des suivis selon D068.
- Exigences bac+5 et accessibilité inconnue affichées sans promesse d'éligibilité.
- D070 : informations minimales exigées à la soumission ; texte avec provenance accepté sans URL ; inconnues de qualification explicites ; publication refusée sans moyen de candidature exploitable, sans bloquer la soumission initiale pour ce seul manque. Détail dans offer-lifecycle.md.
- D072 : proposition en doublon confirmée manuellement par CME rejetée avec motif ; D077 : doublon déjà publié clôturé avec motif « doublon ». Référence de l'offre conservée seulement si accès autorisé ; aucun suivi supprimé/fusionné ou changé automatiquement.
- D073 : réexamen autorisé uniquement par CME du même établissement avec motif ; auteur ne rouvre pas seul ; après correction retour en attente ; rejet initial conservé. Vérifier aussi absence de motif et accès inter-établissements.
- D075 : auteur sur sa propre demande de retrait avant publication ; rejet motivé par CME seulement, données conservées ; refus d'accès d'autrui et autre établissement ; si déjà publiée, clôture D068. Détails de demande/concurrence à spécifier.

## Prochaine étape

Consolidations C08/C09 documentaires terminées, ordre des trois tranches validé D086 et accord global D007 obtenu le 26 octobre 2026. Phase Architecture : stack et architecture générale validées D008, Docker retenu D088 ; détails techniques puis spécifications des parcours concernés avant développement. Portage officiel, responsabilités des données et protocole d'essais réels toujours à préciser avant ces essais.
