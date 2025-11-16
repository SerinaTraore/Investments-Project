Spring 2024

> ⚠️ **Note :** Ceci est une **fraction du projet initial** que j'ai choisi de reproduire et documenter pour partager mon approche et mes analyses. Le projet complet comporte plusieurs autres sections et analyses qui ne sont pas incluses ici.

## Contexte du projet

Ce projet a été réalisé dans le cadre du cours **Investments (Spring 2024)**. L'objectif principal était de construire des portefeuilles optimaux combinant plusieurs signaux de marché, en particulier :  

- **Beta**  
- **Idiosyncratic Volatility (IV)**  
- **Momentum (MoM)**  

Ensuite, j'ai dû analyser la performance des stratégies optimales, en utilisant des facteurs de risque standards de Ken French, puis analyser l'exposition aux risques sectoriels et comparer deux approches pour construire des portefeuilles industry-neutral.

## Données

- **Période** : Janvier 1964 – Décembre 2023  
- **Sources** : CRSP pour les actions cotées sur NYSE et AMEX, CRSP market return value-weighted, 1-month T-bill comme taux sans risque.  
- **Prétraitement** : Rolling 5-year regressions, winsorisation aux 5% et 95%.

## Stratégies implémentées dans cette fraction

### 1. Betting against Beta (BaB)
- Calcul des betas mensuels sur rolling 5 ans.  
- Construction de portefeuilles déciles basés sur le beta.  
- Construction du facteur BAB selon Frazzini & Pedersen (2014).  

### 2. Idiosyncratic Volatility (IV)
- Estimation de la volatilité idiosyncratique sur rolling 5 ans.  
- Portefeuilles déciles et construction d’un facteur IV long-short.

> ⚠️ La **stratégie Momentum (MoM)** a été **exclue** dans cette fraction car la construction naïve réalisée affichait des performances trop faibles et je manquais de temps pour l’améliorer.

> ⚠️ Une **section “Industry-neutral strategy”**, potentiellement la plus intéressante du projet,n'est pas encore incluse dans cette fraction. Cette section consiste à :  
> - Construire séparément les stratégies BaB, IV et MoM pour chacune des 12 industries afin d’obtenir un portefeuille industry-neutral.  
> - Combiner ensuite ces 12 stratégies via des pondérations égales pour générer un **STRAT industry-neutral**.  
> - Analyser la performance du portefeuille neutralisé en régressant sur les 17 facteurs de risque (12 industries + 5 Fama-French), et discuter de sa consistance avec le CAPM, l’APT et les marchés efficients.  

> ⚠️ Les sections **Optimal Fund Portfolio** et **Performance Analysis** ne sont pas encore incluses dans cette version

## Comment utiliser ce notebook

1. Cloner le dépôt :  
```bash
git clone [URL_DU_DEPOT]
