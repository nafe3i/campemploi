# IA-Q03 — Classes, inscriptions et changements de classe

Date : 27 octobre 2026. Statut : **Proposed — comparaison préparatoire**. Mandat : D100. **Aucune option ni proposition CC01–CC08 n'est validée.** IA-Q01 P01–P06 D099 et IA-Q02 B/RP01–RP06 D100 restent acquis ; leurs modalités ouvertes ne sont pas tranchées ici.

## 1. Problème et périmètre

Déterminer combien de classes peuvent produire des droits courants pour un apprenant, comment une inscription devient effective et comment un changement retire les anciens accès sans perdre l'historique ni ouvrir des dossiers hors périmètre.

Le compte identifie une personne ; le rattachement l'autorise dans un établissement ; l'inscription la situe dans une classe de cet établissement ; l'affectation de référent donne à un formateur un périmètre de revue. Ces quatre relations ne se remplacent pas. La limite d'un établissement actif au pilote D099 ne fixe pas le nombre de classes simultanées.

Exemple fictif : P1 appartient à C1 de E1, T1 est référent de C1 ; P1 demande C2 de E1, référée par T2. La demande n'est pas le changement. Il faut décider si C1 et C2 peuvent être courantes simultanément, qui autorise la transition, à quel moment T1 perd le périmètre P1 et ce que T2 peut consulter. C3 appartient à E2 : rejoindre C3 relève aussi d'IA-Q04, sans copie automatique de dossier.

Cette préparation ne crée aucun rôle, code, migration, configuration, bibliothèque, politique JWT ou choix d'isolation/ORM. Les règles d'expiration/répétition des liens restent IA-Q06 ; concurrence IA-Q08, isolation IA-Q09, données/traces IA-Q11/12. Les fiches F/S ne sont pas renumérotées.

Sources locales : [décisions](../product/decisions.md), [spécification et matrice IA](identity-organization-access.md), [IA-Q01](ia-q01-account-membership-options.md), [IA-Q02](ia-q02-roles-permissions-options.md), [administration](../scope/establishment-administration.md), [revues](../scope/cv-portfolio-review.md), [première tranche](../scope/first-slice.md), [socle](socle-technique.md), [workflow](../workflow.md). Les documents de contexte précédemment adaptés sont des sources, pas des autorisations nouvelles.

## 2. Exigences acquises et besoins à confirmer

| Sujet | Exigence ACQUISE | Limite / UNKNOWN |
|---|---|---|
| Entrée apprenant | Compte individuel, demande via lien de classe réutilisable et validation CME avant accès interne D038/D059 | Pas de preuve d'appartenance par lien ; procédure précise des demandes et approbations ouverte |
| Administration | CME avec permission locale gère classes/rattachements/affectations de son établissement D056/D076/D078 | Autorité et procédure précise du changement d'inscription à arbitrer ; délégations/auto-actions IA-Q05/07 |
| Référent | Au plus un courant par classe, zéro temporairement ; un formateur peut référer plusieurs classes D078/D084 | Cela ne fixe pas les classes simultanées d'un apprenant |
| Revue par classe | Formateur affecté examine CV/portfolio des apprenants de ses classes ; CME couvre son établissement D058 | Aucun accès général aux candidatures ou bilans par la classe |
| Avis et contenu | Deux avis distincts, formateur/CME, par document ; nouvelle revue après modification D057/D083 | Traitement d'un changement de classe sur contenu inchangé non décidé par ces seules règles |
| Remplacement de référent | Retrait de l'ancienne affectation, autres droits indépendants conservés, avis/auteurs et validations sur contenu inchangé préservés D080/D081 | Remplacer un référent et déplacer un apprenant sont deux opérations différentes ; ne pas étendre automatiquement D081 |
| Retours historiques | Apprenant, CME locale et référent actuel consultent les retours selon D082 ; historique d'auteur sans droit courant | Périmètre exact lors d'une sortie/changement de classe à expliciter, surtout inter-établissements IA-Q04 |
| Absence de référent | Dépôt/avis CME possibles, aucun avis formateur positif automatique D084 | Aucun référent de substitution ni délai maximal inventé |
| Identité / établissement | D099 : identité globale, rattachements distincts, un actif au pilote ; pas de transfert/attribution automatique | Notion d'activité, réentrée et concurrence encore ouvertes |
| Droits effectifs | D100 : attributions locales dans rattachement courant/approuvé/autorisé, règles par action ; pas de nouveau cumul ni union suffisante pour action sensible | Une inscription historique ou une ancienne permission ne suffit pas ; point d'effet IA-Q08 |

