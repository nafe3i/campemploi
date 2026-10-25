# Scope du pilote — consolidation du 17 octobre 2026

Statut : décisions individuelles validées, scope consolidé à relire avant validation globale (D007). Aucun code applicatif, aucune stack choisie, aucune fonctionnalité Accepted.
Référence : docs/product/decisions.md. Cette consolidation ne transforme pas les propositions restantes en décisions.
Mise à jour du 24 octobre 2026 (D054) : fonctions principales en priorité, évolutions globales ensuite. Prototype de collecte par API/flux/script gardé comme expérimentation indépendante ultérieure, sans bloquer la première tranche humaine. Cadrage de cette tranche dans docs/scope/first-slice.md ; règles proposées non automatiquement validées.

## Objectif et public validés

Priorité de preuve validée (D047) : pertinence, accessibilité et effort de recherche. Changement de séquencement D053 : première tranche par contributions humaines pour mutualiser et qualifier les offres ; collecte automatique maintenue pour une tranche ultérieure avec étude/expérimentation, sans bloquer le démarrage de l'approche humaine. Aucun gain de découverte automatique revendiqué. Protocole proposé dans docs/scope/opportunity-experiment.md ; suivi et accompagnement conservés, D007 en attente. Portage officiel non confirmé.

Réduire la difficulté de découverte des offres, guider la préparation et le suivi des candidatures, et permettre un accompagnement humain traçable.
Pilote interne dans un établissement au Maroc : environ 43 apprenants de première année, 36 de deuxième année, une CME et 3 à 4 responsables techniques (effectif exact à confirmer).
Profils full stack Java/Angular, MERN et PHP/Laravel, niveaux bac+2 et bac+3 (D050), sans limiter la vision à ces stacks. Français et anglais utilisables au travail (D051) ; niveaux individuels, répartition des niveaux par année et diplôme exact à confirmer. Ne pas supposer la maîtrise des trois stacks ou un bilinguisme uniforme par chaque apprenant.

| Public | Objectif de recherche | Début et durée |
|---|---|---|
| Première année | Stages | Deux mois obligatoires ; début flexible en avril ou mai 2027, y compris en cours de mois ; limites de fin et débuts plus tardifs à confirmer (D048–D049) |
| Deuxième année | Stages de préembauche et premiers emplois | Pas de préférence de mois ; durée des stages à confirmer |

Références : D001–D004, D016–D018, D048. Engagement officiel de l'établissement non confirmé ; ne pas supposer de mandat. Ces objectifs ne constituent pas une restriction d'accès par année ni une disponibilité immédiate individuelle.
Opportunités au Maroc ou à l'étranger, remote ou sur place, si accessibles aux candidats.

## Périmètre fonctionnel validé

### Offres et collecte (D010, D028–D032)

Modération nominale validée D061 : soumission en attente ; décision CME de publier, demander correction ou rejeter ; motif pour correction/rejet, correction par auteur puis nouvelle soumission en attente. Complément D068 validé le 25 octobre : disponibilité distincte, clôture/réouverture et modification du contenu publié par CME, signalements des contributeurs, versions et suivis préservés, retrait temporaire si doute sérieux. Échéance dépassée à vérifier, aucun refus automatique ni notification externe imposée. Détail et contrôles dans docs/scope/offer-lifecycle.md ; conservation détaillée et autres exceptions encore ouvertes.

