# OpenIntro Statistics (4th Ed) — Chapter 1 Summary  
## Introduction to Data / Introduction aux données

> **Source**: Diez, D. M., Barr, C. D., & Çetinkaya-Rundel, M. (2019). *OpenIntro Statistics* (4th ed.)  
> **Notebook**: `notebooks/01_data_understanding.ipynb`

---

## Core Concepts / Concepts clés 

### 1.1 Basic Terminology / Terminologie de base 
| English | Français | Definition |
|---------|----------|------|
| Observation| Observation / Individu | A row in the dataset representing a single entity (e.g., one passenger)/Donnée individuelle représentant une entité unique (ex: un passager) | 
| Variable| Variable |A column representing a characteristic (e.g., age, sex)/ Colonne représentant une caractéristique (ex: âge, sexe) |
| Data Matrix| Matrice de données|Table structure: rows = observations, columns = variables / Structure tabulaire : lignes = observations, colonnes = variables | 

---

### 1.2 Types of Variables / Types de variables

#### Categorical Variables / Variables catégorielles

| Subtype | English | Français | Titanic Example |
|---------|---------|----------|-----------------|
| Nominal | Nominal | Nominale |`sex` (male/female), `embarked` (C/Q/S) |
| Ordinal | Ordinal | Ordinale |`pclass` (1st > 2nd > 3rd), `class` |

> **Note pratique / Practical Note**:  
> Variables nominales : pas d'ordre intrinsèque (sexe)  
> Variables ordinales : ordre logique significatif (classe de cabine)  
> Nominal variables: no inherent order (sex)  
> Ordinal variables: meaningful logical order (cabin class)  

#### Numerical Variables / Variables numériques

| Subtype | English | Français | Titanic Example |
|---------|---------|----------|-----------------|
| Discrete | Discrete | Discrète | `sibsp` (0,1,2...), `parch` |
| Continuous | Continuous | Continue | `age` (22.0, 38.5...), `fare` |

> **Critical Insight / Insight critique**:  
> EN: `age` is mathematically discrete (years) but **treated as continuous** in practice due to dense values (88 unique) + decimals  
> FR: `age` est mathématiquement discret (années) mais **traité comme continu** car valeurs denses (88 uniques) + décimales  

---

### 1.3 Explanatory vs. Response Variables / Variables explicatives vs réponse

| Role | English | Français | Titanic Example |
|------|---------|----------|-----------------|
| Response | Response Variable | Variable réponse | `survived` (0/1) — target to predict |
| Explanatory | Explanatory Variable | Variable explicative | `pclass`, `sex`, `age` — predictors |

> **Golden Rule / Règle d'or**:  
> EN: Always identify Y (response) before X (explanatory) — confusion leads to wrong analysis  
> FR: Toujours identifier Y (réponse) avant X (explicative) — confusion mène à une mauvaise analyse  
> ZH: 建模前必须明确 Y（响应）和 X（解释）—— 混淆角色导致错误分析

---

### 1.4 Types of Studies / Types d'études 

| Type | English | Français | Causal Inference? |
|------|---------|----------|-------------------|
| Observational| Observational Study | Étude observationnelle | Association only |
| Experiment | Experiment | Expérience contrôlée | Causation possible |

> **Critical Limitation / Limitation critique / 关键局限**:  
> EN: Observational studies show **association ≠ causation** (e.g., "1st class → survival" may reflect cabin location, not ticket price)  
> FR: Les études observationnelles montrent **association ≠ causalité** (ex: "1ère classe → survie" peut refléter la localisation de la cabine, non le prix du billet)  
> ZH: 观察性研究只能发现**关联≠因果**（例："头等舱→生还"可能反映舱位位置，而非票价）

---

### 1.5 Common Biases / Biais courants / 常见偏差

| Bias | English | Français | 中文 | Titanic Example |
|------|---------|----------|------|-----------------|
| Survivorship | Survivorship Bias | Biais de survivant | 幸存者偏差 | Only boarded passengers observed (no cancellations) |

