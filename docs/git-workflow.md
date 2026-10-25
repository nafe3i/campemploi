# Mise en place du suivi Git/GitHub

Date : 25 octobre 2026. Adoption D066, premier commit et publication autorisés par D067 et réalisés. Aucun code applicatif.
Règle courante D069 : après chaque validation explicite, commit descriptif et push des changements concernés autorisés, sans confirmation supplémentaire pour le même périmètre. Le lot D068 est inclus et publié avec D069 au commit de732bdaca71bef05aaf62b372c9c052c1c4b870, concordance distante vérifiée. Les restrictions d'accord individuel ci-dessous décrivent la préparation historique, désormais complétée par cette règle.
Accord reçu le 25 octobre 2026 (D067) : premier commit et envoi documentaire autorisés, dépôt public accepté. Les mentions d'accord en attente ci-dessous décrivent la préparation antérieure et ne sont plus un blocage. Aucun changement de visibilité demandé.
Vérification renouvelée le 25 octobre 2026 : main/origin déjà présents, aucun commit ; API publique confirmant private=false, taille 0 et aucune référence Git distante annoncée. Pas de réinitialisation, modification de visibilité ou push. Capture 0004 réellement créée lors de cette reprise ; pas de capture du même identifiant présente avant.

## État vérifié

- Git installé, dépôt local initialisé sur main.
- Premier commit : 2082f296e075c6f3a0b1d68a214f1de417c9d54b, envoyé sur origin/main le 25 octobre 2026. Concordance vérifiée par lecture distante ; suivi local de origin/main établi. Les descriptions de préparation ci-dessous restent historiques.
- origin : https://github.com/nafe3i/campemploi.git ; URL sans identifiant secret.
- Dépôt public confirmé avant envoi puis explicitement accepté par l'utilisateur D067 ; aucun changement de visibilité. Il contient désormais le commit documentaire initial ; les contrôles de taille nulle concernaient l'état antérieur.
- Identité d'auteur déjà configurée ; aucune identité inventée ni configuration globale modifiée.
- .gitignore protège les chemins prévus pour secrets, données utilisateur, dépendances et sorties générées. C'est un garde-fou, pas une preuve que tout fichier hors de ces chemins est sûr.
- .gitattributes normalise les documents courants et préserve les octets des anciens instantanés pour leurs empreintes.

## Premier contenu à revoir

README.md, AGENTS.md, docs/, tracking/ et les deux fichiers de configuration Git. Uniquement cadrage, méthode, suivi et références ; aucun CV réel, secret, binaire ou code applicatif prévu. Les instantanés 0001–0004 font partie du contenu afin de conserver les états déjà capturés.

Message de commit proposé : `docs: initialiser le cadrage et le suivi de CapEmploi Campus`.

Avant commit : relire la sélection/diff, contrôler secrets, exclusions et empreintes. Avant push : vérifier le dépôt et l'autorisation de publication ; le dépôt public fourni est accepté D067 pour ce contenu. Ne pas écraser un historique distant ni utiliser force push. Conserver les opérations de suivi dans de petits commits distincts ; un nouvel envoi respecte le périmètre d'accord.

## À chaque validation — D069

1. Consigner la décision et appliquer le seul périmètre validé ; mettre à jour documents concernés, état, tableau et journal. D074 : les commits remplacent les nouvelles copies snapshots ; anciennes captures inchangées.
2. Relire les fichiers sélectionnés et le diff ; vérifier secrets, données personnelles et contrôles pertinents. Préserver les anciennes captures sans les recopier. Écarter les changements sans rapport.
3. Créer un petit commit descriptif, puis le pousser normalement vers origin sur la branche de travail, sans force push ni réécriture.
4. Vérifier la concordance locale/distante et informer l'utilisateur du résultat. Si l'opération échoue, rapporter ce qui reste local ; ne pas annoncer une publication réussie.

Cette règle autorise la synchronisation du travail validé et de son suivi. Les nouvelles décisions métier/techniques restent soumises à D064 ; aucune publication de données personnelles réelles, aucun déploiement ni création d'Issues/Project autorisés par cette seule règle.

## Suite produit et organisation

Conserver les décisions/spécifications dans les fichiers versionnés. Préparer un petit ensemble de tâches à partir du tableau courant avant d'en créer sur GitHub ; configurer un Project après revue du contenu. Aucune Issue, aucun Project, aucune invitation à collaborateur ni aucun déploiement créé pendant l'initialisation locale.

Arrêt des nouvelles captures manuelles explicitement validé D074 le 25 octobre 2026. Les captures 0001–0018 restent inchangées, sans suppression ni réécriture de l'historique Git. Les commits conservent désormais les nouveaux états enregistrés ; ils ne reconstituent pas des versions passées jamais sauvegardées. Exemple de consultation sans modifier le dossier de travail : `git show 492951a:docs/scope/pilot.md` ; exemple de comparaison : `git diff 6ad6a5f 492951a -- docs/scope/pilot.md`.
