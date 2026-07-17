# Reporting DSI — Suivi de la performance du support IT

Projet de reporting BI simulant le pilotage de la performance d'un service support IT (DSI), à partir de 100 000 tickets. Réalisé en Excel (Power Query, formules) et Power BI (DAX), avec identification d'axes d'amélioration concrets à partir des données.

## Contexte et problème

Un service support IT traite chaque jour un grand nombre de tickets : demandes d'accès, pannes, questions de facturation, problèmes de sécurité... Mais sans outil de pilotage centralisé, personne ne sait vraiment, en un coup d'œil, si le support fonctionne bien.

Les questions restent sans réponse claire : combien de temps prend-on en moyenne pour résoudre un ticket ? Les clients sont-ils satisfaits ? Certains types de problèmes posent-ils plus de difficultés que d'autres ? Le plan premium payé par certains clients leur apporte-t-il vraiment un traitement plus rapide ?

Sans visibilité consolidée sur ces indicateurs (temps de résolution, taux de réouverture, satisfaction client, charge par catégorie), impossible d'identifier rapidement les points de friction ni de prioriser les actions d'amélioration.

## Solution

Ce projet transforme 100 000 tickets de support bruts en un système de reporting qui centralise les données, calcule automatiquement les indicateurs clés (KPI), et les visualise dans un dashboard interactif — d'abord en Excel, puis dans un dashboard Power BI pour l'exploration visuelle.

L'objectif n'était pas seulement de calculer des chiffres, mais d'aller jusqu'au bout de la démarche : identifier de vrais problèmes dans les données et proposer des actions concrètes pour les résoudre, au-delà du reporting brut.

## KPI suivis

- MTTR (temps moyen de résolution), global et par priorité / plan SLA
- Taux de résolution et taux de réouverture
- CSAT moyen et taux de réponse à l'enquête de satisfaction
- Répartition du sentiment client
- Tendance mensuelle du volume de tickets

## Résultats et axes d'amélioration identifiés

1. **Écart de satisfaction selon la nature du problème** — Les tickets liés à la sécurité, à l'accès aux comptes, à la performance et à la facturation obtiennent une note moyenne de 2,8/5, contre 3,7/5 pour les simples demandes d'aide ou de fonctionnalités — alors que le temps de résolution est identique entre ces catégories. La lenteur n'explique donc pas l'insatisfaction : c'est plutôt la qualité de communication sur ces sujets sensibles qui doit être investiguée.

2. **Le plan SLA Platinum ne raccourcit pas le délai de résolution** — Les clients qui paient pour un plan de support "Platinum" attendent normalement une résolution plus rapide. Dans les faits, l'écart de MTTR avec le plan Standard est de moins de 1% (27,6h contre 27,8h) — quasiment inexistant. La promesse commerciale associée au plan premium n'est pas tenue dans les faits.

3. **Le sentiment client est plus négatif que ne le laisse penser le CSAT moyen** — Le score de satisfaction moyen (3,2/5) paraît correct à première vue, mais 42,5% des tickets sont associés à un sentiment négatif ou très négatif, contre seulement 24,9% en positif. La moyenne masque une vraie polarisation qu'il faut creuser.

4. **Près de 30% des clients ne répondent pas à l'enquête de satisfaction** — Le taux de réponse CSAT n'est que de 70% en moyenne, stable sur tous les canaux. Un tiers du volume de tickets échappe donc totalement au pilotage de la satisfaction, ce qui limite la fiabilité du suivi.

## Structure du projet

- `Reporting_DSI.xlsx` — Classeur Excel (données, calendrier, dashboard KPI, recommandations)
- `Reporting_DSI.pbix` — Fichier Power BI (modèle, mesures DAX, visuels)
- `README.md`

### Classeur Excel — 4 onglets
- **KPI_Dashboard** : indicateurs calculés en formules (SUMIFS, AVERAGEIFS, COUNTIFS)
- **Recommandations** : axes d'amélioration détaillés (constat + action proposée)
- **Donnees** : 100 000 tickets nettoyés (traitement des valeurs manquantes)
- **Calendrier** : table de dimension temporelle (2022-2025)

### Power BI
- Modèle relationnel entre la table de faits (tickets) et la dimension calendrier
- 11 mesures DAX (MTTR, CSAT, taux de résolution, sentiment, écarts par plan SLA...)
- Dashboard interactif avec cartes KPI, graphiques par priorité / type de problème / plan SLA, tendance mensuelle
- Page de synthèse des recommandations

## Outils utilisés

Excel (Power Query, formules avancées) · Power BI (modèle de données, DAX) · Python (nettoyage et exploration des données, Pandas)

## Note sur les données

Le jeu de données utilisé est un dataset de tickets de support IT synthétique (structure et volumétrie réalistes), utilisé ici à des fins de démonstration méthodologique.
