# Solutions pour suivre le projet dans le temps

Date : 24 octobre 2026. Statut : comparaison et recommandation Proposed, pas choix validé. Méthode par fonctionnalité validée séparément (D065). Git 2.51.0.windows.1 présent, aucun dossier .git local lors de la vérification ; pas d'accès GitHub du projet vérifié, aucune création distante.

## Comparaison

| Solution | Utilité | Limite |
|---|---|---|
| Documents et instantanés actuels | Vue courante, décisions, raisons, copies figées | Copies manuelles et comparaison moins commode ; pas d'historique complet avant capture |
| Git local avec documents | Commits pour conserver chaque état enregistré, diff pour comparer ; adapté aussi à la conception avant le code | Ne suit pas automatiquement tâches, données réelles ou déploiements ; pas de copie distante par défaut |
| Git + dépôt GitHub + Issues/Projects | Historique partagé, tâches, tableau, jalons, PR et lien à la réalisation | Configuration et discipline nécessaires ; plan, confidentialité et quotas des automatisations à vérifier avant usage |
| Git + GitLab | Alternative intégrant suivi, merge requests, jalons et releases | Migration/installation éventuelles sans avantage établi pour notre pilote ; ne pas multiplier les plateformes |

## Recommandation, à valider

Git local dès les documents de conception, puis dépôt GitHub privé avec Issues/Projects si approuvé. Une tâche/issue par résultat concret, reliée au document de décision, à une branche et PR, aux tests, puis à une version et un déploiement enregistré. Jalons sans imposer de date : accès/offres, candidatures, accompagnement, pilote. Ajouter l'automatisation des tests au développement, pas avant la stack. Déploiement seulement après autorisation.

Git ne remplace ni les décisions ni les preuves de production. Une release marque une version ; elle peut ne pas être déployée. Le suivi doit enregistrer version/commit réellement déployé, environnement, date et résultat. Les données de base et fichiers utilisateur demandent une sauvegarde distincte ; aucun CV ni secret dans le dépôt.

Éviter deux tableaux manuellement concurrents : proposition, si GitHub adopté, tâches opérationnelles dans Issues/Projects, décisions/spécifications dans les fichiers versionnés, BOARD.md comme point de reprise et liens. La migration de D062/D063 demanderait validation ; ne pas supprimer les captures existantes ou remplacer leur règle avant accord.

Si Git est adopté : préparer le premier contenu et les exclusions, relire les données sensibles puis présenter le périmètre avant commit/publication. Une première capture enregistrée aujourd'hui ne recrée pas les commits des semaines passées. Rien n'a encore été initialisé ni envoyé.

## Sources officielles consultées

- Git, instantanés et commits : https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F
- GitHub Issues : https://docs.github.com/en/issues/tracking-your-work-with-issues/learning-about-issues/about-issues
- Projects : https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects
- Jalons : https://docs.github.com/en/issues/using-labels-and-milestones-to-track-work/about-milestones
- Pull requests : https://docs.github.com/en/pull-requests/reference/pull-requests
- GitHub Actions : https://docs.github.com/en/actions/get-started/understand-github-actions
- Versions : https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases
- Déploiements : https://docs.github.com/en/actions/how-tos/deploy/configure-and-manage-deployments/view-deployment-history
- GitLab : https://docs.gitlab.com/user/project/milestones/ ; https://docs.gitlab.com/user/project/releases/
