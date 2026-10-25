# Historique des états du projet

## Principe — D063

BOARD.md et STATUS.md montrent l'état courant ; JOURNAL.md explique les changements. Les instantanés dans tracking/snapshots/ conservent les versions observées à un moment précis. Un instantané existant n'est pas réécrit ; toute correction donne lieu à un nouvel instantané et une explication au journal.

Créer un instantané après chaque changement significatif de décision, périmètre ou avancement, et en fin de session si le suivi a changé. Utiliser un identifiant croissant même pour plusieurs états le même jour, indiquer prédécesseur, motif, date d'enregistrement et fichiers conservés. Inclure les preuves/documents concernés et leurs références ; une référence à un fichier courant seul ne garantit pas son contenu historique. Ne pas copier de secrets ou de données personnelles réelles.

Ce sont des copies documentaires, pas une sauvegarde complète du poste ou une restauration de l'application. Git est désormais initialisé et un premier état a été publié (D066–D067) ; il complète les captures sans les remplacer. Les nouveaux changements locaux ne sont pas automatiquement publiés.

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

## Limites du passé et du futur

Avant 0001, le journal et le registre permettent de comprendre des changements consignés mais pas de garantir une copie complète des fichiers à chaque instant passé. Aucun ancien instantané fabriqué rétroactivement. Les états futurs ne sont enregistrés qu'après observation réelle, jamais à partir d'un résultat prévu.

Lecture t−n / t / t+n : choisir deux ou plusieurs identifiants de l'index et comparer leurs versions des mêmes fichiers. Les numéros ordonnent les états ; ils ne représentent pas une durée égale entre captures.
