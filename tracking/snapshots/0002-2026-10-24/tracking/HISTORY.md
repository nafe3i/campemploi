# Historique des états du projet

## Principe — D063

BOARD.md et STATUS.md montrent l'état courant ; JOURNAL.md explique les changements. Les instantanés dans tracking/snapshots/ conservent les versions observées à un moment précis. Un instantané existant n'est pas réécrit ; toute correction donne lieu à un nouvel instantané et une explication au journal.

Créer un instantané après chaque changement significatif de décision, périmètre ou avancement, et en fin de session si le suivi a changé. Utiliser un identifiant croissant même pour plusieurs états le même jour, indiquer prédécesseur, motif, date d'enregistrement et fichiers conservés. Inclure les preuves/documents concernés et leurs références ; une référence à un fichier courant seul ne garantit pas son contenu historique. Ne pas copier de secrets ou de données personnelles réelles.

Ce sont des copies documentaires, pas une sauvegarde complète du poste ou une restauration de l'application. Git n'est pas encore initialisé ; son introduction pourra fournir ensuite l'historique des fichiers/code par commits. Ne pas prétendre que cet historique existe déjà.

## Index

| Instantané | Date d'enregistrement | Prédécesseur | Motif |
|---|---|---|---|
| [0001](snapshots/0001-2026-10-24/SNAPSHOT.md) | 24 octobre 2026 | Aucun état complet sauvegardé | Premier état figé du suivi et des documents de cadrage courants |
| [0002](snapshots/0002-2026-10-24/SNAPSHOT.md) | 24 octobre 2026 | 0001 | Règle d'accord explicite avant application des décisions (D064) |

## Limites du passé et du futur

Avant 0001, le journal et le registre permettent de comprendre des changements consignés mais pas de garantir une copie complète des fichiers à chaque instant passé. Aucun ancien instantané fabriqué rétroactivement. Les états futurs ne sont enregistrés qu'après observation réelle, jamais à partir d'un résultat prévu.

Lecture t−n / t / t+n : choisir deux ou plusieurs identifiants de l'index et comparer leurs versions des mêmes fichiers. Les numéros ordonnent les états ; ils ne représentent pas une durée égale entre captures.
