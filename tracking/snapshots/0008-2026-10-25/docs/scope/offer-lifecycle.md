# Cycle de vie des offres — règles validées et propositions restantes

Mise à jour : 25 octobre 2026. Statut : partiellement validé. D061 valide le parcours nominal ; D068 valide disponibilité, clôture/réouverture et modifications après publication, selon la section finale ci-dessous. Les autres propositions restent Proposed. Références : D028–D032, D052–D054, D060–D061 et D068. Aucun code ni choix technique.

## Deux dimensions

Modération : en attente, à corriger, publiée, rejetée (D061). Disponibilité : ouverte, clôturée, à confirmer ; séparation conceptuelle validée D068, sans préjuger du schéma de base de données.
« Publiée » signifie autorisée à être vue, pas emploi encore ouvert. « Ouverte » reste une observation de la source, pas garantie d'embauche. Sans information suffisante, ne pas inventer une date de clôture ou une ouverture confirmée.

## Responsabilités proposées

Auteur rattaché : soumet une offre, consulte ses propositions, corrige après retour et signale une correction/clôture après publication. Ne peut pas publier par lui-même en tant que contributeur.
CME du même établissement : examine, demande correction, publie ou rejette avec motif, corrige le contenu publié et enregistre la clôture. Une CME peut contribuer ; son droit de publication provient de son rôle CME, avec acte de validation explicite. Pas de second valideur indépendant imposé par les décisions actuelles.
Autres apprenants rattachés : consultent les offres publiées de leur établissement, pas les propositions en attente, à corriger ou rejetées.
Administrateur général : pas de droit de validation d'offre automatiquement déduit de l'administration technique.

## Parcours et transitions proposés

| Départ | Action et acteur | Arrivée | Condition / résultat |
|---|---|---|---|
| Nouvelle proposition | Soumettre, contributeur | En attente | Source/provenance, entreprise, intitulé et type ; validation minimale des champs |
| En attente | Demander correction, CME | À corriger | Commentaire expliquant l'information ou correction attendue |
| À corriger | Corriger et soumettre, auteur | En attente | Nouvelle lecture CME nécessaire ; pas de publication automatique |
| En attente | Publier, CME | Publiée | Examen du contenu et signalement des incertitudes ; choix explicite |
| En attente | Rejeter, CME | Rejetée | Motif expliqué à l'auteur |
| Publiée | Signaler correction, utilisateur autorisé | Publiée, signalement à traiter | Signaler ne remplace pas le contenu validé |
| Publiée | Corriger et confirmer, CME | Publiée | Trace et version selon D068 ; source et incertitudes mises à jour |
| Publiée / disponibilité ouverte ou incertaine | Constater fin, CME | Publiée / clôturée | Source ou motif de clôture enregistré ; hors liste des offres ouvertes |

Proposition : pas de réouverture autonome d'un rejet par l'auteur ; une nouvelle soumission pourra être décidée après échange. Corrections après rejet et retrait d'une proposition par l'auteur restent à arbitrer. Le retrait temporaire pour doute sérieux est désormais validé D068, selon la section finale. Rien n'impose un état brouillon sauvegardé dans cette première version.

## Informations et travail de la CME proposés

Afficher ensemble : lien/provenance, entreprise, intitulé/type, lieu/mode de travail, niveau demandé, compétences, durée/début/échéance quand connus et disponibilité observée. Champs de qualification inconnus signalés sans bloquer systématiquement la soumission. Niveau demandé bac+5 conservable et publiable avec écart signalé (D052). Accessibilité depuis le Maroc inconnue publiable après validation avec mention explicite (D029). Qualification ne doit pas inventer le consentement de l'entreprise à d'autres profils.

Liste de travail CME : propositions en attente, date de soumission, auteur et éléments manquants. Détail/commentaire/action accessibles sans ouvrir tous les dossiers apprenants. Temps de traitement et ancienneté du stock mesurables à terme ; aucun délai garanti ni alerte automatique décidé.

Historique : auteur, date, motif et versions utiles validés D068 pour clôture/réouverture/modifications. Extension aux autres actions et visibilité détaillée des traces à préciser ; pas de collecte intégrale inutile de données ni de copie de toute annonce par défaut. La validation de la CME n'est pas une certification juridique ou une garantie de fiabilité de l'employeur.

## Cas limites et vérifications proposés

- Doublon : montrer la correspondance et relier au contenu existant après examen CME ; ne pas fusionner sur le seul intitulé ni activer un dédoublonnage complexe sans décision.
- Lien inaccessible : proposer une provenance et un texte utile ; statut à corriger ou vérification supplémentaire selon décision CME, pas fausse ouverture.
- Annonce expirée avant publication : ne pas la proposer comme recrutement ouvert ; conservation comme référence ou rejet à arbitrer.
- Date limite explicite dépassée : signalement à vérifier et confirmation CME de la clôture validés D068 ; toujours distinguer date limite de candidature et date de début.
- Retrait d'une offre publiée : conserver le suivi des candidatures existantes ; ne pas transformer automatiquement une candidature en refusée.
- Modification importante : CME contrôle/confirme la nouvelle version ; mention dans le suivi existant validée D068, sans notification externe imposée.
- Double clic ou décision concurrente : éviter deux publications ou un écrasement silencieux ; détails techniques après architecture.
- Accès : contrôler côté serveur compte/rattachement, rôle CME, établissement et propriété de la proposition à chaque action ; tester aussi URL directe et tentative de changement d'identifiant.
- Expiration d'une invitation ne supprime pas un compte déjà validé ; les cycles de vie sont distincts.