**Pilote :** organiser les classes, approuver les demandes et affecter les référents pour les accès nécessaires à la tranche 1 ; anticiper la revue de tranche 2 sans la développer. Le corpus ne confirme pas le besoin de plusieurs classes simultanées pour un apprenant. Une progression d'année, une correction d'erreur, un redoublement ou une réinscription sont des scénarios raisonnables à examiner, pas des fonctionnalités déjà approuvées. Année/filière/promotion ne sont pas des identités de classe interchangeables par hypothèse.

**Futur conditionnel :** atelier transverse, groupe de projet, double cursus et affiliations pédagogiques multiples. Un atelier n'est pas nécessairement une classe ouvrant l'accès au dossier complet. Aucune simultanéité ni nouvel accès n'est acquis par cette liste.

## 3. Axes et cardinalités indépendants

| Relation / axe | Connu | À arbitrer |
|---|---|---|
| Classe → établissement | Une classe gérée dans son établissement D056/D059 | Identité durable, année/promotion, renommage/archivage et éventuel déplacement ; aucun déplacement acquis |
| Classe → apprenants | Plusieurs apprenants possibles via le même lien D059 | Capacité maximale, classe vide, fermeture des inscriptions |
| Apprenant dans un rattachement → classes courantes | Aucun nombre acquis | Au plus une ; plusieurs ; principale + participations distinctes |
| Apprenant → inscriptions historiques | Historique ne vaut pas accès courant D099/D100 | Épisodes successifs, réentrée même classe, périodes et conservation IA-Q12 |
| Classe → référent courant | 0..1 D078/D084 | Point d'effet/conflit du remplacement IA-Q08 |
| Formateur → classes référées | Plusieurs D078 | Pas de rôle référent global ni droit sur classe non affectée |
| Compte → demandes en attente | Aucune cardinalité précise acquise | Demandes multiples et répétées IA-Q06 ; l'attente ne consomme pas automatiquement une place active |
| Validité d'une inscription | À distinguer de la demande et de l'historique | Préconditions d'activité, approbation, début/fin, retrait/suspension, absence temporaire de classe |

On ne peut pas conclure « exactement une classe à tout instant » à partir de « au plus une ». La période avant première approbation existe sans droit interne D038. Le cas d'un membre déjà approuvé temporairement sans classe doit être décidé séparément ; aucune suppression automatique de ses droits d'établissement n'est déduite ici.

## 4. Modèles possibles

### A — Inscriptions distinctes avec historique, au plus une classe courante au pilote

L'inscription est une relation locale dont on distingue demande, validité courante et épisodes terminés. Le compte et le rattachement établissement ne sont pas réécrits lors d'un changement de classe. Au pilote, au plus une inscription courante d'apprenant dans le rattachement ; une demande concurrente n'est pas une seconde inscription effective.

Avantages : parcours et responsabilité de revue lisibles ; un périmètre de classe courant, moins de cas de double revue ; suivi des mouvements sans effacer les auteurs. Coûts : assurer la cohérence d'unicité et du changement ; définir l'absence temporaire et la réentrée. Limite : ne couvre pas d'emblée double cursus ou deux classes métier actives. La restriction serait une règle du pilote explicitement validée, pas une limitation permanente de représentation.

Sécurité : ancien et nouveau périmètres doivent être évalués selon leur validité, sans union d'historiques ; cette simplicité ne dispense pas des droits par ressource. Une simple colonne de classe remplacée sans histoire ne suffirait pas au suivi des transitions ; ce raccourci n'est pas une variante recommandée. Aucun schéma SQL imposé.

### B — Plusieurs inscriptions de classe courantes dans le même établissement

Un apprenant peut être inscrit simultanément dans plusieurs classes. Chaque classe garde au plus un référent, mais plusieurs référents peuvent devenir concernés par les documents d'une même personne.

Avantages : double cursus et groupes pédagogiques simultanés représentés directement. Coûts : définir précisément qui porte l'avis formateur, si plusieurs référents peuvent consulter les mêmes documents, comment retirer une inscription et conserver une autre. D057 n'autorise pas implicitement plusieurs avis formateur concurrents ni une règle « premier avis gagné ».

