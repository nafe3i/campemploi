# IA-Q04 — Départ, changement d'établissement et dossiers historiques

Date : 27 octobre 2026. Statut : **Proposed — comparaison préparatoire**. Mandat documentaire D101. **HP01–HP08 ne sont pas adoptés.** IA-Q01/02/03 et CC06/V1 restent acquis D099/D100/D101/D102 ; aucun code, migration, configuration, bibliothèque, ORM, mécanisme JWT, isolation ou protocole transactionnel choisi.

## 1. Question et distinctions fondamentales

Déterminer ce qui reste conservé, qui peut encore le consulter et ce qui pourrait être transmis après un départ. Ces questions ne sont pas équivalentes : garder une candidature dans E1 n'autorise ni l'ancien membre à la consulter, ni E2 à l'importer. L'identité globale ne transporte pas les permissions locales ni les dossiers.

Exemple fictif : P1 quitte E1 et demande E2. Son compte global reste identifiable ; la fin de son rattachement E1 retire les droits correspondants. E2 doit examiner une nouvelle demande. Le CV, les avis et les candidatures créés en E1 ne deviennent pas automatiquement des ressources E2. Un éventuel accès personnel après départ et un export sont des permissions distinctes à décider ici.

| Concept | Signification | Ce qui ne doit pas être déduit |
|---|---|---|
| Identité globale | Compte stable D099, email modifiable sans changer l'identifiant | Fin d'un rattachement ≠ suppression du compte ; email seul ≠ propriété d'un compte historique |
| Fin du rattachement | Fin des droits locaux correspondants D099/D100, au point d'effet encore ouvert IA-Q08 | Ni suppression automatique des ressources, ni approbation du nouvel établissement |
| Nouvelle demande / rattachement | Nouvelle relation examinée dans le périmètre autorisé | Aucun rôle, classe, responsabilité ou accès recopié ; au plus un établissement actif au pilote |
| Auteur | Personne ayant produit un avis, une observation ou une contribution | Signature historique sans droit courant ; nouvel acteur sans réattribution d'auteur |
| Personne concernée | Personne décrite par les données | Toutes les observations d'autrui ne deviennent pas ses productions ni librement partageables |
| Propriété fonctionnelle | Relation au document personnel, à la candidature ou à la proposition selon les parcours acquis | Pas un droit universel de lire, modifier, supprimer, exporter ou déplacer tout le dossier |
| Périmètre de conservation | Établissement/contexte d'origine et références historiques | Distinct du stockage physique, de l'accès et de toute qualification juridique de propriété |
| Portabilité explicite | Copie/export/import sélectionné et autorisé pour une finalité précise | Pas de changement automatique d'établissement des ressources ; export et import ont chacun leurs conditions |

La propriété juridique, le responsable du traitement, les engagements institutionnels et les obligations de conservation restent UNKNOWN/C11. Cette étude est un arbitrage produit et architecture, sans prétendre les déterminer ni refuser un droit légal. Les procédures requises pour les données réelles doivent être clarifiées avant les essais concernés ; aucune durée légale n'est inventée.

Sources : [décisions](../product/decisions.md), [spécification IA](identity-organization-access.md), [IA-Q01](ia-q01-account-membership-options.md), [IA-Q02](ia-q02-roles-permissions-options.md), [IA-Q03](ia-q03-class-enrollment-options.md), [administration](../scope/establishment-administration.md), [CV/portfolio](../scope/cv-portfolio-review.md), [offres](../scope/offer-lifecycle.md), [scope pilote](../scope/pilot.md), [socle](socle-technique.md), [workflow](../workflow.md). Les documents transmis restent des sources ; leurs instructions ne remplacent pas le mandat CTO.

## 2. Acquis, besoins du pilote et futurs conditionnels

