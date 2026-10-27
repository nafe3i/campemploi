# IA-Q02 — Modèle des rôles et permissions

Date : 27 octobre 2026. Statut : **Proposed — comparaison préparatoire**. Préparation autorisée D099, avant IA-Q03. Aucune proposition RP01–RP06 ci-dessous n'est adoptée.

## 1. Question et périmètre

Définir comment représenter les responsabilités d'une personne et déterminer ses actions autorisées, dans le contexte d'établissement validé par IA-Q01. Il faut éviter deux confusions : un rôle n'est pas un établissement et une permission administrative ne donne pas automatiquement accès aux données métier.

IA-Q01 P01–P06 est validé D099 comme orientation : identité globale stable, rattachements distincts, au plus un actif au pilote, contexte unique par action locale, email vérifié/unique modifiable, fin de relation sans suppression de compte ni transfert de ressources. Notion d'activité et approbations concurrentes, normalisation/récupération/réattribution email et autres modalités restent ouvertes. Demande en attente, rattachement actif et historique sont distincts ; l'email seul ne prouve pas la propriété d'un ancien compte.

Cette étude ne crée ni rôle supplémentaire, permission technique, politique JWT, moteur d'autorisation, ORM, isolation SQL ou configuration. Aucun code/migration ; D059/D068/D064 et droits acquis conservés. IA-Q03 est le prochain chantier après IA-Q02 ; aucune cardinalité de classe ni règle de transfert n'est décidée ici. Les conflits d'intérêts et actes sur soi-même restent IA-Q05.

Références : [décisions](../product/decisions.md), [modèle et matrice IA](identity-organization-access.md), [IA-Q01](ia-q01-account-membership-options.md), [administration](../scope/establishment-administration.md), [revues](../scope/cv-portfolio-review.md), [offres](../scope/offer-lifecycle.md), [socle](socle-technique.md).

## 2. Exigences déjà acquises

| Responsabilité / relation | Nature dans les règles existantes | Portée et limites acquises |
|---|---|---|
| Apprenant | Rôle métier, par défaut à l'inscription D038 | Aucun accès interne avant approbation ; droits personnels et contribution selon parcours |
| Formateur / responsable technique | Un seul rôle métier D079 | Revue des classes affectées D058, demandes adressées D020–D022 ; pas d'accès global aux candidatures ou bilans |
| CME | Rôle métier D019/D028/D056 | Modération, revues et suivi dans son établissement ; ses droits d'écriture restent ceux du parcours, pas ceux de toute consultation |
| Administration locale | Permission/responsabilité distincte de CME D056 | Classes, personnel, rôles/rattachements locaux ; cumul CME + administration locale autorisé, pas de pouvoir général ni accès confidentiel implicite |
| Administration générale | Pouvoir général D056 | Créer établissements/désigner première administration locale selon procédure à définir ; aucun accès métier global implicite |
| Référent de classe | Affectation D078/D079, pas second rôle global | Au plus un référent courant par classe, plusieurs classes possibles par formateur ; retrait selon D080 |
| Accompagnant du rendez-vous | Relation au rendez-vous D025/D026 | Droits sur ce bilan ; aucun accès à tous les dossiers d'une classe ou aux bilans d'autres accompagnants |
| Porteur consultant le tableau | Droit explicite D044/D045 | Son établissement et indicateurs autorisés ; distinction avec administration, pas contenu confidentiel de bilan |
| Auteur / propriétaire | Relation à une ressource D036/D037/D071 | Autorise des actions personnelles précises ; pas de rôle administratif nouveau |
| Personnel contributeur | Public pouvant proposer une offre D031 | N'implique pas un rôle « staff » avec tous les pouvoirs ; catégories et permissions détaillées ouvertes D056 |

Il n'existe pas de hiérarchie acquise « administrateur > CME > formateur > apprenant ». Un droit de consulter une candidature ne donne pas celui de la modifier ; le droit de gérer un rôle ne donne pas de droit sur un bilan. Les noms techniques et libellés définitifs restent à préciser.

## 3. Axes de conception à distinguer

