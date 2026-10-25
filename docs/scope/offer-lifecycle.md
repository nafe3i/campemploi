# Cycle de vie des offres — règles validées et propositions restantes

Mise à jour : 25 octobre 2026. Statut : règles référencées validées, détails restants signalés. D061 : parcours nominal ; D068 : disponibilité/modifications ; D070–D073 : qualification, consultation, doublons et réexamen ; D075 : retrait demandé ; D077 : doublons déjà publiés. Les autres propositions restent Proposed. Références : D028–D032, D052–D054, D060–D061, D068, D070–D073, D075 et D077. Aucun code ni choix technique.

## Deux dimensions

Modération : en attente, à corriger, publiée, rejetée (D061). Disponibilité : ouverte, clôturée, à confirmer ; séparation conceptuelle validée D068, sans préjuger du schéma de base de données.
« Publiée » signifie autorisée à être vue, pas emploi encore ouvert. « Ouverte » reste une observation de la source, pas garantie d'embauche. Sans information suffisante, ne pas inventer une date de clôture ou une ouverture confirmée.

## Responsabilités et points restant à préciser

Auteur rattaché : soumet une offre, consulte ses propositions, corrige après retour et signale une correction/clôture après publication. Ne peut pas publier par lui-même en tant que contributeur.
CME du même établissement : examine, demande correction, publie ou rejette avec motif, corrige le contenu publié et enregistre la clôture. Une CME peut contribuer ; son droit de publication provient de son rôle CME, avec acte de validation explicite. Pas de second valideur indépendant imposé par les décisions actuelles.
Autres apprenants rattachés : consultent les offres publiées de leur établissement, pas les propositions en attente, à corriger ou rejetées.
Administrateur général : pas de droit de validation d'offre automatiquement déduit de l'administration technique.

## Consultation avant publication — Validé D071

Accord explicite du 25 octobre 2026 (« oui je valide »). L'auteur rattaché consulte ses propres propositions, leur état et les motifs de correction ou de rejet ; la CME consulte celles de son établissement. Les autres membres attendent la publication pour consulter l'offre. D028 concerne la visibilité collective ; D071 précise la consultation individuelle de la contribution par son auteur.

| Acteur | Consultation autorisée avant publication |
|---|---|
| Auteur apprenant ou membre du personnel rattaché | Ses propres propositions, leur état et les motifs de correction/rejet |
| CME du même établissement | Propositions de son établissement dans le cadre de la modération |
| Autre apprenant ou formateur non auteur | Aucune consultation de cette proposition non publiée ; attendre publication |
| CME d'un autre établissement | Aucun accès à cette proposition interne |

Le droit de consulter ne permet pas de publier, de modifier les décisions de la CME ni de consulter les dossiers des autres candidats. Correction par l'auteur après retour et nouvelle soumission selon D061 ; modifications publiées et retrait pour doute sérieux selon D068. Aucun droit supplémentaire sur le contenu problématique retiré ou l'historique détaillé. Un rôle administratif ne confère pas automatiquement les permissions métier de la CME.

### Contrôles à prévoir — aucune preuve applicative

| Cas | Résultat attendu |
|---|---|
| Auteur consulte sa proposition en attente, à corriger ou rejetée | Proposition et état accessibles ; motif de correction/rejet accessible lorsqu'il existe |
| Autre membre tente le même accès par liste ou URL directe | Accès refusé, contenu et motif non exposés ; données inchangées |
| Formateur consulte une proposition non publiée d'un apprenant de sa classe | Refus : affectation de classe ne vaut pas permission de modération |
| CME du même établissement consulte | Accès autorisé pour la modération |
| CME d'un autre établissement connaît l'identifiant | Refus sans exposition du contenu ou du motif |
| Auteur tente d'utiliser son droit de consultation pour publier | Refus selon D061, aucune publication |

Vérifier identité, état du compte, rattachement, rôle, propriété et établissement côté serveur à chaque accès selon D060. Détails de présentation, historique et effets d'un changement de rattachement à spécifier ; aucune autorisation supplémentaire inventée pour ces cas.

## Parcours et transitions proposés

