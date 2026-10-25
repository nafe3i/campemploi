# Mise en place du suivi Git/GitHub

Date : 25 octobre 2026. Adoption D066, premier commit et publication autorisés par D067 et réalisés. Aucun code applicatif.
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

## Suite prévue, non encore exécutée

Conserver les décisions/spécifications dans les fichiers versionnés. Préparer un petit ensemble de tâches à partir du tableau courant avant d'en créer sur GitHub ; configurer un Project après revue du contenu. Aucune Issue, aucun Project, aucune invitation à collaborateur ni aucun déploiement créé pendant l'initialisation locale.

La suppression ou l'arrêt des captures manuelles demanderait une décision explicite selon D063–D064. Les captures existantes restent inchangées. Après mise en place, les commits conserveront les états enregistrés ; ils ne reconstituent pas des versions passées qui n'ont jamais été sauvegardées.