| Axe | Question | Dépendance |
|---|---|---|
| Représentation des responsabilités | Une responsabilité métier principale ou plusieurs attributions locales ? | IA-Q02 ; cumul supplémentaire à autoriser explicitement |
| Définition des permissions | Catalogue stable par action ou permissions composables/personnalisables ? | IA-Q02 ; aucune bibliothèque déduite |
| Contexte de la décision | Rôle + appartenance + ressource + relation + état ? | Règles acquises ; mécanisme de politique encore à définir |
| Pouvoir d'attribution | Qui accorde/retire quoi dans quel périmètre ? | D056 acquis, délégations fines et auto-actions IA-Q05/07 |
| Validité et retrait | Quelle attribution est encore valable à l'évaluation ? | D060/D080/D099 ; mécanisme/fraîcheur/concurrence IA-Q08/10 |

Ces axes sont combinables : plusieurs rôles locaux ne nécessitent pas un éditeur libre de permissions, et un rôle principal ne supprime pas les contrôles sur les ressources. RBAC décrit l'effet du rôle ; attributs/relations complètent le périmètre. Une capacité de représentation n'autorise pas automatiquement tous les cumuls.

## 4. Alternatives argumentées

### A — Un rôle métier principal, permissions administratives séparées

La personne possède une responsabilité métier principale dans son rattachement ; l'administration locale est traitée séparément, conformément à D056. Les affectations et relations restent nécessaires pour les classes et bilans.

Avantages : affichage simple, peu de combinaisons, parcours pilote faciles à expliquer. Inconvénients : une personne réellement CME et formateur demanderait changement de rôle, exception ou évolution du modèle ; ces cas ne doivent pas être masqués par le rôle administrateur. Le rôle principal historique ne doit pas effacer l'auteur des avis passés.

Sécurité : réduit certaines combinaisons à tester, sans prévenir un accès inter-classes si les requêtes restent insuffisamment bornées. Cette alternative est viable si le campus confirme l'absence de cumuls métier nécessaires ; ce besoin n'est pas encore établi.

### B — Attributions locales explicites, catalogue fermé d'actions

Le modèle peut représenter plusieurs responsabilités nommées dans un rattachement. Les permissions administratives restent distinguées, et les classes/accompagnements sont des relations, pas des rôles ajoutés. Le catalogue des actions et politiques est maîtrisé dans la conception de chaque fonctionnalité ; aucune permission personnalisée libre n'est nécessaire.

Avantages : reflète les responsabilités sans hiérarchie artificielle, conserve le cumul acquis et prépare des cumuls futurs explicitement décidés. Inconvénients : il faut définir les attributions autorisées, leur validité et les éventuels conflits ; la présence de deux rôles ne suffit pas à autoriser une action sensible. L'interface peut montrer plusieurs responsabilités sans présenter tous les parcours comme accessibles.

Sécurité : chaque action doit encore vérifier établissement, rattachement, relation/propriété et état. Pas d'union aveugle des pouvoirs ni de changement automatique d'attribution lors d'une inscription ou d'un transfert. Le seul cumul acquis CME + administration locale reste le seul explicitement autorisé à ce jour.

### C — Profils personnalisables ou permissions individuelles fines

Des gestionnaires assemblent des actions dans des profils ou les attribuent individuellement. Ce mécanisme peut se combiner avec A/B, mais ajoute une dimension de délégation/configuration.

Avantages : souplesse pour établissements aux organisations différentes. Inconvénients : interface de gestion, compréhension des droits effectifs, attribution des pouvoirs d'administration de profils, héritage/conflits, version des politiques et tests plus coûteux. Des noms anodins peuvent masquer des combinaisons excessives.

Au pilote, aucun besoin acquis ne justifie encore cet éditeur. La souplesse ne dispense pas des politiques sur les ressources et peut accroître les erreurs de configuration. Cette comparaison n'autorise ni délégation générique, ni permission « tout », ni super-administrateur de données.

### Synthèse comparative

| Critère | A | B | C |
|---|---|---|---|
| Simplicité de lecture | Forte pour rôle unique | Bonne si responsabilités explicites et catalogue limité | Plus difficile : calcul des droits effectifs |
| Cumul CME + administration locale | Compatible en distinguant permission administrative | Compatible explicitement | Compatible mais outil supplémentaire inutile pour ce seul cas |
| Cumuls métier futurs | Évolution ou exceptions nécessaires | Représentables après décisions de cumul | Très souples, gouvernance à établir |
| Contrôle par classe/bilan/propriétaire | Toujours nécessaire | Toujours nécessaire | Toujours nécessaire |
| Coût de test relatif | Moins de combinaisons métier | Combinaisons explicites + retrait/conflits | Combinaisons configurables et pouvoir d'édition à tester |
| Adéquation au pilote | Possible si rôle principal suffisant | Recommandation préparatoire | Surcroît de capacité non justifié actuellement |

