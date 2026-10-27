# IA-Q01 — Compte, rattachements et contexte d'action

Date : 27 octobre 2026. Statut : **Proposed — arbitrage préparé, aucune option adoptée**. Mandat documentaire : D098. Référence de conception : [Identité / Organisation / Accès](identity-organization-access.md).

## 1. Problème reformulé et périmètre

La formulation précédente comparait ensemble des choix de nature différente. Un compte global peut avoir plusieurs rattachements distincts dans son histoire, un seul rattachement actif pendant le pilote, puis éventuellement plusieurs actifs après une décision future. Dans tous ces cas, une action métier peut être limitée à un seul contexte d'établissement vérifié. Ces propriétés ne sont pas contradictoires.

Cette étude prépare les décisions IA-Q01. Elle ne valide ni le modèle recommandé ni une capacité multi-rattachement en production. IA-Q02–IA-Q12 restent ouverts, en particulier cumuls de rôles, classes, transferts, conflits d'intérêts, invitations, bootstrap, retrait concurrent, isolation, JWT, champs exposés et conservation. D059/D068/D064 restent intégralement applicables. Aucun code, migration, configuration ou schéma SQL produit.

## 2. Cinq axes indépendants

| Axe | Question exacte | Options / distinction |
|---|---|---|
| Identité | Où existe le compte et qui peut gérer ses moyens de connexion ? | Identité de plateforme ou identité propre à chaque établissement ; cela ne choisit pas un fournisseur d'authentification |
| Rattachements | Combien de relations existent dans le temps, et combien sont actives simultanément ? | Plusieurs relations historiques possibles ; limite simultanée indépendante ; aucun nombre de rôles/classes déduit |
| Contexte | Dans quel périmètre cette action est-elle évaluée ? | Contexte unique vérifié, choix explicite s'il existe plusieurs rattachements ; opérations générales explicitement distinctes |
| Identification | Comment retrouve-t-on le compte lors de connexion, activation et récupération ? | Identifiant technique stable distinct de l'email ; unicité globale ou locale du login ; vérification et changements à préciser |
| Fin d'un rattachement | Que devient l'identité, et que deviennent droits et ressources ? | Fin des droits locaux distincte de fermeture du compte ; historique et accès aux anciens dossiers à traiter selon leurs règles |

Un « établissement actif » peut désigner l'établissement sélectionné dans l'interface ou l'unique rattachement valide du compte : nous emploierons **contexte de l'action** pour le premier et **rattachement actif** pour le second. Une relation historique conservée n'est pas un rattachement actif ni une autorisation actuelle.

## 3. Besoins établis et scénarios raisonnables

| Situation | Statut | Ce qu'elle exige réellement |
|---|---|---|
| Pilote dans un établissement, premiers essais restreints | ACQUIS D001/D034/D076 | Accès simples, approbation locale, fonctions administratives nécessaires ; aucun besoin démontré de rattachements simultanés pour les testeurs |
| Ouverture ultérieure à plusieurs écoles | ACQUIS pour la vision D002 | Séparer les établissements ; ne prouve pas qu'une personne doit appartenir simultanément à plusieurs |
| Compte apprenant déjà existant utilise le lien partagé d'une classe | ACQUIS D059 | Reconnexion/demande individuelle ; pas de compte de classe ni transfert automatique |
| Formateur intervient dans deux établissements | Scénario futur plausible, non validé | Met en évidence une éventuelle utilité de rattachements indépendants et d'un contexte par action |
| Personne quitte E1 puis rejoint E2 | Cas à préparer, règles non tranchées IA-Q04 | Retirer droits anciens sans copier ni partager automatiquement les dossiers |
| Personne revient dans E1 après un départ | Hypothèse d'évolution | Distinguer identité, relation et périodes ; réactivation et accès historiques non automatiques |
| Porteur administre la plateforme sans appartenir à une classe | Pouvoir général ACQUIS D056 | Opérations générales explicitement autorisées, sans accès métier confidentiel implicite |

L'hypothèse « apprenant dans E1, formateur dans E2 » sert à examiner le modèle, pas à autoriser ce cumul. Aucun nouveau parcours recruteur ni identité fédérée n'est ajouté. Aucun besoin commercial ou effectif futur non confirmé ne sert de justification à une infrastructure supplémentaire.

Sources métier : [vision](../product/vision.md), [administration](../scope/establishment-administration.md), [décisions](../product/decisions.md), [socle](socle-technique.md).

## 4. Combinaisons de modèles comparées

