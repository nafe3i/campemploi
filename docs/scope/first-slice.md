# Première tranche — proposer, valider et consulter des offres

Mise à jour : 25 octobre 2026. Statut : périmètre fondé sur D053–D054, modération D061 et clôture/modifications D068 validées ; règles complémentaires non arbitrées ci-dessous Proposed. D007 encore en attente. Aucune stack ni architecture technique choisie.

## Résultat utilisateur

Un membre rattaché propose une offre ; la CME de son établissement l'examine et, si elle la valide, les apprenants rattachés peuvent la consulter avec les exigences et incertitudes clairement indiquées. Cette tranche mutualise et qualifie la recherche humaine, sans promettre un gain de collecte automatique.

## Éléments déjà validés à inclure

- Invitation par classe (D059) : lien partagé généré par CME, compte individuel ou connexion existante, demande de rattachement puis validation CME avant accès interne ; lien expirant, désactivable et renouvelable, aucun rôle privilégié ni changement de classe automatique.

- Inscription ouverte, rôle apprenant par défaut, attente du rattachement validé par l'administrateur ; changement de rôle sur demande par ce dernier (D038–D039).
- Proposition d'offre par apprenants et personnel, lien ou texte avec provenance, entreprise, intitulé, type (D031–D032).
- Validation par CME avant visibilité aux apprenants de l'établissement (D028).
- Mention explicite des conditions inconnues d'accessibilité et du niveau demandé, y compris bac+5, sans prétendre l'apprenant éligible (D029, D052).
- Permissions et séparation des établissements ; administration des comptes distincte de l'accès aux contenus confidentiels.

## Règles validées et propositions à trancher avant spécification

Approfondissement du cycle, des transitions, de la disponibilité et des vérifications dans docs/scope/offer-lifecycle.md. La demande initiale d'explication ne valait pas validation.
Proposition finale C07 explicitement validée le 25 octobre (D068) : clôture/réouverture par CME, modifications contrôlées, versions et suivis préservés, retrait temporaire si doute sérieux et contrôles spécifiques. Voir section finale de offer-lifecycle.md. Décision documentée, fonctionnalité non développée.

| Sujet | Proposition | État |
|---|---|---|
| États de modération | En attente, à corriger, publiée, rejetée ; décision par CME | Validé D061 |
| Visibilité avant publication | CME et auteur consultent la proposition ; les autres apprenants ne la voient pas | Proposed pour l'accès auteur ; invisibilité collective avant publication déjà validée |
| Correction / rejet | Motif communiqué à l'auteur ; correction par l'auteur puis retour en attente de validation | Validé D061 |
| Modification après publication | CME seule modifie/confirme ; signalement par contributeur, version des conditions et mention dans les suivis ; retrait temporaire si doute sérieux | Validé D068 ; conservation détaillée à spécifier |
| Fin de recrutement | Disponibilité distincte ; CME clôture/rouvre avec trace ; retrait de la recherche courante, suivis existants conservés, sans refus automatique | Validé D068 ; échéance dépassée à vérifier par CME |
| Informations absentes | Champs de qualification inconnus affichés « à confirmer », sans inventer date, niveau, durée ou accès géographique | Proposed comme règle générale ; géographie déjà encadrée par D029 |

Les quatre états et le cycle correction/rejet ont été validés explicitement par D061, puis clôture et modifications par D068. Les autres propositions restent ouvertes ; transitions et champs obligatoires précis à spécifier.

## Limites de cette première tranche

Préparation/CV et suivi des candidatures, demandes d'accompagnement, rendez-vous/progression et tableau transversal restent dans les fonctions principales à réaliser progressivement ; pas supprimés. Leur disponibilité dans les tranches suivantes ne doit pas être annoncée comme déjà réalisée. Liste d'entreprises à enrichir conservée ; position précise à définir. Prototype de collecte séparé, sans fournisseur ni langage choisis.

## Vérifications à prévoir, preuves applicatives absentes

- Compte en attente : aucune offre interne accessible ; compte rattaché : offres publiées de son établissement uniquement.
- Un contributeur ne peut pas publier directement ni usurper le rôle CME.
- Aucune proposition non validée visible par les autres apprenants, même par URL directe.
- Refus de tout accès inter-établissements avec un identifiant connu.
- Cycle de correction et motif selon D061 ; clôture/réouverture, versions, retrait temporaire et continuité des suivis selon D068.
- Exigences bac+5 et accessibilité inconnue affichées sans promesse d'éligibilité.

## Prochaine étape

Consolider les droits, champs et critères restants de la première tranche (C09), puis soumettre le périmètre à validation avant comparaison de stack et spécifications d'architecture. Pas de code applicatif avant ces décisions. Portage officiel et responsabilités pour les données réelles toujours non confirmés.