> **Why it matters / Pourquoi c'est important / 为何重要**:  
> EN: Overestimates survival probability; limits generalizability  
> FR: Surestime la probabilité de survie ; limite la généralisation  
> ZH: 高估生还概率；限制结论普适性

---

## Key Principles / Principes clés / 核心原则

| Principle | English | Français | 中文 |
|-----------|---------|----------|------|
| 1 | "Variable type determines analysis method" | "Le type de variable détermine la méthode d'analyse" | "变量类型决定分析方法" |
| 2 | "Association ≠ Causation in observational studies" | "Association ≠ Causalité dans les études observationnelles" | "观察性研究中关联≠因果" |
| 3 | "Always acknowledge data limitations" | "Toujours reconnaître les limites des données" | "始终承认数据局限性" |

---

## Common Pitfalls / Pièges courants / 避坑指南

| Mistake | English | Français | 中文 | Correct Approach |
|---------|---------|----------|------|------------------|
| **Mean for categories** | Calculating mean of "male/female" | Calculer la moyenne de "homme/femme" | 对性别计算平均值 | → Use **frequency/proportion** (65% male) |
| **Ordinal as nominal** | Treating cabin class as unordered | Traiter la classe comme non ordonnée | 将舱位当作无序处理 | → Preserve order: 1st > 2nd > 3rd |
| **Causation claim** | "Buying 1st class causes survival" | "Acheter 1ère classe cause la survie" | "买头等舱导致生还" | → State as **association**: "1st class passengers had higher survival rates" |

---

## Trilingual Glossary / Glossaire trilingue / 三语术语表

| Concept | English | Français | 中文 |
|---------|---------|----------|------|
| Categorical | Categorical variable | Variable catégorielle | 分类型变量 |
| Numerical | Numerical variable | Variable numérique | 数值型变量 |
| Discrete | Discrete | Discrète | 离散型 |
| Continuous | Continuous | Continue | 连续型 |
| Bias | Bias | Biais | 偏差 |
| Confounding | Confounding variable | Variable de confusion | 混杂变量 |
| Association | Association | Association | 关联 |
| Causation | Causation | Causalité | 因果 |


## ✅ Chapter 1 Summary: Key Concepts You Must Understand

### 🔑 Core Principles (OpenIntro Ch 1)
| Concept | English | Français | 中文 | Why It Matters |
|---------|---------|----------|------|----------------|
| Observation | Row = single entity | Ligne = entité unique | 行 = 单个实体 | Foundation of data structure |
| Variable | Column = characteristic | Colonne = caractéristique | 列 = 特征 | Determines analysis method |
| Categorical | Nominal/Ordinal/Binary | Nominale/Ordinale/Binaire | 名义/有序/二元 | Use frequency tables, bar plots |
| Numerical | Discrete/Continuous | Discrète/Continue | 离散/连续 | Use mean/median, histograms |
| Response (Y) | Target to predict | Cible à prédire | 预测目标 | Always identify FIRST |
| Explanatory (X) | Predictors | Prédicteurs | 预测变量 | Used to explain Y |
| Observational Study | No intervention | Pas d'intervention | 无干预 | → **Association ≠ Causation** |
| Confounding | Hidden variable affects X & Y | Variable cachée | 混杂变量 | Explains spurious associations |
| Bias | Systematic error | Erreur systématique | 偏差 | Limits generalizability |

### ⚠️ Critical Mistakes to Avoid
1. ❌ Using mean for categorical variables → meaningless  
   ✅ Use **frequency/proportion** instead
2. ❌ Claiming causation from observational data → unethical  
   ✅ State findings as **association** only
3. ❌ Ignoring missing data → biased results  
   ✅ Always report missingness % and handling strategy
4. ❌ Confusing observation (row) vs variable (column) → analysis errors  
   ✅ Visualize data matrix structure first

### 🔗 Next Steps (Chapter 2 Preview)
- Chapter 2: Summarizing Data → Mean/Median/IQR for numerical variables
- Chapter 2: Box plots for outlier detection
- Chapter 3: Conditional probability `P(survive | female)`









