# Essai d'échauffement : Claude Code · todo-list Flask

> Essai **hors protocole**, pour prendre l'outil en main. Il ne compte pas dans les résultats officiels, mais il donne de premières observations et des pistes de critères d'évaluation.

## Contexte

| | |
|---|---|
| Membre | Abdullah |
| Date | 9 novembre 2026 |
| Outil | Claude Code (abonnement Claude) |
| Application | Todo-list web : Python, Flask, SQLite, pytest |
| Durée totale | environ 2 h (de 11 h 40 à 13 h 40, pause déjeuner comprise) |
| Prompts envoyés | 4 |
| Lignes de code (hors tests) | environ 290 |
| Code | Dossier local « Essai AI » (non versionné dans ce dépôt) |

## Méthode

Une boucle en trois temps, répétée trois fois :

1. **L'agent produit** (ou corrige) le code et ses tests.
2. **Un vérificateur indépendant** contrôle le résultat sans se fier au compte rendu de l'agent : relecture du code, tests relancés sur une copie, couverture (pytest-cov), analyse de sécurité (Bandit), attaques scriptées, et **tests de mutation** (on casse volontairement une protection pour voir si un test échoue).
3. Les problèmes trouvés sont renvoyés à l'agent dans le prompt suivant.

Prompt initial : todo-list avec inscription et connexion (mots de passe hachés), tâches privées à chaque utilisateur, CRUD, filtre par statut, structure propre, tests pytest, README, et présentation du plan avant de coder.

## Déroulé

| Tour | Ce que l'agent a livré | Ce que la vérification indépendante a trouvé |
|---|---|---|
| 1 | Appli fonctionnelle en 6 commits, **46 tests**, 98 % de couverture. Il a testé lui-même l'interface dans un navigateur (dont l'accès aux tâches d'un autre utilisateur). | **1 bug** : un id énorme dans l'URL provoquait une erreur 500.<br>**3 failles** : pas de protection contre la force brute (100 essais sans blocage), noms d'utilisateur sensibles à la casse (« Alice » à côté de « alice »), pas d'en-têtes de sécurité HTTP. |
| 2 | Les 4 problèmes corrigés, un commit chacun, **84 tests**. Pour chaque problème : reproduction, test qui échoue, puis correction. | Correctifs confirmés, et les tentatives de contournement échouent (casse, changement d'IP, en-tête `X-Forwarded-For`).<br>**Nouvelle faille** : 4 comptes imitant « alice » acceptés grâce à l'Unicode, dont un avec un caractère **invisible**. L'agent n'avait signalé qu'un seul de ces cas (le « а » cyrillique). |
| 3 | Noms limités à `a-z 0-9 . _ -`, **103 tests**, anciens comptes préservés. | Correctif confirmé sur 10 variantes piégées.<br>Restent des détails mineurs : `alice.` et `___` sont acceptés. |

## Mesures

| Critère | Résultat | Commentaire |
|---|---|---|
| Fonctionnalités | 100 % | Toutes les fonctionnalités demandées fonctionnent |
| Tests | 46 → 103 tests, 98 % de couverture | Tests de qualité : **11 mutations sur 11 détectées** |
| Sécurité (tour 1) | 1 bug + 3 failles | Malgré 98 % de couverture |
| Sécurité (final) | 2 détails mineurs | Après 2 tours de correction guidés |
| Analyse statique (Bandit) | 1 alerte bénigne | Clé secrète de la configuration de test |
| Effort humain | 4 prompts | Mais une vérification indépendante approfondie à chaque tour |

## Observations

**Points forts**
- Code propre et bien structuré dès le départ : CSRF actif, mots de passe hachés (scrypt), ORM (pas d'injection SQL), échappement HTML, redirections malveillantes bloquées.
- **Méthode rigoureuse** une fois guidé : test d'abord, vérification que le test échoue, correction, un commit par problème.
- **Il vérifie ses propres tests** par mutation. Il a ainsi repéré seul des tests qui passaient sans rien prouver (apostrophe transformée en `&#39;` par Jinja).
- Il anticipe des effets de bord : la nouvelle politique CSP aurait cassé la confirmation de suppression, il l'a vu et corrigé.
- Il signale ses propres erreurs et les limites restantes (comptes bloquables 15 min, compteurs en mémoire).

**Limites**
- **Il ne trouve pas ce qu'il ne pense pas à tester.** 46 tests verts et 98 % de couverture n'ont empêché ni le crash, ni la faille de force brute.
- Il corrige très bien ce qu'on lui signale, mais n'étend pas de lui-même la recherche aux cas voisins (4 variantes Unicode, il n'en avait cité qu'une).
- Fragilité face aux imprévus : une session coupée pendant une pause, une navigation lancée trop tôt. Il s'en est remis seul.
- Certaines décisions restent humaines : bloquer un compte après 5 échecs protège contre la force brute, mais permet aussi à quelqu'un de bloquer un compte exprès.

## Pistes pour la grille d'évaluation

1. **La couverture de code ne suffit pas** à juger des tests générés par une IA : il faut aussi mesurer leur capacité à détecter des erreurs (**tests de mutation**).
2. Compter le **nombre de tours de vérification** nécessaires avant d'atteindre un niveau de sécurité acceptable.
3. Distinguer ce que l'agent **trouve seul** de ce qu'il **corrige quand on le lui signale**.
4. Toujours faire vérifier par **quelqu'un (ou quelque chose) d'indépendant** de l'agent qui a produit le code.
