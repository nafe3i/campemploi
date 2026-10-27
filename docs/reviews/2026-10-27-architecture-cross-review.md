# Relecture critique de la revue d'architecture transmise

Date : 27 octobre 2026. Nature : revue documentaire, sans code applicatif à auditer.

## Périmètre et résultat

Texte source : revue des quatre documents transmise dans la pièce jointe « Texte collé.txt ». Comparaison avec les fichiers réels, le registre des décisions, les règles d'administration et le cycle des offres. Le texte est une contribution à analyser ; ses propositions de rôle, architecture, priorités ou gouvernance ne constituent pas un accord d'application.

La revue identifie correctement le principal travail restant : transformer les règles métier acquises et les questions ouvertes en contrats de données, d'authentification et d'autorisation vérifiables. Elle ne démontre aucune vulnérabilité applicative : aucun code, migration ou test applicatif n'existe à ce stade. Les P0 de cette revue sont ses priorités proposées avant la fonctionnalité concernée, pas des incidents découverts.

Stack et architecture générale D008, Docker D088/D089, responsabilités/SOLID/injection D093, JWT D094 et organisation GitHub D095 restent acquis. Aucune preuve justifiant de remplacer cette stack n'est fournie. Le socle D096 reste Proposed ; les risques ouverts y sont déjà en partie explicités.

## Constats vérifiés et nuances

| Sujet de la revue | Résultat de la vérification locale | Suite proposée, sans application technique |
|---|---|---|
| Identité, rattachements et rôles incomplets | Confirmé comme conception à compléter : socle sections 7–9/Q05–Q07. D056/D059/D078–D082 fixent déjà une partie des règles | Modèle conceptuel et cardinalités, matrice d'accès et scénarios de retrait des droits avant migrations métier |
| Isolation des établissements non choisie | Mécanisme ouvert, exigences déjà validées ; base partagée n'est encore qu'une hypothèse T05 | Comparer les stratégies sur les données et droits réels, puis contraintes et requêtes bornées ; aucune RLS imposée |
| Cycle de vie JWT incomplet | Confirmé et explicitement ouvert D094/Q06 : transport, stockage, durée, renouvellement/révocation, claims et clés | Politique cohérente et preuves avant S04 ; pas de refresh token ou durée inventés |
| Initialisation du premier compte privilégié | Acteurs et limites déjà décidés D056/D076 ; procédure technique effectivement ouverte | Définir bootstrap, absence d'accès public permanent et récupération ; modalité précise à valider |
| Rôles insuffisants à eux seuls | Déjà décrit T05 et socle section 8 ; contrat concret encore manquant | Rôle et contexte courant/action/ressource à expliciter. RBAC/ABAC sont des concepts, pas une bibliothèque ni un moteur à installer |
| Modération et disponibilité à distinguer « si confirmé » | Déjà confirmé D068, repris dans le cycle des offres : modération et disponibilité sont distinctes | Préserver cette décision ; spécifier transitions, atomicité, répétitions et concurrence |
| Invitations : consommation et réutilisation | D059 exige un lien de classe partagé et réutilisable, avec expiration/désactivation/renouvellement et validation CME | Ne pas convertir automatiquement ce lien en invitation à usage unique. Distinguer lien de classe, invitation individuelle du personnel et récupération de compte |
| Deux CME décident simultanément | Scénario hypothétique utile ; effectif annoncé et droits de délégation ne prouvent pas deux modérateurs effectifs | Vérifier répétition/concurrence même avec un acteur sur plusieurs onglets ; ne pas ajouter un rôle ou effectif pour justifier le test |
| Contrats API, outils de test et exploitation génériques | Détails ouverts T07/T09/T10 ; socle définit déjà preuves et prérequis | Compléter au moment utile ; aucun outil CI, framework de test ou monitoring retenu par cette revue |
| Comparaison de stack historiquement ambiguë | En-tête courant indique déjà D008 et annonce l'historique. Certaines phrases locales, dont « PostgreSQL proposé, non validé », restent faciles à lire hors contexte | Clarification éditoriale ciblée recommandée, sans remettre D008 en débat et sans réécrire l'historique |
| Catalogues F00–F15 et S01–S06 | Chevauchement documentaire confirmé ; F vise les capacités globales, S les unités du socle ; les relations ne sont pas assez explicites | Ajouter une correspondance et garder BOARD comme référence D095, plutôt qu'introduire immédiatement un nouvel identifiant universel |
| Trois niveaux de validation proposés | Changement de gouvernance, pas correction d'un bug. D064 exige actuellement un accord avant toute nouvelle décision ; une action explicitement demandée est déjà autorisée dans son périmètre | Ne pas assouplir D064 implicitement. Une évolution de cette règle nécessiterait une proposition et un accord spécifiques |