| Départ | Action et acteur | Arrivée | Condition / résultat |
|---|---|---|---|
| Nouvelle proposition | Soumettre, contributeur | En attente | Intitulé, entreprise, type et lien source ou texte avec provenance selon D070 |
| En attente | Demander correction, CME | À corriger | Commentaire expliquant l'information ou correction attendue |
| À corriger | Corriger et soumettre, auteur | En attente | Nouvelle lecture CME nécessaire ; pas de publication automatique |
| En attente | Publier, CME | Publiée | Qualification et moyen de candidature exploitable selon D070 ; incertitudes signalées et choix explicite |
| En attente | Rejeter, CME | Rejetée | Motif expliqué à l'auteur |
| Rejetée | Autoriser un réexamen, CME du même établissement | À corriger | Nouveaux éléments justifiant réexamen, motif et rejet initial conservé selon D073 |
| Proposition non publiée encore à traiter | Traiter la demande de retrait de l'auteur, CME du même établissement | Rejetée | Motif « retrait demandé par l'auteur » ; proposition et historique conservés selon D075 |
| Publiée | Signaler correction, utilisateur autorisé | Publiée, signalement à traiter | Signaler ne remplace pas le contenu validé |
| Publiée | Corriger et confirmer, CME | Publiée | Trace et version selon D068 ; source et incertitudes mises à jour |
| Publiée / disponibilité ouverte ou incertaine | Constater fin, CME | Publiée / clôturée | Source ou motif de clôture enregistré ; hors liste des offres ouvertes |

Réexamen après rejet validé D073 ci-dessous, sans réouverture autonome par l'auteur. Retrait demandé par auteur avant publication validé D075, traité par CME sans suppression. Le retrait temporaire pour doute sérieux reste régi par D068. Rien n'impose un état brouillon sauvegardé dans cette première version.

## Retrait demandé par auteur avant publication — Validé D075

Accord explicite du 25 octobre 2026 (« valider »). Avant publication, l'auteur rattaché peut demander le retrait de sa propre proposition à la CME du même établissement. La demande ne vaut ni suppression ni rejet automatique. La CME termine le traitement par un rejet motivé « retrait demandé par l'auteur » ; proposition et historique restent conservés. Aucun nouvel état de modération.

Les autres membres ne peuvent pas demander ce retrait au nom de l'auteur ni rejeter eux-mêmes la proposition. Consultation selon D071 et réexamen éventuel du rejet selon D073. Pour une offre déjà publiée, appliquer les règles de clôture D068 : une demande de retrait avant publication ne permet pas de contourner ce parcours ni d'effacer les suivis.

### Contrôles à prévoir — aucune preuve applicative

| Cas | Résultat attendu |
|---|---|
| Auteur demande retrait de sa proposition non publiée | Demande adressée à la CME ; pas de suppression ou de rejet automatique |
| CME du même établissement traite la demande | Rejet avec motif prévu, proposition et historique conservés et consultables selon D071 |
| Autre membre tente de retirer une proposition dont il n'est pas auteur | Refus sans modification ni exposition non autorisée |
| Auteur tente de rejeter/supprimer directement | Refus, données conservées |
| CME d'un autre établissement tente de traiter | Refus sans modification ni exposition interne |
| Offre déjà publiée au moment du traitement | Ne pas appliquer ce rejet avant publication ; règles de clôture D068, suivis conservés |

Modalités de la demande, traitement d'une demande encore en attente, actions répétées et concurrence publication/retrait à spécifier selon D060 ; aucun automatisme supplémentaire décidé.

## Réexamen après rejet — Validé D073

Accord explicite du 25 octobre 2026 (« valider »). Si de nouveaux éléments justifient un réexamen, la CME du même établissement peut remettre la proposition rejetée « à corriger », avec un motif. L'auteur peut ensuite corriger et soumettre de nouveau : retour « en attente » selon D061, puis décision CME et conditions de publication D070 habituelles. Aucune réouverture autonome ni publication automatique par l'auteur.

Le rejet initial reste dans l'historique ; le motif de réexamen est distinct et ne remplace pas le précédent. Les droits D071 et les règles de doublons D072 restent applicables : un réexamen ne donne aucun accès supplémentaire et ne dispense pas de vérifier l'offre.

### Contrôles à prévoir — aucune preuve applicative

