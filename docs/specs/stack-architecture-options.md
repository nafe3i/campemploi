# Stack et architecture — comparaison initiale

Date : 26 octobre 2026. Statut : propositions, aucune stack ni architecture technique validée. R01 en cours ; D008 reste UNKNOWN. Aucun code ni installation autorisé par cette comparaison.

## Contraintes de référence

Scope D007 validé, ordre D086 conservé. Première tranche : accès, établissement/classes et offres humaines ; autres domaines ajoutés progressivement. Comptes individuels, rôles contextualisés, confidentialité et séparation des établissements dès la conception. Pilotage initial par un développeur en apprentissage, sans date fixe. Automatisation ultérieure indépendante.

## Priorité confirmée D087

JavaScript/React est la priorité pédagogique explicitement indiquée par l'utilisateur. Expérience en application complète encore à préciser. Le serveur, la base et l'architecture restent ouverts ; aucune technologie déduite automatiquement.

## Comparaison préliminaire

| Option | Intérêt pour le projet et apprentissage | Contrepartie |
|---|---|---|
| Laravel + React/TypeScript via Inertia + PostgreSQL | Application intégrée, conventions Laravel et interface React ; bon compromis proposé pour avancer sur le métier tout en apprenant PHP et React | Deux langages et Inertia à apprendre ; pas une API REST indépendante par défaut |
| Spring Boot + React ou Angular + PostgreSQL | Approfondissement Java, services métier, API REST et sécurité ; séparation explicite interface/serveur | Intégration et exploitation de deux applications à prévoir, davantage de concepts à coordonner ; choix du frontend encore ouvert |
| Next.js + TypeScript + PostgreSQL | Cohérence de langage interface/serveur et apprentissage React | Bibliothèques d'accès aux données/authentification à comparer ; règles métier et frontières serveur/client à structurer explicitement |

Alternative si priorité à la simplicité PHP : Laravel avec Blade/Livewire, réduisant la place de React mais impliquant les concepts Livewire. Aucun gain de temps chiffré, coût d'hébergement ou supériorité universelle affirmé. Les comparaisons de charge sont des appréciations pour ce contexte, pas des mesures.

Recommandation initiale conditionnelle, avant réponse D087 : Laravel + React/Inertia + PostgreSQL si priorité à la réalisation progressive du produit avec PHP/React. Spring Boot devient préférable si l'objectif pédagogique principal est Java. D087 confirme désormais JavaScript/React comme priorité ; la recommandation finale doit être réexaminée en conséquence, après clarification de l'expérience réelle. Versions, dépendances, hébergement et budget restent à décider ultérieurement.

## Architecture proposée, indépendante du choix final

Un monolithe modulaire : un serveur métier déployable comme une unité, organisé par responsabilités. Une interface séparée reste possible avec Spring ; elle ajoute un composant à exploiter sans imposer plusieurs services métier.

Domaines introduits au rythme des tranches : identité/organisation, offres, puis documents/revues et candidatures/entreprises, puis accompagnement/pilotage. Pas de modules vides ou de couches systématiques imposées d'avance.

Base relationnelle recommandée : les liens établissement/classe/membre, offre/candidature et document/avis se prêtent aux relations et contraintes SQL. PostgreSQL proposé, non validé. Stratégie de séparation des établissements (base partagée, schémas ou bases séparées) à comparer ; un identifiant d'établissement seul ne constitue pas une protection suffisante. Accès vérifiés côté serveur et tests de séparation attendus.

Exemple de responsabilités : interface de publication → réception et validation → contrôle CME/établissement → règles de publication → écriture en base. Une interface masquant un bouton ne remplace pas le contrôle serveur. Les fichiers CV seront privés ; stockage et accès techniques restent à choisir pour leur tranche.

## Prochaine discussion

Priorité JavaScript/React confirmée D087 ; clarifier les réalisations déjà maîtrisées, notamment connexion, API et base de données. Puis soumettre une proposition concrète de stack à validation avant de modifier D008. Architecture détaillée, modèle de données, authentification et hébergement nécessiteront leurs arbitrages ; aucun accord global implicite.

## Sources officielles consultées

- [Laravel : starter kits React/Inertia, Livewire et authentification](https://laravel.com/framework/docs/13.x/starter-kits)
- [Spring Boot : applications autonomes et configuration](https://spring.io/projects/spring-boot/)
- [Spring Boot : intégration Spring Security](https://docs.spring.io/spring-boot/reference/web/spring-security.html)
- [Next.js : backend pour le frontend et limites](https://nextjs.org/docs/app/guides/backend-for-frontend)
- [Next.js : authentification, sessions et autorisation](https://nextjs.org/docs/app/guides/authentication)
- [PostgreSQL : contraintes relationnelles](https://www.postgresql.org/docs/current/ddl-constraints.html)

Les pages consultées ne fixent pas les versions du projet. Ces choix restent ouverts.
