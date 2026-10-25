# Collaboration

Répondre principalement en français. Agir comme un mentor : concept, pourquoi, exemple minimal, application, implémentation progressive, vérification et revue.

## Reprise

Lire README.md, tracking/STATUS.md, tracking/JOURNAL.md et les documents du sujet.
Distinguer explicitement les décisions validées, les propositions et UNKNOWN.
Ne pas transformer une proposition de la conversation en décision validée.

## Accord avant application d'une décision — D064

Avant d'appliquer une nouvelle décision, présenter concrètement la proposition, ses conséquences et les fichiers/actions concernés, puis poser la question de validation et attendre la réponse explicite de l'utilisateur. Une demande d'analyse, un échange, un silence ou un accord ambigu ne valent pas autorisation. En cas d'ambiguïté, clarifier avant l'action dépendante. Une instruction explicite d'effectuer l'action vaut autorisation pour cette action ; ne pas redemander un accord déjà donné pour le même périmètre. Consigner ensuite l'accord et exécuter uniquement le périmètre validé. Les mises à jour documentaires et instantanés découlant des règles déjà autorisées restent applicables ; ne pas y introduire une nouvelle décision non validée.

## Développement

Inspecter les fichiers et conventions avant de modifier. Expliquer la stratégie avant une modification importante. Privilégier simplicité, lisibilité et responsabilités claires.
Ne pas choisir une stack sans décision documentée.
Construire par tranches fonctionnelles complètes et petites.
Vérifier le fonctionnement réel et tester les comportements importants, dont les permissions et la séparation entre établissements.
Pour chaque fonctionnalité et chaque étape, définir les contrôles communs et les règles spécifiques : accès, entrées, transitions, cas limites/erreurs et confidentialité ; prévoir les preuves et tests pertinents selon docs/workflow.md (D060). Ne pas se limiter au parcours nominal ni appliquer mécaniquement les mêmes règles métier partout.
Ne pas marquer une fonctionnalité Accepted sans preuves de validation.

## Produit et sécurité

Prévoir plusieurs établissements, avec un pilote interne initial.
Protéger CV, coordonnées et candidatures ; ne pas stocker de secrets ni de données personnelles réelles dans le dépôt.
Distinguer la visibilité personnelle, l'accompagnement et le partage collectif.
Une condition d'accès géographique absente d'une offre reste à confirmer.
Ne pas envoyer de candidature ni de message externe sans autorisation explicite.

## Documentation et Git

Suivre docs/workflow.md. Mettre à jour l'état et le journal en fin de session.
Tenir tracking/BOARD.md à jour après chaque avancée réelle (D062) : tâche, statut et preuve ; distinguer documentation/décision terminée et fonctionnalité développée puis vérifiée. Ne pas marquer terminé sur la seule base d'une discussion.
Conserver les états successifs selon tracking/HISTORY.md (D063) : instantané après changement significatif et en fin de session si le suivi a changé, identifiant/date/motif et preuves pertinentes. Ne pas écraser une capture existante ni inventer un état passé/futur.
À chaque décision validée par l'utilisateur, l'inscrire immédiatement dans docs/product/decisions.md et dans le document concerné ; actualiser l'état et le journal. Ne pas attendre la fin du cadrage. Garder les propositions et les ambiguïtés explicitement non validées.
Petits commits cohérents, diff relu et recherche de secrets avant commit. Pas de commande destructive sans expliquer ses conséquences.
Les noms /scope, /architect, etc. sont des phases : ne pas prétendre que les skills JSM sont installés.
Ne pas déléguer à des agents sans demande explicite.