| Cas | Résultat attendu |
|---|---|
| CME du même établissement autorise réexamen justifié avec motif | Passage de rejetée à « à corriger », rejet initial conservé |
| Auteur tente de rouvrir ou soumettre directement une proposition encore rejetée | Refus ; rejet et contenu inchangés |
| Autre membre ou CME d'un autre établissement tente de rouvrir | Refus sans modification ni exposition non autorisée |
| Motif de réexamen absent | Transition refusée ; rejet initial conservé |
| Auteur corrige après autorisation puis soumet | Retour en attente, pas de publication automatique |
| CME prend ensuite une nouvelle décision | Parcours D061 et vérifications D070/D072, sans effacement du rejet initial |

Présentation et conservation détaillée de l'historique à spécifier ; aucun nouveau mécanisme technique choisi.

## Informations de soumission et qualification — Validé D070

Proposition explicitement validée le 25 octobre 2026 (« oui je valide »). Deux niveaux pour faciliter les contributions tout en rendant les offres publiées utilisables.

| Étape | Informations et règle validées |
|---|---|
| Soumettre | Intitulé, entreprise, type : stage, préembauche ou emploi |
| Fournir la source | Lien source, ou texte de l'annonce accompagné de sa provenance ; les deux ne sont pas exigés ensemble |
| Qualifier avant publication, CME | Pays/ville, mode présentiel/hybride/remote, compétences et niveau demandés, selon les informations disponibles |
| Qualifier un stage, CME | Durée et début souhaité lorsqu'ils sont indiqués |
| Permettre la candidature avant publication | Page de candidature, adresse professionnelle publiée ou instructions exploitables de l'annonce |

Une information de qualification absente reste « non précisé » ou « à confirmer » ; ne pas inventer durée, niveau, lieu ni restriction géographique. Cette seule absence ne bloque pas systématiquement la publication. Niveau bac+5 conservable avec exigence et écart signalés (D052) ; accessibilité depuis le Maroc inconnue publiable avec mention explicite après validation CME (D029). Ne pas inventer le consentement de l'entreprise à d'autres profils.

La CME demande correction selon D061 si aucun moyen exploitable ne permet de comprendre comment candidater ; ne pas publier dans cette situation. Un lien source peut aussi être le canal de candidature, s'il permet effectivement la démarche ; sa seule présence ne suffit pas. Cette vérification humaine ne garantit ni disponibilité permanente du canal ni résultat de la candidature. Aucun contact externe ou envoi automatique.

Exemple illustratif : stage Laravel exigeant bac+5, durée absente et page de candidature utilisable. Conserver « bac+5 demandé », signaler l'écart au public bac+2/+3 et afficher « durée non précisée » ; examen CME sans présumer l'éligibilité.

### Vérifications à prévoir — aucune preuve applicative

| Cas | Résultat attendu |
|---|---|
| Intitulé, entreprise, type ou source/provenance requis manquant | Soumission refusée avec explication du champ manquant ; aucune publication |
| Texte avec provenance, sans URL | Soumission possible si les autres informations requises sont présentes |
| Soumission sans moyen de candidature | Peut entrer en attente ; la CME demande correction avant publication |
| Tentative de publication sans moyen exploitable, même avec lien source | Publication refusée ; correction demandée, motif explicite selon D061 |
| Durée, lieu ou niveau absent, moyen de candidature exploitable | Valeur inconnue explicite ; pas de blocage pour cette seule absence, validation CME toujours nécessaire |
| Niveau bac+5 ou accessibilité inconnue | Exigence/écart ou incertitude affichés selon D052/D029, sans promesse d'éligibilité |
| Contributeur tente de contourner la qualification/publication | Refus selon permissions D060/D061 ; pas de publication directe |

Champs, formats, longueurs, validation des liens et détails d'interface à spécifier ; cette décision ne choisit pas un formulaire technique ni une collecte automatique. Les contrôles D060 de permissions, établissement, entrées et confidentialité restent à couvrir.

## Travail de la CME et informations supplémentaires proposés

Affichage complémentaire proposé : échéance quand connue et disponibilité observée, distinctes de la date de début. Les règles de clôture D068 restent applicables.

Liste de travail CME : propositions en attente, date de soumission, auteur et éléments manquants. Détail/commentaire/action accessibles sans ouvrir tous les dossiers apprenants. Temps de traitement et ancienneté du stock mesurables à terme ; aucun délai garanti ni alerte automatique décidé.

