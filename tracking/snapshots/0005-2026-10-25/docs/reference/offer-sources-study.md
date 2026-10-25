# Étude initiale des sources — 17 octobre 2026

Statut : recherche documentaire et recommandations, aucune source intégrée ni sélection validée. Autorisation : accord utilisateur pour comparer les possibilités gratuites de collecte.
Méthode : documentation officielle et conditions publiées ; lecture d'un endpoint public Arbeitnow via l'outil web. Aucun compte, abonnement, contact externe ou code applicatif créé. Aucun test de connecteur de production. Conditions à revérifier avant intégration.

## Résultats

| Source | Constat officiel | Conséquence proposée pour le pilote |
|---|---|---|
| LinkedIn | Conditions excluant scraping et copie automatisée sans autorisation ; API Job Posting destinée à publier/gérer des offres | Ne pas prévoir de robot de collecte LinkedIn. Examiner les droits de partage pour les contributions ; ne pas assimiler lien et permission de recopier |
| Indeed | Documentation partenaire : gestion d'offres/candidats et Publisher JavaScript Plugin pour intégrer la recherche ; accès console provisionné par Indeed | Ne pas conclure que toute intégration est impossible. Accès, gratuité, couverture Maroc et compatibilité avec notre file de validation non confirmés |
| Emploi.ma | CGU comportant restrictions sur robots et redistribution dans les engagements candidat | Pas de collecte robotisée proposée sans accord ou clarification ; source de recherche humaine, republication non présumée autorisée |
| ReKrute | Services candidats gratuits décrits ; pas de preuve d'API de collecte ouverte dans les pages consultées | Automatisation et droits de redistribution UNKNOWN, pas d'affirmation d'absence définitive d'API |
| Lever | API Postings documentée par entreprise, offres publiées publiques ; documentation reconnaissant leur collecte par des tiers | Piste technique prioritaire pour une liste d'entreprises ciblées ; pas un moteur mondial de découverte. Conditions des entreprises et pertinence à vérifier |
| Greenhouse | Job Board API : lecture GET publique sans authentification, par entreprise | Piste technique par entreprise ; accès public ne prouve pas une permission générale de republication. Conditions et adéquation à vérifier |
| Remotive | API publique, attribution/lien requis, décalage 24 h ; conditions interdisant de conditionner l'affichage à inscription/email | Ne pas retenir sans clarification pour notre espace réservé aux comptes validés. Interprétation de compatibilité, pas avis juridique |
| Arbeitnow | Endpoint JSON public lié depuis le site et lisible lors de l'étude ; site centré Allemagne | Piste secondaire : droits de réutilisation, gratuité durable et utilité pour juniors marocains non établis. Remote ne signifie pas accessible depuis le Maroc |

## Sources primaires

- LinkedIn : https://www.linkedin.com/legal/user-agreement (section 8.2) ; https://learn.microsoft.com/en-us/linkedin/talent/job-postings/api/create-jobs
- Indeed : https://docs.indeed.com/ ; https://docs.indeed.com/getstarted/
- Emploi.ma : https://www.emploi.ma/conditions-generales-utilisation
- ReKrute : https://www.rekrute.com/conditions-utilisation.html
- Lever : https://github.com/lever/postings-api
- Greenhouse : https://docs.greenhouse.io/job-board
- Remotive : https://github.com/remotive-com/remote-jobs-api
- Arbeitnow : https://www.arbeitnow.com/ ; https://www.arbeitnow.com/api/job-board-api ; https://www.arbeitnow.com/terms

## Recommandation à valider

1. Conserver contributions humaines et validation CME, sans promettre l'extraction automatique du contenu de tout lien ni une copie intégrale autorisée.
2. Étudier d'abord les pages carrières d'entreprises pertinentes au Maroc ou recrutant explicitement depuis le Maroc, notamment celles utilisant Lever/Greenhouse ou un flux officiel autorisé.
3. Pour chaque entreprise : vérifier offres junior/stage, restrictions géographiques, dates/durée, conditions de réutilisation et absence de frais pour notre usage ; tester ensuite une lecture minimale et la disponibilité réelle.
4. Évaluer un petit échantillon avant choix définitif : une API techniquement disponible ne garantit pas un volume utile de stages locaux.
5. Indeed reste une piste partenaire/plugin à clarifier ; ne pas en faire une dépendance du pilote gratuit.

## Inconnues et limites

Complément utilisateur : Capgemini, Tessi et Sofrecom (nom confirmé après clarification de « Sofricom ») citées comme premières entreprises à examiner ; voir docs/product/target-companies.md. Partenariats, offres et modes de collecte non vérifiés. Cette liste constitue des cibles d'étude, pas une sélection d'intégrations validée.

Aucune entreprise concrète sélectionnée, aucun échantillon de pertinence mesuré pour le Maroc, aucune couverture des stages de deux mois démontrée. Coûts de fonctionnement de notre propre plateforme non évalués. Conditions de réutilisation à préciser avant intégration ; possibilité de demander une autorisation, sans aucun message envoyé lors de cette étude.
Conclusion : automatisation ciblée techniquement plausible, couverture utile et droits pour les sources précises encore à démontrer. La collecte automatique reste dans l'objectif ; aucune réduction au seul partage manuel décidée.
