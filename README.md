# Programmation IA agentique : vers le développement facile de systèmes

**Projet tutoré 2026-2027 : possibilités et limites des outils de développement agentique**

Équipe : Abdullah · Salmane · Victor

---

## Le projet en bref

On étudie les outils de développement agentique (Claude Code, GitHub Copilot, Gemini, JetBrains) et les LLM qu'ils utilisent pour coder. Le cœur du travail :

1. **Reprendre une application déjà développée à la main** (notre référence).
2. **La redévelopper avec chaque outil**, selon plusieurs stratégies de prompting.
3. **Comparer les résultats** : fonctionnalités, mais aussi robustesse, maintenabilité, testabilité, qualité de la base de données et sécurité.
4. **Montrer la valeur ajoutée du développeur** : contrôle des outils, validation du code, prise de décision, compréhension des limites des LLM.

Livrables : un rapport (une vingtaine de pages, introduction aux LLM, usage en développement, comparaison des outils, critères d'évaluation) et les versions de l'application produites avec l'IA.

Soutenances : janvier/février 2027 puis fin mars 2027 (dates à confirmer).

## Organisation du dépôt

```
.
├── application-reference/   L'application faite à la main (la référence)
├── cahier-des-charges/      Le cahier des charges commun, utilisé comme prompt (stratégie A)
├── experimentations/        Un dossier par outil, une branche par essai
│   ├── protocole.md         Les règles communes à tous les essais
│   ├── journal-modele.md    Modèle de journal à remplir pour chaque essai
│   ├── claude-code/
│   ├── github-copilot/
│   ├── gemini/
│   └── jetbrains/
├── evaluation/              Grille d'évaluation et résultats chiffrés
├── docs/
│   ├── rapport/             Plan et brouillons du rapport
│   ├── bibliographie/       Références et fiches de lecture
│   └── reunions/            Comptes rendus (encadrant et équipe)
```

## Conventions de travail

**Branches**
- `main` : uniquement ce qui est relu et validé.
- `exp/<outil>-<strategie>` pour chaque essai, par exemple `exp/claude-code-A`, `exp/copilot-B`.
- `docs/<sujet>` pour le rapport, par exemple `docs/intro-llm`.

**Stratégies de prompting** (détails dans `experimentations/protocole.md`)
- **A** : cahier des charges complet donné en une fois
- **B** : prompts progressifs, fonctionnalité par fonctionnalité
- **C** : corrections et itérations à partir des erreurs

**Règles**
- Chaque essai a son **journal** rempli (temps, prompts, interventions humaines).
- Le code généré par l'IA est committé **tel quel** d'abord, puis nos corrections dans des commits séparés : c'est ce qui permet de mesurer notre propre apport.
- Messages de commit clairs : `exp(copilot-A): génération initiale`, `fix(copilot-A): correction manuelle de l'authentification`.
- Aucune clé d'API ni mot de passe dans le dépôt (fichier `.env`, ignoré par Git).
- On passe par une **pull request** relue par un autre membre avant de fusionner dans `main`.

## Répartition (proposition, à ajuster)

| Membre | Outils | Rapport |
|---|---|---|
| Abdullah | Claude Code, JetBrains | Introduction aux LLM, principes et mise en œuvre |
| Salmane | GitHub Copilot | LLM et agents dans le développement |
| Victor | Gemini | Comparaison des outils |
| Équipe | Stratégie A sur tous les outils | Critères d'évaluation, conclusion |

Le suivi du planning se fait dans le diagramme de Gantt partagé.