Risque : si chaque inscription ouvre mécaniquement tous les documents à chaque référent, le partage augmente. D100 exige des conditions par action ; plusieurs responsabilités ou classes ne suffisent pas à résoudre le conflit. La simultanéité inter-établissements reste distincte et n'est pas autorisée au pilote D099.

### C — Une classe principale de revue et des participations secondaires distinctes

Une relation principale détermine la classe de référence ; d'autres participations représenteraient projets/ateliers sans devenir automatiquement des inscriptions de revue. Il faut préciser quelle activité donne quel droit et qui peut la gérer.

Avantages : prépare les besoins transverses sans ouvrir tous les dossiers aux animateurs. Coûts : concepts, écrans et catalogue de droits supplémentaires ; distinguer principal/secondaire, changements de classe principale et conflits. Une étiquette « secondaire » sans règles n'est pas une protection. Aucun rôle animateur ni groupe supplémentaire n'est créé par cette étude.

Ce modèle est une évolution possible d'A si un besoin transverse est confirmé ; il peut aussi demander des décisions propres. Ne pas l'introduire au pilote pour un besoin encore hypothétique.

| Critère | A | B | C |
|---|---|---|---|
| Classes courantes de revue | Au plus une au pilote, zéro à encadrer | Plusieurs, responsabilité de revue à décider | Une principale ; participations d'une autre nature |
| Continuité d'historique | Épisodes distincts nécessaires | Plusieurs épisodes et recouvrements à distinguer | Historique de principale + participations |
| Accès des référents | Périmètre courant simple à expliciter | Risque d'élargissement à plusieurs référents | Dépend des droits propres aux participations |
| Double avis D057 | Aucun nouveau type d'avis requis | Porteur de l'avis formateur à arbitrer avant activation | Avis lié à la principale à confirmer |
| Simplicité pilote | Meilleure si une classe suffit | Coût sans besoin confirmé | Concepts supplémentaires sans besoin confirmé |
| Évolution | Restriction pilote révisable après décision | Capacité immédiate plus large | Extension ciblée si projets/ateliers réels |

Comparaison qualitative et recommandation de conception, sans coût chiffré ni besoin métier inventé. Les modèles historiques ne dispensent pas d'une politique de conservation IA-Q12.

## 5. Demandes et transitions — propositions de parcours

Ces parcours sont **PROPOSÉS** pour A et ne constituent pas des états SQL ou un workflow technique approuvé.

| Parcours | Préconditions à spécifier | Résultat proposé | Refus / dépendance |
|---|---|---|---|
| Première inscription | Compte individuel, demande visée, classe et établissement cohérents, approbation CME autorisée D059 | Inscription effective seulement lorsque rattachement et inscription satisfont leurs conditions | Ne pas imposer deux écrans/deux approbations distinctes ; articulation métier à préciser |
| Nouvelle demande pendant C1 | Demande C2 distincte de l'inscription C1 | Garder C1 jusqu'à changement approuvé ; C2 en attente sans droit nouveau | Possession du lien insuffisante D059 ; demandes répétées IA-Q06 |
| Changement C1 → C2 de E1 | CME avec permission locale autorisée, inscription source courante, cible admissible, pas d'acte sur soi-même tranché | Une transition cohérente termine C1 et rend C2 effective au point d'effet décidé | Aucun chevauchement sous A ; point d'effet/requêtes en cours IA-Q08 et mécanisme IA-Q09 ouverts |
| Réinscription dans C1 après sortie | Même identité/rattachement autorisé, nouvelle approbation dans un parcours à définir | Nouvel épisode identifiable, ancien épisode conservé selon IA-Q12 | Historique C1 ne vaut ni réactivation ni accès automatique ; pas d'unicité compte/classe « pour toujours » imposée |
| Changement C1 → C3 de E2 | IA-Q04 et D099 requis avant parcours | Demande distincte, aucun nouveau rôle/accès/dossier automatiquement transféré | Ce n'est pas un changement de classe local ; ne pas contourner limite d'un établissement actif |
| Sortie sans classe cible | Motif et pouvoir à définir | Variante 1 : maintenir rattachement avec droits d'établissement autorisés ; variante 2 : procédure explicite de fin/restriction | Aucun choix ici ; conséquences CV/revues et droits d'offres à arbitrer avant ce parcours |
| Renommage, archivage ou fusion de classe | Cycle de vie et portée à définir | Distinguer correction de libellé et mouvement des apprenants | Ne pas simuler un transfert par simple édition d'établissement de classe ; aucun déplacement collectif automatique |

