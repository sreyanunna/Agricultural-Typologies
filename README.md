# 🌾 Agricultural Typologies: Mapping Sustainability and Efficiency Across Nations
## —— A Policy-Oriented Analysis to Support FAO’s Strategic Principles

![badge](https://img.shields.io/badge/agriculture-sustainability-green)

**FEEDING 10 BILLION PEOPLE BY 2050 WITHIN PLANETARY LIMITS MAY BE ACHIEVABLE**  
— *University of Oxford, 2018*

**FARMERS VIEW THE PRICE OF INPUTS... AS TOP RISKS TO PROFITS FOR THE NEXT TWO YEARS.**  
— *McKinsey Global Agriculture Survey, 2022*

This repository presents a comprehensive analysis of agricultural efficiency and sustainability across countries. Through data integration, machine learning, and predictive modeling, we address three key questions that relate to the future of sustainable agriculture.

---

## Table of Contents

- [Security](#security)
- [Motivation](#motivation)
- [Research Questions](#research-questions)
- [Data & Processing](#data--processing)
- [Analysis Highlights](#analysis-highlights)
- [Question 1: Efficiency \& Sustainability Index Construction](#question-1-efficiency--sustainability-index-construction)   
- [Question 2: Forecasting Framework for Agricultural Efficiency & Sustainability](#question-2-forecasting-framework-for-agricultural-efficiency--sustainability)  
- [Question 3: Clustering Analysis](#question-3-clustering-analysis)  
- [Install](#install)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

---

## Security

This project uses publicly available datasets from OECD, FAO, and UN sources. No sensitive data is involved; all analyses adhere to source-specific licensing agreements.

---

## Motivation

Feeding a projected global population of 10 billion by 2050 without exceeding planetary boundaries is a formidable challenge. Agricultural systems around the world show wide disparities in efficiency and sustainability. Policymakers, researchers, and stakeholders need actionable insights to transition toward more efficient and environmentally responsible models.

---

## Research Questions

1. **How efficient and sustainable is agricultural production across countries, and what factors drive these differences?**

2. **Can we predict future agricultural efficiency based on historical and environmental indicators?**

3. **Can we classify countries into clusters based on their agricultural efficiency and resource intensity?**

---

## Data & Processing

### Data Overview
**34 Datasets including:**
Nutrient balances, pesticide use, energy use, GHG emissions.
Producer Support Estimate (PSE), Consumer Support Estimate (CSE), General Services Support (GSSE).
OECD-FAO Agricultural Outlook (2024–2033).

**Countries:** 20 countries with high data completeness (2012–2020).

**Preprocessing:**
Removed duplicates, standardized column names.
Handled missing data with median imputation (SimpleImputer).
Normalized features for modeling.

---

## Analysis Highlights

📐 **FORECAST** critical agricultural and environmental indicators for multiple countries using advanced time series models.

📈 **QUANTIFY** future efficiency and sustainability scores using predictive outputs and calibrated metrics.

🌏 **INFORM** national and global stakeholders with future-oriented assessments of agricultural performance and environmental resilience.

---

## Analytical Approach
**Question 1:** SHAP value analysis to identify key drivers of efficiency/sustainability.

**Question 2:** Time series forecasting with XGBoost and LSTM for indicators like GHG emissions.

**Question 3:** Unsupervised clustering (K-Means, DBSCAN) to classify countries into 4 clusters.

---

## Question 1: Efficiency & Sustainability Index Construction

### Objective
We create two composite indices to measure national agricultural performance:

1. **Efficiency Score**  
   Output per unit of environmental input. Combines five normalized “calories per unit input” ratios with weights:  
   - Energy (0.408)  
   - GHG emissions (0.400)  
   - Freshwater use (0.132)  
   - Phosphorus input (0.041)  
   - Nitrogen input (0.020)

2. **Sustainability Score**  
   Output adjusted for environmental pressure. Aggregates six normalized environmental load indicators with weights:  
   - On-farm energy (0.282)  
   - Freshwater withdrawal (0.242)  
   - Pesticide application (0.235)  
   - GHG emissions (0.131)  
   - Phosphorus balance (0.067)  
   - Nitrogen balance (0.044)

These standardized indices enable cross-country comparisons and feed into clustering analysis.

To understand which variables most strongly influence each country’s, we used **SHAP (SHapley Additive exPlanations)** to quantify the contribution of each variable to the model outputs, improving interpretability of the composite scores.

---

### Key Findings

| Insight | Explanation |
|--------|-------------|
| **Crop-dominant systems (higher `crop_ratio`)** | Tend to outperform livestock-heavy systems in both efficiency and sustainability dimensions. |
| **Public investment (GSSE)** | Significantly enhances sustainability outcomes by reducing environmental pressure. |
| **Producer support (PSE)** | Has small positive or mixed influence — not all subsidies lead to better outcomes; policy design is crucial. |
| **Consumer support (CSE)** | More relevant to market behavior than to environmental performance. |

---

### Policy Recommendations

| Recommendation | Purpose |
|----------------|---------|
| 🌱 **Promote crop diversification and crop-intensive systems** | Where agroecologically feasible, to enhance efficiency and sustainability. |
| 🛠️ **Prioritize GSSE funding** | Invest in infrastructure, training, and R&D to reduce resource pressure without sacrificing productivity. |
| 💰 **Redesign PSEP policies** | Introduce **eco-conditionalities** to link subsidies to sustainable practices. |
| 🧾 **Maintain CSE transparency** | Ensure that demand-side incentives don’t indirectly promote unsustainable production. |

## Question 2: Forecasting Framework for Agricultural Efficiency & Sustainability

### Objective

To forecast key agricultural and environmental indicators across countries and derive:

- **Efficiency Score** – How effectively food is produced relative to environmental inputs  
- **Sustainability Score** – The balance between food output and total ecological pressure

---

### Methodology

We collected historical time series data (2012–2020) for variables including:

- Calorie availability  
- Greenhouse gas emissions  
- Energy use  
- Pesticide sales  
- Nitrogen and phosphorus balances  
- Agricultural land area

Using this data, we developed predictive models to forecast these variables from **2021 to 2023**. Three models were tested:

| Model | Description |
|-------|-------------|
| **LSTM (Long Short-Term Memory)** | Captures complex, nonlinear temporal dependencies in multivariate sequences |
| **XGBoost** | Tree-based model using lag features, handles missing data well |
| **Prophet** | Additive model suitable for irregular time intervals, robust to outliers |

---

### Model Selection

After evaluating the models across multiple countries and indicators:

- **LSTM was selected** as the final model due to:
  - Better performance on long-range patterns  
  - Ability to model multi-target, multivariate forecasts  
  - Flexibility in capturing variable interactions

---

### Score Computation

With the LSTM-forecasted values, we computed:

| Score Type | Description |
|------------|-------------|
| **Efficiency Score** | Measures output per unit of environmental input |
| **Sustainability Score** | Reflects the balance between agricultural output and environmental pressure |

These scores were derived using calibrated formulas built on input-output relationships and environmental intensity factors.

---

### Implications

This forward-looking framework enables:

- **Proactive policymaking** under climate and resource constraints  
- **Comparative insights** into national agricultural performance  
- **Support for long-term sustainability planning** with data-driven foresight

## Question 3: Clustering Analysis

### Objective

To explore differences in agricultural efficiency across countries, we used unsupervised learning to group countries by **resource intensity** and **output efficiency**. Key indicators include:

- GHG emissions per agricultural output  
- Water and energy use per unit production  
- Pesticide application per hectare  

### Methodology

- Constructed **resource efficiency metrics**  
- Applied **K-Means clustering** (optimal `k=4`)  
- Used **PCA** for 2D visualization  
- Interpreted clusters for policy recommendations

### Clusters Summary

| Cluster | Description | Key Challenges | FAO Principles | Policy Recommendations |
|--------|-------------|----------------|----------------|--------------------------|
| 0 | **Resource-intensive agriculture** (e.g., China, Brazil, Canada) | High input, low output; environmental stress | P1, P2 | - Introduce precision ag. <br> - Reform subsidies <br> - Promote crop rotation |
| 1 | **High-intensity agriculture** (e.g., South Korea) | High inputs and externalities | P2, P5 | - Promote green alternatives <br> - Audit resource use <br> - Enforce environmental limits |
| 2 | **Technically refined but low-efficiency** (e.g., Japan) | Moderate input, low caloric output | P1, P4 | - Invest in vertical farming <br> - Encourage high-value crops |
| 3 | **High-efficiency sustainable** (e.g., Norway, Switzerland) | Low input, high output | P3, P4, P5 | - Create demo zones <br> - Facilitate knowledge sharing <br> - Lead global governance |

### FAO Principles

| Code | Description |
|------|-------------|
| P1 | Increasing productivity |
| P2 | Conserving natural resources |
| P3 | Improving livelihoods |
| P4 | Enhancing resilience |
| P5 | Fostering responsible governance |

---

## Install

This repository assumes basic familiarity with [Markdown](https://www.markdownguide.org/) and Jupyter Notebooks.

```bash
git clone https://github.com/ese-ada-lovelace-2024/acds3-bigdata-datanauts.git
cd acds3-bigdata-datanauts  
pip install -r requirements.txt  
```

## Project Structure

This project is organized around six Jupyter notebooks, each addressing a key component of our agricultural sustainability and efficiency analysis:

- **Data Preprocessing Notebook**: Handles data cleaning, merging, transformation, and feature engineering across multiple sources (OECD, FAO, UN, etc.), ensuring a consistent and structured dataset for analysis and modeling.

- **OVE Visualization Notebook**: Implements the OVE to visually compare countries' agricultural development situation along multiple dimensions. This notebook visually presents the data clearly and beautifully.

- **Core Analysis Notebooks (4 Total)**: These notebooks are dedicated to the three central research questions of the project:
  1. Composite scoring of efficiency and sustainability
  2. Forecasting future agricultural and environmental indicators
  3. Clustering and segmentation of countries based on performance metrics

Each notebook integrates advanced modeling (e.g., LSTM, SHAP, clustering algorithms), interpretable visualizations, and policy-relevant insights to support data-driven decision-making.

## Contributing
PRs are welcome! Please contact Datanauts Group!

## License

This project is licensed under the [MIT License](LICENSE) © 2025 Datanauts Group.