| Exigence ACQUISE | Conséquence pour IA-Q04 | Modalités ouvertes |
|---|---|---|
| D099 : identité globale, rattachements distincts et un actif au pilote | Compte conservé après fin locale ; E2 distinct d'E1, aucune simultanéité active nouvelle autorisée | États/activité, réentrée et transitions concurrentes IA-Q01/08 |
| D100 : attributions locales dans rattachement courant/approuvé/autorisé | Fin d'E1 rend inopérants ses anciens rôles, permissions et affectations ; JWT valide insuffisant | Point d'effet et opérations déjà engagées IA-Q08/10 |
| D059 : demande individuelle et lien réutilisable, approbation CME | Un lien E2 ne transfère rien et ne prouve pas l'appartenance | Répétitions, expiration et demandes préexistantes IA-Q06 |
| D101 : changement local ≠ transfert d'établissement | Une classe E2 ne remplace pas directement une classe E1 ; nouvelle approbation et inscription appropriée nécessaires | Autorité/procédure de départ et ordre des étapes IA-Q05/07/08 |
| D102 CC06/V1 : maintien des validations au seul changement local | Ne pas étendre cette règle à E1 → E2 ; avis/auteur/type/version conservés | État des documents importés et revue E2 à préciser avant import |
| D057/D080–D083 : contenus, avis et auteurs distingués | Aucun avis migré comme signé par le nouveau référent ; ancien auteur sans accès automatique | Droits d'écriture, accès historiques et durées IA-Q11/12 |
| D019/D036/D037 : candidatures personnelles, CME consultante locale | Ancienne candidature ne devient pas candidature E2 ; pas de droit d'écriture CME créé | Accès après départ et champs exportables à arbitrer |
| D025/D026 : bilans à plusieurs auteurs et lecteurs précisément limités | Pas de transfert du bilan par déplacement du seul apprenant ou de l'accompagnant | Sort des demandes/rendez-vous en cours et accès après départ à décider |
| D068/D072/D077 : offres, versions et suivis préservés | Départ d'un auteur n'efface ni ne fusionne l'offre et les suivis liés | Conservation détaillée et successeur éditorial selon pouvoirs existants |
| D056/D044 : administration et consultation confidentielle distinctes | Gestionnaire de départ ou porteur ne devient pas lecteur universel des archives | Droits d'archive spécifiques à décrire par action avant ouverture |

**Besoin pilote confirmé :** protéger les périmètres dès la conception malgré une identité commune ; fermer les droits locaux sans perte automatique des références ; préparer les cas de départ avant leur mise en œuvre. Le corpus ne confirme ni portail alumni, ni accès ancien membre à tous ses anciens dossiers, ni import de dossier pédagogique dans un autre établissement.

**Scénarios futurs raisonnables, non validés comme fonctionnalités :** fin de formation, retrait du rattachement, erreur d'approbation corrigée, reprise après interruption, changement d'école, départ d'un formateur/CME, récupération d'un document personnel et demande de transmission volontaire. Départ définitif, suspension, désactivation globale du compte et effacement de données ne sont pas un même état par hypothèse.

## 3. Axes de décision — options combinables

| Axe | Alternatives | Conséquence à mesurer |
|---|---|---|
| Conservation des ressources | Origine E1 avec historique utile ; suppression sélective après politique ; dossier personnel séparé pour certaines productions | Références, versions, auteurs, confidentialité et durée ; aucune conservation éternelle implicite |
| Accès personnel après départ | Aucun accès métier via ancien rattachement ; accès personnel distinct limité ; maintien large du dossier | Continuité pour l'apprenant, nouveaux droits et surface exposée |
| Personnel restant dans E1 | Droits historiques explicitement définis par action ou absence d'accès faute de règle | Pas de lecture de tous les anciens membres par simple rôle administratif/CME |
| Portabilité | Aucune fonction au pilote ; export sélectionné ; export puis import approuvé | Copie, destinataire, consentement produit/pouvoir, contenus tiers et validité des avis |
| Nouvelle appartenance | Examen indépendant puis nouveaux droits explicites | Ne pas réactiver une période historique ni transporter un rôle |

La conservation à l'origine peut se combiner avec un accès personnel limité et un export. Choisir une option d'accès ne choisit ni stockage physique, ni durée, ni politique complète de suppression. La conservation d'un lien technique à une ressource ne doit pas révéler son contenu à un lecteur non autorisé.

## 4. Comparaison des modèles d'accès et de continuité

### A — Ressources dans l'origine, aucun accès métier de l'ancien membre après départ

Conserver les ressources utiles dans E1 selon une politique à définir ; fermer les droits issus du rattachement. Le compte global reste utilisable pour les opérations générales autorisées et la demande E2. L'ancien membre ne consulte pas son dossier E1 par un rôle historique.