Le maintien proposé de C1 pendant l'attente C2 ne s'applique pas si les droits C1 ont été retirés séparément : D100 prévaut. Un refus de demande ou un échec technique ne doit pas devenir un mouvement partiel non autorisé. Aucune programmation future d'effet, notification ou envoi externe n'est acquis.

## 6. Effets sur affectations, documents et autorisations

Un changement d'inscription déplace le périmètre de l'apprenant ; il ne remplace pas les référents des classes. Si T1 reste référent de C1, il conserve ses droits sur les autres apprenants de C1. L'accès à P1 par l'ancienne inscription doit cesser selon le point d'effet retenu ; T1 peut avoir un droit indépendant à réévaluer, sans accès général aux retours ou bilans.

| Ressource / action | Acquis à préserver | Proposition ou question propre au changement |
|---|---|---|
| CV/portfolio et retours de P1 | D058/D082 : apprenant concerné, CME locale, référent actuel dans le périmètre ; pas d'historique-auteur donnant accès | Sous A, proposer relais au référent de C2 et fin du seul accès issu de C1, y compris listes/fichiers/URL connues ; périmètre de continuité à approuver CC05 |
| Avis déjà rendus | Auteurs et anciens avis ne sont pas réattribués ; modification du contenu déclenche D057/D083 | Contenu inchangé : conserver validations sans remise à revalider, ou exiger nouvel avis formateur de destination ? Recommandation CC06 ci-dessous, non acquise par D081 seul |
| Document modifié pendant changement | Nouvelle revue des deux intervenants D057 ; aucune validation positive fabriquée | Qui peut finaliser une revue commencée avant effet ? Dépend d'IA-Q08 et du point d'effet retenu |
| Candidatures / offres | Droits personnels/CME et cycle D068 inchangés ; formateur sans accès général | Même établissement : pas de nouveau lecteur ni droit d'écriture CME par la classe ; fin du rattachement relève IA-Q04 |
| Bilans / accompagnements | D025/D080 : droits propres, pas de visibilité par la seule classe | Changement de classe sans transfert implicite de bilan ; droit indépendant réévalué sans l'élargir |
| Statistiques, listes et exports | D044/D045 et confidentialité conservés | Effectif à une date, classe courante et classe historique ne se confondent pas ; conventions de calcul/trace à décider IA-Q11/12 |
| Classe cible sans référent | D084 : dépôt/avis CME possibles, pas d'avis formateur automatique | Ne pas garder T1 comme référent implicite de P1 ; attente de revue manquante selon règle de validation qui sera retenue |

