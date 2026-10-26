# Stack et architecture — comparaison initiale

Date : 26 octobre 2026. Statut courant : stack et architecture générale validées D008 ; Docker retenu D088. React/Vite + TypeScript, Node.js/NestJS, API REST, PostgreSQL et serveur en monolithe modulaire. R01 en cours pour les détails et hébergement ; aucun code ni installation réalisés. Les comparaisons et mentions de propositions ci-dessous décrivent les étapes ayant précédé cet accord.

## Contraintes de référence

Scope D007 validé, ordre D086 conservé. Première tranche : accès, établissement/classes et offres humaines ; autres domaines ajoutés progressivement. Comptes individuels, rôles contextualisés, confidentialité et séparation des établissements dès la conception. Produit réel destiné au campus, avec réalisation progressive et accompagnement du porteur, sans date fixe. Les choix sont évalués sur les besoins, la sécurité, la maintenabilité et les moyens de réalisation/exploitation. Automatisation ultérieure indépendante.

## Priorité confirmée D087

JavaScript/React est la préférence technologique indiquée par l'utilisateur. Rectification : le projet vise un usage réel pour le campus ; la qualification de priorité pédagogique par l'assistant était une interprétation corrigée. Le serveur, la base et l'architecture restent ouverts ; aucune technologie déduite automatiquement.

## Comparaison préliminaire

| Option | Intérêt pour le projet | Contrepartie |
|---|---|---|
| Laravel + React/TypeScript via Inertia + PostgreSQL | Application intégrée, conventions Laravel et interface React ; bon compromis proposé pour avancer sur le métier tout en apprenant PHP et React | Deux langages et Inertia à apprendre ; pas une API REST indépendante par défaut |
| Spring Boot + React ou Angular + PostgreSQL | Écosystème Java, services métier, API REST et sécurité ; séparation explicite interface/serveur | Intégration et exploitation de deux applications à prévoir, davantage de concepts à coordonner ; choix du frontend encore ouvert |
| Next.js + TypeScript + PostgreSQL | Cohérence de langage interface/serveur avec React | Bibliothèques d'accès aux données/authentification à comparer ; règles métier et frontières serveur/client à structurer explicitement |

Alternative si priorité à la simplicité PHP : Laravel avec Blade/Livewire, réduisant la place de React mais impliquant les concepts Livewire. Aucun gain de temps chiffré, coût d'hébergement ou supériorité universelle affirmé. Les comparaisons de charge sont des appréciations pour ce contexte, pas des mesures.

La recommandation initiale conditionnelle Laravel/PHP est à réexaminer selon la préférence JavaScript/React D087 et les besoins réels du campus. La comparaison doit porter sur les permissions, la séparation des établissements, les parcours métier, les tests, la maintenabilité et les moyens de réalisation/exploitation. La recommandation JavaScript concrète ci-dessous est désormais validée D008 ; versions, dépendances détaillées, hébergement et budget restent à décider.

## Proposition concrète après D087 — validée D008

Recommandation : React avec Vite et TypeScript pour l'interface, Node.js avec NestJS et TypeScript pour une API REST, PostgreSQL pour les données ; serveur organisé en monolithe modulaire. Proposition désormais validée par accord explicite D008 ; aucun démarrage applicatif inclus.

Motifs : préférence JavaScript/React, interface de gestion interactive, nombreuses règles de rôles/établissements et transitions métier. NestJS propose modules, contrôleurs, services, validation et mécanismes de contrôle d'accès ; leur présence ne remplace pas la conception de nos permissions. TypeScript aide à détecter des incohérences de types avant exécution, sans remplacer la validation des données reçues. PostgreSQL proposé pour les relations et contraintes d'intégrité ; les autres bases SQL restent possibles.

Comparaison déterminante : Next.js intégré permet de réunir interface et fonctions serveur dans une application, avec moins de séparation opérationnelle ; il reste viable pour le pilote. React + NestJS fournit une frontière API explicite et un cadre serveur structuré, au prix de deux composants à intégrer, sécuriser et exploiter. Cette séparation est un choix de maintenabilité proposé pour nos règles métier, pas un besoin de volume ni une obligation pour du multi-établissements. React recommande généralement un framework ; le choix Vite suppose de prévoir explicitement routage, appels réseau, chargements et erreurs. Express seul constitue une autre option plus légère, avec davantage de conventions à définir et maintenir nous-mêmes.

