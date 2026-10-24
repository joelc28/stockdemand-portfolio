# StockDemand

**Analyse des ventes et prévision de la demande commerciale**  
*Projet personnel — Joël Cédric Ondoum | MBA Data & Intelligence Artificielle, MyDigitalSchool Angers*

## Présentation

StockDemand est un projet d’analyse de transactions commerciales et de prévision hebdomadaire des quantités vendues. Il couvre la préparation des données, la constitution d’un historique par produit, les indicateurs métier et la comparaison de deux approches de prévision.

Le projet a été développé sur un jeu de données public réel : **Online Retail II**, publié par UCI Machine Learning Repository. Les données couvrent décembre 2009 à décembre 2011.

## Vue synthétique

| Périmètre | Résultat |
|---|---:|
| Transactions initiales | 1 067 371 |
| Transactions retenues après nettoyage | 1 041 670 |
| Transactions exclues | 25 701 |
| Références distinctes du catalogue | 4 916 |
| Ventes positives analysées | 20,97 M£ |
| Références sélectionnées pour la prévision | 15 |
| Semaines dans le panel de prévision | 106 |

Le montant présenté correspond aux **ventes positives**, hors retours et annulations, et non aux ventes nettes.

## Travail réalisé

- Importation et contrôle qualité des données commerciales avec Python et Pandas.
- Normalisation des champs, filtrage des lignes invalides et agrégation hebdomadaire.
- Structuration d’un panel produit/semaine et export dans SQLite pour l’analyse SQL.
- Construction de variables historiques : retards de ventes, moyennes mobiles et saisonnalité.
- Entraînement d’un modèle de régression par gradient boosting (Scikit-learn).
- Comparaison avec une prévision de référence basée sur les quatre semaines précédentes.
- Réalisation d’un tableau de bord Streamlit avec KPI, tendances commerciales et prévisions par article.

**Technologies :** Python, Pandas, NumPy, SQL, SQLite, Scikit-learn, Streamlit, Plotly, Pytest.

## Résultats de l’évaluation

Test chronologique : **25 juillet au 5 décembre 2011**, sur **300 observations**.

| Indicateur | Régression (gradient boosting) | Moyenne mobile 4 semaines |
|---|---:|---:|
| MAE (unités) | 406,20 | **303,48** |
| RMSE (unités) | 662,16 | **534,51** |
| WAPE | 71,15 % | **53,16 %** |

![Comparaison des erreurs absolues moyennes](assets/comparaison_mae.png)

**Analyse :** la moyenne mobile de quatre semaines présente une erreur plus faible sur cette période. La comparaison permet de retenir une méthode simple lorsque les résultats expérimentaux ne justifient pas un modèle plus complexe. La sélection finale devrait être confirmée sur un jeu de test indépendant.

## Tableau de bord

Le tableau de bord est organisé en trois sections :

1. **Vue d’ensemble** : indicateurs commerciaux, tendances hebdomadaires, références les plus vendues.
2. **Évaluation des prévisions** : comparaison des erreurs, résultats par référence, séries observées et estimées.
3. **Prévisions par référence** : volumes estimés pour la semaine suivant la fin de l’historique.

*Une capture réelle de l’application sera ajoutée après validation de l’interface sur l’ordinateur de développement.*

## Cadre et limites

- Le jeu de données s’achève en décembre 2011 : les prévisions ne concernent pas 2026.
- Le périmètre modélisé comprend 15 références sélectionnées, et non l’ensemble du catalogue.
- Les informations sur les stocks et fournisseurs sont absentes. Ce projet prévoit des ventes, pas des ruptures de stock.
- Les données et résultats sont issus d’un exercice d’analyse sur données publiques, et non d’une mission en entreprise.

## Accès au projet

Ce dépôt est une **présentation publique**. Le code source de l’application, les données de travail et les modèles sont conservés dans un espace privé. La méthodologie, les résultats et les visuels sont disponibles ici pour consultation.

## Source des données

Chen, D. (2012). *Online Retail II*. UCI Machine Learning Repository. [DOI : 10.24432/C5CG6D](https://doi.org/10.24432/C5CG6D) — licence CC BY 4.0.
