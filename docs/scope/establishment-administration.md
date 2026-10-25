# Administration des établissements — organisation validée

Mise à jour : 25 octobre 2026. Références D056 et D076. Statut : organisation et périmètre administratif du pilote validés ; procédures techniques détaillées à spécifier. Aucun code applicatif.

## Organisation proposée par l'utilisateur

Administrateur général → création de l'établissement et de la CME → CME crée classes, formateurs et personnel de son établissement.

## Organisation retenue après analyse

Le découpage global/local facilite l'autonomie des établissements. Distinguer toutefois deux responsabilités : rôle métier CME (offres, accompagnement et suivi) et administration locale (classes, rattachements et rôles). La CME peut cumuler les deux, mais les séparer permet le remplacement ou la délégation sans ouvrir les données confidentielles à tout gestionnaire de comptes.

- Administrateur général : création des établissements, désignation du premier administrateur local ; aucun accès automatique aux CV/bilans déduit.
- Administrateur local, éventuellement CME : gestion locale des classes, invitations du personnel, rattachements, rôles locaux et affectations.
- Personnel invité : activation de son propre compte et choix du mot de passe ; pas de gestion manuelle des mots de passe par la CME.
- Apprenants : inscription/rattachement selon D038 ; l'invitation du personnel ne remplace pas implicitement cette règle.
- Aucun administrateur local ne crée d'administrateur général ni ne gère un autre établissement.
- « Staff » reste à définir en permissions précises, sans rôle unique donnant accès à tout.
- Affectations de revue D078 : CME avec permission locale gère un formateur référent par classe ; un formateur peut suivre plusieurs classes. D079 : formateur et responsable technique sont le même rôle métier ; référent est une affectation. Remplacement à préciser, sans accès automatique aux autres classes/bilans ni permission d'administration ajoutée.

Périmètre pilote validé D076 : mise en place du premier établissement et de sa CME par l'administrateur général, puis classes, invitations/rattachements et rôles nécessaires par CME avec permission locale. Écrans complets de gestion simultanée de plusieurs établissements reportés ; limites d'établissement et séparation des rôles dès la conception. Modalité de création initiale à comparer en architecture, sans choix technique implicite.

## Arbitrages ouverts

### Invitation des apprenants par classe — D059 validée

La CME génère un lien réutilisable propre à une classe de son établissement. Elle peut partager un seul lien avec la classe ; chaque personne crée son compte individuel ou se connecte, puis demande le rattachement. Accès interne après validation CME uniquement, comme D038. Un lien transféré ne suffit pas à obtenir l'accès. Expiration, désactivation et renouvellement prévus ; pas de mot de passe ou donnée personnelle dans le lien. Aucun changement automatique de classe d'un compte déjà rattaché. Envoi externe non effectué par l'assistant sans autorisation explicite.

Durée d'expiration, demandes multiples et changement de classe/établissement à définir dans les spécifications. Ce parcours ne remplace pas les invitations du personnel ni n'attribue leurs rôles.

1. Administration générale par le porteur et gestion locale par la CME validées ; périmètre pilote précisé D076, écrans détaillés à spécifier. D039 modifiée par D056.
2. Distinction CME/administration locale et invitations du personnel retenues ; modalités d'activation à spécifier.
3. Quels membres du personnel et quelles délégations locales sont nécessaires ?
4. Désignation, remplacement et récupération d'accès d'un administrateur local ; création du premier administrateur général.
5. Écrans complets multi-établissements reportés D076 ; détails de leur évolution ultérieure à spécifier.

Décision documentaire enregistrée, aucune permission technique appliquée et aucun code applicatif. Les protections des documents et observations restent régies par les décisions existantes.