- Première tranche (D053) : contributions des apprenants et du personnel, validation CME puis consultation ; pas de collecte automatique requise dans cette tranche.
- Collecte mixte à terme : automatisation ciblée prévue dans une tranche ultérieure, vers la même file de validation, après preuve de faisabilité et d'utilité. Étude/expérimentation conservée sans bloquer l'approche humaine ; aucune source intégrée ni promesse de collecte exhaustive.
- Proposition d'offre par lien ou texte copié avec provenance ; entreprise, intitulé et type d'opportunité.
- Toutes les offres collectées passent par la validation de la CME avant visibilité aux apprenants.
- Niveau demandé (D052) : une offre exigeant bac+5 peut être conservée et publiée après validation CME, avec exigence et écart au profil bac+2/+3 clairement signalés. Aucun rejet automatique pour ce seul motif ; aucune éligibilité ou dérogation présumée. Visibilité distincte de la pertinence vérifiée.
- Une offre sans information d'accessibilité peut être publiée après validation CME avec « Accessibilité depuis le Maroc à confirmer ». Une restriction explicite n'est pas une information inconnue.
- Recherche d'entreprises à prospecter et candidatures spontanées incluse dans le besoin (D012) ; détail du parcours et position dans les tranches à préciser.
- Liste d'entreprises évolutive (D046) : ajout par la CME ; propositions des apprenants et responsables validées par la CME avant ajout à la liste commune. Nom, site et page carrières prévus, caractère obligatoire à préciser. Ajout distinct de l'activation d'une collecte automatique, qui nécessite vérification et configuration. Une fiche d'entreprise ne vaut ni partenariat ni offre active.

### Préparation et suivi (D036–D037)

Accès de revue D058 : le formateur consulte et examine les CV/portfolios de ses classes sans demande préalable ; CME sur son établissement. Cette règle précise les questions d'accès ci-dessous et fait évoluer D042 pour les formateurs affectés. Aucun accès général aux autres classes, établissements ou bilans confidentiels. Effet des changements d'affectation à définir.

Cycle de revue validé D057 : CV et portfolio séparés, deux avis formateur/CME (en attente, non validé, validé, à revalider), validation globale si les deux avis sont positifs sur le document examiné. Après modification, nouvelle revue et anciens avis dans l'historique. Cette décision tranche la combinaison des avis précédemment ouverte ci-dessous ; accès par classe, autres statuts globaux et gestion des changements d'un portfolio externe à définir.

Revue CV/portfolio et classes (D055) : besoin confirmé d'avis distincts CME/formateur, affectation de chaque formateur à sa classe, visibilité CME sur les apprenants de l'établissement et tri/filtrage classe/année/formateur. États CV souhaités : validé, non validé, à revalider ; sens et agrégation des avis à préciser. Cadrage dans docs/scope/cv-portfolio-review.md. Accès du formateur par classe ou sur demande D042 à arbitrer ; aucune extension aux bilans confidentiels ni modification implicite de la première tranche.

- Documents (D041) : CV déposé dans la plateforme, portfolio par lien. Formats, limites, versions, caractère obligatoire et permissions précises restent à définir ; protection des données requise, sans choix technique de stockage à ce stade.
- Précision validée (D042) : CV PDF remplaçable par l'apprenant, consultable par lui et la CME de son établissement ; accès du responsable technique uniquement pour une demande d'accompagnement qui lui est adressée. Aucun accès aux autres apprenants ni par lien public. Taille, conservation des versions et caractère obligatoire restent ouverts.

- Checklist liée à l'offre : CV adapté, motivation, portfolio et pièces demandées.
- Brouillon personnel rédigé par l'apprenant et demande possible de retour humain.
- Envoi par l'apprenant sur le canal indiqué par l'entreprise.
- États : en préparation, envoyée, entretien, acceptée, refusée, retirée. Un refus ne nécessite pas de passer par un entretien.
- Date d'envoi renseignée après envoi effectif, prochaine action, date de relance si nécessaire.
- Mise à jour du suivi par l'apprenant ; consultation par la CME de son établissement.

### Accompagnement, rendez-vous et progression (D020–D027)

- Préparation technique, retour sur portfolio ou simulation d'entretien avec un accompagnant humain.
- Choix direct du responsable technique de l'établissement par l'apprenant.
- Le responsable accepte ou demande une réorientation ; état visible par l'apprenant.
- Rendez-vous lié à la demande, à l'apprenant et à l'accompagnant : date, heure, lieu ou lien de visioconférence, état planifié/réalisé/annulé/absent, bref bilan et prochaine action.
- Organisation possible hors plateforme, mais suivi obligatoire dans la plateforme.
- L'accompagnant et l'apprenant rédigent leurs propres observations ; chacun modifie les siennes, jamais celles de l'autre.
- Progression par actions : à faire, en cours, réalisée, sans note globale ; revue possible au rendez-vous suivant.