## Clôture et modification — 25 octobre 2026 — Validé D068

Cette section précise les lignes précédentes pour C07. Proposition présentée puis explicitement validée par l'utilisateur : « oui on vat suivre cette approche ». D068 complète D061 ; les autres propositions du document ne sont pas automatiquement validées.

### Disponibilité distincte de la modération

Conserver modération (en attente/à corriger/publiée/rejetée) et disponibilité (ouverte/clôturée/à confirmer) séparées. Le lieu, niveau, durée et accès géographique restent des conditions distinctes. Une offre peut être publiée et clôturée ; elle n'est pas rejetée par la CME pour ce seul motif. Une date limite de candidature n'est pas une date de début de stage.

### Clôturer

- La CME du même établissement peut clôturer une offre publiée ; enregistrer auteur, date et motif, avec source/preuve lorsqu'elle est disponible. Exemples : recrutement terminé, annonce retirée, échéance confirmée.
- Apprenant/formateur rattaché peut signaler une fermeture, sans modifier directement la disponibilité. Pas d'accès supplémentaire aux dossiers d'autres candidats.
- Une offre clôturée sort de la recherche courante d'opportunités et reste dans le suivi personnel des candidatures existantes, avec une mention de clôture. Les états, notes et prochaines actions des candidatures sont conservés ; aucun refus automatique.
- La plateforme ne propose plus d'initier une nouvelle candidature depuis cette offre clôturée ; cette limite d'interface ne prétend pas empêcher une démarche externe ni ne modifie les droits sur les suivis existants. Saisie rétrospective d'une candidature déjà envoyée avant clôture à spécifier avec le parcours candidatures.
- Une échéance explicite dépassée est signalée « échéance dépassée — à vérifier » ; la CME confirme la clôture. Pas de clôture automatique sur une date déduite, une ancienneté arbitraire ou un lien momentanément inaccessible. La liste ne doit pas présenter l'offre comme certainement ouverte sur cette seule base.
- Réouverture uniquement par CME, après nouvelle vérification de la même opportunité, avec motif/date et conditions actualisées. Une nouvelle campagne/poste distinct donne lieu à une nouvelle offre ; pas de réutilisation silencieuse du suivi des anciens candidats.

### Modifier après publication

- L'auteur, l'apprenant et le formateur signalent une correction ; seule la CME modifie et confirme le contenu publié dans cette première version.
- La CME enregistre le changement avec auteur, date et motif. Conserver les versions utiles pour comprendre les changements de conditions ; pas de suppression physique de l'offre liée à une candidature dans ce parcours.
- Modification mineure (orthographe/mise en forme) : correction confirmée par CME, offre maintenue publiée.
- Modification d'une condition (niveau, durée, dates, lieu, mode de travail, type, canal de candidature) : la CME vérifie la source, enregistre les écarts avant/après et confirme explicitement la publication de la nouvelle version. L'ancienne version reste celle consultée tant que la nouvelle n'est pas confirmée ; pas de période où un contributeur peut imposer le nouveau contenu.
- S'il existe un doute sérieux (fausse offre, contenu dangereux, incohérence nécessitant examen), la CME retire immédiatement l'offre de la consultation commune et la remet en attente de vérification. Les candidatures ne sont pas supprimées ; leur suivi affiche un avis de retrait sans exposer le contenu problématique. Réexamen avant toute republication, sans inventer une nouvelle validation automatique.
- Pour une candidature existante, conserver la référence de version examinée lors de sa création et indiquer dans son suivi qu'une nouvelle version des conditions existe. Pas de changement d'état ni de nouvelle candidature automatique. Versions anciennes non exposées au-delà des droits autorisés ; détails de conservation à spécifier.
- Aucune notification externe ou alerte automatique ajoutée par cette proposition. Le signalement dans l'interface suffit au pilote ; il ne garantit pas qu'un candidat déjà parti sur le site source soit informé immédiatement.

### Contrôles et preuves à prévoir avant acceptation applicative

| Vérification | Résultat attendu selon D068 |
|---|---|
| Apprenant tente de clôturer/modifier directement | Refus côté serveur, données inchangées |
| CME d'un autre établissement connaît l'identifiant | Refus sans exposer le contenu interne |
| Fermeture signalée, mais non encore examinée | Signalement visible à la CME, pas de clôture silencieuse par le contributeur |
| CME clôture | Offre absente de la recherche courante, suivis existants conservés et marqués |
| Échéance dépassée / lien inaccessible | Avertissement/incertitude, pas de fausse preuve de clôture ou d'ouverture |
| CME change une condition et confirme | Nouvelle version affichée, précédent utile conservé, suivi indiquant le changement |
| Retrait pour doute sérieux | Pas d'accès commun au contenu problématique, suivi personnel conservé |
| Double clic ou deux modifications concurrentes | Pas de doublon d'événement ni écrasement silencieux d'une décision plus récente |
| Réouverture | Vérification CME et trace ; aucune candidature ancienne modifiée automatiquement |

Accord consigné D068 ; première tranche et synthèse réalignées. Avant code : spécifier champs/transitions et tests ; détails de conservation, concurrence et affichage à traiter sans choisir la stack implicitement. Ces contrôles sont à réaliser ; aucune preuve applicative disponible.

Parcours nominal et motifs validés D061 ; disponibilité, clôture/réouverture, modifications et historique utile validés D068 dans le périmètre ci-dessus. Restent notamment ouverts : accès auteur avant publication, corrections après rejet, retrait par l'auteur, doublons, champs obligatoires précis, visibilité/conservation détaillée des traces et saisie rétrospective d'une candidature. D007 reste ouverte.