Avantages : respecte directement la fin des droits locaux, peu de pouvoirs supplémentaires, séparation E1/E2 lisible. Limites : récupération du CV personnel et continuité de recherche plus difficiles ; une procédure de demande peut devenir nécessaire. L'absence d'accès applicatif automatique ne décide pas du traitement d'une demande relative aux données ni de sa réponse réglementaire.

Sécurité : ne pas remplacer le rattachement clos par un rôle « ancien membre » omnipotent. Le personnel E1 n'acquiert pas pour autant un droit d'archive global. Les procédures manuelles ne doivent pas contourner les contrôles d'identité ou envoyer le dossier à l'email simplement présenté.

### B — Conservation à l'origine et accès personnel distinct, limité et en lecture

Ajouter une autorisation personnelle explicitement définie, indépendante des anciens rôles locaux, pour certaines productions propres. Au périmètre minimal proposé : CV PDF déposé par l'apprenant et référence de portfolio déclarée, selon les versions encore conservées et exposables. Les dossiers d'autres personnes, offres internes, avis, commentaires, bilans et candidatures liés à des tiers ne sont pas inclus dans ce minimum.

Avantages : rend possible la récupération de ses documents sans rouvrir l'établissement ni partager avec E2 ; continuité d'usage mieux adaptée à la recherche d'emploi. Coûts : définir cette nouvelle permission, ses conditions d'ouverture/fin et les versions/champs exposables ; vérifier les fichiers et anciennes URL. Ce serait un droit produit nouveau soumis à HP05, pas une conséquence déjà acquise de l'identité globale.

Une inscription active E1 n'est pas maintenue artificiellement : cet accès distinct ne donne ni rôle E1, ni classe, ni visibilité sur ses autres ressources. Identité vérifiée, état du compte et autorisation personnelle doivent être réévalués ; les règles de récupération restent IA-Q01/07/10. Durée et retrait de ce droit restent IA-Q12 et doivent être fixés avant ouverture.

### C — Conservation à l'origine et portabilité explicite sélectionnée

Permettre une demande d'export de ressources éligibles ; une réutilisation/import dans E2 constitue ensuite une opération différente, dans un rattachement E2 autorisé. Le transfert ne réécrit pas l'établissement d'origine, ne vide pas E1 et ne transporte pas un avis positif comme validation E2.

Avantages : continuité volontaire et contrôle de la sélection/destination. Coûts : éligibilité par catégorie et champ, contenus de tiers, contrôle d'identité/destinataire, copies, provenance et traitement des échecs. Un export autorisé ne vaut pas autorisation d'import, de publication ou de suppression à l'origine.

Ce mécanisme peut compléter A ou B. Le dossier complet, les bilans coécrits et les annotations d'autrui ne sont pas présumés portables. Export déjà reçu et consultation future sont des réalités distinctes : retirer un accès n'efface pas une copie remise ; cela doit être expliqué avant envoi, sans promettre de rappel rétroactif.

| Critère | A | B | C |
|---|---|---|---|
| Fin des droits locaux | Respectée | Respectée, droit personnel séparé à approuver | Respectée, opération d'export distincte à autoriser |
| Récupération personnelle | Procédure dédiée éventuelle | Lecture limitée des productions éligibles | Copie choisie, sans accès permanent nécessaire |
| Confidentialité des tiers | Faible périmètre nouveau | Liste minimale à borner | Sélection/redaction et destinataire à contrôler |
| Continuité dans E2 | Aucun dossier transporté | Documents récupérables, aucune visibilité E2 automatique | Import explicite possible après décisions et approbation |
| Complexité relative | La plus faible | Autorisation personnelle et fichiers supplémentaires | Provenance, copies et parcours d'export/import supplémentaires |
| Risque principal | Perte d'accès utile malgré compte conservé | Portail personnel trop large ou sans durée | Dossier complet/copies partagés à tort, validation prétendument transférée |

Le maintien de tous les droits de l'ancien rattachement ou le déplacement automatique de tout le dossier ne sont pas des alternatives compatibles avec D099/D100. Aucun changement de ces acquis n'est proposé. Comparaison qualitative sans coûts ni besoin institutionnel inventés.