Pour CC06, deux options réelles : **V1**, changement de classe seul sans invalidation du contenu inchangé (continuité, pas de reprise artificielle ; le nouveau référent n'est pas auteur des anciens avis) ; **V2**, nouvelle appréciation formateur de destination exigée (reprise pédagogique, mais nouveau déclencheur de revue à formaliser et charge supplémentaire). Effets de V2 sur l'avis CME et statut global à décider si retenue. Ni modification de contenu ni avis en attente/non validé ne deviennent positifs sous V1.

La recommandation V1 ne rend pas une nouvelle appréciation libre du nouveau référent implicitement possible : droits de correction/révision d'un avis restent à spécifier. Aucune copie de documents, déplacement de ressources entre établissements ou conservation illimitée n'est choisi.

## 7. Conséquences JWT et PostgreSQL — garanties avant mécanismes

| Enjeu | Conséquence conceptuelle à examiner | Ce qui reste ouvert |
|---|---|---|
| Compte / rattachement / classe | Identité stable D099, inscription rattachée au bon périmètre local | Tables/clés/ORM, état d'activité et représentation des épisodes |
| A : au plus une courante | Si approuvé, garantie face à deux approbations C2/C4 concurrentes ; pas simple contrôle d'interface | Frontière d'unicité, protocole transactionnel, conflit/reprise IA-Q08/09 |
| Cohérence de cible | Classe et rattachement concernés dans le même établissement autorisé | Mécanisme de référence/contraintes, absence de référence inter-établissements |
| Historique et réentrée | Ne pas remplacer l'identité ni effacer l'ancien épisode pour créer le nouveau | Périodes, corrections, traces/durées/accès IA-Q12 ; pas de schéma ni event sourcing imposé |
| JWT encore valide | Les anciennes informations de classe ne suffisent pas à autoriser après fin des droits D100 | Claims, fraîcheur/cache/invalidation IA-Q08/10 ; ni nouveau JWT obligatoire ni lecture SQL systématique choisis |
| Changement et référent concurrents | Décider à quelle situation le contrôle s'applique ; aucun double accès résiduel présumé acceptable | Point d'effet, requêtes commencées, cohérence lecture/écriture IA-Q08 |
| Classe archivée / suppression | Conservation d'avis/auteurs et de références utiles à préserver | Archivage, suppression et rétention ; aucune cascade automatique |

Les contraintes doivent correspondre à la règle retenue ; une vérification d'une ligne ne garantit pas à elle seule toutes les relations et restrictions entre lignes. La [documentation PostgreSQL sur les contraintes](https://www.postgresql.org/docs/current/ddl-constraints.html) distingue ces portées ; aucun type de contrainte ni version n'est adopté ici.

Vérifier les autorisations sur les requêtes concernées et les fichiers, selon D060/D100, rejoint [OWASP Authorization](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html). Ce soutien technique ne décide ni des classes simultanées ni des droits métier du campus.

## 8. Recommandation argumentée — non adoptée

Je recommande **A : inscriptions locales distinctes avec historique et au plus une classe courante d'apprenant au pilote**, sans limitation permanente du modèle à cette seule cardinalité. Le besoin de simultanéité n'est pas établi ; B obligerait dès maintenant à résoudre plusieurs référents et le porteur de l'avis formateur. C reste une piste future si ateliers/projets sont confirmés, avec permissions propres.

Pour les changements locaux, recommander une demande séparée, approbation par CME avec permission locale dans son périmètre, et transition cohérente ancien/nouveau sans chevauchement effectif sous A. Le protocole, le point d'effet et les opérations en cours restent IA-Q08/09 ; aucune transaction ou isolation n'est sélectionnée.

Pour les documents inchangés, recommander V1 par continuité : conservation des validations et auteurs, sans fabriquer d'avis manquant. Cette règle est une proposition nouvelle CC06 pour le changement d'apprenant, distincte du remplacement de référent déjà décidé D081. L'absence temporaire de classe, l'archivage et les déplacements collectifs doivent rester explicitement ouverts tant que leurs règles ne sont pas décrites.

## 9. Propositions précises soumises à arbitrage D064

CC01–CC08 sont des propositions locales IA-Q03, pas des décisions acquises, ni des fiches F/S. Elles peuvent être approuvées séparément ; certaines réaffirment des limites existantes tout en proposant leur application au nouveau parcours.

| ID | Proposition à approuver ou modifier | Conséquences / limites |
|---|---|---|
| CC01 — Relations | Distinguer compte, rattachement établissement, demande et inscription de classe avec validité/historique | Pas de classe directement réécrite comme identité ; stockage, états et périodes non décidés |
| CC02 — Cardinalité pilote | Au plus une inscription de classe courante par apprenant dans le rattachement pendant le pilote ; demandes/historiques exclus du décompte courant | Garantie contre approbations concurrentes requise ; pas de capacité multi-classe activée ni de limite permanente ; zéro classe après approbation reste à arbitrer |
| CC03 — Autorité / attente | Changement local approuvé par CME avec permission locale ; une demande C2 ne modifie pas C1 et ne donne aucun accès C2 | D059 conservée ; ancien accès maintenu seulement tant qu'autorisé, aucune auto-approbation/délégation nouvelle |
| CC04 — Transition | Après approbation, fin de C1 et début de C2 cohérents au point d'effet, sans chevauchement effectif sous A ni état partiel accordant des droits | Conflit/échec sans mouvement non autorisé ; point d'effet/requêtes en cours IA-Q08 et mécanisme IA-Q09 ouverts |
| CC05 — Relais des accès | Référent de C2 prend le périmètre de revue/retours autorisé sur P1 ; T1 perd le seul accès issu de C1 à P1 | T1 garde autres apprenants/droits indépendants ; pas de bilan, candidature ou pouvoir supplémentaire ; D058/D082 et IA-Q04 préservés |
| CC06 — Avis inchangés | Retenir V1 : changement de classe seul sans remise à revalider des documents inchangés ; auteurs/avis conservés | Proposition nouvelle, pas extension silencieuse de D081 ; modification déclenche D057/D083 ; aucun avis positif créé ni droit de révision libre ajouté |
| CC07 — Réentrée | Une nouvelle entrée dans une ancienne classe nécessite une approbation ; épisodes historiques distincts du nouvel épisode effectif | Pas de réactivation/accès par historique seul ; modèle de conservation/rétention IA-Q12 ouvert |
| CC08 — Frontières | Distinguer mouvement local et changement d'établissement ; pas de copie de ressource, rôle, accompagnement ou permission automatique | IA-Q04 nécessaire avant parcours inter-établissements ; D099/D100/D068 conservées, cycle de vie des classes non décidé |

Approuver ces principes n'autoriserait pas leur implémentation, les parcours encore ouverts, ni les décisions IA-Q04–IA-Q12. Un futur besoin multi-classe nécessiterait nouvel arbitrage avec droits de revue, cardinalités et scénarios correspondants.

## 10. Scénarios, refus et preuves futures

Jeux fictifs E1/E2 ; C1/C2/C4 de E1, C3 de E2 ; P1 apprenant de C1 ; T1/T2 référents de C1/C2. Vérifier API directe, listes/compteurs, retours et fichiers, états avant/après, absence d'effet non autorisé. Aucun test applicatif exécuté.

| ID | Action / situation | Attente acquise ou proposition à vérifier après arbitrage |
|---|---|---|
| CC-S01 | Deux apprenants différents utilisent le même lien valide C1 | Deux demandes possibles, lien non consommé, validation requise D059 ; répétitions IA-Q06 |
| CC-S02 | P1 demande C2 pendant inscription C1 | Aucun transfert automatique D059 ; maintien courant C1 et attente C2 selon CC03 si approuvé |
| CC-S03 | Lien C2 expiré/désactivé/falsifié | Aucun accès ou changement accordé ; traitement de demande préexistante IA-Q06 ouvert |
| CC-S04 | CME sans permission locale ou membre E2 approuve mouvement local E1 | Aucun changement au titre d'un pouvoir absent ; pas de données exposées D056/D100 |
| CC-S05 | Changement C1 → C2 approuvé | Si CC02–CC05 approuvés : une inscription courante, relais T2 et fin de l'accès T1 à P1 ; mêmes auteurs |
| CC-S06 | T1 utilise ancien JWT / URL connue après effet | Pas de nouvel accès fondé sur l'inscription retirée D100 ; moment et traitement en cours IA-Q08 |
| CC-S07 | T1 reste référent C1 pour d'autres apprenants ou accompagnant autorisé | Droits indépendants évalués sans accès général au dossier de P1 ; ne pas retirer arbitrairement toute C1 |
| CC-S08 | CV inchangé puis document modifié autour du changement | Si CC06 approuvé : inchangé conservé ; modifié nouvelle revue D057/D083, pas d'avis manquant devenu positif |
| CC-S09 | C2 temporairement sans référent | D084 conservée, pas d'accès T1 par défaut ; validation selon avis réels et CC06 éventuel |
| CC-S10 | Deux approbations concurrentes vers C2 et C4 | Si CC02 approuvé : jamais deux inscriptions courantes ; conflit/résultat déterminé par IA-Q08/09, pas arbitrairement dans le test |
| CC-S11 | Échec au milieu du mouvement ou répétition de validation | Aucun état partiel non autorisé ; résultat de répétition à définir IA-Q06/08, pas d'idempotence universelle choisie |
| CC-S12 | Retour ultérieur de P1 en C1 | Si CC07 approuvé : approbation nouvelle, épisode antérieur non réactivé tacitement |
| CC-S13 | Tentative de C1 → C3 par modification de l'identifiant de classe | Pas de transfert inter-établissements ni attribution automatique D059/D099 ; IA-Q04 nécessaire |
| CC-S14 | Fin du rattachement E1 avec inscriptions historiques | Droits locaux non effectifs D099/D100 même si lien/avis historique existe |
| CC-S15 | Archive/renommage collectif ou apprenant approuvé sans classe | UNKNOWN : règle à arbitrer avant parcours ; aucun test ne choisit suppression, transfert ou droits résiduels |
| CC-S16 | Changement concurrent avec remplacement T2 ou revue déjà commencée | IA-Q08 : fixer point d'effet/écriture avant attente de test, pas de tolérance implicite à l'ancien contexte |

Ces scénarios ne sont pas des preuves d'une application développée. Les attentes conditionnelles restent telles jusqu'à approbation et précision des contrats ; permissions nominales de la matrice IA inchangées.

## 11. Registre des questions résiduelles et correspondance

| Question à garder ouverte | Options / conséquences | Dépendance |
|---|---|---|
| Zéro classe après approbation ? | Maintien de droits d'établissement explicites ou fin/restriction décidée ; impacts offres/documents à expliquer | IA-Q03 avant ce parcours |
| Classe, année, promotion, archivage ? | Même identité de classe durable ou nouvelle cohorte ; conservation des épisodes et liens à expliciter | IA-Q03/06/12 |
| Plusieurs demandes / demandes anciennes ? | Remplacement, coexistence ou fermeture explicite ; une approbation ne règle pas tacitement toutes les autres | IA-Q06/08 |
| Auto-action et pouvoir délégué ? | Abstention, autre acteur autorisé ou procédure limitée ; aucune nouvelle délégation | IA-Q05/07 |
| Date d'effet et requêtes en cours ? | Frontière et résultat de concurrence à comparer avant transaction/cache/JWT | IA-Q08/09/10 |
| Données anciennes et changement d'établissement ? | Conservation locale, accès personnel, portabilité éventuelle ; aucun partage automatique | IA-Q04/11/12 |
| Révision d'avis et futurs groupes multiples ? | Droits d'écriture, porteur de l'avis et conflits à définir ; ni cumul ni revue supplémentaire implicite | IA-Q02/03/05 et revues F09 |

| Unités / fonctionnalités existantes | Apport de cette préparation | Condition avant mise en œuvre |
|---|---|---|
| S03 ; socle Q05 | Relations, cardinalités et cohérence historique | IA-Q03 et IA-Q08/09/12 nécessaires au modèle concerné ; ORM ouvert |
| S04 ; F02 ; socle Q06 | Classe courante indépendante du JWT | Politique et point d'effet IA-Q08/10 avant tests applicatifs |
| S05 ; F01/F03/F04 ; socle Q07 | Administration locale, demandes, inscriptions, affectations | CC à arbitrer, IA-Q05/06/07 selon parcours ; pas de développement autorisé |
| F08/F09 | Relais de revue, droits sur anciens retours, avis inchangés | CC05/06 et contrats de revue avant tranche 2 |
| F05–F07/F10/F12–F14 | Absence d'élargissement des offres/candidatures/bilans/tableau par la classe | Règles métier acquises conservées, données/champs IA-Q11/12 |

Prochaine action : présenter A/B/C, risques et CC01–CC08 au CTO ; attendre arbitrage D064. Aucun passage automatique à IA-Q04 ni choix technique dépendant. BOARD reste le suivi de référence ; aucun second inventaire de fonctionnalités ou Issue créé.

## 12. Rapport documentaire de cette session D100

Fichiers réellement concernés : `README.md`, `docs/product/decisions.md`, `docs/specs/ia-q02-roles-permissions-options.md`, `docs/specs/identity-organization-access.md`, `docs/specs/socle-technique.md`, présente comparaison, `docs/plan-realisation.md`, `tracking/BOARD.md`, `tracking/STATUS.md`, `tracking/JOURNAL.md`.

Contrôles exécutés : dix fichiers Markdown, 76 liens locaux résolus ; encodage et blocs fermés ; D100 unique, registre antérieur conservé intégralement ; D059/D068/D064/D099 et fichier IA-Q01 inchangés. Les 42 lignes IA-A, 15 invariants IA-I, 20 scénarios IA-S, lignes IA-Q01/IA-Q04–IA-Q12 et identifiants/intitulés F/S sont identiques à HEAD avant ce travail. Huit propositions CC et seize scénarios CC-S uniques, six RP/dix RP-S conservés ; diff sans erreur d’espacement. Recherche ciblée de secrets et relecture manuelle sans anomalie détectée, sans garantie absolue. Publication D069 vérifiée : commit 6bdf7fd755efcba206dfec38b4e212a2c9462a4e sur origin/main le 27 octobre 2026, concordance exacte avec le commit local.

Aucun test/build applicatif : aucun code, migration ou configuration créé ; aucune nouvelle permission ni règle IA-Q03 validée. Les contrôles documentaires ne prouvent aucun comportement applicatif ; CC01–CC08 restent proposés. Publication documentaire vérifiée ; elle n’autorise aucune implémentation.