Comparaison qualitative pour notre produit, sans gain de performance, délai ou coût chiffré inventé.

## 5. Évaluation d'une action et exemple minimal

PROPOSÉ : une décision explicite reçoit l'identité, le contexte local autorisé, l'action et les attributs utiles de la ressource ; elle évalue droits courants, relations/propriété et conditions métier. Les contrôles communs n'effacent pas les règles spécifiques du cas d'utilisation D093.

Exemple fictif : T1 est formateur, référent de C1. Il peut examiner les documents de C1 selon D058, sans publier une offre ni lire le bilan d'un autre accompagnant. Lui accorder une permission administrative locale, si ce cumul est approuvé ultérieurement, ne ferait pas de ce pouvoir un accès à tous les documents. Exemple conditionnel, pas nouveau cumul autorisé.

| Action acquise | Responsabilité pertinente | Conditions supplémentaires indispensables |
|---|---|---|
| Publier une offre | CME locale | Offre du bon établissement, état/préconditions D061/D070 |
| Lire sa proposition non publiée | Auteur autorisé | Propriété et rattachement, pas rôle formateur de l'auteur |
| Examiner un CV par classe | Formateur référent | Affectation courante, classe et établissement, contenu examiné |
| Lire un bilan | Acteur D025 | Lien au rendez-vous ou CME locale ; pas simple affectation de classe |
| Modifier ses observations | Auteur D026 | Ses propres observations, pas droit de lecture seul |
| Gérer rattachement/rôle local | Permission administrative locale | Personnes/cibles dans le périmètre et attribution autorisée D056 |
| Lire indicateur de suivi | Droit de tableau D044 | Champs autorisés et établissement, pas contenu de bilan |

Ce contrôle par action/ressource s'appuie sur les règles existantes et rejoint les recommandations [OWASP Authorization](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html). La [documentation NestJS](https://docs.nestjs.com/security/authorization) présente des mécanismes d'autorisation ; elle ne vaut pas choix d'une bibliothèque, d'un guard particulier ou d'un moteur de politiques pour le campus.

## 6. Attribution, retrait et séparation des pouvoirs

ACQUIS : gestion locale dans l'établissement, absence de délégation du pouvoir général par l'administration locale, invitations personnelles du personnel et approbation de rattachement. Le rôle apprenant par défaut D038 n'ouvre pas les données internes pendant l'attente. D059 conserve le lien de classe partagé/réutilisable et interdit le transfert automatique.

PROPOSÉ pour B : attribution liée au contexte local et à la responsabilité nommée, identifiable indépendamment du compte global. Un acteur ne peut attribuer que les responsabilités relevant d'un pouvoir explicitement accordé ; l'interface ou le corps d'une requête ne crée pas ce pouvoir. Les changements utiles sont traçables selon politique à préciser IA-Q12, sans conservation illimitée implicite.

L'autorité générale ne devient pas un accès métier confidentiel automatique. Le bootstrap, la désignation/remplacement d'une CME et les garanties de récupération restent IA-Q07. Les actes sur soi-même, la récusation et la capacité de la même personne à rendre les deux avis restent IA-Q05. Aucune validation de B ne réglerait ces conflits à elle seule.

Le retrait d'un rôle, d'une permission administrative, d'une affectation ou d'un rattachement a des portées distinctes. Retirer C1 ne retire pas arbitrairement C2 ; retirer une permission administrative ne réécrit pas un avis métier signé. Les droits provenant uniquement de l'élément retiré ne doivent plus autoriser un nouvel accès, même avec un JWT encore valide ; point d'effet et concurrence IA-Q08 restent à définir. Aucun modèle de cache, de session ou de révocation n'est adopté.

## 7. Conséquences JWT et PostgreSQL, sans choix d'implémentation