## 5. Devenir par catégorie de ressource

Chaque ligne distingue la conservation de la lecture et du transfert. Hors acquis cités, il s'agit de recommandations/UNKNOWN, pas d'une nouvelle matrice d'autorisations approuvée.

| Catégorie | Conservation proposée / acquis | Ancien membre / personnel d'origine | Portabilité proposée / questions |
|---|---|---|---|
| Compte / email / identité | Compte global conservé D099, fin locale sans suppression automatique | Opérations générales selon droits ; email seul sans preuve de propriété historique | Pas de duplication de compte E2 ni fusion automatique ; modalités de récupération ouvertes |
| Rattachements, inscriptions, attributions | Épisodes/requêtes distincts, historique utile selon IA-Q12 ; fin d'activité sans réactivation | Historique sans droit courant D099/D100/D101 ; pouvoir de consulter traces à préciser | Aucun rôle/classe/permission copié ; nouvelle relation approuvée |
| CV PDF personnel / portfolio déclaré | Garder provenance/version dans E1 tant que politique l'autorise ; pas de suppression automatique D099 | HP05 propose accès personnel distinct limité, personnel E1 sans droit nouveau sur ancien dossier | HP06 propose export demandé du seul contenu personnel éligible ; import E2 indépendant ; copie du site externe non acquise |
| Avis et retours de revue | Avis auteur réel/type/version, aucune réattribution D057/D080–D083/D102 | D082 fixe les lecteurs dans contexte autorisé ; ne prolonge pas à lui seul l'accès après fin du rattachement | Pas d'export/import des avis comme validation E2 ; champs historiques accessibles après départ restent IA-Q11/12 |
| Candidatures / brouillons / suivis | Garder périmètre d'origine et liens versions/offres sans fusion D068/D077 | Lecture/écriture personnelle et CME pendant contexte autorisé ; après départ et accès CME aux anciens apprenants à décider | Export par champs à étudier : texte propre ≠ annonce interne complète ou observations de tiers ; hors minimum HP05/06 |
| Offres / propositions / signalements | Ressources d'E1 et suivis conservés selon D068 ; départ de l'auteur ne clôture/supprime pas automatiquement | Pouvoir courant de modération requis ; ancienne qualité d'auteur insuffisante pour accès après départ | Aucune copie du catalogue E1 ni de ses propositions privées vers E2 ; contenu de source publique n'est pas un partage de l'objet interne |
| Demandes / rendez-vous / bilans | Conserver références/auteurs selon règles et durées à décider, sans transfert implicite | D025/D026 préservés ; traitement des rendez-vous en cours et lecteurs après départ ouverts | Dossier partagé ou coécrit non assimilé à une production personnelle librement exportable |
| Indicateurs / tableau / historiques d'activité | Historique utile selon finalité/durée, calculs à définir | Pas d'accès au contenu confidentiel déduit des indicateurs D044/D045 | Pas de score ou de profil pédagogique exporté automatiquement ; agrégats/champs IA-Q11/12 |

Pour un membre du personnel sortant, conserver l'auteur de ses avis/bilans ne conserve aucun rôle ni lecture locale. Le remplacement opérationnel d'une CME/référent suit les pouvoirs déjà acquis et les modalités IA-Q05/07/08 ; un successeur ne devient pas auteur des contenus de son prédécesseur.

La conservation n'est pas une durée illimitée : prévoir catégories, finalité, début du délai, durée, traitement à échéance et lecteurs, à arbitrer IA-Q12/C11. Sauvegardes, copies remises et stockage privé exigent leurs propres modalités ; aucune règle de purge, anonymisation ou cascade décidée ici.

## 6. Départ et nouvelle appartenance — séquences conceptuelles

