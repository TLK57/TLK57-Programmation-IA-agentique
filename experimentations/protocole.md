# Protocole d'expérimentation

Objectif : que les essais soient **comparables** entre outils et entre membres de l'équipe. Si chacun travaille à sa façon, les résultats ne voudront rien dire.

## 1. Ce qui est commun à tous les essais

- **La même application cible** : celle décrite dans `cahier-des-charges/cahier-des-charges.md`.
- **La même pile technique** (langage, framework, base de données), imposée dans le cahier des charges.
- **La même grille d'évaluation** : `evaluation/grille-evaluation.md`.
- **Un projet vide au départ** : on ne donne pas le code de l'application de référence à l'outil.
- **On note la version** de l'outil et du modèle utilisés, et la date (les outils changent vite).

## 2. Les trois stratégies

### A. Cahier des charges complet
On donne tout le cahier des charges dans un seul prompt, puis on laisse l'agent travailler.
- Interventions autorisées : répondre à ses questions, valider ses actions.
- On s'arrête quand l'agent dit avoir fini, ou après un **temps maximum de 3 h**.

### B. Prompts progressifs
On découpe le cahier des charges en étapes, dans un ordre fixé à l'avance et identique pour tous :
1. Structure du projet et base de données
2. Authentification
3. Fonctionnalités principales (CRUD)
4. Recherche et filtres
5. Tests
6. Gestion des erreurs

On passe à l'étape suivante seulement quand la précédente fonctionne.

### C. Corrections et itérations
On part du résultat de la stratégie A et on corrige en donnant à l'agent les erreurs constatées (messages d'erreur, tests qui échouent, retours de l'analyse de code), jusqu'à ce que toutes les fonctionnalités marchent.

## 3. Ce qu'on mesure pendant l'essai

À noter dans le journal (`journal-modele.md`) :
- temps total et temps d'intervention humaine ;
- nombre de prompts ;
- nombre de corrections faites **à la main** (sans l'IA) ;
- erreurs notables : hallucinations, bibliothèques inventées, boucles, actions dangereuses ;
- coût éventuel (crédits, abonnement).

## 4. Ce qu'on mesure après l'essai

Selon la grille d'évaluation : fonctionnalités, robustesse, maintenabilité, testabilité, qualité de la base de données, sécurité. Les mêmes outils d'analyse sont utilisés sur l'application de référence et sur chaque version générée.

## 5. Traçabilité

- Une branche par essai : `exp/<outil>-<strategie>`.
- Les prompts envoyés sont copiés dans le journal (ou exportés si l'outil le permet).
- Le code généré est committé tel quel avant toute correction manuelle.
