# Identité / Organisation / Accès

Date : 27 octobre 2026. Statut de spécification : **Proposed**. Mandat documentaire et priorité : **D097 validée**. Mise à jour : principes IA-Q01 P01–P06 validés D099 ; préparation IA-Q02 autorisée, sans adoption de ses propositions.

## 1. Objectif, périmètre et limites

Construire une référence commune pour déterminer qui agit, dans quel établissement, sur quelle ressource et avec quels droits courants. Cette référence précède la politique JWT détaillée et les migrations métier. Elle consolide les règles acquises et rend visibles les arbitrages ; elle ne tranche aucune option nouvelle.

La rédaction, les matrices/scénarios et l'alignement documentaire sont autorisés D097. Aucun code, migration, configuration, ORM, fournisseur d'identité, politique JWT ou stratégie d'isolation n'est créé ou choisi. Les identifiants F00–F15 et S01–S06 restent inchangés. D059, D068 et D064 sont préservées intégralement.

Légende : **ACQUIS** = exigence validée avec référence ; **PROPOSÉ** = représentation ou mécanisme à valider ; **OUVERT/UNKNOWN** = règle ou information manquante. Le statut Proposed concerne le document complet ; il ne remet pas les exigences acquises en discussion. Aucun résultat applicatif ou statut Accepted n'est annoncé.

## 2. Sources et traçabilité des exigences

| Exigence acquise | Références et limites |
|---|---|
| Pilote interne, vision plusieurs établissements, trois tranches | D001/D002/D007/D034/D086 ; pas de développement simultané de toutes les tranches |
| Monolithe modulaire, responsabilités séparées, injection ciblée et JWT | D008/D093/D094 ; mécanismes détaillés ouverts |
| Inscription apprenant en attente, sans données internes avant approbation | D038, précisée par D056/D059 ; D039 historique modifiée par D056 |
| Administration générale par le porteur ; CME avec permission locale, rôles et rattachements locaux | D056/D076 ; aucun accès confidentiel automatique ; délégations détaillées ouvertes |
| Lien de classe partagé et réutilisable, expiration/désactivation/renouvellement | D059 ; compte individuel, validation CME, aucun changement automatique de classe |
| Contribution humaine et modération locale des offres | D031/D053/D061/D068/D070–D077 ; modération distincte de disponibilité |
| Formateur/responsable technique = même rôle ; référent = affectation de classe | D058/D078/D079 ; pas de rôle global « référent » donnant accès à tout |
| Remplacement, continuité et confidentialité des revues | D057/D080–D084 ; auteurs et avis conservés, droits courants réévalués |
| Candidatures personnelles et consultation CME locale | D019/D036/D037/D085 ; partage du brouillon, notes privées et modification CME non acquis |
| Accompagnement et bilans réservés aux acteurs concernés | D020–D027/D042 ; contexte d'accompagnement distinct de la revue par classe |
| Tableau du porteur sans ouverture des contenus confidentiels | D043–D045 ; champs/indicateurs et autres destinataires à spécifier |
| Contrôles par action, accord avant décision, suivi et preuves | D060/D064/D065/D069/D074/D095 ; aucune nouvelle gouvernance |
| Priorité de ce chantier et retrait immédiat malgré JWT valide | D097 ; modalités techniques non choisies |
| Identité globale stable, rattachements distincts, un actif au pilote, contexte unique, email vérifié/unique, fin des droits locaux sans transfert | D099 P01–P06 et compléments ; attente/activité/historique distincts, concurrence à garantir, email seul sans preuve de propriété historique |