| Étape / situation | Acquis | Proposition / arbitrage nécessaire |
|---|---|---|
| Demande de départ | Demande distincte de fin effective et de suppression d'identité | Qui peut initier/confirmer, justification, annulation et désaccord IA-Q05/07 ; aucune auto-fin décidée |
| Fin E1 | Retrait des droits correspondants D099/D100 ; ancien JWT insuffisant | Effet cohérent sur rôles, permissions, inscriptions et affectations ; pas de protocole ni ordre d'écritures choisi IA-Q08/09 |
| Demande E2 avant fin E1 | Une demande n'autorise pas E2 | Distinguer attente et activité ; approbation effective E2 ne doit pas créer deux établissements actifs au pilote |
| Approbation E2 | Examen local et droits explicitement accordés, sans copie des rôles/dossiers | Définir coordination/contrôle et résultat si E1 encore actif ; pas de transaction inter-établissements ou approbation automatique choisie |
| E1 terminé mais E2 refusé | Identité conservée, aucune attribution automatique | Compte éventuellement sans rattachement actif ; opérations générales et accès personnel éventuel selon politique distincte, pas maintien tacite E1 |
| Réentrée E1 | Nouvel examen, aucun accès par ancien épisode seul | Représentation des épisodes de rattachement IA-Q01 ; classe réapprouvée D101, rôles réattribués explicitement |
| Export personnel après départ | Aucun accès local hérité ni preuve par email seul | HP05/06 si approuvés, contenu/identité/destination/durée à préciser ; envoi externe soumis à autorisation explicite |
| Erreur de fermeture / correction | Ne pas réécrire silencieusement l'historique ni accorder droits hors pouvoir | Procédure de correction, revalidation et réattribution IA-Q05/07/08/12 ; pas de restauration générale automatique |

Ne pas ouvrir un instant de partage E1/E2 pour simplifier une transition. Inversement, absence de rattachement actif ne doit pas être présentée comme suppression du compte. Un accès personnel limité approuvé distinctement ne constitue pas un second rattachement actif et ne crée aucun rôle d'alumni.

## 7. Conséquences sur autorisations, JWT et données

| Sujet | Garantie à prévoir | Non décidé |
|---|---|---|
| Ressource d'origine et identité commune | Périmètre source, auteur et personne concernée distingués ; pas de changement du contexte ressource par identifiant utilisateur commun | Modèle SQL, clés, stockage, ORM et stratégie d'isolation |
| Historique | Conservation de références sans autorité courante ; pas de suppression d'auteur automatique | Durées, accès, effacement, pseudonymisation éventuelle IA-Q12/C11 |
| Accès personnel B | Nouvelle autorisation ciblée à approuver, pas réemploi d'un ancien rôle ni simple filtre « propriétaire » | Représentation, ouverture/retrait, catégories/versions/durée ; aucune table ou claim ajouté |
| JWT valide après départ | D099/D100 : nouveaux accès locaux refusés après effet, identité et droits distingués | Point d'effet/requêtes en cours, cache/renouvellement/révocation IA-Q08/10 |
| Lecture E2 et référence E1 | Listes, fichiers, exports, URL directes et jointures sans exposition croisée non autorisée | Contrats/champs/erreurs IA-Q11 et mécanismes IA-Q09 |
| Export / import | Contrôles séparés, sélection et origine conservées ; aucun avis positif E2 importé automatiquement | Format, destinataires, chiffrement éventuel, durée de téléchargement et rétention des copies temporaires |
| Opération interrompue/concurrente | Pas de double appartenance active ni d'effet non autorisé ; résultat explicite | Frontières transactionnelles, reprise, répétition, verrouillage et livraison IA-Q06/08/09 |

« Compte global » ne signifie pas « dossier global partagé ». Une référence historique ne devient ni jeton d'accès, ni lien public. Aucune promesse de retirer une copie déjà remise ; la fin des nouveaux accès et le devenir d'une copie sont des questions distinctes.

## 8. Recommandation argumentée — non adoptée

Je recommande une combinaison ciblée : **conservation dans le périmètre d'origine avec politique par catégorie, accès personnel B au périmètre minimal CV/portfolio propre, et portabilité C uniquement sur sélection explicitement autorisée**. Aucun maintien des rôles locaux ni partage E2 par continuité d'identité.

Pourquoi : A est simple pour la séparation, mais prive l'ancien apprenant de documents personnels utiles alors que son compte subsiste. B limité à ses propres dépôts et référence de portfolio rend ce besoin lisible sans ouvrir les annotations de tiers, candidatures contextualisées ou bilans. L'export ciblé peut répondre à la récupération sans transporter un dossier pédagogique complet. Les contrats de durée, versions, récupération et fichiers sont néanmoins requis avant ouverture ; cette recommandation ne les décide pas.

