# Première tranche — proposer, valider et consulter des offres

Date : 24 octobre 2026. Statut : périmètre fondé sur D053–D054 ; règles complémentaires ci-dessous Proposed. D007 encore en attente. Aucune stack ni architecture technique choisie.

## Résultat utilisateur

Un membre rattaché propose une offre ; la CME de son établissement l'examine et, si elle la valide, les apprenants rattachés peuvent la consulter avec les exigences et incertitudes clairement indiquées. Cette tranche mutualise et qualifie la recherche humaine, sans promettre un gain de collecte automatique.

## Éléments déjà validés à inclure

- Invitation par classe (D059) : lien partagé généré par CME, compte individuel ou connexion existante, demande de rattachement puis validation CME avant accès interne ; lien expirant, désactivable et renouvelable, aucun rôle privilégié ni changement de classe automatique.

- Inscription ouverte, rôle apprenant par défaut, attente du rattachement validé par l'administrateur ; changement de rôle sur demande par ce dernier (D038–D039).
- Proposition d'offre par apprenants et personnel, lien ou texte avec provenance, entreprise, intitulé, type (D031–D032).
- Validation par CME avant visibilité aux apprenants de l'établissement (D028).
- Mention explicite des conditions inconnues d'accessibilité et du niveau demandé, y compris bac+5, sans prétendre l'apprenant éligible (D029, D052).
- Permissions et séparation des établissements ; administration des comptes distincte de l'accès aux contenus confidentiels.

## Règles proposées à valider avant spécification

Approfondissement du cycle, des transitions, de la disponibilité et des vérifications dans docs/scope/offer-lifecycle.md (Proposed, demandé le 24 octobre 2026). La demande d'explication ne vaut pas validation.
Proposition finale C07 préparée le 25 octobre : clôture/réouverture par CME, modifications contrôlées, versions et suivis préservés, retrait temporaire si doute sérieux et contrôles spécifiques. Voir section finale de offer-lifecycle.md ; accord utilisateur encore attendu avant décision ou implémentation.

| Sujet | Proposition | État |
|---|---|---|
| États de modération | En attente, à corriger, publiée, rejetée ; décision par CME | Validé D061 |
| Visibilité avant publication | CME et auteur consultent la proposition ; les autres apprenants ne la voient pas | Proposed pour l'accès auteur ; invisibilité collective avant publication déjà validée |
| Correction / rejet | Motif communiqué à l'auteur ; correction par l'auteur puis retour en attente de validation | Validé D061 |
| Modification après publication | Modification du contenu par la CME pour cette première tranche ; le contributeur signale une correction plutôt que modifier directement l'offre publiée | Proposed |
| Fin de recrutement | Offre marquée clôturée et retirée de la liste des offres ouvertes, sans suppression des liens de suivi ultérieurs | Proposed ; disponibilité distincte de modération |
| Informations absentes | Champs de qualification inconnus affichés « à confirmer », sans inventer date, niveau, durée ou accès géographique | Proposed comme règle générale ; géographie déjà encadrée par D029 |

Les quatre états et le cycle correction/rejet ont été validés explicitement par D061 après approfondissement, pas déduits de D054. Les autres propositions restent ouvertes ; transitions et champs obligatoires précis à spécifier.

## Limites de cette première tranche

Préparation/CV et suivi des candidatures, demandes d'accompagnement, rendez-vous/progression et tableau transversal restent dans les fonctions principales à réaliser progressivement ; pas supprimés. Leur disponibilité dans les tranches suivantes ne doit pas être annoncée comme déjà réalisée. Liste d'entreprises à enrichir conservée ; position précise à définir. Prototype de collecte séparé, sans fournisseur ni langage choisis.

## Vérifications à prévoir, encore proposées

- Compte en attente : aucune offre interne accessible ; compte rattaché : offres publiées de son établissement uniquement.
- Un contributeur ne peut pas publier directement ni usurper le rôle CME.
- Aucune proposition non validée visible par les autres apprenants, même par URL directe.
- Refus de tout accès inter-établissements avec un identifiant connu.
- Cycle de correction et motif vérifiés après validation de leurs règles.
- Exigences bac+5 et accessibilité inconnue affichées sans promesse d'éligibilité.

## Prochaine étape

Trancher le petit groupe de règles de modération/fin de recrutement, consolider le périmètre pour validation, puis comparer la stack et écrire les spécifications d'architecture. Pas de code applicatif avant ces décisions. Portage officiel et responsabilités pour les données réelles toujours non confirmés.
