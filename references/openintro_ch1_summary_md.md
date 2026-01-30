# OpenIntro Statistics (4th Ed) — Chapter 1 Summary  
## Introduction to Data / Introduction aux données / 数据基础

> **Source**: Diez, D. M., Barr, C. D., & Çetinkaya-Rundel, M. (2019). *OpenIntro Statistics* (4th ed.)  
> **Notebook**: `notebooks/01_data_understanding.ipynb`

---

## Core Concepts / Concepts clés / 核心概念

### 1.1 Basic Terminology / Terminologie de base / 基础术语

| English | Français | 中文 | Definition |
|---------|----------|------|------------|
| **Observation** | Observation / Individu | 观测值/样本 | A row in the dataset representing a single entity (e.g., one passenger) | Donnée individuelle représentant une entité unique (ex: un passager) | 数据集的**每一行**，代表一个独立实体（如：一名乘客） |
| **Variable** | Variable | 变量 | A column representing a characteristic (e.g., age, sex) | Colonne représentant une caractéristique (ex: âge, sexe) | 数据集的**每一列**，代表一个特征（如：年龄、性别） |
| **Data Matrix** | Matrice de données | 数据矩阵 | Table structure: rows = observations, columns = variables | Structure tabulaire : lignes = observations, colonnes = variables | 行=观测值，列=变量的表格结构 |

---

### 1.2 Types of Variables / Types de variables / 变量类型

#### Categorical Variables / Variables catégorielles / 分类型变量

| Subtype | English | Français | 中文 | Titanic Example |
|---------|---------|----------|------|-----------------|
| **Nominal** | Nominal | Nominale | 名义型 | `sex` (male/female), `embarked` (C/Q/S) |
| **Ordinal** | Ordinal | Ordinale | 有序型 | `pclass` (1st > 2nd > 3rd), `class` |

> **Note pratique / Practical Note / 实践说明**:  
> Variables nominales : pas d'ordre intrinsèque (sexe)  
> Variables ordinales : ordre logique significatif (classe de cabine)  
> Nominal variables: no inherent order (sex)  
> Ordinal variables: meaningful logical order (cabin class)  
> 名义型：无内在顺序（性别）  
> 有序型：有逻辑顺序（舱位等级 1>2>3）

#### Numerical Variables / Variables numériques / 数值型变量

| Subtype | English | Français | 中文 | Titanic Example |
|---------|---------|----------|------|-----------------|
| **Discrete** | Discrete | Discrète | 离散型 | `sibsp` (0,1,2...), `parch` |
| **Continuous** | Continuous | Continue | 连续型 | `age` (22.0, 38.5...), `fare` |

> **Critical Insight / Insight critique / 关键洞察**:  
> EN: `age` is mathematically discrete (years) but **treated as continuous** in practice due to dense values (88 unique) + decimals  
> FR: `age` est mathématiquement discret (années) mais **traité comme continu** car valeurs denses (88 uniques) + décimales  
> ZH: `age` 数学上是离散的（年为单位），但因取值密集（88个唯一值）+ 含小数 → **实践中视为连续型**

---

### 1.3 Explanatory vs. Response Variables / Variables explicatives vs réponse / 解释变量 vs 响应变量

| Role | English | Français | 中文 | Titanic Example |
|------|---------|----------|------|-----------------|
| **Response** | Response Variable | Variable réponse | 响应变量 | `survived` (0/1) — target to predict |
| **Explanatory** | Explanatory Variable | Variable explicative | 解释变量 | `pclass`, `sex`, `age` — predictors |

> **Golden Rule / Règle d'or / 黄金法则**:  
> EN: Always identify Y (response) before X (explanatory) — confusion leads to wrong analysis  
> FR: Toujours identifier Y (réponse) avant X (explicative) — confusion mène à une mauvaise analyse  
> ZH: 建模前必须明确 Y（响应）和 X（解释）—— 混淆角色导致错误分析

---

### 1.4 Types of Studies / Types d'études / 研究类型

| Type | English | Français | 中文 | Causal Inference? |
|------|---------|----------|------|-------------------|
| **Observational** | Observational Study | Étude observationnelle | 观察性研究 | ❌ Association only |
| **Experiment** | Experiment | Expérience contrôlée | 实验 | ✅ Causation possible |

> **Critical Limitation / Limitation critique / 关键局限**:  
> EN: Observational studies show **association ≠ causation** (e.g., "1st class → survival" may reflect cabin location, not ticket price)  
> FR: Les études observationnelles montrent **association ≠ causalité** (ex: "1ère classe → survie" peut refléter la localisation de la cabine, non le prix du billet)  
> ZH: 观察性研究只能发现**关联≠因果**（例："头等舱→生还"可能反映舱位位置，而非票价）

---

### 1.5 Common Biases / Biais courants / 常见偏差

| Bias | English | Français | 中文 | Titanic Example |
|------|---------|----------|------|-----------------|
| **Survivorship** | Survivorship Bias | Biais de survivant | 幸存者偏差 | Only boarded passengers observed (no cancellations) |

> **Why it matters / Pourquoi c'est important / 为何重要**:  
> EN: Overestimates survival probability; limits generalizability  
> FR: Surestime la probabilité de survie ; limite la généralisation  
> ZH: 高估生还概率；限制结论普适性

---

## Key Principles / Principes clés / 核心原则

| Principle | English | Français | 中文 |
|-----------|---------|----------|------|
| **1** | "Variable type determines analysis method" | "Le type de variable détermine la méthode d'analyse" | "变量类型决定分析方法" |
| **2** | "Association ≠ Causation in observational studies" | "Association ≠ Causalité dans les études observationnelles" | "观察性研究中关联≠因果" |
| **3** | "Always acknowledge data limitations" | "Toujours reconnaître les limites des données" | "始终承认数据局限性" |

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