Références locales : [socle technique](../specs/socle-technique.md), [approches techniques](../specs/technical-guidelines.md), [administration](../scope/establishment-administration.md), [cycle des offres](../scope/offer-lifecycle.md), [comparaison de stack](../specs/stack-architecture-options.md), [catalogue global](../specs/architecture-realisation-campus.md), [décisions](../product/decisions.md).

## Sécurité et données : ce que les sources permettent d'affirmer

Un accès à un objet ne doit pas être autorisé sur la seule présence d'un JWT ou d'un rôle. OWASP décrit le risque BOLA et les vérifications de l'action sur l'enregistrement concerné ; son guide d'autorisation recommande le refus par défaut et des contrôles à chaque requête. Ces références soutiennent les exigences existantes, sans prouver notre implémentation ni imposer une bibliothèque. [OWASP BOLA](https://api-security.owasp.org/editions/2023/en/0xa1-broken-object-level-authorization/), [OWASP Authorization](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html).

Argon2id est recommandé dans le guide OWASP de stockage des mots de passe ; cela en fait une option à comparer pour notre parcours, pas un algorithme ou des paramètres déjà validés dans le projet. [OWASP Password Storage](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html).

Le signalement de la CNDP est pertinent pour C11 : ses pages officielles décrivent des formalités de notification, des cas d'autorisation et la question des transferts. La procédure applicable au campus dépendra du responsable du traitement, des données, finalités, destinataires et hébergement effectivement retenus. Aucune qualification juridique, conformité ou formalité accomplie n'est déduite ici. Cet examen précède les essais/données réels concernés ; il n'attend pas automatiquement la tranche CV. [CNDP : notification](https://www.cndp.ma/notifier-un-traitement/), [CNDP : conditions](https://www.cndp.ma/conditions/).

Une note de gouvernance des données serait utile pour C11, en consolidant responsabilités, catégories/finalités, visibilité, conservation/suppression, hébergement et incidents. Son contenu et ses engagements restent à établir ; aucun fichier de politique définitive ni nouvelle durée ne sont créés par cette revue.

## Recommandation de priorité — proposée, accord attendu

L'ordre de discussion du socle D096 met Q01/Q02 en premier. Ce n'est pas une décision validée de démarrage. Après cette relecture, recommandation affinée : traiter d'abord un chantier de conception **Identité / Organisation / Accès**, puis détailler JWT et la persistance métier. Dossiers, versions et démarrage local restent préparables indépendamment ; ils ne remplacent pas cette conception.

Livrable proposé : une seule spécification métier-technique de référence dans `docs/specs/identity-organization-access.md`, avec :

1. Compte, établissement, rattachement, rôle local, classe et affectation : responsabilités, liens et cardinalités ; pas encore de schéma SQL.
2. Distinction rôle métier/permission administrative/affectation, en reprenant D056/D078–D082.
3. Matrice acteur/action/ressource/préconditions/résultat/refus, sans inventer un accès ou un partage.
4. Scénarios de compte non approuvé, identifiant d'un autre établissement, retrait d'affectation, rôle administratif sans droit confidentiel et changement de rattachement.
5. Questions non tranchées, dont comptes multi-établissements et cumul de rôles ; comparaison de solutions avec conséquences avant accord.
6. Dépendances de la politique JWT et du modèle relationnel, critères et preuves futures avec deux établissements fictifs.

Le document et l'ordre de travail sont proposés ; ils ne sont pas créés/appliqués comme décisions par cette analyse. Après accord, inscrire la priorité dans le registre et aligner seulement les prochaines actions concernées de socle/BOARD/STATUS. Ne pas renuméroter F/S, modifier D064, choisir un ORM ou développer l'authentification au titre de ce seul accord.

Ensuite : politique JWT et initialisation des comptes → modèle relationnel minimal et choix d'accès PostgreSQL → socle exécutable vérifié → accès nécessaires et parcours humains des offres. Les obligations avant données réelles C11/C12 restent séparées et conservées.

## Limites et preuves de cette revue

Pièce jointe lue ; comparaison documentaire et sources primaires consultées. Aucun code ou configuration applicative modifié, aucune architecture nouvelle appliquée, aucun test applicatif, déploiement ou délégation. Les anciennes captures sont préservées. Le rapport relève des exigences ouvertes et améliorations documentaires, sans présenter une sécurité applicative comme démontrée. Les changements techniques ou de gouvernance attendent leur accord D064.
