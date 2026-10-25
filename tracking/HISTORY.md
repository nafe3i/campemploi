# Historique des états du projet

## Organisation courante — D074, 25 octobre 2026

Git conserve désormais les nouveaux états enregistrés des fichiers suivis ; GitHub les reçoit par push vérifié selon D069. STATUS.md décrit l'état courant, BOARD.md les tâches/preuves, JOURNAL.md les avancées et docs/product/decisions.md les décisions et leurs raisons. Plus de nouveaux dossiers snapshots après cet accord.

Les anciennes captures 0001–0018 ci-dessous sont conservées sans modification ni suppression. Leur index décrit les états réellement capturés sous D063 avant son évolution par D074. Toute correction actuelle se documente dans les fichiers courants et un nouveau commit ; ne pas réécrire les copies historiques.

Pour les nouveaux états : consulter `git log`, puis comparer les commits ou lire un fichier à une révision donnée sans modifier le dossier courant (exemples dans docs/git-workflow.md). Seuls les changements enregistrés par commit sont conservés ; publication distante seulement après push vérifié. Aucun historique inventé ni donnée personnelle réelle dans le dépôt. Ce mécanisme ne sauvegarde pas les données applicatives non versionnées.

## Index

| Instantané | Date d'enregistrement | Prédécesseur | Motif |
|---|---|---|---|
| [0001](snapshots/0001-2026-10-24/SNAPSHOT.md) | 24 octobre 2026 | Aucun état complet sauvegardé | Premier état figé du suivi et des documents de cadrage courants |
| [0002](snapshots/0002-2026-10-24/SNAPSHOT.md) | 24 octobre 2026 | 0001 | Règle d'accord explicite avant application des décisions (D064) |
| [0003](snapshots/0003-2026-10-24/SNAPSHOT.md) | 24 octobre 2026 | 0002 | Suivi global/par fonctionnalité validé D065 et comparaison des outils temporels proposée |
| [0004](snapshots/0004-2026-10-25.zip) | 25 octobre 2026 | 0003 | Reprise D066 ; archive ZIP conservant les octets, dont configuration Git capturée. Copie locale décompressée préservée mais exclue de Git. Référence antérieure au 24 octobre corrigée car capture absente |
| [0005](snapshots/0005-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0004 | Contrôles finaux du contenu préparé et conservation des captures ; aucun commit/push |
| [0006](snapshots/0006-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0005 | D067 exécutée : premier commit 2082f29 publié et vérifié ; suivi de fin d'opération |
| [0007](snapshots/0007-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0006 | Proposition finale C07 de clôture/modification, à valider ; pas de nouvelle décision métier |
| [0008](snapshots/0008-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0007 | Accord D068 sur clôture/modification, synthèses alignées et C07 documentaire terminée ; aucun code ni commit/push de ce lot |
| [0009](snapshots/0009-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0008 | D069 : commit descriptif et push après validation autorisés ; synchronisation D068/D069 préparée, non encore vérifiée |
| [0010](snapshots/0010-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0009 | D068/D069 publiées au commit de732bd et concordance distante vérifiée ; suivi de fin d'opération, sans nouvelle décision |
| [0011](snapshots/0011-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0010 | Accord D070 sur informations de soumission et qualification avant publication ; C09 en cours, synchronisation à exécuter |
| [0012](snapshots/0012-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0011 | D070 publiée au commit 86d06ea et concordance distante vérifiée ; suivi de fin d'opération |
| [0013](snapshots/0013-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0012 | Accord D071 sur consultation avant publication ; documents et contrôles attendus alignés, C09 en cours |
| [0014](snapshots/0014-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0013 | D071 publiée au commit 7fc20ee et concordance distante vérifiée ; suivi de fin d'opération |
| [0015](snapshots/0015-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0014 | Accord D072 sur traitement manuel des propositions en doublon ; documents et contrôles attendus alignés, C09 en cours |
| [0016](snapshots/0016-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0015 | D072 publiée au commit 1b4ece2 et concordance distante vérifiée ; suivi de fin d'opération |
| [0017](snapshots/0017-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0016 | Accord D073 sur réexamen après rejet et bilan courant du scope ; documentation alignée, C09 en cours |
| [0018](snapshots/0018-2026-10-25/SNAPSHOT.md) | 25 octobre 2026 | 0017 | D073 et bilan du scope publiés au commit 492951a et concordance distante vérifiée ; suivi de fin d'opération |

## Limites du passé et du futur

Avant 0001, le journal et le registre permettent de comprendre des changements consignés mais pas de garantir une copie complète des fichiers à chaque instant passé. Aucun ancien instantané fabriqué rétroactivement. Les états futurs ne sont enregistrés qu'après observation réelle, jamais à partir d'un résultat prévu.

Lecture t−n / t / t+n : choisir deux ou plusieurs identifiants de l'index et comparer leurs versions des mêmes fichiers. Les numéros ordonnent les états ; ils ne représentent pas une durée égale entre captures.
