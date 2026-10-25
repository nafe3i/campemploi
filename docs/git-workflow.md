# Mise en place du suivi Git/GitHub

Date : 24 octobre 2026. Adoption validée D066 ; premier commit et publication en préparation pour accord final. Aucun code applicatif.
Accord reçu le 25 octobre 2026 (D067) : premier commit et envoi documentaire autorisés, dépôt public accepté. Les mentions d'accord en attente ci-dessous décrivent la préparation antérieure et ne sont plus un blocage. Aucun changement de visibilité demandé.
Vérification renouvelée le 25 octobre 2026 : main/origin déjà présents, aucun commit ; API publique confirmant private=false, taille 0 et aucune référence Git distante annoncée. Pas de réinitialisation, modification de visibilité ou push. Capture 0004 réellement créée lors de cette reprise ; pas de capture du même identifiant présente avant.

## État vérifié

- Git installé, dépôt local initialisé sur main.
- origin : https://github.com/nafe3i/campemploi.git ; URL sans identifiant secret.
- Dépôt distant lisible via Git et aucune référence annoncée lors de la vérification. API GitHub : private=false, dépôt actuellement public, taille 0 ; ne pas envoyer en supposant qu'il est privé. Clarification requise avant publication, sans modification de visibilité à cette étape.
- Identité d'auteur déjà configurée ; aucune identité inventée ni configuration globale modifiée.
- .gitignore protège les chemins prévus pour secrets, données utilisateur, dépendances et sorties générées. C'est un garde-fou, pas une preuve que tout fichier hors de ces chemins est sûr.
- .gitattributes normalise les documents courants et préserve les octets des anciens instantanés pour leurs empreintes.

## Premier contenu à revoir

README.md, AGENTS.md, docs/, tracking/ et les deux fichiers de configuration Git. Uniquement cadrage, méthode, suivi et références ; aucun CV réel, secret, binaire ou code applicatif prévu. Les instantanés 0001–0004 font partie du contenu afin de conserver les états déjà capturés.

Message de commit proposé : `docs: initialiser le cadrage et le suivi de CapEmploi Campus`.

Avant commit : relire les fichiers sélectionnés et le résumé du diff, contrôler les secrets, les exclusions et les empreintes des copies. Avant push : vérifier ou faire confirmer la visibilité privée du dépôt puis obtenir l'accord sur le contenu et l'envoi. Ne pas écraser un historique distant, ne pas utiliser de force push. Un push ultérieur devra être précédé d'une nouvelle vérification de l'état distant.

## Suite prévue, non encore exécutée

Conserver les décisions/spécifications dans les fichiers versionnés. Préparer un petit ensemble de tâches à partir du tableau courant avant d'en créer sur GitHub ; configurer un Project après revue du contenu. Aucune Issue, aucun Project, aucune invitation à collaborateur ni aucun déploiement créé pendant l'initialisation locale.

La suppression ou l'arrêt des captures manuelles demanderait une décision explicite selon D063–D064. Les captures existantes restent inchangées. Après mise en place, les commits conserveront les états enregistrés ; ils ne reconstituent pas des versions passées qui n'ont jamais été sauvegardées.