## Accès validés et limites

Invitation par classe (D059) : lien partagé réutilisable généré par la CME ; inscription/connexion individuelle, puis rattachement à la classe validé par la CME avant accès interne. Expiration, désactivation et renouvellement prévus ; aucun changement de classe automatique ni rôle privilégié conféré. Détail dans docs/scope/establishment-administration.md.

Évolution administrative validée (D056) : porteur administrateur général créant établissement/CME, puis gestion locale des classes, invitations du personnel, rattachements et rôles par la CME avec permission d'administration locale. Rôle métier et administration locale distincts, cumulables ; D039 modifiée, inscription apprenant D038 conservée. Aucun accès inter-établissements ou aux contenus confidentiels automatiquement accordé. Étendue des écrans multi-établissements au pilote à spécifier ; voir docs/scope/establishment-administration.md.

Suivi du travail (D043) : besoin validé de suivre le travail de chaque apprenant, de la CME et des responsables techniques. Actions suivies, responsabilités, indicateurs, visibilité et délais à définir ; aucun score, classement ou accès général aux contenus confidentiels déduit. Les actions réalisées hors plateforme ne sont pas automatiquement observables.
Consultation du suivi (D044, validé) : le porteur du projet consulte le tableau des trois rôles dans son établissement. Permission distincte de l'administration des comptes, sans accès automatique aux CV, bilans ou remarques confidentiels et sans accès aux autres établissements. Champs, indicateurs et niveau de détail du tableau restent à définir ; aucun droit de modification déduit.

| Rôle | Droits validés | Limites / questions ouvertes |
|---|---|---|
| Nouveau compte | Rôle apprenant par défaut ; compte en attente | Aucun accès aux données internes avant validation du rattachement |
| Apprenant rattaché | Préparer et mettre à jour son suivi, proposer des offres, demander un accompagnement | Accès aux données des autres apprenants non validé |
| CME | Valider les offres et consulter toutes les candidatures de son établissement | Pas de modification des candidatures ni d'accès aux notes privées validés |
| Responsable technique | Accompagnement sur les demandes qui lui sont adressées | Aucun accès global aux candidatures ou aux bilans des autres responsables |
| Administrateur | Valider les rattachements, changer les rôles après demande | Administration des comptes sans accès automatique aux données confidentielles |

Bilans et remarques d'un rendez-vous visibles uniquement par l'apprenant concerné, l'accompagnant concerné et la CME de l'établissement, même lorsqu'ils sont liés à la progression (D025).
Le porteur du projet administre le pilote. Plus tard, chaque établissement aura son administrateur limité à son établissement (D038–D039).
Séparation entre établissements à anticiper dès la conception ; ouverture multi-établissements ultérieure.
Aucune donnée personnelle réelle ni secret dans le dépôt. Aucune candidature ou message externe envoyé sans autorisation explicite.

## Ordre, budget et ouverture validés

### Tableau de suivi du travail (D045)

Consultation par le porteur du projet dans son établissement (D044). Première version validée :

| Rôle | Informations suivies |
|---|---|
| Apprenant | Candidatures par état, prochaines actions, actions de progression, présence aux rendez-vous |
| CME | Offres en attente et traitées, demandes d'accompagnement, rendez-vous réalisés |
| Responsable technique | Demandes en attente et traitées, rendez-vous réalisés, bilans renseignés |

Filtre par période et signalement des échéances dépassées. L'existence d'un bilan est visible sans son contenu. Sans échéance définie, aucun retard déduit. Définition des calculs et dates de référence, résumé des actions sans contenu confidentiel et droits d'attribution des échéances à spécifier. Aucun score ni classement validé. Position de cette vue dans les tranches à préciser ; elle n'élargit pas les droits d'accès aux observations et CV.

