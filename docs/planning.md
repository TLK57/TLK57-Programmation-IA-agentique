# Planning du projet

Diagramme de Gantt du projet, d'octobre 2026 à fin mars 2027. Les dates des soutenances sont à confirmer avec l'encadrant.

```mermaid
gantt
    title Programmation IA agentique · planning 2026-2027
    dateFormat YYYY-MM-DD
    axisFormat %d/%m
    todayMarker stroke-width:3px,stroke:#e0442f

    section Organisation
    Réunion de lancement et répartition (Équipe)          :org1, 2026-10-26, 2026-11-01
    Dépôt GitHub et outils d'équipe (Victor)              :org2, 2026-10-26, 2026-11-01
    Choix de l'application de référence (Équipe)          :org3, 2026-10-26, 2026-11-08

    section Prise en main des outils
    Claude Code (Abdullah)                                :out1, 2026-11-02, 2026-11-22
    GitHub Copilot mode agent (Salmane)                   :out2, 2026-11-02, 2026-11-22
    Gemini CLI et Code Assist (Victor)                    :out3, 2026-11-02, 2026-11-22
    JetBrains Junie et AI Assistant (Abdullah)            :out4, 2026-11-09, 2026-11-29

    section Rapport bibliographique
    Introduction aux LLM (Abdullah)                       :bib1, 2026-11-02, 2026-12-06
    LLM et agents en développement (Salmane)              :bib2, 2026-11-02, 2026-12-06
    Comparaison des outils (Victor)                       :bib3, 2026-11-16, 2026-12-13
    Critères d'évaluation (Équipe)                        :bib4, 2026-11-23, 2026-12-20

    section Préparation de l'expérimentation
    Cahier des charges de l'appli de référence (Salmane)  :pre1, 2026-11-09, 2026-11-29
    Mesures de référence de l'appli manuelle (Victor)     :pre2, 2026-11-23, 2026-12-13
    Grille d'évaluation et protocole finalisés (Équipe)   :pre3, 2026-12-07, 2026-12-20

    section Expérimentation 1 · stratégie A
    Stratégie A sur les 4 outils (Équipe)                 :exA, 2027-01-04, 2027-01-24
    Analyse des premiers résultats (Abdullah)             :anA, 2027-01-18, 2027-01-31
    Mail à l'encadrant (Salmane)                          :milestone, mail1, 2027-01-25, 0d
    Préparer la soutenance 1 (Équipe)                     :sp1, 2027-01-18, 2027-01-31
    Soutenance 1 à confirmer                              :milestone, crit, sou1, 2027-02-01, 0d

    section Expérimentation 2 · stratégies B et C
    Stratégie B prompts progressifs (Salmane)             :exB, 2027-02-08, 2027-02-28
    Stratégie C corrections et itérations (Victor)        :exC, 2027-02-08, 2027-02-28
    Mesures qualité et sécurité (Abdullah)                :mes, 2027-02-22, 2027-03-14

    section Finalisation
    Rédaction du rapport final et annexes (Équipe)        :red, 2027-03-01, 2027-03-21
    Relecture croisée (Équipe)                            :rel, 2027-03-15, 2027-03-25
    Préparer la soutenance finale (Équipe)                :sp2, 2027-03-15, 2027-03-28
    Soutenance finale à confirmer                         :milestone, crit, sou2, 2027-03-29, 0d
```

## Mettre à jour l'avancement

Dans le bloc ci-dessus, ajoutez un mot-clé juste après les deux-points de la tâche :

| Statut | Exemple |
|---|---|
| En cours | `Claude Code (Abdullah) :active, out1, 2026-11-02, 2026-11-22` |
| Terminée | `Claude Code (Abdullah) :done, out1, 2026-11-02, 2026-11-22` |
| Prioritaire / urgente | `... :crit, out1, ...` (combinable : `:crit, active, out1, ...`) |

Pour décaler une tâche, changez simplement ses dates. Le diagramme se met à jour dès que le fichier est enregistré sur GitHub.

## Suivi au quotidien

Le planning interactif partagé (statuts cliquables, filtre par personne, tâches en retard) reste disponible dans l'artefact Claude « Gantt IA Agentique », partagé par Abdullah. Ce fichier en est la version de référence dans le dépôt.