Historique : auteur, date, motif et versions utiles validés D068 pour clôture/réouverture/modifications. Extension aux autres actions et visibilité détaillée des traces à préciser ; pas de collecte intégrale inutile de données ni de copie de toute annonce par défaut. La validation de la CME n'est pas une certification juridique ou une garantie de fiabilité de l'employeur.

## Propositions en doublon — Validé D072

Accord explicite du 25 octobre 2026 (« oui je valide »). Pendant l'examen d'une proposition, la CME du même établissement vérifie manuellement si elle répète une offre existante. Conserver une seule offre dans le catalogue et rejeter la proposition répétée avec le motif « déjà présente », selon le rejet motivé D061. Pas de nouvel état de modération ni de système complexe de détection automatique requis au pilote.

Indiquer l'offre existante à l'auteur seulement s'il a le droit de la consulter (D071). La comparaison ou le motif de rejet ne donne aucun accès supplémentaire à une proposition non publiée d'autrui ni à un autre établissement. Conserver la décision de rejet et son motif dans le suivi de la proposition selon D061/D071. Aucun suivi de candidature supprimé ou fusionné automatiquement.

### Contrôles à prévoir — aucune preuve applicative

| Cas | Résultat attendu |
|---|---|
| CME confirme qu'une proposition répète une offre existante | Proposition rejetée avec motif « déjà présente », offre existante conservée, pas de seconde publication |
| Auteur autorisé à consulter l'offre existante | Référence consultable indiquée avec le motif |
| Auteur non autorisé à consulter l'offre existante | Motif accessible sur sa proposition, mais aucun lien/contenu interne inaccessible exposé ; accès direct toujours refusé |
| Suivis de candidatures déjà présents sur l'offre conservée | Aucun suivi supprimé, fusionné ni changé automatiquement par le rejet du doublon |
| Autre contributeur tente de rejeter comme doublon | Refus selon D061 ; seul le rôle CME autorisé prend cette décision |

Un intitulé similaire ne suffit pas à prouver que deux annonces sont la même opportunité : examen humain des informations disponibles, sans décision automatique. Nouvelle campagne/poste distinct reste une nouvelle offre selon D068. Doublons déjà publiés désormais encadrés par D077 ci-dessous ; D072 n'autorise pas leur suppression ou fusion automatique. Aucun outil automatique de rapprochement choisi.

## Doublons après publication — Validé D077

Accord explicite du 25 octobre 2026 (« je valides les deux propositions », arbitrage B). La CME du même établissement conserve l'offre de référence et clôture l'offre répétée avec motif explicite « doublon », sans annoncer une fin de recrutement. Appliquer la clôture D068 : retrait de la recherche courante, conservation de l'offre et des suivis existants. Les candidatures restent liées à leur offre d'origine, sans fusion, suppression ou changement automatique.

Indiquer la référence conservée seulement si l'utilisateur peut la consulter selon D071 et les droits d'établissement. Aucune comparaison entre établissements ne crée un droit d'accès. Cette règle complète le rejet de proposition en doublon D072 ; ce ne sont pas les mêmes transitions.

| Contrôle à prévoir | Résultat attendu, non encore testé |
|---|---|
| CME traite le doublon déjà publié | Offre répétée clôturée avec motif « doublon », référence conservée ; pas de faux message « recrutement terminé » |
| Suivi existant sur l'offre répétée | Même offre liée, état/notes/actions conservés ; mention de clôture selon D068, sans transfert automatique |
| Référence conservée inaccessible à l'utilisateur | Aucun lien ou contenu interne non autorisé exposé |
| Autre membre ou CME d'un autre établissement tente l'action | Refus sans modification ni exposition interne |

Représentation de la référence et protections contre répétition/concurrence à spécifier selon D060. Aucun système automatique de détection/fusion ajouté.

## Autres cas limites et vérifications proposés

- Doublon d'une proposition : rejet motivé D072 ; doublon déjà publié : clôture motivée D077, suivis conservés.
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

Parcours nominal et motifs D061, disponibilité/modifications D068, compléments D070–D073, retrait demandé D075 et doublons déjà publiés D077 validés dans les périmètres ci-dessus. Restent à spécifier : formats/limites précis des champs, visibilité/conservation détaillée des traces, détails de traitement des demandes et saisie rétrospective d'une candidature. D007 reste ouverte.