- Ordre fonctionnel (D032 précisé par D053) : offres proposées par les utilisateurs et validation → candidatures et suivi → accompagnement et progression. Collecte automatique dans une tranche ultérieure à positionner après étude ; elle ne bloque pas la première tranche.
- Prévoir l'accès et l'isolation nécessaires à chaque tranche avant de l'exposer aux utilisateurs ; détail technique à spécifier.
- Solutions gratuites initialement ; évolution payante possible après décision explicite (D030).
- Avancement progressif sans date fixe, avec développement accompagné et participation de l'utilisateur (D011, D014).
- Premiers essais : 8 à 12 apprenants des deux années, la CME et 1 à 2 responsables techniques ; élargissement après retours et corrections (D034). Ce groupe n'est pas une limite de capacité.

## Critères de réussite validés, non encore vérifiés (D035)

| Critère | Base de vérification |
|---|---|
| Autonomie | Au moins 80 % trouvent une offre et enregistrent leur suivi sans aide |
| Utilité | Au moins 70 % trouvent une opportunité jugée pertinente |
| Charge CME | Validation compatible avec la disponibilité indicative de 30 minutes par jour ; mesurer le temps réel |
| Accompagnement | Parcours vérifié de la demande au rendez-vous, bilan et prochaine action |
| Confidentialité | Aucun accès non autorisé lors des vérifications ; problèmes détectés corrigés avant élargissement |

Arrondir au supérieur le nombre minimal de réussites pour les pourcentages. La disponibilité annoncée est de 30 minutes par jour ou plus (D033), pas un délai garanti de traitement.
Comparer aussi avec la recherche actuelle : temps passé, nouvelles opportunités pertinentes, suivi et traitement des demandes. Réponses et entretiens obtenus ne sont pas seuls déterminants.
Durée d'observation, participants précis et protocole : UNKNOWN.

## Reports et propositions restantes

Report validé (D032) : traitement des offres sous forme d'images et PDF.
Calendrier interactif et synchronisation externe non retenus à ce stade (D022–D023) ; le suivi des rendez-vous reste inclus.

Hors pilote, à réaliser dans les versions futures (D040, validé) : envoi automatique de candidatures, chat interne, simulation automatique d'entretien, matching complexe, espace recruteur et facturation. Ces fonctionnalités ne sont pas abandonnées ; priorité, calendrier, faisabilité, coûts et spécifications à définir. Voir docs/product/roadmap.md. L'envoi automatique futur reste soumis à autorisation explicite avant envoi externe ; simulations humaines incluses dans le pilote.
Aide automatique à la rédaction et rappels automatiques : non tranchés, non requis pour l'approche guidée validée.
Profil détaillé (compétences, mobilité, CV et portfolio), filtres, dédoublonnage, vue CME détaillée et objectif d'ajout en moins d'une minute : propositions à spécifier/valider, pas critères déjà acceptés.

## Questions ouvertes avant architecture ou spécification des tranches

- Sources gratuites concrètes, modes de collecte autorisés, fréquence et limites ; critères de validation CME, doublons et détails des champs/historique. Clôture et modifications publiées désormais encadrées par D068 ; conservation détaillée et autres exceptions restent à préciser.
  Étude initiale disponible dans docs/reference/offer-sources-study.md : pistes documentées, pas de sélection de sources validée ni de couverture Maroc démontrée.
- Modalités techniques de stockage du CV déposé et partage des CV, liens portfolio et brouillons ; formats, limites et versions ; distinction entre notes privées et observations partagées. Principe dépôt CV / lien portfolio validé par D041.
- Droits détaillés par champ, création/mise à jour des actions et rendez-vous ; contribution CME hors rôle d'accompagnante ; réorientation, demandes sans réponse, suppression et historique.
- Périmètre initial de la prospection d'entreprises et des candidatures spontanées.
- Pouvoirs administrateur précis, création du premier compte et éventuelle administration globale future.
- Validation globale du scope ; protocole du pilote. Les exclusions listées par D040 sont désormais validées comme fonctionnalités futures.
- Stack, architecture technique et hébergement : UNKNOWN, à comparer ensemble après cadrage.
