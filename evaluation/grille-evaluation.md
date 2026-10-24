# Grille d'évaluation (version de travail)

À compléter avec la bibliographie, comme l'a demandé l'encadrant. Point de départ possible : le modèle de qualité logicielle **ISO/IEC 25010** (aptitude fonctionnelle, fiabilité, maintenabilité, sécurité…).

Chaque critère est mesuré **sur l'application de référence** et **sur chaque version générée**, avec les mêmes outils.

| Critère | Ce qu'on vérifie | Mesure / outil | Note |
|---|---|---|---|
| Fonctionnalités | Les fonctionnalités du cahier des charges marchent | % de fonctionnalités validées (liste de tests d'acceptation) | /5 |
| Robustesse | Comportement face aux entrées invalides, erreurs gérées | Scénarios de test d'erreurs, plantages observés | /5 |
| Maintenabilité | Structure, lisibilité, duplication, complexité | SonarQube : dette technique, duplication, complexité | /5 |
| Testabilité | Présence et qualité des tests | Nombre de tests, couverture de code | /5 |
| Qualité de la BD | Normalisation, clés, contraintes, index | Comparaison avec le schéma de référence | /5 |
| Sécurité | Injections SQL, mots de passe hachés, failles connues | Semgrep / SonarQube, vérifications manuelles | /5 |
| Effort humain | Ce que nous avons dû faire nous-mêmes | Temps, nombre de prompts, corrections manuelles | – |
| Coût | Prix pour réaliser l'essai | Abonnement, crédits consommés | – |

## Questions encore ouvertes

- Faut-il pondérer les critères ? Si oui, comment le justifier ?
- Quels tests d'acceptation exacts pour mesurer les fonctionnalités ?
- Quelle échelle de notation retenir (/5, pourcentage, rang) ?
