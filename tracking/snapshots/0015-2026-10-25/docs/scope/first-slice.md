# Première tranche — proposer, valider et consulter des offres

Mise à jour : 25 octobre 2026. Statut : périmètre fondé sur D053–D054, modération D061, clôture/modifications D068, informations/qualification D070, consultation D071 et traitement manuel des propositions en doublon D072 validés ; règles complémentaires non arbitrées ci-dessous Proposed. D007 encore en attente. Aucune stack ni architecture technique choisie.

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

Les quatre états et le cycle correction/rejet ont été validés explicitement par D061, puis clôture/modifications D068, informations/qualification D070, consultation D071 et propositions en doublon D072. Les autres propositions restent ouvertes ; autres droits, formats/limites des champs et transitions restantes à préciser.

## Limites de cette première tranche

Préparation/CV et suivi des candidatures, demandes d'accompagnement, rendez-vous/progression et tableau transversal restent dans les fonctions principales à réaliser progressivement ; pas supprimés. Leur disponibilité dans les tranches suivantes ne doit pas être annoncée comme déjà réalisée. Liste d'entreprises à enrichir conservée ; position précise à définir. Prototype de collecte séparé, sans fournisseur ni langage choisis.

## Vérifications à prévoir, preuves applicatives absentes

- Compte en attente : aucune offre interne accessible ; compte rattaché : offres publiées de son établissement, plus ses propres propositions selon D071 ; CME avec ses droits de modération.
- Un contributeur ne peut pas publier directement ni usurper le rôle CME.
- Aucune proposition non validée visible par les autres membres non auteurs et sans droit CME, même par URL directe ou affectation à la même classe (D071).
- Refus de tout accès inter-établissements avec un identifiant connu.
- Cycle de correction et motif selon D061 ; clôture/réouverture, versions, retrait temporaire et continuité des suivis selon D068.
- Exigences bac+5 et accessibilité inconnue affichées sans promesse d'éligibilité.
- D070 : informations minimales exigées à la soumission ; texte avec provenance accepté sans URL ; inconnues de qualification explicites ; publication refusée sans moyen de candidature exploitable, sans bloquer la soumission initiale pour ce seul manque. Détail dans offer-lifecycle.md.
- D072 : doublon confirmé manuellement par CME rejeté avec motif ; référence de l'offre existante seulement si accès autorisé ; aucun suivi de candidature supprimé/fusionné automatiquement. Cas de doublons déjà publiés à préciser.

## Prochaine étape

Consolider les droits, champs et critères restants de la première tranche (C09), puis soumettre le périmètre à validation avant comparaison de stack et spécifications d'architecture. Pas de code applicatif avant ces décisions. Portage officiel et responsabilités pour les données réelles toujours non confirmés.