Sources locales : [décisions](../product/decisions.md), [administration](../scope/establishment-administration.md), [revues CV/portfolio](../scope/cv-portfolio-review.md), [première tranche](../scope/first-slice.md), [offres](../scope/offer-lifecycle.md), [scope pilote](../scope/pilot.md), [socle](socle-technique.md), [principes](technical-guidelines.md), [workflow](../workflow.md) et [relecture d'architecture](../reviews/2026-10-27-architecture-cross-review.md).

Les anciennes mentions historiques « à préciser » ne priment pas sur une décision ultérieure explicite : D079 précise D055 ; D080/D082 précisent le remplacement ; D056 précise l'administration D039. Le présent document ne réécrit pas ces décisions.

## 3. Concepts : identité, appartenance, rôle et affectation

Un compte répond à « qui est cette personne dans le système ? ». Le rattachement répond à « à quel établissement appartient-elle dans ce contexte ? ». Un rôle décrit une responsabilité ; une affectation précise le périmètre d'une responsabilité. Aucun de ces éléments, isolément, ne donne accès à toutes les ressources.

Exemple fictif : une personne est formateur et référent de la classe C1 dans l'établissement E1. Elle peut examiner les CV de C1 selon D058, sans lire les bilans confiés à un autre accompagnant. Après remplacement, son compte et son rôle peuvent subsister, mais C1 n'est plus un périmètre accessible par cette affectation.

### 3.1 Modèle conceptuel proposé, indépendant du SQL

| Concept | Responsabilité | Acquis et questions |
|---|---|---|
| Compte | Identité individuelle, état et moyens de connexion | Identité globale et identifiant stable indépendant de l'email, email vérifié/unique modifiable D099 ; normalisation/récupération/réattribution et états exacts OUVERTS |
| Établissement | Frontière d'organisation et d'accès métier | Plusieurs établissements à prévoir ; création générale et administration locale D056 |
| Rattachement établissement | Relation entre un compte et un établissement, avec validité métier | Approbation avant accès D059 ; relations distinctes avec validité/histoire, au plus un actif au pilote D099 ; activité/états/périodes et concurrence OUVERTS |
| Attribution de rôle local | Responsabilité exercée dans un rattachement autorisé | Apprenant/CME/formateur connus ; représentation et cumul complet OUVERTS |
| Permission administrative locale | Pouvoir de gestion dans l'établissement | Distincte du rôle CME et cumulable avec lui D056 ; encodage OUVERT |
| Pouvoir d'administration générale | Création/désignation au niveau général | Portage D056 acquis ; bootstrap/récupération et représentation OUVERTS |
| Classe | Groupe organisé dans un établissement | Classes gérées localement ; structure année/filière et cycle de vie OUVERTS |
| Inscription en classe | Relation entre apprenant et classe, distincte de l'identité | Validation et absence de transfert automatique D059 ; simultanéité/historique OUVERTS |
| Affectation de référent | Relation formateur/classe autorisant la revue dans son périmètre courant | Un référent par classe, plusieurs classes possibles par formateur ; absence temporaire D084 |
| Lien de classe | Point d'entrée partagé pour demander un rattachement | Réutilisable D059 ; ce n'est ni une session de connexion ni une preuve d'appartenance |
| Invitation du personnel | Parcours individuel d'activation prévu D056 | Distinct du lien de classe ; validité, destinataire, répétitions OUVERTS |
| Demande de rattachement | Demande d'un compte, cible et examen local | Ne confère aucun accès interne avant approbation ; représentation OUVERTE |
| Ressource métier | Offre, document, avis, candidature, demande, bilan, indicateur | Propriété, établissement, contexte et états pertinents vérifiés selon chaque métier |

Ces concepts ne prescrivent pas douze tables ni une architecture Domain/Application/Infrastructure. Identité globale, rattachements distincts et au plus un actif au pilote sont acquis D099 ; plusieurs actifs futurs ne sont pas autorisés par cette capacité conceptuelle. Un utilisateur présent dans deux contextes hypothétiques n'obtient aucun droit croisé par ce seul fait.

```text
Compte ── Rattachement établissement ── Établissement ── Classe
                 │                                  │
          Rôle / permission locale            Inscription apprenant
                                                    │
Compte formateur ── Affectation de référent ───────── Classe

Lien de classe ── Demande individuelle ── Approbation locale
Invitation du personnel ── Activation personnelle (autre parcours)

Ressource métier ── propriétaire + établissement + contexte + état
```

Le dessin décrit des responsabilités et liens ; seules les cardinalités acquises du tableau suivant sont contraintes métier retenues.

### 3.2 Cardinalités connues et ouvertes

| Relation | Cardinalité connue | Ce qui ne doit pas être déduit |
|---|---|---|
| Établissement / classes | Plusieurs classes possibles ; chaque classe est gérée dans un établissement D056/D059 | Nombre minimal, limites, archivage ou transfert d'une classe OUVERTS |
| Classe / référent courant | Au plus un référent ; zéro temporairement possible D078/D084 | Durée maximale sans référent ou délégation automatique non décidées |
| Formateur / classes référées | Plusieurs classes possibles D078 | Aucun accès aux autres classes par son rôle seul |
| Classe / apprenants | Plusieurs personnes peuvent utiliser le même lien D059 | Nombre de classes simultanées par apprenant OUVERT |
| Compte / établissements actifs | Au plus un rattachement actif au pilote ; relations historiques distinctes D099 | Définition d’activité et garantie concurrente à formaliser ; pas de limite permanente ni simultanéité future autorisée |
| Compte / rôles dans un établissement | Cumul CME + permission d'administration locale explicitement permis D056 | Autres cumuls, auto-approbation et conflits d'intérêts OUVERTS |
| Lien partagé / demandes individuelles | Même lien réutilisé pour plusieurs comptes D059 | Usage unique, compte partagé ou accès automatique interdits par la règle acquise |
| Formateur / accompagnements | Accès selon demandes adressées/attribuées et rôle d'accompagnant D020–D025 | Aucun nombre maximal, transfert automatique ou lecture globale déduit |
| Document examiné / types d'avis | Avis CME et formateur distincts ; CV et portfolio séparés D057 | Deux types d'avis ne tranchent pas le cumul par une même personne ni toute cardinalité d'historique |

PROPOSÉ pour une représentation minimale : un objet « rattachement établissement » relie un compte et un établissement déterminés ; un objet « affectation » relie un formateur et une classe déterminés. Cela ne tranche pas le nombre de relations par compte ni leur stockage.

## 4. Invariants à préserver et exigences de contrôle

| ID | Invariant / exigence | Statut et référence |
|---|---|---|
| IA-I01 | Aucune donnée interne accordée par la seule inscription, connexion ou possession du lien de classe | ACQUIS D038/D059 |
| IA-I02 | L'acteur n'obtient pas un rôle, propriétaire ou établissement en falsifiant une entrée | ACQUIS D060 ; contrat exact à spécifier |
| IA-I03 | Chaque action respecte les droits sur la ressource et le périmètre d'établissement concerné | ACQUIS D060 ; mécanisme OUVERT |
| IA-I04 | Administration de comptes et accès aux données confidentielles restent séparés | ACQUIS D056/D025/D044 |
| IA-I05 | Aucune administration locale ne crée un administrateur général ou ne gère un autre établissement | ACQUIS D056 |
| IA-I06 | Au plus un référent courant par classe ; autre formateur non autorisé du seul fait d'une vacance | ACQUIS D078/D084 |
| IA-I07 | Remplacement retire les accès de l'affectation remplacée, préserve autres droits indépendants et auteurs/avis | ACQUIS D080–D082 |
| IA-I08 | Un contenu inchangé conserve ses validations lors du seul remplacement ; aucun avis positif fabriqué | ACQUIS D057/D081/D084 |
| IA-I09 | Droits réévalués à chaque accès ; un JWT encore valable ne prolonge pas une affectation retirée | ACQUIS D060/D080/D097 ; mécanisme OUVERT |
| IA-I10 | Lien de classe réutilisable, expirant/désactivable/renouvelable ; pas de transfert de classe automatique | ACQUIS D059 |
| IA-I11 | Modération et disponibilité restent distinctes ; clôture/version/doublon préservent les suivis selon leur règle | ACQUIS D068/D072/D077 |
| IA-I12 | Bilan d'un accompagnement et retours de revue sont deux périmètres différents | ACQUIS D025/D080/D082 |
| IA-I13 | Historique d'auteur ou indicateur d'activité ne vaut pas droit courant de lire le contenu | ACQUIS D044/D045/D080/D082 |
| IA-I14 | Une action refusée ne produit pas d'effet non autorisé ni de fuite par accès direct | ACQUIS D060 |
| IA-I15 | Une question ouverte ne devient pas une permission par défaut documentaire | ACQUIS D064 ; politique technique de refus T05 encore proposée |

## 5. Modèle d'autorisation proposé

Entrées conceptuelles : identité vérifiée, action, ressource, établissement concerné, rattachement courant et approuvé, responsabilités/permissions courantes, propriété, classe/affectation, état métier et contexte spécifique. Certains champs ne s'appliquent pas à toutes les actions : créer le premier établissement n'exige pas déjà un rattachement à cet établissement.

PROPOSÉ : des contrôles communs réutilisables pour l'identité et le contexte, des règles par action dans les cas d'utilisation, et des accès aux données bornés au périmètre. Le rôle seul ne suffit pas et un guard unique ne remplace pas les conditions de ressource. RBAC/ABAC décrivent ici rôle et attributs/relations ; aucun moteur de politiques ni bibliothèque n'est retenu.

La proposition de refus par défaut et de vérification systématique est cohérente avec [OWASP Authorization](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html). Les refus acquis viennent des règles du projet ; la factorisation, l'emplacement exact des politiques et leurs mécanismes restent à arbitrer.

Pour listes, détails, recherches, compteurs, exports et fichiers : vérifier le même périmètre pertinent, sélectionner les champs exposables et éviter de charger un contenu confidentiel pour ensuite le masquer uniquement dans l'interface. Codes HTTP et confidentialité de l'existence des ressources restent OUVERTS ; cette spécification fixe le contenu autorisé et les effets, pas un contrat HTTP définitif.

## 6. Matrice d'autorisations

Résultats : **A** = autorisation acquise sous les préconditions indiquées ; **R** = refus acquis pour ce motif ; **U** = autorisation ou procédure non définie, aucune permission nouvelle accordée ici. Les acteurs portent uniquement les droits du contexte décrit ; un cumul éventuel se réévalue séparément. Les parcours des tranches 2/3 sont des contraintes futures, pas des fonctionnalités réalisées dans le socle. Les lignes A expriment les droits nominaux acquis ; elles ne tranchent pas les actes sur soi-même et conflits de rôles IA-Q05, ni les situations de transfert IA-Q03/04.

### 6.1 Identité et organisation — tranche 1

| ID | Acteur | Action / ressource | Contexte et préconditions | Résultat / limite | Source |
|---|---|---|---|---|---|
| IA-A01 | Personne demandant un compte apprenant | S'inscrire | Compte individuel ; parcours technique à définir | A pour inscription, aucun accès interne acquis | D038 |
| IA-A02 | Compte connecté non approuvé | Lire une donnée interne | Rattachement non validé | R ; connexion seule insuffisante | D038/D059 |
| IA-A03 | Compte individuel | Demander rattachement via lien de classe | Lien valide selon politique à fixer, classe visée | A pour demande ; pas d'approbation ni changement automatique de classe | D059 |
| IA-A04 | CME avec permission locale | Générer/désactiver/renouveler le lien de classe | Classe de son établissement, identité/droits courants | A ; lien réutilisable, durée/mécanisme ouverts | D056/D059 |
| IA-A05 | CME avec permission locale | Valider un rattachement / gérer rôles locaux | Demande et personnes du périmètre autorisé | A ; pas de rôle général ni accès confidentiel implicite | D056 |
| IA-A06 | Administrateur général | Créer établissement et désigner CME/administration locale | Pouvoir général acquis, procédure initiale à préciser | A sur organisation ; aucun accès CV/bilan déduit | D056/D076 |
| IA-A07 | Administrateur local | Gérer classes, personnel invité, rattachements/rôles | Permission explicite, même établissement | A dans limites D056 ; délégations fines U | D056/D076 |
| IA-A08 | Administrateur local | Attribuer administration générale / gérer autre établissement | Pouvoir seulement local | R | D056 |
| IA-A09 | Personnel invité | Activer son compte et définir son mot de passe | Invitation le concernant, validité à définir | A pour principe ; modalités U, aucun partage de mot de passe par CME | D056 |
| IA-A10 | CME avec permission locale | Affecter/remplacer le référent | Classe et formateur dans périmètre autorisé ; règle d'unicité | A ; préserver avis/auteurs et autres droits | D078/D080 |
| IA-A11 | Autre membre / CME étrangère | Modifier une affectation locale | Absence de permission ou autre établissement | R, aucun changement | D056/D060/D078 |
| IA-A12 | Compte déjà rattaché | Changer de classe/établissement via un autre lien | Ancien rattachement existant | R pour changement automatique ; procédure de transfert U | D059 |
| IA-A13 | Tout compte | Voir/corriger états, rôles ou identités d'autrui hors pouvoir établi | Aucun droit spécifique acquis | U pour parcours non décrit ; aucune permission créée | D056/D064 |

### 6.2 Offres — tranche 1, sans redéfinir D068

| ID | Acteur | Action / ressource | Contexte et préconditions | Résultat / limite | Source |
|---|---|---|---|---|---|
| IA-A14 | Apprenant/personnel rattaché | Proposer une offre | Établissement autorisé, champs D070 | A ; état en attente, aucun droit de publier | D031/D061/D070 |
| IA-A15 | Auteur de proposition | Consulter état/motifs, corriger puis soumettre | Sa proposition ; correction autorisée par le cycle | A dans ce parcours ; aucun accès aux propositions d'autrui | D061/D071/D073 |
| IA-A16 | Autre membre, y compris référent de l'auteur | Lire proposition non publiée | Ni auteur ni CME autorisée | R ; classe seule insuffisante | D071 |
| IA-A17 | CME locale | Examiner/publier/corriger/rejeter | Même établissement ; préconditions et motifs du cycle | A ; moyen de candidature exploitable avant publication | D061/D070 |
| IA-A18 | Membre rattaché | Consulter offre publiée | Son établissement et état visible selon cycle | A ; incertitude géographique/niveau explicitée, pas éligibilité garantie | D029/D052/D071 |
| IA-A19 | CME d'un autre établissement | Lire/modérer une offre interne étrangère | Identifiant connu mais périmètre étranger | R, y compris URL directe | D060/D071 |
| IA-A20 | Auteur / membre autorisé | Demander retrait avant publication / signaler | Propriété pour retrait, offre accessible pour signalement | A pour demande/signalement, pas mutation directe de publication | D068/D075 |
| IA-A21 | CME locale | Clôturer/rouvrir/modifier une offre publiée, traiter doublon/réexamen | Préconditions D068/D072–D077 ; auteur/date/motif requis selon action | A ; suivis préservés, pas fusion/suppression implicite | D068/D072–D077 |
| IA-A22 | Apprenant/formateur seul | Publier, clôturer ou rouvrir directement | Sans permission CME pertinente | R | D061/D068 |

### 6.3 Documents, candidatures et entreprises — tranche 2

| ID | Acteur | Action / ressource | Contexte et préconditions | Résultat / limite | Source |
|---|---|---|---|---|---|
| IA-A23 | Apprenant concerné | Déposer/remplacer/lire son CV, référencer son portfolio | Propriété/rattachement valides ; formats/limites à compléter | A ; pas de lien public CV | D041/D042/D057/D084 |
| IA-A24 | CME locale | Consulter documents et donner avis CME | Apprenant de son établissement | A ; avis formateur reste distinct, même si référent absent | D057/D058/D084 |
| IA-A25 | Référent courant | Lire/examiner CV/portfolio de ses classes | Affectation courante et même établissement | A sans demande préalable ; pas de droit aux autres classes | D058/D078/D079 |
| IA-A26 | Ancien référent | Lire documents/retours via ancienne affectation ou qualité d'auteur | Affectation terminée, aucun autre droit pertinent | R ; anciennes validations et auteurs conservés | D080–D082 |
| IA-A27 | Nouveau référent | Lire retours historiques de revue | Nouvelle affectation courante autorisée | A ; pas de réattribution d'avis ni lecture de bilans d'autrui | D080/D082 |
| IA-A28 | Autre apprenant/formateur non affecté | Lire CV/retours de revue | Ni propriétaire ni droit contextuel reconnu | R ; vacance du référent ne crée aucun droit | D058/D082/D084 |
| IA-A29 | Responsable technique destinataire d'un accompagnement | Consulter CV dans ce contexte | Demande adressée ; champs/documents pertinents à préciser | A pour accès CV prévu, pas accès général de classe ou retours de revue | D020/D042/D080 |
| IA-A30 | Apprenant concerné | Signaler changement portfolio, même URL | Son portfolio | A ; date/résumé, nouvelle revue portfolio, CV inchangé préservé | D083 |
| IA-A31 | Auteur d'avis / tiers | Réviser un avis existant ou modifier les retours d'autrui | Modalités non décidées | U pour correction d'avis ; aucune modification par tiers accordée | D057/D082 |
| IA-A32 | Apprenant concerné | Préparer/suivre ses candidatures | Droits personnels, rattachement et règles d'offre respectés | A même sans documents validés ; envoi réalisé par l'apprenant hors automatisation | D036/D037/D068/D085 |
| IA-A33 | CME locale | Consulter candidatures du suivi | Apprenants de son établissement | A pour suivi ; modification/envoi/notes privées/brouillon partagé non acquis | D019/D036/D037 |
| IA-A34 | Formateur seul / autre apprenant | Accéder globalement aux candidatures d'autrui | Aucun droit contextuel spécifique | R pour accès global | D019/D020/D037 |
| IA-A35 | CME / contributeurs autorisés | Ajouter / proposer une entreprise | CME locale ou proposition soumise à validation | A selon rôle ; aucun partenariat/collecte automatique déduit | D046 |

### 6.4 Accompagnement et pilotage — tranche 3

| ID | Acteur | Action / ressource | Contexte et préconditions | Résultat / limite | Source |
|---|---|---|---|---|---|
| IA-A36 | Apprenant | Adresser une demande à un responsable technique | Responsable choisi dans son établissement | A ; pas d'attribution préalable CME nécessaire | D020/D021 |
| IA-A37 | Responsable destinataire | Consulter/traiter demande, accepter ou demander réorientation | Demande qui lui est adressée/attribuée | A ; réattribution et absence de réponse U | D020–D023 |
| IA-A38 | Apprenant concerné / accompagnant du rendez-vous / CME locale | Lire bilan et remarques | Relation au rendez-vous ou rôle CME local | A pour ces seuls acteurs ; aucune lecture via simple classe | D025 |
| IA-A39 | Autre formateur/apprenant, même établissement | Lire bilan d'un autre accompagnement | Aucun des droits IA-A38 | R, même via progression/indicateur | D025/D027 |
| IA-A40 | Accompagnant / apprenant concerné | Rédiger/modifier ses propres observations | Auteur du contenu concerné | A ; pas de modification du texte de l'autre | D026 |
| IA-A41 | CME non accompagnante / autre gestionnaire | Modifier observations d'autrui ou gérer toutes les actions | Droit de consultation seul ou responsabilité non définie | U ; consultation ne donne pas écriture | D026/D027 |
| IA-A42 | Porteur avec droit de tableau | Lire indicateurs de suivi | Son établissement, champs autorisés à spécifier | A pour tableau ; pas de CV/contenu de bilan, score ou classement déduit | D043–D045 |

La liste de données personnelles consultables dans l'administration, les contenus de demande, les exports et les filtres détaillés doit être définie par parcours. Aucun accès « tout le profil », export complet ou politique de notes privées n'est déduit de la matrice.

## 7. Changements et retrait immédiat des droits

### 7.1 Sens du retrait demandé

ACQUIS D060/D080/D097 : après effet du remplacement autorisé, un nouvel accès ne doit pas être accordé sur la base de l'ancienne affectation, même avec un JWT encore valide. Les autres droits indépendants sont réévalués, pas supprimés globalement. La conservation d'un ancien avis ne conserve pas son droit de lecture.

Le retrait d'une permission n'implique pas nécessairement l'invalidation de tous les JWT ou la déconnexion globale. Le choix de ces mécanismes reste OUVERT. Un jeton valide apporte une identité vérifiée selon D094, sans figer les droits pour toute sa durée de vie.

Limite : des données déjà reçues ne peuvent pas être rendues inconnues à leur lecteur. Le traitement d'une requête en cours, d'une transaction ayant lu l'ancien contexte, d'un téléchargement déjà engagé ou d'un lien signé encore utilisable doit être arbitré IA-Q08 ; ne pas promettre une annulation rétroactive ou un « immédiatement » non défini.

PROPOSÉ comme référence vérifiable : point d'effet identifié par la validation atomique de la modification ; toute nouvelle évaluation d'accès après ce point utilise les droits courants. Pour les opérations concurrentes, définir si leur autorisation doit être réévaluée avant écriture/envoi du contenu et comment sérialiser les effets. Cette précision technique attend arbitrage, sans assouplir le refus déjà acquis.

### 7.2 Scénarios de changement

| Situation | Ce qui est acquis | Ce qui reste à décider |
|---|---|---|
| Remplacement de référent | Ancien privé du périmètre remplacé, nouveau prend relais ; avis/auteurs et validations inchangées si contenu inchangé | Point d'effet, concurrence, mécanisme de fraîcheur, éventuelle information UI |
| Formateur reste référent d'une autre classe | Son autre affectation peut continuer à autoriser les ressources correspondantes | Représentation technique et cache éventuel |
| Ancien référent aussi accompagnant | Évaluer les droits de ce rendez-vous séparément ; aucun accès global aux retours de revue restauré | Champs CV accessibles et fin d'un accompagnement |
| Classe temporairement sans référent | Dépôt et avis CME possibles, aucun avis formateur positif automatique | Délais et procédures d'affectation, sans délégation implicite |
| Demande de changement de classe | Un autre lien ne change pas automatiquement la classe D059 | Acteur validant le transfert, date d'effet, anciens retours, dossiers en cours, nouvelle revue éventuelle |
| Départ/changement d'établissement | Aucune nouvelle permission inter-établissements par simple demande | Conservation/rattachement des anciennes candidatures/documents/bilans, accès de l'ancien/nouveau personnel et portabilité |
| Retrait de rôle ou désactivation du compte | Contrôles de compte/droits courants requis D060 ; pas de droits forgés par JWT | Acteurs autorisés, statuts, effets globaux/locaux, restauration, traces et sessions |

Pour les transitions non décidées, exposer la question et bloquer l'implémentation dépendante ; ne pas copier automatiquement les données vers la nouvelle classe ou le nouvel établissement. Conserver un historique ne justifie pas de le rendre visible au nouvel acteur sans règle.

## 8. Scénarios de sécurité et preuves futures

Jeux entièrement fictifs : établissements E1/E2, classes C1/C2 de E1 et C3 de E2 ; apprenant P1 de C1 ; référent T1 remplacé par T2 ; T1 peut garder C2 ; CME locale L1 et CME étrangère L2. Ces données illustrent les règles et n'imposent pas une capacité métier nouvelle. La simultanéité multi-rattachement n'est pas activée par D099 ; ses scénarios restent conditionnels à une décision future.

Chaque preuve doit enregistrer version, contexte initial, action, résultat/refus et absence d'effets non autorisés. Vérifier API directe, listes et fichiers à la tranche correspondante ; une interface masquée ne suffit pas.

| ID | Scénario et précondition | Résultat attendu / arbitrage | Preuve à produire |
|---|---|---|---|
| IA-S01 | Compte connecté en attente demande une offre interne | Refus sans contenu, aucune mutation | Test API et absence d'effet |
| IA-S02 | Deux comptes utilisent le même lien de C1 encore valide | Deux demandes individuelles possibles ; aucun accès automatique ; lien non consommé par le premier | Parcours et données des demandes, politiques de répétition à fixer |
| IA-S03 | Lien expiré/désactivé ou falsifié | Ne pas accorder rattachement/accès ; présentation/reprise selon IA-Q06 | Tests négatifs, absence d'attribution |
| IA-S04 | P1 utilise un lien d'une autre classe alors qu'il est déjà rattaché | Pas de transfert automatique ; suite OUVERT selon IA-Q03 | Lecture avant/après, aucun mouvement implicite |
| IA-S05 | Administrateur local E1 tente de créer un administrateur général ou gérer E2 | Refus sans changement | API directe et base |
| IA-S06 | L2 connaît l'identifiant d'une ressource réservée E1 | Refus de lecture/action, sans fuite par liste/compteur | Tests de deux établissements fictifs |
| IA-S07 | T1 invoque sa classe pour lire la proposition non publiée de P1 | Refus ; auteur/CME seulement | Test par identifiant connu |
| IA-S08 | L1 remplace T1 par T2 ; T1 utilise son JWT antérieur encore valable | Refus du CV et des retours par l'ancienne affectation ; avis conservés | Test même jeton avant/après, prochain accès après effet |
| IA-S09 | Même remplacement, T1 garde une affectation sur C2 | Lecture de C2 selon ses droits indépendants ; pas de révocation globale arbitraire | Test positif de contrôle et négatif C1 |
| IA-S10 | T1 est accompagnant d'un rendez-vous autorisé après remplacement | Évaluation du bilan dans son contexte ; pas de lecture générale des retours C1 | Deux ressources distinctes, non régression |
| IA-S11 | T2 lit les retours historiques de C1 | Autorisé ; auteurs inchangés ; autre bilan non autorisé | Historique et refus de bilan étranger |
| IA-S12 | C1 sans référent, P1 dépose et L1 rend avis CME | Dépôt/avis CME possibles ; pas de double validation inventée | Parcours de tranche 2 et états/avis |
| IA-S13 | Deux demandes concurrentes affectent deux référents à C1 | Jamais deux référents courants ; échec/conflit explicite selon protocole à décider | Test concurrent et intégrité finale |
| IA-S14 | Retrait d'affectation concurrence une écriture/lecture autorisée initialement | Politique de point d'effet et requête en cours à fixer IA-Q08 ; aucun test ne l'invente | Scénario reproductible après arbitrage |
| IA-S15 | Client ajoute role, auteur, établissement ou publication à l'entrée | Aucun privilège/attribution illégitime | Test de requête forgée, base inchangée hors action autorisée |
| IA-S16 | JWT absent, expiré, altéré, mauvaise signature ou mauvais usage | Refus selon politique JWT future ; aucun contenu/effet | Tests de validation après IA-Q10 |
| IA-S17 | Apprenant consulte candidature d'autrui ou CME la modifie au titre de son droit de lecture | Aucun accès d'apprenant étranger ; pas de mutation CME déduite | Test personnel, local et inter-établissements |
| IA-S18 | Référent lit bilan d'un autre accompagnant via progression ou tableau | Refus du contenu ; présence d'indicateur ne l'autorise pas | Parcours et champs de réponse |
| IA-S19 | Offre clôturée/répétée, suivis existants liés | Règles D068/D077 conservées ; pas de nouvelle candidature depuis offre clôturée ni fusion/suppression des suivis | Tests métier des offres puis candidatures, sans anticiper une fonction livrée |
| IA-S20 | Changement d'établissement, simultanéité multi-rattachement ou double rôle CME/formateur | D099 interdit tout transfert/attribution automatique et limite le pilote ; cumuls et double approbation non décidés | Modalités D099 et arbitrages IA-Q02/04/05 ; simultanéité future à décider séparément |

Aucun de ces tests n'a été exécuté ; les comportements des parcours futurs seront vérifiés à leur tranche. Les cas U ont des attentes d'arbitrage, pas des assertions de comportement déjà décidées.

## 9. Cohérence, transactions et concurrence

Les garanties ci-dessous découlent des invariants ; le protocole SQL/ORM reste PROPOSÉ/OUVERT. Une transaction seule ne choisit pas la règle de conflit et ne garantit pas, sans conception adaptée, que des droits n'ont pas changé entre vérification et écriture. Les niveaux d'isolation PostgreSQL offrent des garanties différentes ; verrous, conditions atomiques et reprises sont à comparer. [PostgreSQL : isolation](https://www.postgresql.org/docs/current/transaction-iso.html)

| Opération | Garanties nécessaires | Arbitrage / dépendance |
|---|---|---|
| Approuver rattachement | Acteur local autorisé, cible cohérente, pas de privilège général ; cohérence entre approbation, relation et droits effectivement attribués | États et demandes répétées IA-Q03/06 ; unicité selon cardinalités décidées |
| Attribuer/retirer rôle local | Limite d'établissement/pouvoir de l'acteur respectée ; pas d'élargissement par course ou entrée forgée | Cumul IA-Q02/05, effet et traces IA-Q08/12 |
| Remplacer référent | Contrôle de permission et unicité, retrait ancien/relais nouveau cohérents ; avis et auteurs non réécrits | PROPOSÉ : fermeture ancienne affectation et ouverture nouvelle atomiques ; mécanisme/conflit IA-Q08/09 |
| Désactiver/renouveler lien de classe | Réutilisation du lien valide préservée ; demandes simultanées cohérentes avec la date d'effet | IA-Q06 : ancienne validité et demandes déjà soumises ; pas de consommation à usage unique |
| Changer classe/établissement | Ne jamais créer un état intermédiaire de partage inter-établissements ; ressources existantes préservées selon règles à définir | IA-Q03/04 avant migration/transition concernée |
| Contrôler une écriture métier | Vérifier droits et préconditions sur la ressource sans utiliser silencieusement un ancien contexte | Retrait concurrent IA-Q08, frontières transactionnelles IA-Q09 |
| Modifier état/version d'offre | État, historique et liens/suivis conformes à D068 ; pas d'écrasement silencieux | Conservation détaillée et protocole de version ouverts, indépendants de la présente modélisation |

PROPOSÉ pour les traces organisationnelles nouvelles : acteur, action, cible, contexte, moment d'effet et résultat utile, sans secret ni contenu confidentiel. D060/D065 imposent preuves/cohérence ; ils ne valident pas une conservation illimitée ni un module d'audit universel. Durée, accès aux traces et suppression sont IA-Q12.

Prévoir résultat explicite pour action répétée ou conflit : opération déjà effectuée, refus ou reprise contrôlée selon la règle décidée. Ne pas choisir une idempotence universelle ou promettre « exactement une fois ». Les réinitialisations de tests restent bornées à une base fictive, sans donnée réelle.

## 10. Alternatives de modèle et mécanismes — aucune sélection implicite

### 10.1 Comptes et établissements — principes IA-Q01 validés D099

[Comparaison IA-Q01](ia-q01-account-membership-options.md) préparée D098, principes P01–P06 approuvés D099 : identité globale stable indépendante de l'email ; rattachements distincts avec validité/historique ; au plus un actif au pilote sans limite permanente ; contexte unique et autorisé par action locale avec opérations générales séparées ; email vérifié et unique à la plateforme, modifiable sans changer l'identifiant ; fin de relation retirant ses droits sans supprimer l'identité ni transférer les ressources.

Demande en attente, relation active et historique ne sont pas confondus. Notion d'activité/garantie face aux approbations concurrentes, normalisation/récupération/réattribution email, réentrée et droits historiques restent ouverts dans leurs arbitrages. L'identité commune ne crée aucun partage, rôle ou nouveau rattachement automatique ; la possession d'une adresse ne suffit pas à prouver la propriété d'un compte historique. Les modalités JWT et d'isolation ne sont pas décidées.

### 10.2 Rôles et permissions — IA-Q02 en préparation

[Comparaison IA-Q02](ia-q02-roles-permissions-options.md), Proposed selon mandat D099 : rôle principal, attributions locales explicites et permissions personnalisables ; recommandation/RP01–RP06 à examiner avant nouvelle décision.

ACQUIS : CME + permission administrative locale possible ; formateur et responsable technique désignent le même rôle ; référent est une affectation. OUVERT : rôles multiples supplémentaires, conflits d'intérêts et actes sur soi-même.

| Option | Avantage | Conséquence |
|---|---|---|
| Un rôle métier principal, permissions administratives distinctes | Simplicité des parcours | Limite les autres cumuls ; transitions de rôle/historique à spécifier |
| Plusieurs rôles métier locaux explicites | Représente des responsabilités cumulées | Réévaluer chaque permission dans son contexte et définir conflits d'intérêts ; pas d'union aveugle |
| Profils prédéfinis assemblant des permissions | Peut rendre la délégation plus lisible | Catalogue et gouvernance à maintenir ; ne pas introduire un rôle « staff » tout-puissant |

Ces options ne remettent pas en cause le cumul déjà autorisé. Le cas d'une même personne rendant les deux avis CME/formateur est IA-Q05 ; deux avis distincts ne suffisent pas à décider si deux personnes différentes sont exigées.

### 10.3 Isolation et fraîcheur des droits

| Alternative | Intérêt | Points à démontrer avant choix |
|---|---|---|
| Tables partagées et contrôles applicatifs bornés | Migrations/exploitation centralisées | Contraintes et accès directs/listes/jointures respectent systématiquement le périmètre |
| Tables partagées avec RLS supplémentaire | Défense en profondeur sur les lignes | Rôles SQL, propriétaire/BYPASSRLS, contexte par connexion, pool, tâches et migrations correctement maîtrisés |
| Schémas par établissement | Espace logique séparé | Routage, connexions, migrations multiples, comptes globaux et erreurs de contexte |
| Bases par établissement | Frontière technique plus marquée | Exploitation, sauvegarde, migrations et besoins transversaux plus complexes |

RLS ne remplace pas les règles d'action et présente des exceptions selon le rôle SQL ; aucun mécanisme n'est adopté par cette comparaison. [PostgreSQL : sécurité des lignes](https://www.postgresql.org/docs/current/ddl-rowsecurity.html)

Pour des droits courants malgré JWT valide : lecture de l'état faisant autorité à l'autorisation ; cache avec invalidation/cohérence prouvée ; version de droits avec contrôle côté serveur sont des options à comparer. Une version incluse seulement dans le JWT ne prouve pas qu'elle est encore actuelle. Aucun Redis, moteur externe, cache, consultation SQL systématique ou révocation globale n'est choisi. Toute option doit satisfaire IA-I09 et la sémantique IA-Q08 retenue.

## 11. Dépendances pour JWT et les futures migrations

| Décision / invariant d'accès | Influence sur JWT et connexion | Influence sur PostgreSQL, sans migration créée |
|---|---|---|
| Principes IA-Q01 D099 et modalités ouvertes | Identité globale stable, contexte métier autorisé ; mécanismes JWT/récupération à définir | Compte global et relations distinctes, limite pilote et concurrence, email vérifié/unique ; contraintes précises et historique à définir |
| Rôles/permissions IA-Q02/05 | Éviter de figer les pouvoirs ; identifier l'action et les conflits | Attribution locale, portée et contraintes utiles |
| Transferts IA-Q03/04 | Contexte courant, données consultables et droits retirés | Validité temporelle, liens anciens/nouveaux, conservation sans copie non autorisée |
| Liens et activation IA-Q06/07 | Séparer JWT de connexion, lien de classe et invitation personnel | Validité/révocation, demandes, relations et bootstrap |
| Effet immédiat IA-Q08 | Fraîcheur des droits, sessions/jetons existants et éventuelles invalidations | Point d'effet et coordination atomique des opérations |
| Isolation IA-Q09 | Source de contexte autorisé, pas une simple valeur déclarée par le client | Partition logique, contraintes, compte SQL/pool et tests |
| Traçabilité/conservation IA-Q12 | Ne pas journaliser les secrets/jetons | Auteur/date et historique utile ; durées et accès à décider |

Une permission métier « retirée » et un JWT « révoqué » sont deux décisions distinctes. Les choix de signature, claims, stockage, expiration, renouvellement et récupération sont à détailler en politique JWT après les arbitrages qui conditionnent ces parcours. Les recommandations de validation JWT ne définissent pas les permissions métier. [RFC 8725](https://www.rfc-editor.org/rfc/rfc8725.txt)

Avant migrations métier : décisions applicables figées, règles de cohérence inter-établissements explicites, stratégie de concurrence documentée, preuve prévue sur PostgreSQL réel avec deux établissements fictifs. Driver/ORM et versions restent ouverts ; leur comparaison doit vérifier la capacité à réaliser ces garanties, pas déterminer les règles métier à leur place.

## 12. Registre — principes IA-Q01 acquis, modalités et autres arbitrages ouverts

Les identifiants IA-Q ci-dessous sont locaux à cette spécification ; ils ne remplacent ni Q01–Q09 du socle ni les fiches F/S. Aucune recommandation n'est une décision.

| ID | Question et options | Conséquences / recommandation à discuter | Bloque |
|---|---|---|---|
| IA-Q01 | Principes P01–P06 validés D099 ; activité et concurrence, modalités email/identification/réentrée encore ouvertes | Identité globale, relations distinctes, un actif au pilote, contexte unique, email vérifié/unique et fin des droits sans transfert ; ne pas confondre attente/activité/historique, pas de preuve de propriété par email seul | Principes acquis, modalités nécessaires avant identité persistée/JWT/migrations ; socle Q05/Q06/Q07 |
| IA-Q02 | Rôle principal, attributions locales ou permissions personnalisables ? | Préparation ia-q02-roles-permissions-options.md Proposed ; RP01–RP06 à discuter ; cumul CME/administration locale et rôle commun formateur acquis, autres cumuls non autorisés implicitement | Matrice technique et modèle de rôles ; Q07 |
| IA-Q03 | Combien de classes simultanées pour un apprenant ? Qui autorise un changement et quand ? | Comparer une classe active et plusieurs inscriptions ; préserver D059 sans transfert automatique ; définir historique et droits après changement | Rattachement/affectations, F03/F04, Q05/Q07 |
| IA-Q04 | Départ ou changement d'établissement : quels anciens dossiers et accès, quelles données rejoignent le nouveau contexte ? | Comparer conservation dans l'ancien périmètre, accès personnel limité et éventuelle portabilité explicite ; aucune copie/visibilité nouvelle par défaut | Transfert et conservation ; Q05/Q07/Q09 |
| IA-Q05 | Quels actes sur soi-même et conflits de rôles ? Une même personne peut-elle rendre les deux avis ? | Comparer séparation des personnes, récusation/délégation autorisée ou cumul encadré ; deux types d'avis distincts maintenus D057, aucun choix ici | Administration selon cas ; revues F09 avant tranche 2 |
| IA-Q06 | Lien de classe, demandes répétées et invitation personnel : durées, renouvellement, destinataires, validation concurrente ? | Séparer les parcours ; lien de classe réutilisable acquis, activation personnelle du personnel acquise ; préciser demandes déjà déposées et ancienne URL après renouvellement | F03/F04, S05, Q07 |
| IA-Q07 | Première administration générale/CME et récupération : procédure contrôlée hors web public, invitation initiale ou autre parcours limité ? | Comparer traçabilité, réexécution, secret initial et suppression/fermeture du bootstrap ; aucun endpoint public permanent proposé comme acquis | Première organisation F01/S05, Q06/Q07 |
| IA-Q08 | Retrait immédiat : point d'effet, requêtes/transferts en cours, cache, sessions et réattribution ? | Refus des nouveaux accès par ancienne affectation acquis ; recommander une frontière explicite avec tests avant/après/concurrents ; choix de mécanisme ouvert | Accès affectations, JWT et transactions S03–S05, Q05/Q06/Q07 |
| IA-Q09 | Isolation : tables partagées, RLS additionnelle, schémas ou bases séparées ? Quelle stratégie atomique/conflits ? | Comparer complexité et preuves de périmètre/concurrence ; base partagée reste une hypothèse, RLS non imposée | Persistance métier et accès, Q05/Q07 |
| IA-Q10 | Politique JWT/compte : transport, stockage, durées, renouvellement/révocation, récupération et états du compte ? | Faire découler la politique de IA-Q01/02/07/08 ; aucune durée, bibliothèque ou refresh token implicite | F02/S04, Q06 |
| IA-Q11 | Quels champs/existence/exports sont visibles et quelles erreurs éviteront une fuite ? | Réponses minimales et homogènes recommandées, comparer refus explicite ou masquage d'existence selon ressource ; code HTTP ouvert | Contrats et parcours concernés, Q03/Q07 |
| IA-Q12 | Traces, conservation, suppression et accès aux anciens rattachements/avis/bilans ? | D068/D080–D082 préservées ; comparer historique minimal et durées justifiées avec C11, sans stockage illimité implicite | Conservation/transferts et données réelles, Q05/Q09 |

Principes IA-Q01 acquis D099 ; ordre demandé : **IA-Q02**, puis **IA-Q03** ; traiter **IA-Q07/08/09** avant les décisions dépendantes de JWT et migrations. IA-Q04 est nécessaire avant le parcours de transfert, même si ce parcours n'est pas implémenté d'abord. IA-Q05 doit être tranchée avant un parcours autorisant un tel cumul ; aucune urgence artificielle de développer toutes les revues en tranche 1. Les options et engagements de chaque groupe restent soumis à D064.

## 13. Correspondance avec socle, fonctionnalités et suivi

| Référence existante | Apport de la présente spécification | Dépendances et limites |
|---|---|---|
| S01/S02 ; F00 | Frontières de responsabilité et contraintes de secrets/contexte | Structure/outillage peuvent être préparés ; pas d'authentification ou d'accès métier prétendu |
| S03 ; F00–F04 | Modèle conceptuel, cardinalités, invariants/transactions | IA-Q01/02/03/09 avant modèle métier concerné ; ORM non choisi |
| S04 ; F02 | Identité, droits courants et refus malgré jeton valide | IA-Q07/08/10 ; politique JWT complète reste à rédiger |
| S05 ; F01/F03/F04 | Bootstrap, gestion locale, inscriptions et référents | Matrice IA-A01–A13 et scénarios correspondants ; IA-Q01–Q09 selon parcours |
| S06 ; F00 et intégration aux offres | Revue de preuves/limites et vérification de périmètre | Aucun Accepted sans preuves, ni protection supposée pour module futur |
| F05–F07 | Permissions propositions/publications/cycle | IA-A14–A22 ; D068 intacte, transitions précises dans fiche d'offre |
| F08/F09 | Propriété, revue par classe, remplacement et confidentialité historique | IA-A23–A31 ; pas d'accès général via accompagnement ; IA-Q05 avant cumul |
| F10/F11 | Suivi personnel/CME et entreprises | IA-A32–A35 ; ni écriture CME sur candidature ni collecte automatique |
| F12/F13/F14 | Demandes, bilans, observations, indicateurs | IA-A36–A42 ; IA-Q11/12 et règles métier propres |
| F15 | Gouvernance des données et vérifications d'ouverture | C11/C12/Q09 du socle restent ouverts avant essais réels |

BOARD demeure la référence D095. Les F sont le catalogue fonctionnel proposé ; S sont les unités du socle proposées ; IA-I/A/S/Q identifient le contenu de cette spécification, sans nouvel inventaire parallèle de tâches. Aucun numéro de fiche existante, Issue ou PR n'est créé/renuméroté.

## 14. Critères de complétude documentaire et acceptation future

Livrable documentaire : concepts et cardinalités explicites, matrice traçable, scénarios acquis/ouverts séparés, alternatives avec conséquences, invariants/transactions, dépendances JWT/PostgreSQL, correspondance F/S et arbitrages. Le rapport associé indique les fichiers réellement modifiés et les vérifications effectivement réalisées.

Avant implémentation d'un parcours : ses questions bloquantes doivent être arbitrées et les contrats/actions concernés complétés ; ne pas choisir une option dans un test pour contourner D064. La seule validation de D097 n'autorise ni migrations, configuration, setup ni développement.

Avant Accepted : exécution réelle des critères applicables, tests pertinents réussis et revue traitée selon workflow ; permissions/isolation prouvées avec deux établissements fictifs, retrait des droits vérifié avec le même JWT valide selon politique décidée, absence d'effet après refus. Les parcours non encore développés restent des exigences futures et aucune preuve n'est déclarée pour eux.

Prochaine discussion : alternatives et propositions RP01–RP06 de la comparaison IA-Q02, puis préparation IA-Q03 après les choix nécessaires ; modalités IA-Q01 toujours ouvertes. Les décisions validées seront inscrites séparément et alignées section par section avant toute implémentation ; le reste de la spécification conservera son statut Proposed.