Au pilote, recommander un périmètre restreint : consultation/récupération de productions personnelles éligibles seulement après les règles nécessaires ; pas d'outil de transfert de dossier E1 → E2 ni import automatique. La préparation d'un import plus large reste ultérieure et exige un nouvel arbitrage de ressources/champs, en plus de l'approbation du rattachement. Si le besoin d'accès personnel est reporté, A est une alternative explicite à choisir, sans présenter ce report comme validation de B.

La recommandation ne fixe aucune durée et ne rend aucun contenu accessible immédiatement. Les droits sur candidatures, avis, retours et bilans après départ restent à comparer par champ ; une approbation des principes ne suffirait pas à ouvrir ces catégories hors liste minimale.

## 9. Propositions précises soumises à approbation D064

HP01–HP08 sont des propositions IA-Q04, ni décisions acquises ni fiches F/S. Toute approbation future resterait documentaire tant qu'une implémentation n'est pas autorisée et ses dépendances arbitrées.

| ID | Proposition à approuver ou modifier | Conséquences / limites |
|---|---|---|
| HP01 — Séparation | Distinguer identité globale, fin E1, nouvelle demande/approbation E2, contexte ressource et droits sur les données | Réaffirme D099/D100 ; aucun rôle/classe/accès transporté, aucun compte supprimé par seule fin locale |
| HP02 — Origine et conservation | Garder les ressources et références dans leur périmètre d'origine selon politique par catégorie, sans suppression/transfert automatique | Pas de conservation illimitée ni choix juridique de propriété ; durée/lecteurs/échéance IA-Q12/C11 à fixer |
| HP03 — Fin et nouvelle entrée | Fin des droits locaux après effet ; demande E2 sans droits, approbation indépendante sans deux établissements actifs au pilote | Rôles et affectations réattribués explicitement ; point d'effet, autorités, concurrence et réentrée restent à spécifier |
| HP04 — Historique et personnel | Auteurs/avis/types/versions préservés sans donner accès ; pas de pouvoir d'archive global à CME, référent, porteur ou administrateur | Lecteurs E1 après départ à définir par action/ressource, D025/D056/D082 conservées ; pas de nouveau privilège approuvé par cette seule formulation |
| HP05 — Accès personnel minimal B | Prévoir une autorisation personnelle distincte, en lecture/récupération, sur CV PDF déposé par l'apprenant et référence de portfolio déclarée encore conservés et exposables | Nouveau droit à approuver ; pas d'ancien rôle actif, classe ou accès E1 général. Avis/retours, candidatures, offres et bilans exclus du minimum ; versions/durée/conditions d'ouverture à décider avant mise en œuvre |
| HP06 — Export ciblé | Prévoir une demande explicite de copie des seules productions éligibles HP05, avec identité et sélection autorisées | Pas de dossier complet ni de contenus tiers ; destinataire/canal/trace/durée à définir, aucun envoi externe sans instruction explicite ; pas d'import E2 autorisé par l'export |
| HP07 — Import et validations | Traiter toute réutilisation E2 comme un parcours distinct à faire approuver ; ne transférer ni validation E1, ni avis comme avis E2 | D102 limité au changement local ; pas d'import au pilote acquis, état initial/revue E2 et provenance à arbitrer avant parcours |
| HP08 — Contrats préalables | Avant ouverture, définir par catégorie conservation, accès, export/import, retrait et preuve, y compris fin du droit personnel | IA-Q05/07/08/10/11/12 et C11 selon le parcours ; aucune durée, protocole ou mécanisme choisi ici |

HP05 et HP06 sont des extensions de droits/parcours proposées : elles peuvent être rejetées ou reportées séparément au profit d'A. Leur approbation ne permettrait pas de combler une modalité manquante par un accès illimité. HP07 exige un futur arbitrage d'import et n'en autorise pas la construction.

## 10. Scénarios de sécurité et preuves futures

Données fictives uniquement : E1/E2 ; P1 apprenant sortant ; T1 formateur sortant ; L1 CME courante E1 ; L2 CME E2. Chaque preuve future doit vérifier action, identité, état, ressource, résultat/refus, absence d'effet non autorisé, listes et fichiers/API directe. Aucun test applicatif exécuté.