Toutes les combinaisons ci-dessous sont PROPOSÉES pour comparaison. La capacité historique et le contexte unique peuvent s'appliquer à plusieurs modèles.

| Modèle | Identité | Rattachements | Contexte d'une action métier | Positionnement |
|---|---|---|---|---|
| M1 — Compte local | Un compte distinct par établissement | Compte local à un établissement ; périodes à modéliser | Établissement du compte, toujours vérifié avec la ressource | Séparation administrative de l'identité forte, expérience multi-écoles plus coûteuse |
| M2 — Compte global, simultanéité limitée | Compte de plateforme indépendant d'un établissement | Relations distinctes dans le temps ; au plus une active selon la politique envisagée | Unique et vérifié, même s'il n'y a qu'un rattachement actif | Simplicité d'usage du pilote sans fusionner compte et appartenance |
| M3 — Compte global, plusieurs rattachements actifs | Même identité de plateforme | Plusieurs relations actives autorisées | Un contexte choisi et autorisé par action, sans union globale des droits | Besoin futur possible, parcours et cas de sécurité supplémentaires |

**M2 et M3 peuvent partager une structure conceptuelle.** Les rendre évolutifs ne consiste pas à ajouter dès maintenant tous les écrans et mécanismes de M3. La règle de simultanéité peut évoluer après décision et vérification ; ses garanties doivent néanmoins être prévues dans les contraintes et services futurs. Passer de M2 à M3 ne sera pas présenté comme un simple interrupteur sans tests ou reprise des règles.

### 4.1 Effets fonctionnels et d'exploitation

| Critère | M1 | M2 | M3 |
|---|---|---|---|
| Connexion courante | Établissement + login ou découverte d'organisation ; comptes multiples possibles | Un compte, contexte local simple | Un compte, choix du contexte lorsque plusieurs relations sont actives |
| Récupération | Limitée à l'identité locale ; plusieurs récupérations possibles pour une personne | Récupération de plateforme, distincte du rattachement | Même compte récupéré pour tous ses contextes, impact plus large à protéger |
| Départ puis nouvel établissement | Nouvelle identité ou rapprochement à gérer ; continuité plus complexe | Identité préservable ; fin/création de relations | Ajouter/retirer une relation sans retirer les autres, si autorisé |
| Support | Délimitation locale lisible, doublons et comptes oubliés | Responsabilité plateforme pour l'identité et locale pour les droits | Même séparation, avec davantage de cas de contexte et d'assistance |
| Évolution | Rapprochement de comptes souvent délicat | Prépare la continuité sans nécessiter la simultanéité | Capacité immédiate plus large que le besoin établi du pilote |
| Coût de conception relatif | Complexité de découverte/identités multiples | Charge proportionnée si limite du pilote explicite | Charge supérieure sur sélection, multi-onglets, retraits et tests |

Ces coûts sont une appréciation de conception, pas un benchmark ni un engagement de délai. Aucun des modèles n'est sûr par sa seule topologie d'identité.

### 4.2 Risques et mesures à spécifier

| Modèle / risque | Conséquence possible | Exigence ou proposition de maîtrise |
|---|---|---|
| M1 : mauvais établissement à la connexion ou récupération | Identification du mauvais compte ou confusion de périmètre | Distinguer namespace local et login ; pas de rapprochement automatique d'emails |
| M1 : même personne avec plusieurs comptes | Fusion erronée, anciennes permissions ou historique dissocié | Procédure explicite de rapprochement si un besoin apparaît ; non décidée ici |
| M2/M3 : compte global compromis | Plusieurs relations historiques ou actuelles potentiellement concernées | Protection de récupération/changement d'email au niveau plateforme ; aucune permission locale ne suffit à prendre le contrôle de l'identité globale |
| M2 : limite d'un rattachement actif vérifiée seulement par l'interface | Deux approbations concurrentes contournent la restriction proposée | Si retenue, garantie serveur/transactionnelle à définir et tester |
| M3 : contexte de l'interface différent du contexte de requête | Accès ou écriture dans le mauvais établissement | Contexte vérifiable pour chaque action et ressource ; pas de bascule silencieuse entre onglets |
| Tous : fin de rattachement sans retrait effectif | Ancien accès conservé malgré JWT valide | Exigence D060/D080/D097 ; mécanisme et concurrence restent IA-Q08/10 |
| Tous : utilisation de l'identité commune comme droit de partage | Dossiers E1 visibles à E2 | Propriété/périmètre de chaque ressource conservés, pas de union de droits ni transfert automatique |

