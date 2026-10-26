# Stack et architecture — comparaison initiale

Date : 26 octobre 2026. Statut : propositions, aucune stack ni architecture technique validée. R01 en cours ; D008 reste UNKNOWN. Aucun code ni installation autorisé par cette comparaison.

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

La recommandation initiale conditionnelle Laravel/PHP est à réexaminer selon la préférence JavaScript/React D087 et les besoins réels du campus. La comparaison doit porter sur les permissions, la séparation des établissements, les parcours métier, les tests, la maintenabilité et les moyens de réalisation/exploitation. Aucune recommandation finale validée. Versions, dépendances, hébergement et budget restent à décider.

## Architecture proposée, indépendante du choix final

Un monolithe modulaire : un serveur métier déployable comme une unité, organisé par responsabilités. Une interface séparée reste possible avec Spring ; elle ajoute un composant à exploiter sans imposer plusieurs services métier.

Domaines introduits au rythme des tranches : identité/organisation, offres, puis documents/revues et candidatures/entreprises, puis accompagnement/pilotage. Pas de modules vides ou de couches systématiques imposées d'avance.

Base relationnelle recommandée : les liens établissement/classe/membre, offre/candidature et document/avis se prêtent aux relations et contraintes SQL. PostgreSQL proposé, non validé. Stratégie de séparation des établissements (base partagée, schémas ou bases séparées) à comparer ; un identifiant d'établissement seul ne constitue pas une protection suffisante. Accès vérifiés côté serveur et tests de séparation attendus.

Exemple de responsabilités : interface de publication → réception et validation → contrôle CME/établissement → règles de publication → écriture en base. Une interface masquant un bouton ne remplace pas le contrôle serveur. Les fichiers CV seront privés ; stockage et accès techniques restent à choisir pour leur tranche.

## Prochaine discussion

Préférence JavaScript/React précisée D087 ; comparer les options adaptées au produit réel, en tenant compte des moyens disponibles. Puis soumettre une proposition concrète de stack à validation avant de modifier D008. Architecture détaillée, modèle de données, authentification et hébergement nécessiteront leurs arbitrages ; aucun accord global implicite.

## Sources officielles consultées

- [Laravel : starter kits React/Inertia, Livewire et authentification](https://laravel.com/framework/docs/13.x/starter-kits)
- [Spring Boot : applications autonomes et configuration](https://spring.io/projects/spring-boot/)
- [Spring Boot : intégration Spring Security](https://docs.spring.io/spring-boot/reference/web/spring-security.html)
- [Next.js : backend pour le frontend et limites](https://nextjs.org/docs/app/guides/backend-for-frontend)
- [Next.js : authentification, sessions et autorisation](https://nextjs.org/docs/app/guides/authentication)
- [PostgreSQL : contraintes relationnelles](https://www.postgresql.org/docs/current/ddl-constraints.html)

Les pages consultées ne fixent pas les versions du projet. Ces choix restent ouverts.