| ID | Situation | Attente acquise ou conditionnelle |
|---|---|---|
| HP-S01 | P1 quitte E1 et réutilise un JWT valide pour ses offres/documents internes | Aucun nouvel accès par rattachement clos D099/D100 ; point d'effet/requêtes commencées IA-Q08 |
| HP-S02 | P1 demande E2 avant fin d'E1 | Pas de droits E2 par demande ; pas de double établissement actif lors d'approbation au pilote |
| HP-S03 | E1 terminé, E2 refuse la demande | Identité globale conservée ; aucun rétablissement E1 ni rôle E2 automatique |
| HP-S04 | L2 connaît l'identifiant d'un CV/avis E1 de P1, qui a rejoint E2 | Aucun accès E1 par identité commune, y compris listes/fichiers et historique |
| HP-S05 | Ancien référent ou T1 invoque son avis signé pour lire l'ancien dossier | Auteur préservé sans droit local courant D080/D100 ; aucun accès au seul titre de l'avis |
| HP-S06 | L1 ou gestionnaire de comptes ouvre tous les dossiers des sortants | Aucune permission d'archive globale déduite ; lecteurs/actions à arbitrer avant parcours |
| HP-S07 | P1 consulte son CV après départ via accès personnel B | Si HP05 approuvé et modalités fixées : seulement son fichier/versions exposables, aucun rôle E1 recréé |
| HP-S08 | P1 tente d'inclure avis, bilan ou candidature contextualisée dans l'accès minimal B | Hors minimum HP05 : aucune nouvelle permission ; règles par catégorie à définir |
| HP-S09 | Nouveau détenteur d'un ancien email demande le CV historique | Email seul insuffisant D099 ; aucune récupération/attribution par cette seule preuve |
| HP-S10 | Demande d'export explicitement autorisée d'un CV personnel | Si HP06 et contrats approuvés : contenu sélectionné uniquement, destination/canal autorisés ; aucun dossier tiers |
| HP-S11 | Export autorisé puis L2 importe automatiquement avis E1 comme validation E2 | Aucun import ni avis positif E2 automatique ; D102 ne couvre pas E1 → E2 |
| HP-S12 | Retrait d'accès après téléchargement autorisé | Nouveaux accès refusés selon politique ; aucune promesse d'effacement de copie déjà reçue |
| HP-S13 | T1 quitte E1 avec avis/bilans et rendez-vous en cours | Auteurs conservés, droits locaux retirés ; reprise/annulation/réattribution des rendez-vous à arbitrer |
| HP-S14 | Départ de l'auteur d'offre avec candidatures liées | D068 conservée : pas de suppression/fusion/clôture automatique par son seul départ |
| HP-S15 | Deux approbations E2/E3 concurrentes pendant fin E1 | Limite D099 respectée ; conflit/point d'effet IA-Q08/09 à définir, pas de résultat inventé dans un test |
| HP-S16 | Export/revue commence avant départ et se termine après | Point d'effet et réévaluation à arbitrer IA-Q08 ; aucune tolérance implicite à l'ancien contexte |
| HP-S17 | Réentrée E1 après épisode historique clos | Nouvel examen/rôles explicites ; classe réapprouvée D101, aucune restauration générale automatique |
| HP-S18 | Fin de durée ou demande d'effacement du dossier | UNKNOWN IA-Q12/C11 : procédure/durées à définir ; ni purge automatique ni conservation éternelle décidée |

Les scénarios conditionnels ne créent pas d'autorisation. Les exigences acquises restent applicables même si un besoin fonctionnel est reporté. Aucun résultat Accepted ni preuve de système développé annoncé.

## 11. Questions résiduelles et dépendances

