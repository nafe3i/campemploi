# Cycle de vie des offres — proposition détaillée

Date : 24 octobre 2026. Statut : partiellement validé. D061 valide le parcours nominal (soumission en attente, décision CME publier/corriger/rejeter, motifs et nouvelle soumission après correction). Disponibilité, clôture, modifications publiées et autres règles restent Proposed. Références : D028–D032, D052–D054 et D060–D061. Aucun code ni choix technique.

## Deux dimensions

Modération : en attente, à corriger, publiée, rejetée. Disponibilité : ouverte, clôturée, à confirmer. Séparation conceptuelle proposée ; ne préjuge pas du schéma de base de données.
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
| Publiée | Corriger, CME | Publiée | Trace minimale de la modification proposée ; source et incertitudes mises à jour |
| Publiée / disponibilité ouverte ou incertaine | Constater fin, CME | Publiée / clôturée | Source ou motif de clôture enregistré ; hors liste des offres ouvertes |

Proposition : pas de réouverture autonome d'un rejet par l'auteur ; une nouvelle soumission pourra être décidée après échange. Corrections après rejet, retrait d'une proposition par l'auteur et dépublication d'urgence restent à arbitrer. Rien n'impose un état brouillon sauvegardé dans cette première version.

## Informations et travail de la CME proposés

Afficher ensemble : lien/provenance, entreprise, intitulé/type, lieu/mode de travail, niveau demandé, compétences, durée/début/échéance quand connus et disponibilité observée. Champs de qualification inconnus signalés sans bloquer systématiquement la soumission. Niveau demandé bac+5 conservable et publiable avec écart signalé (D052). Accessibilité depuis le Maroc inconnue publiable après validation avec mention explicite (D029). Qualification ne doit pas inventer le consentement de l'entreprise à d'autres profils.

Liste de travail CME : propositions en attente, date de soumission, auteur et éléments manquants. Détail/commentaire/action accessibles sans ouvrir tous les dossiers apprenants. Temps de traitement et ancienneté du stock mesurables à terme ; aucun délai garanti ni alerte automatique décidé.

Historique minimal proposé : auteur de l'action, date, action et motif pertinent. Définir la visibilité de ces traces ; pas de collecte intégrale inutile de données ni de copie de toute annonce par défaut. La validation de la CME n'est pas une certification juridique ou une garantie de fiabilité de l'employeur.

## Cas limites et vérifications proposés

- Doublon : montrer la correspondance et relier au contenu existant après examen CME ; ne pas fusionner sur le seul intitulé ni activer un dédoublonnage complexe sans décision.
- Lien inaccessible : proposer une provenance et un texte utile ; statut à corriger ou vérification supplémentaire selon décision CME, pas fausse ouverture.
- Annonce expirée avant publication : ne pas la proposer comme recrutement ouvert ; conservation comme référence ou rejet à arbitrer.
- Date limite explicite dépassée : signalement automatique envisageable, mais règle de clôture automatique non décidée ; toujours distinguer date limite de candidature et date de début.
- Retrait d'une offre publiée : conserver le suivi des candidatures existantes ; ne pas transformer automatiquement une candidature en refusée.
- Modification importante : pas de changement silencieux par un contributeur ; CME contrôle et la politique d'information des candidats reste à définir.
- Double clic ou décision concurrente : éviter deux publications ou un écrasement silencieux ; détails techniques après architecture.
- Accès : contrôler côté serveur compte/rattachement, rôle CME, établissement et propriété de la proposition à chaque action ; tester aussi URL directe et tentative de changement d'identifiant.
- Expiration d'une invitation ne supprime pas un compte déjà validé ; les cycles de vie sont distincts.

## Limites et décisions attendues

Parcours nominal et motifs validés par D061. Disponibilité, historique, détail de visibilité avant publication, corrections publiées et clôture restent proposés. Le document rend ces règles discutables et testables ; prochaines décisions : clôture/modifications et exceptions. D007 reste ouverte.