La séparation de contexte et sa validation côté serveur sont cohérentes avec [OWASP Multi Tenant Security](https://cheatsheetseries.owasp.org/cheatsheets/Multi_Tenant_Security_Cheat_Sheet.html). Cette référence éclaire la comparaison ; elle n'impose ni stockage, middleware, JWT de tenant ou stratégie SQL particulière.

## 5. Contexte d'action : principe et alternatives de sélection

Recommandation PROPOSÉE : une action portant sur les données d'un établissement possède un contexte d'établissement unique, compatible avec la ressource et un droit courant de l'acteur. « Unique » concerne l'action, pas le nombre de relations de l'identité. La sélection ne vaut jamais autorisation.

| Sélection possible | Intérêt | Coût / risque à traiter |
|---|---|---|
| Contexte explicite dans la requête, validé côté serveur | Action identifiable, comportement multi-onglets explicite | Valeur client non fiable ; vérifier relation, action et ressource, sans confiance dans l'identifiant transmis |
| Contexte attaché à un état de connexion côté serveur | Parcours navigateur centralisé | Une bascule peut affecter un autre onglet ; cohérence et concurrence à définir |
| Contexte lié à un jeton dédié | Liaison de contexte possible à la vérification du jeton | Réémission, changements de droits et révocation à concevoir ; ne remplace pas les permissions courantes |
| Contexte dérivé d'une ressource cible | Peut convenir au détail d'une ressource | Listes/créations ont aussi besoin d'un périmètre ; ne pas lire un contenu confidentiel avant contrôle |

**Aucune de ces options de transport, état ou jeton n'est retenue.** IA-Q10 définit la politique JWT ; IA-Q09 définit l'isolation ; IA-Q08 définit la fraîcheur et la concurrence. Une exigence de contexte unique reste compatible avec plusieurs implémentations.

Pour le pilote, le seul rattachement approuvé pourrait préremplir le contexte de l'interface si la restriction proposée est approuvée. Le serveur le contrôlerait toujours. Pas de sélecteur multi-écoles nécessaire au pilote par ce seul principe ; comportement exact en absence de rattachement, changement en cours ou sélection périmée à spécifier.

Exceptions explicites : connexion, récupération du compte et opérations générales D056 ne sont pas artificiellement rattachées à une classe ou à un établissement. Elles ont leur propre autorisation et ne permettent aucune consultation globale des offres, CV ou bilans. Les tableaux multi-établissements et opérations métier transversales ne sont pas autorisés par l'exception.

## 6. Identification, unicité, activation et récupération

| Choix | Avantage | Conséquence et état |
|---|---|---|
| Identifiant technique stable, email modifiable comme moyen de contact/login | Historique et liens indépendants des changements d'adresse | Recommandé, non retenu ; type/génération de clé non choisis |
| Email comme clé d'identité immuable | Modèle apparent plus court | Changement d'adresse et réattribution de boîtes compliquent les liens ; non recommandé pour les relations métier |
| Login email unique à la plateforme pour un compte global | Recherche du compte et récupération plus simples | Politique de vérification, normalisation et conflit à définir ; empêcher découverte et prise de contrôle d'un compte existant |
| Unicité établissement + login pour comptes locaux | Même adresse possible dans plusieurs établissements | Établissement requis pour la bonne identité ; récupération et UX plus complexes |

Recommandation PROPOSÉE pour le modèle global : identifiant stable indépendant de l'email et un email de connexion vérifié, unique au niveau plateforme pour le périmètre des comptes concernés. Les règles exactes de normalisation, changement d'adresse, unicité après fermeture et adresses alternatives restent ouvertes. Ne pas assimiler possession d'une boîte email à appartenance institutionnelle ou à identité civile garantie.

La vérification d'adresse et la récupération de compte ont des exigences de sécurité à définir : contrôle de la nouvelle adresse, récupération après perte de l'adresse institutionnelle, réattribution d'une boîte, réponses évitant la découverte de comptes. Aucun canal, durée, jeton d'activation ou envoi effectif n'est choisi ici. [OWASP Authentication](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)

Pour D059 : le lien de classe reste partagé/réutilisable ; une personne se connecte à son compte individuel ou en crée un, puis demande l'approbation locale. Reconnaître le compte n'approuve pas la demande. Pour le personnel D056 : invitation et activation personnelles restent distinctes de la création des droits locaux. Si une adresse correspond à un compte existant, ne pas créer ni fusionner une identité ni rattacher ce compte sur cette seule correspondance ; procédure à définir avant ce parcours.

Proposition de séparation des responsabilités dans M2/M3 : la CME locale gère les relations/rôles autorisés de son établissement, sans réinitialiser les secrets du compte global ni voir ses autres affiliations par défaut. Les pouvoirs précis d'administration de l'identité globale restent IA-Q07/10/11 ; aucun rôle ou fournisseur nouveau n'est créé.

## 7. Conséquences sur JWT et les permissions

| Sujet | M1 | M2 | M3 |
|---|---|---|---|
| Identité authentifiée | Compte local dont le namespace doit être clair | Compte global distinct du contexte métier | Même identité globale, plusieurs droits locaux possibles |
| Contexte d'action | Vérifier établissement du compte, action et ressource | Vérifier rattachement actif unique si restriction retenue | Vérifier relation sélectionnée ; jamais union de toutes les relations |
| Fin d'une relation | Retirer ses accès locaux ; récupération de l'identité locale à décider | Le compte peut exister sans accès interne | Retirer seulement le périmètre terminé, autres droits indépendants réévalués |
| Reconnexion / renouvellement | Ne recrée pas une appartenance retirée | Ne réactive pas l'ancien rattachement | Ne rétablit aucun ancien contexte ni droit local |

JWT D094 reste acquis. Le modèle d'identité influencera le sujet authentifié et la vérification de contexte ; il ne tranche pas le contenu exact des claims, leur transport, durée, stockage, refresh token ou invalidation. Les contrôles cryptographiques et d'émetteur/destinataire sont à définir selon [RFC 8725](https://www.rfc-editor.org/rfc/rfc8725.txt), sans confondre destinataire du jeton et permission métier.

Un rattachement terminé doit cesser d'autoriser l'action concernée malgré un JWT valide selon D097. La manière de consulter l'état courant, la propagation de retrait, les requêtes déjà engagées et les éventuelles sessions restent IA-Q08/10. Le présent arbitrage ne peut pas les considérer résolus.

## 8. Conséquences conceptuelles sur PostgreSQL

Les relations ci-dessous sont des implications à vérifier après décision, pas des tables ou migrations validées.

| Aspect | M1 | M2/M3 |
|---|---|---|
| Référence d'identité | Compte local et établissement cohérents dans les références | Compte indépendant ; rattachement relie compte et établissement |
| Attribution locale | Compte local ou relation locale explicite | Attribution attachée au bon contexte local, pas automatiquement au compte global |
| Unicité du login | Clé dans le namespace décidé, souvent liée à l'établissement | Unicité de plateforme si l'option correspondante est approuvée |
| Historique de rattachement | Périodes éventuellement portées par relation locale | Relations/périodes distinctes ; existence historique ne signifie pas validité courante |
| Limite d'un actif | Peut découler du compte local sans empêcher plusieurs comptes pour une personne | Garantie spécifique si restriction pilote retenue ; approbations concurrentes à traiter |
| Ressource et acteur | Conserver établissement de la ressource et identité locale d'auteur | Conserver établissement de la ressource, auteur global et contexte pertinent ; identité commune ne déplace pas la ressource |
| Fin d'appartenance | Ne pas effacer l'auteur/historique par cascade non décidée | Fin de validité locale distincte de suppression d'identité ou de contenu |

Clés stables, unicité, références et contraintes de cohérence doivent matérialiser les règles retenues ; la capacité d'une contrainte dépend de sa portée et de l'opération. Un contrôle de lignes liées ou d'états concurrents ne se résout pas toujours par un simple CHECK. [Contraintes PostgreSQL](https://www.postgresql.org/docs/current/ddl-constraints.html)

OUVERT : relation unique par couple compte/établissement avec plusieurs périodes, ou relations successives par épisode ; dates/statuts ; règle de réentrée ; unicité sur login fermé ; audit et conservation. Ne pas fixer une unicité « compte/établissement pour toujours » sans traiter la réinscription.

Compte global ne signifie ni base partagée, ni RLS, ni connexion SQL globale. M2/M3 restent compatibles avec différentes organisations de données, dont les coûts de routage et d'intégrité changent ; IA-Q09 doit les comparer séparément. ORM et gestion du pool restent ouverts.

## 9. Départ, changement d'établissement et historiques

Scénario étudié : la même personne quitte E1 et souhaite rejoindre E2.

| Modèle | Enchaînement conceptuel | Risque à éviter |
|---|---|---|
| M1 | Mettre fin aux droits du compte E1 et créer/activer l'identité E2 selon procédure | Fusion d'identités sur email ou transfert de dossiers sans règle |
| M2 | Garder l'identité si option approuvée, terminer relation E1, examiner nouvelle demande E2 | Activer deux relations malgré restriction du pilote ; présenter fin E1 comme approbation E2 |
| M3 | Gérer indépendamment fin E1 et demande E2 ; coexistence possible seulement si autorisée | Réutiliser le rôle E1 en E2 ou laisser l'interface écrire dans l'ancien contexte |

Dans tous les modèles, D059 interdit le transfert automatique au moyen d'un nouveau lien. D068 conserve les offres et leurs suivis selon les règles acquises ; les avis/auteurs restent régis par D080–D082. Aucun dossier, historique de revue ou bilan ne rejoint le nouvel établissement par simple continuité de l'identité.

Recommandation PROPOSÉE : la fin d'un rattachement ne supprime pas à elle seule le compte global ni les références d'auteur ; elle retire les accès provenant de cette relation. Cela n'accorde pas un accès personnel perpétuel aux anciens dossiers. Consultation par l'ancien établissement, accès de l'ancien membre, éventuelle portabilité, suppression et durées restent IA-Q04/12. Fermeture globale du compte et changement de rattachement sont des opérations distinctes à spécifier.

Ne pas effacer immédiatement les rattachements pour « réinitialiser » la sécurité : les traces utiles et relations doivent rester cohérentes selon la politique à décider. Inversement, « historique » ne signifie pas conservation illimitée. Le responsable des données et le cadre des essais réels restent C11/C12, sans ouverture à des données réelles par cette étude.

## 10. Recommandation proportionnée — non adoptée

Je recommande comme cible conceptuelle **un compte de plateforme, des rattachements distincts et un contexte unique par action métier**. Pour le pilote, je recommande **au plus un rattachement d'établissement actif par compte**, tout en prévoyant que plusieurs relations puissent exister dans son histoire.

Justification : le pilote n'a pas de besoin confirmé de simultanéité multi-écoles. Séparer compte et rattachement évite de faire dépendre toute l'identité d'une classe ou d'une école, permet de concevoir le départ sans réécrire l'auteur des ressources et prépare raisonnablement l'ouverture. La restriction d'activité limite les parcours du pilote ; elle ne doit pas être une unicité à vie cachée.

Cette recommandation se situe entre M2 au pilote et une capacité conceptuelle pouvant évoluer vers M3. Elle ne promet ni simultanéité activée, ni migration gratuite, ni compatibilité déjà prouvée. L'ouverture de plusieurs rattachements actifs exigerait une décision future sur les parcours, le contexte, les conflits et les preuves. Aucun sélecteur multi-écoles, service IAM, synchronisation externe ou fusion de comptes n'est requis maintenant par cette proposition.

Coût accepté à discuter : identité et récupération de plateforme à protéger, relation d'appartenance explicite, garantie de la restriction pilote et examen des anciens dossiers. Si le besoin réel impose que chaque établissement contrôle intégralement son identité, M1 devrait être reconsidéré sur ce critère ; ce besoin n'est pas établi dans les décisions actuelles.

## 11. Décisions précises soumises à approbation

Les propositions P01–P06 sont des sous-questions de préparation IA-Q01, pas de nouveaux identifiants de tâches ni des décisions acquises. Chaque accord peut être donné séparément ou ajusté. IA-Q02–IA-Q12 restent ouverts après un éventuel accord sur IA-Q01.

| Proposition | Formulation à approuver ou modifier | Effet et limite |
|---|---|---|
| P01 — Identité | Retenir une identité de compte de plateforme, indépendante des établissements ; identifiant stable distinct de l'email | Influence les références d'auteur et la récupération ; aucun fournisseur, format de clé ou mécanisme JWT choisi |
| P02 — Relations | Représenter des rattachements distincts du compte, avec validité et histoire, sans imposer un seul établissement à vie | Prépare les relations futures ; épisodes/statuts et droits historiques restent à préciser |
| P03 — Pilote | Limiter le pilote à au plus un rattachement d'établissement actif par compte ; plusieurs actifs futurs nécessitent un accord distinct | Une plateforme avec deux établissements de test reste possible ; pouvoir administratif général D056 n'exige pas un rattachement local ni accès métier global |
| P04 — Contexte | Exiger un contexte d'établissement unique et autorisé pour chaque action métier locale, compatible avec la ressource ; opérations générales explicitement distinctes | Aucun rôle/droit croisé ; mode de sélection/transport, JWT et isolation restent à arbitrer |
| P05 — Identification | Pour le compte global proposé, retenir le principe d'un email de connexion vérifié et unique à la plateforme, modifiable sans changer l'identifiant stable | Ne tranche pas normalisation, adresses alternatives, cas de compte fermé, activation/récupération concrètes, ni pouvoirs d'administration ; ces règles bloquent leur implémentation |
| P06 — Fin de relation | La fin d'un rattachement retire ses droits sans supprimer à elle seule l'identité ou déplacer les ressources ; approbation d'un nouvel établissement distincte | D059/D068 conservées ; aucun accès historique perpétuel, durée, transfert de données ou mécanisme de révocation adopté |

P02/P03 combinent capacité conceptuelle et restriction du pilote ; elles ne sont pas deux alternatives exclusives. P05 dépend de P01 et devra être revue si un modèle local est choisi. P06 fixe une séparation de responsabilités proposée, sans clôturer IA-Q04/08/12. Si une réponse est ambiguë, D064 impose de clarifier avant d'appliquer la partie dépendante.

## 12. Points laissés ouverts et preuves à prévoir

IA-Q01 reste **OUVERT** tant que les propositions n'ont pas été approuvées. Paramètres restants : règles exactes du login/email et réattribution d'adresse, cycle de récupération, réentrée dans un établissement, droits lorsque tous les rattachements sont terminés, garantie de la restriction pilote et historique des épisodes.

IA-Q02–IA-Q12 restent **OUVERTS et inchangés** dans le registre de la spécification principale. L'étude peut exposer leurs dépendances sans choisir leur solution. En particulier : ni durée/refresh token, ni encodage du contexte dans JWT, ni base partagée/RLS, ni fusion automatique d'identités ou de dossiers.

Preuves futures après décision :

- Une personne en attente ou sans rattachement actif n'accède pas aux données internes ; opérations de compte prévues séparément.
- Même compte global hypothétique et deux établissements fictifs : aucun droit ou contenu traversant les contextes sans règle acquise.
- Deux approbations concurrentes ne contournent pas la restriction d'activité si P03 est retenue ; résultat du conflit à définir.
- Départ E1 et demande E2 : ni accès E1 maintenu par ancien JWT, ni activation E2 automatique, ni copie de dossier.
- Changement d'email et email institutionnel réattribué : identité/historique non déplacés et pas de prise de contrôle par simple correspondance d'adresse.
- Si la simultanéité est décidée ultérieurement : actions multi-onglets conservent leur contexte explicite, retrait E1 sans suppression des droits E2 autorisés.

Ces scénarios sont préparatoires, non exécutés. Ils ne valent pas des tests d'un code ou des migrations inexistants. La [spécification principale](identity-organization-access.md) et le [socle](socle-technique.md) gardent leur statut Proposed.

## 13. Vérification documentaire et conservation

Fichiers du périmètre : présente comparaison, section 10.1 et ligne IA-Q01 de la spécification principale, référence du socle, README, ajout du mandat D098 au registre et suivi BOARD/STATUS/JOURNAL. Les autres questions IA-Q02–IA-Q12 et les catalogues F/S ne sont pas modifiés.

Vérifications documentaires exécutées : huit fichiers Markdown concernés ; 43 liens locaux valides ; treize sections et six propositions P01–P06 identifiées ; D098 unique, ancien registre conservé intégralement. Blocs D059/D068/D064, lignes IA-Q02–IA-Q12, invariants/matrice/scénarios IA-I/IA-A/IA-S et identifiants/intitulés F/S comparés à HEAD avant ce travail : inchangés. Diff sans erreur d'espacement ; recherche ciblée de secrets sans résultat et relecture manuelle sans donnée personnelle réelle détectée, sans garantie absolue.

Fichiers réellement concernés : `docs/specs/ia-q01-account-membership-options.md`, `docs/specs/identity-organization-access.md`, `docs/specs/socle-technique.md`, `docs/product/decisions.md`, `README.md`, `tracking/BOARD.md`, `tracking/STATUS.md` et `tracking/JOURNAL.md`. Aucun test applicatif, build, migration ou configuration exécuté.

Preuve Git à compléter après publication vérifiée. Aucune application de P01–P06 par la publication du document ; toute adoption reste soumise à D064.