| Question ouverte | Options et conséquences | Avant quoi ? |
|---|---|---|
| Qui confirme un départ et traite une erreur ? | Demande personnelle, décision locale, autre acteur autorisé ; conflits et auto-actions sans délégation implicite | IA-Q05/07/08 avant procédure de fin |
| Accès personnel B : ouverture, fin et compte inactif ? | Permission limitée sous conditions explicites ou report A ; ni rattachement fictif ni accès perpétuel | HP05, IA-Q01/08/10/12 avant récupération |
| Versions/champs de documents exposables ? | Dépôt courant ou versions sélectionnées encore conservées, pas tous les historiques sans règle | IA-Q11/12 avant consultation/export |
| Anciens avis/candidatures/bilans, lecteurs E1 et personne concernée ? | Lecture sélective par catégorie, champs propres vs tiers ; aucun maintien par auteur/administration seuls | IA-Q04/11/12 avant archives étendues |
| Nouvelles revues et import E2 ? | Nouvelle revue locale, provenance et état initial à définir ; pas de validité pédagogique héritée | HP07, IA-Q05 et F09 avant import |
| Demandes/rendez-vous/actions encore ouverts ? | Maintien de références, annulation ou reprise approuvée selon métier ; pas de transfert tacite | IA-Q04/05/08 et F12/F13 |
| Durées, échéance, suppression et données réelles ? | Politique par catégorie, traitement des références et sauvegardes ; cadre institutionnel à confirmer | IA-Q12/C11/C12 avant essais concernés |
| Canal d'export, destinataire et copies temporaires ? | Procédure contrôlée ou mécanisme futur limité ; exposition, traçabilité et échec à analyser | IA-Q08/10/11/12 avant remise effective |

| Références existantes | Apport documentaire | Limite avant mise en œuvre |
|---|---|---|
| S03 ; socle Q05/Q07/Q09 ; F01/F03/F04 | Validité des relations et contexte d'origine, historique sans droit courant | Modalités IA-Q01/04/08/09/12 nécessaires au modèle concerné |
| S04 ; F02 ; socle Q06 | Identité conservée et refus malgré JWT valide ; accès personnel éventuel séparé | Aucun claim/mécanisme adopté ; IA-Q07/08/10 |
| S05 ; F01/F03/F04 | Départ, demande E2, réentrée et pouvoirs locaux | HP et modalités avant parcours ; pas d'écrans multi-établissements complets ajoutés |
| F08/F09/F10 | Productions personnelles, avis, candidatures et portée d'export | Nouvelle permission HP05/06 non adoptée ; import et validations ouverts |
| F05–F07/F12–F14/F15 | Offres et suivis, bilans, indicateurs et données réelles | D068/D025/D044 et C11/C12 conservés ; aucune livraison anticipée |

Prochaine discussion : A/B/C et HP01–HP08, notamment les nouveaux droits HP05/06, avant toute décision D064. IA-Q05–IA-Q12 restent ouverts ; cette préparation ne tranche ni les modalités IA-Q01–03 restantes ni un parcours d'import.

## 12. Rapport documentaire de la session D101/D102

Fichiers concernés : `README.md`, `docs/product/decisions.md`, `docs/specs/ia-q03-class-enrollment-options.md`, `docs/specs/identity-organization-access.md`, `docs/specs/socle-technique.md`, présente comparaison, `docs/plan-realisation.md`, `docs/scope/cv-portfolio-review.md`, `docs/scope/establishment-administration.md`, `tracking/BOARD.md`, `tracking/STATUS.md`, `tracking/JOURNAL.md`.

Contrôles exécutés : douze fichiers Markdown/84 liens locaux résolus ; encodage, blocs fermés et en-têtes de tableaux vérifiés. D101/D102 distinctes et uniques, ancien registre intégralement préservé ; blocs D059/D068/D064/D081/D099/D100 et fichiers IA-Q01/02 inchangés. Les 42 lignes IA-A, 15 invariants IA-I, 20 scénarios IA-S, lignes IA-Q01/02/05–IA-Q12 et identifiants/intitulés F/S sont identiques à HEAD avant ce travail. Huit CC acquis, seize CC-S conservés, huit HP proposés et dix-huit HP-S uniques. Diff sans erreur d’espacement ; recherche ciblée de secrets et relecture manuelle sans anomalie détectée, sans garantie absolue. Publication D069 vérifiée : commit 0f89f0dc672ef7fe409f37b8ec9fcd1fa7c7cdda sur origin/main le 27 octobre 2026, concordance exacte avec le commit local.

Aucun code, migration, configuration ou bibliothèque créé ; aucun test/build applicatif. D102 est une règle métier nouvelle approuvée, HP05/06 sont des droits proposés non adoptés. Les contrôles documentaires ne constituent aucune preuve applicative ; publication documentaire vérifiée, sans autorisation d’implémentation.
