# Revue des CV et portfolios — cadrage progressif

Mise à jour : 25 octobre 2026. Références : D055, D057–D058 et D078–D079. Double validation, cycle de revue, référent et équivalence des appellations validés ; modalités restantes à approfondir, pas spécification technique ni fonctionnalité Accepted.

## Besoin exprimé

- CV PDF déposé, portfolio par lien (D041–D042).
- Revue par la CME et les formateurs, en conservant séparément leurs avis.
- Formateur affecté à sa classe ; visibilité CME sur les apprenants de son établissement.
- D078 : un formateur référent par classe porte l'avis formateur ; un formateur peut suivre plusieurs classes, affectations gérées par la CME dans son établissement avec permission locale. D079 : formateur et responsable technique désignent le même rôle métier ; être référent est une affectation, pas un second rôle global.
- Tri/filtrage par classe, année, formateur.
- Accès validé D058 : formateur affecté consultant/examinant les CV et portfolios de ses classes sans demande préalable ; CME pour tous les apprenants de son établissement. Aucune extension aux bilans confidentiels ou aux autres classes/établissements.
- États de chaque avis (D057) : en attente (non examiné), non validé (corrections nécessaires après revue), validé, à revalider (modifié depuis revue).

## Modèle de revue validé (D057) et compléments proposés

Deux avis distincts par élément examiné : formateur et CME. CV et portfolio évalués séparément. Validation globale seulement lorsque les deux avis sont positifs pour le document examiné ; après modification, nouvelle revue des deux intervenants et conservation des anciens avis sans les reporter au nouveau contenu. Première revue en attente. Les autres statuts globaux restent à définir.
Compléments proposés : auteur, date et référence de version pour chaque avis ; répartition technique/projets côté formateur, présentation et candidature côté CME. Détail à spécifier/valider. Pour un portfolio externe, la méthode d'identification du contenu examiné et de signalement des modifications est ouverte : aucun suivi automatique du site promis.

Exemple fictif : CV version 1 validé par le formateur, non validé par la CME → pas de validation globale. Deux avis positifs → globalement validé. Remplacement par version 2 → nouvelle revue, anciens avis conservés comme historique de version 1.

## Questions à trancher par petits groupes

1. Organisation du référent D078 et rôle commun formateur/responsable technique D079 validés ; remplacement du référent et classe sans référent à préciser.
2. Accès par classe sans demande préalable validé D058, faisant évoluer D042 pour le formateur affecté ; sort des accès et historique lors d'un changement d'affectation à préciser.
3. Deux avis positifs et revues séparées validés (D057) ; autres statuts globaux à spécifier.
4. En attente/non validé distingués par D057 ; règles détaillées de correction à spécifier.
5. Modification déclenchant nouvelle revue validée ; historique/versions et détection ou déclaration des changements d'un portfolio externe à préciser.
6. Qui voit les commentaires de revue ? Ne pas les assimiler automatiquement aux bilans de rendez-vous D025 ni aux notes privées.
7. Les filtres et compteurs sont-ils destinés à la CME, au formateur limité à sa classe et/ou au tableau porteur ? Voir un statut ne donne pas automatiquement accès au fichier.
8. Une absence de validation empêche-t-elle de candidater ? Aucun blocage de candidature décidé ; ne pas inventer de condition supplémentaire.

## Organisation du référent — Validé D078

Un référent par classe porte l'avis formateur de la revue ; un même formateur peut être référent de plusieurs classes. La CME gère les affectations dans son établissement avec permission d'administration locale D056. La CME conserve son propre avis D057 et sa visibilité établissement D058 ; les deux avis ne sont pas fusionnés. Aucune extension aux autres classes, établissements ou bilans confidentiels.

L'équivalence des termes formateur et responsable technique est explicitement validée D079 : un seul rôle métier. Revue par classe et accompagnement restent des parcours aux permissions contextuelles distinctes ; aucun accès à d'autres classes ou bilans d'autres accompagnants n'est ajouté par cette clarification. Avis formateur et CME restent séparés ; libellés d'interface et identifiant technique non choisis.

| Vérification à prévoir | Résultat attendu, non encore testé |
|---|---|
| CME affecte un référent dans son établissement | Un référent pour la classe ; son avis formateur reste distinct de l'avis CME |
| Même formateur affecté à plusieurs classes | Organisation permise ; accès limité aux classes affectées selon D058 |
| Tentative de deux référents simultanés pour une classe | Ne pas créer deux référents en même temps ; procédure explicite de remplacement à définir |
| Formateur tente de consulter une autre classe ou un autre établissement | Refus selon D058/D060, sans exposition de document |
| Membre sans permission locale d'affectation ou CME d'un autre établissement tente de modifier | Refus sans modification ; respecter D056 et le périmètre local |
| Même rôle nommé formateur ou responsable technique consulte/revoit un document | Même règle D058 : classe affectée et établissement vérifiés ; pas de double rôle requis |
| Responsable technique non affecté à la classe invoque le rôle commun pour lire ses CV/portfolios | Aucun accès général par classe ; autres accès éventuels uniquement selon leur contexte déjà autorisé, pas par l'équivalence |
| Référent invoque sa classe pour lire un bilan d'un autre accompagnant | Refus selon droits propres aux bilans ; affectation ne les élargit pas |

Remplacement, retrait d'affectation, visibilité des anciens avis et situation d'une classe sans référent à discuter ; aucune invalidation automatique des avis ni conservation d'accès après remplacement n'est décidée ici.

## Limites et articulation

Pas de choix de stack. Pas d'accès général aux bilans confidentiels via la classe. Droits à arbitrer avant implémentation, avec tests d'accès inter-classes et inter-établissements. Aucun changement implicite du parcours initial offres D053. Les quatre états d'offre proposés restent distincts de ceux de la revue CV.
