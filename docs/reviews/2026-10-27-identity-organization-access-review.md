# Rapport documentaire — Identité / Organisation / Accès

Date : 27 octobre 2026. Mandat : D097. Nature : vérification de spécification, sans audit applicatif.

## Livrables et portée

[Spécification](../specs/identity-organization-access.md) au statut **Proposed** : modèle conceptuel et cardinalités connues/ouvertes, 15 invariants, 42 lignes d'autorisation, 20 scénarios de sécurité, garanties transactionnelles, alternatives, 12 questions avec options/conséquences et correspondance avec les F/S existantes.

L'accord D097 valide la priorité et le travail documentaire. Il ne valide aucune option de compte multi-établissements, cumul, isolation, stockage/renouvellement JWT, ORM ou fournisseur d'identité. Les règles métier déjà acquises ne sont pas modifiées.

## Fichiers effectivement créés ou modifiés

| Fichier | Nature | Motif |
|---|---|---|
| docs/specs/identity-organization-access.md | Créé | Spécification demandée, matrice/scénarios/arbitrages et correspondance F/S |
| docs/reviews/2026-10-27-identity-organization-access-review.md | Créé | Présent rapport de portée, fichiers et vérifications |
| docs/product/decisions.md | Modifié par ajout | D097 consignée avant rédaction, sans réécriture des décisions précédentes |
| docs/specs/socle-technique.md | Modifié | Référence à la spécification ; prérequis S03/S04/S05 et prochaines discussions alignés, numéros inchangés |
| docs/specs/technical-guidelines.md | Modifié | Lien vers la spécification, sans validation implicite de T05–T10 |
| docs/specs/architecture-realisation-campus.md | Modifié | Référence et priorité D097, catalogue F inchangé |
| docs/plan-realisation.md | Modifié | Prochaine discussion alignée sur priorité D097, plan global toujours proposé |
| README.md | Modifié | Accès au nouveau document |
| tracking/BOARD.md | Modifié | R01f livrable documentaire ; R02 partiellement en cours, pas de fonctionnalité acceptée |
| tracking/STATUS.md | Modifié | État courant, questions proposées et limites, publication selon résultat réel |
| tracking/JOURNAL.md | Modifié | Accord D097, rédaction, contrôles et preuve de publication |

AGENTS.md, workflow, règles métier d'administration/revues/offres, archives sources et anciennes captures non modifiés. Aucun fichier applicatif, migration, configuration, script de production ou dépendance ajouté.

## Vérifications et résultats

Vérifications exécutées et réussies :

- Onze fichiers sélectionnés, tous au format Markdown ; aucun fichier applicatif/configuration/migration ni fichier sans rapport modifié.
- Soixante-cinq liens locaux résolus ; encodage sans caractère de remplacement et blocs de code fermés.
- Quatorze sections ; identifiants uniques et continus : 15 IA-I, 42 IA-A, 20 IA-S et 12 IA-Q ; références Dxxx présentes dans le registre.
- D097 unique ; registre antérieur conservé intégralement en préfixe de la version courante. Comparaison intégrale supplémentaire des blocs D059, D068 et D064 : identiques à HEAD avant ce travail.
- Identifiants et intitulés du catalogue F et des unités S comparés à HEAD : inchangés, sans renumérotation.
- Diff sans erreur d'espacement ; recherche ciblée de motifs de secrets sans résultat, revue manuelle des ajouts sans donnée personnelle réelle détectée. Cette recherche ne constitue pas une garantie absolue.
- Relecture de cohérence : cas nominaux séparés des conflits/transferts ouverts, demandes par lien réutilisable, droits courants et autorisations des futures tranches distinctes.

Périmètre des contrôles réalisés : diff et sélection des seuls fichiers documentaires concernés ; liens locaux et syntaxe des blocs ; unicité de D097 ; exhaustivité des identifiants IA-I/IA-A/IA-S/IA-Q ; comparaison des blocs D059/D068/D064 avec HEAD ; conservation des identifiants et intitulés F/S ; références des décisions et sources locales ; recherche ciblée de secrets/données personnelles dans le diff ; revue manuelle des permissions et ambiguïtés.

Points de revue manuelle : D039 historique lu avec D056 ; lien de classe réutilisable séparé de l'invitation du personnel ; une personne par compte non confondue avec compte global unique ; deux avis distincts non confondus avec deux personnes obligatoires ; administration/affectation/accompagnement séparés ; retrait d'un périmètre sans suppression globale des autres droits ; demandes de transfert et requêtes concurrentes restent ouvertes ; aucune promesse de récupération de données déjà reçues.

## Limites

Aucun test applicatif, migration, compilation/build ou déploiement exécuté : il n'existe pas de code applicatif pour ces parcours. Les scénarios décrivent des preuves futures ; leurs lignes ouvertes ne définissent pas un comportement par défaut. La conformité juridique et la sécurité d'une application en fonctionnement ne sont pas démontrées.

Sources techniques primaires consultées pour la comparaison, référencées dans la spécification : OWASP Authorization, PostgreSQL RLS/isolation et RFC 8725. Ces sources n'autorisent ni dépendance ni mécanisme supplémentaire. La publication Git ne prouve pas une mise en place du Project/Issues ni une implémentation.

## Arbitrages à présenter avant implémentation

Premier groupe recommandé, non appliqué : IA-Q01 (comptes/rattachements/contexte), puis IA-Q02/03 (rôles et classes). IA-Q07/08/09 doivent précéder les décisions dépendantes de bootstrap, JWT et persistance. IA-Q05 traite notamment le cumul des deux avis avant le parcours concerné. Les 12 questions restent explicitement ouvertes et soumises à D064.

## Conservation et publication

Commit et résultat du push à consigner uniquement après vérification. Lien vers la preuve durable : [journal](../../tracking/JOURNAL.md) ; état des tâches : [BOARD](../../tracking/BOARD.md).