Périmètre exact de l'accord à demander : React/Vite, TypeScript, Node.js/NestJS, PostgreSQL et organisation serveur en monolithe modulaire. Les modules seraient introduits par tranches : identité/organisation et offres d'abord ; autres domaines ensuite. Aucun microservice requis pour le pilote proposé. Frontend et serveur séparés ne constituent pas à eux seuls des microservices.

ORM, authentification/sessions, stratégie précise de séparation des établissements, stockage privé, bibliothèque UI, versions et hébergement restent à comparer et valider. Conséquences de déploiement à spécifier avant initialisation ; documentation D008 et suivi mis à jour sans code applicatif.

## Organisation métier proposée

Un monolithe modulaire : un serveur métier déployable comme une unité, organisé par responsabilités. Une interface séparée reste possible avec Spring ; elle ajoute un composant à exploiter sans imposer plusieurs services métier.

Domaines introduits au rythme des tranches : identité/organisation, offres, puis documents/revues et candidatures/entreprises, puis accompagnement/pilotage. Pas de modules vides ou de couches systématiques imposées d'avance.

Base relationnelle recommandée : les liens établissement/classe/membre, offre/candidature et document/avis se prêtent aux relations et contraintes SQL. PostgreSQL proposé, non validé. Stratégie de séparation des établissements (base partagée, schémas ou bases séparées) à comparer ; un identifiant d'établissement seul ne constitue pas une protection suffisante. Accès vérifiés côté serveur et tests de séparation attendus.

Exemple de responsabilités : interface de publication → réception et validation → contrôle CME/établissement → règles de publication → écriture en base. Une interface masquant un bouton ne remplace pas le contrôle serveur. Les fichiers CV seront privés ; stockage et accès techniques restent à choisir pour leur tranche.

## Prochaine discussion

Stack et architecture générale validées D008, Docker retenu D088. Prochaine discussion : organisation du dépôt et périmètre Docker en développement, puis détails de données/authentification/hébergement. Aucun accord global implicite sur ces modalités.

## Sources officielles consultées

- [Laravel : starter kits React/Inertia, Livewire et authentification](https://laravel.com/framework/docs/13.x/starter-kits)
- [Spring Boot : applications autonomes et configuration](https://spring.io/projects/spring-boot/)
- [Spring Boot : intégration Spring Security](https://docs.spring.io/spring-boot/reference/web/spring-security.html)
- [Next.js : backend pour le frontend et limites](https://nextjs.org/docs/app/guides/backend-for-frontend)
- [Next.js : authentification, sessions et autorisation](https://nextjs.org/docs/app/guides/authentication)
- [PostgreSQL : contraintes relationnelles](https://www.postgresql.org/docs/current/ddl-constraints.html)
- [NestJS : organisation du serveur et fonctionnalités](https://docs.nestjs.com/)
- [React : création d'application et recommandation de frameworks](https://react.dev/learn/creating-a-react-app)
- [Vite : outil de développement et de build](https://vite.dev/guide/)

Les pages consultées ne fixent pas les versions du projet. Ces choix restent ouverts.

## Docker — ajout validé D088, modalités ouvertes

Docker est retenu. Proposition à discuter : Docker Compose pour décrire et démarrer les services nécessaires au développement ; interface, API et PostgreSQL pourraient être conteneurisés, ou seulement la base avec applications lancées localement. Tout conteneuriser uniformise davantage les commandes ; la base seule allège le démarrage mais requiert Node.js local. Choix pas encore arbitré. Volumes persistants, secrets, accès réseau, images et différences développement/production devront être spécifiés avant configuration. Aucun outil installé, aucune image téléchargée, aucun conteneur lancé.

Sources : [Docker, présentation](https://docs.docker.com/get-started/docker-overview/) et [Docker Compose](https://docs.docker.com/compose/).