| Sujet | Conséquence à prendre en compte | Ce qui reste ouvert |
|---|---|---|
| Identité globale D099 | Les rôles locaux ne deviennent pas une autorité globale attachée à l'identité | Claims, transport et vérification JWT IA-Q10 |
| Rattachement actif du pilote | Attribution ne remplace ni approbation ni activité ; historique/demande distincts | Définition d'activité et unicité concurrente, modalités IA-Q01/08 |
| Attributions multiples proposées B | Relations locales distinctes et cohérentes, pas une valeur de rôle unique réécrivant le passé | Tables, cardinalités historiques, contraintes et ORM non décidés |
| Rôle et affectation | Rôle formateur commun, relation de classe séparée ; pas doublon technique « responsable technique » | Modèle de classe IA-Q03 et représentation exacte |
| Changement concurrent | Permission d'attribuer, modification et retrait cohérents ; pas d'auto-élévation par course | Transaction, verrouillage/version, trace IA-Q08/09/12 |
| Anciennes ressources | Auteurs et données d'établissement préservés selon règles acquises | Conservation/consultation ancienne IA-Q04/12 |

Un tableau de rôles contenu dans le JWT ne devient pas la source permanente des droits. Une signature valide ne démontre pas qu'un rôle, rattachement ou référent est encore courant. Le contrôle de fraîcheur reste à concevoir ; pas de requête SQL systématique, Redis, RLS ou modèle de stockage sélectionné ici.

## 8. Recommandation argumentée — non adoptée

Je recommande **B : attributions locales explicites, catalogue limité d'actions, permissions administratives distinctes et politiques contextuelles**, sans éditeur libre de droits au pilote.

Pourquoi : cela conserve D056/D079, représente les responsabilités plutôt qu'une hiérarchie et évite de reconstruire l'identité lors d'un changement de mission. Le catalogue limité garde les droits lisibles et testables pour le pilote. Le coût supplémentaire est l'explicitation des attributions et des conflits, déjà nécessaire pour CME/administration/référent/accompagnant.

Cette recommandation porte sur la capacité de représentation et les principes d'évaluation, pas sur l'autorisation de tous les cumuls. Les nouveaux cumuls métier restent à examiner avant leur activation ; le cas des deux avis ne doit pas être résolu par addition de rôles. A reste une alternative raisonnable si un rôle métier principal suffit au campus, mais ses restrictions doivent être explicites. C est à réexaminer seulement si des besoins concrets de délégation/configuration émergent.

## 9. Propositions précises soumises à approbation

RP01–RP06 sont des sous-propositions de cette préparation IA-Q02, pas des fiches F/S ni des décisions acquises.

| Proposition | Orientation à approuver ou modifier | Limites |
|---|---|---|
| RP01 — Séparation | Distinguer rôles métier nommés, permissions administratives et relations d'affectation/propriété, sans hiérarchie donnant tous les droits | Préserve les séparations acquises ; aucun rôle supplémentaire créé |
| RP02 — Représentation | Permettre de représenter plusieurs responsabilités locales explicites dans un rattachement, plutôt qu'un champ global exclusif | Seul cumul CME + administration locale déjà acquis ; nouveaux cumuls à valider avant activation, conflits IA-Q05 ouverts |
| RP03 — Catalogue | Retenir un catalogue limité d'actions et de règles explicites par fonctionnalité au pilote | Noms techniques à préciser ; pas d'éditeur libre de profils/permissions ou moteur imposé |
| RP04 — Évaluation | Évaluer chaque action avec droits courants, contexte, ressource et relations nécessaires ; aucun accès par simple hiérarchie administrative | Aucun choix d'outil, JWT, cache ou isolation ; permissions de la matrice conservées |
| RP05 — Attribution | Rattacher les attributions au contexte local et au pouvoir explicite de celui qui les gère ; pas de nouveau droit automatique au changement d'établissement | D056/D099 conservées ; délégations fines, actes sur soi-même et bootstrap restent ouverts |
| RP06 — Retrait | Distinguer les portées de retrait et préserver autres droits indépendants/auteurs ; un droit retiré n'est pas prolongé par JWT valide | Sémantique concurrente, fraîcheur, invalidation des jetons et traces IA-Q08/10/12 non choisies |

L'approbation éventuelle de RP02 ne répond pas automatiquement « oui » aux cumuls CME/formateur/apprenant. Toute activation non déjà acquise devra être spécifiée avec ses conflits et approuvée D064. Les modalités de classes IA-Q03 seront préparées ensuite, sans renumérotation des questions.

## 10. Scénarios à vérifier après arbitrage

| ID | Situation | Attente de preuve future |
|---|---|---|
| RP-S01 | CME avec administration locale consulte un bilan étranger à son établissement | Aucun contournement par cumul ou pouvoir administratif |
| RP-S02 | Formateur référent tente de publier une offre sans droit CME | Refus selon D061 ; affectation de classe insuffisante |
| RP-S03 | CME consulte une candidature puis tente de la modifier au titre de la consultation | Aucun droit d'écriture créé par lecture D019/D037 |
| RP-S04 | Membre forge rôle/permission dans une requête | Pas d'élévation ni attribution hors pouvoir ; absence d'effet |
| RP-S05 | Retrait d'affectation C1 avec rôle formateur et affectation C2 conservés | Refus C1, évaluation indépendante C2, auteurs inchangés |
| RP-S06 | Administrateur local tente de créer un administrateur général | Refus D056 même si interface modifiée |
| RP-S07 | Même compte change d'établissement | Aucun rôle/accès recopié automatiquement D099 |
| RP-S08 | Même personne cumule CME/formateur et tente deux avis sur un document | Attente d'arbitrage IA-Q05, aucun résultat inventé |
| RP-S09 | Attribution administrative retirée pendant une opération | Politique de concurrence à décider IA-Q08 ; aucun maintien implicite via ancien JWT |
| RP-S10 | Personnel contributeur sans catégorie de délégation définie | Contribution acquise selon rattachement, pas permission générale « staff » |

Aucun test applicatif exécuté ; scénarios à intégrer aux fiches concernées après décisions. Le droit de contribuer ne remplace pas les autres préconditions et une question ouverte n'est pas une nouvelle permission.

## 11. Arbitrages restants et correspondance

IA-Q02 reste ouvert jusqu'à accord sur les propositions. À préciser même après une orientation : catalogue concret, délégations nécessaires, cumuls métier à activer, trace des attributions et représentation des périodes. IA-Q03 (classes), IA-Q05 (conflits), IA-Q07 (bootstrap), IA-Q08/09 (concurrence/isolation), IA-Q10 (JWT), IA-Q11/12 (données/traces) ne sont pas clôturés par cette étude.

| Référence | Dépendance apportée |
|---|---|
| Socle Q05/Q07 ; S03/S05 ; F01/F03/F04 | Portée des attributions, limites de pouvoir et cohérence des relations avant schéma/parcours |
| Socle Q06 ; S04 ; F02 | Identité distincte des pouvoirs courants ; mécanisme JWT à concevoir après principes nécessaires |
| F05–F07 | Catalogue d'actions offres, permissions existantes D061/D068/D070–D077 conservées |
| F08/F09 | Rôle commun et affectations distinctes ; conflit de double avis IA-Q05 |
| F10/F12–F14 | Propriété, accompagnement et tableaux sans élargissement des contenus confidentiels |

Prochaine discussion : alternatives A/B/C et RP01–RP06. Après arbitrage IA-Q02, préparer IA-Q03 ; ne pas implémenter le modèle des rôles au titre de la seule préparation documentaire.


## 12. Vérifications documentaires et conservation

Périmètre réel : dix fichiers Markdown — `README.md`, `docs/product/decisions.md`, `docs/specs/ia-q01-account-membership-options.md`, `docs/specs/identity-organization-access.md`, `docs/specs/socle-technique.md`, présente comparaison, `docs/plan-realisation.md`, `tracking/BOARD.md`, `tracking/STATUS.md`, `tracking/JOURNAL.md`.

Contrôles exécutés : 70 liens locaux résolus, encodage et blocs fermés, D099 unique et registre antérieur intégralement conservé ; blocs D059/D068/D064, lignes IA-Q03–IA-Q12, matrice/invariants acquis et intitulés/identifiants F/S identiques à HEAD avant ce travail. Six RP et dix scénarios RP-S uniques ; diff sans erreur d'espacement. Recherche ciblée de secrets et relecture manuelle sans anomalie détectée, sans garantie absolue.

Aucun code, migration, configuration, bibliothèque ou test applicatif créé/exécuté. P01–P06 sont validés D099 ; RP01–RP06 restent proposés. Commit documentaire c5a37c55f8dcf87be7c606a48b5dd9b4656fff92 publié sur origin/main ; concordance distante vérifiée le 27 octobre 2026. Commit/push seuls n'autorisent aucune implémentation.
