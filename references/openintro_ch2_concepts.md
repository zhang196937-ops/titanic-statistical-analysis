## OpenIntro Statistics (4th Ed) - Chapter 2 Core Concepts##
Summarizing Data / Résumé des données / 数据汇总

---
> **Source**: Diez, D. M., Barr, C. D., & Çetinkaya-Rundel, M. (2019). *OpenIntro Statistics* (4th ed.), Chapter 2  
> **Dataset**: Titanic passenger records (891 passangers)  
> **Golden Rule**: *"The shape of a distribution determines which summaries are appropriate"*  
> **Notebook**: [02_summarizing_data.ipynb](../notebooks/02_summarizing_data.ipynb)
---
## Concept 1: Measures of Center（中心趋势度量）

|English|French|Chinese|
|-----|----|----|
|**Mean(Arithmetic Average)**|Moyenne arithmétique| 算术平均数|
|**Median**|Médiane|中位数|
|**Mode**|Mode|众数|

### Formulas & Rules（公式与规则）

#### Mean（均值）
$$\bar{x} = \frac{\sum_{i=1}^{n} x_i}{n}$$

- **适用条件**: 对称分布（symmetric）或轻度偏斜
- **敏感性**: **受异常值影响极大**（outlier-sensitive）
- **OpenIntro Principle**: *"The mean is pulled in the direction of skewness"*（均值被拉向偏斜方向）

#### Median（中位数）
- 将数据排序后位于**中间位置**的值
- 奇数个观测值: $x_{(n+1)/2}$
- 偶数个观测值: $\frac{x_{(n/2)} + x_{(n/2+1)}}{2}$
- **适用条件**: 偏斜分布（skewed）或含异常值
- **稳健性**: **对异常值不敏感**（robust to outliers）

#### Mode（众数）
- 出现频率**最高**的值
- 可能有多个众数（bimodal/multimodal）
- **适用条件**: 分类型变量或识别多峰分布

### Titanic Examples（泰坦尼克号实例）

| Variable | Mean | Median | Mode | Interpretation（解读） |
|----------|------|--------|------|------------------------|
| **`age`** | 29.7 years | 28.0 years | 24.0 years | 轻度右偏（mean > median）→ 中位数更能代表"典型年龄" |
| **`fare`** | £32.20 | £14.45 | £8.05 | 严重右偏（mean ≫ median）→ **中位数是更稳健的摘要** |
| **`survived`** | 0.38（比例） | — | 0（死亡） | 二元变量：均值 = 生还比例（38.4%） |
| **`pclass`** | 2.3 | 3.0 | 3（三等舱） | 有序分类：中位数=3 表示"典型乘客是三等舱" |

> **Critical Insight**:  
> EN: For `fare`, mean (£32.20) is **misleading** — pulled up by extreme outlier (£512 first-class ticket). Median (£14.45) better represents "typical passenger fare".  
> FR: Pour `fare`, la moyenne (£32.20) est **trompeuse** — tirée vers le haut par une valeur aberrante (£512). La médiane (£14.45) représente mieux le "tarif typique".  
> ZH: `fare` 的均值 (£32.20) **具有误导性** — 被极端异常值 (£512 头等舱票价) 拉高。中位数 (£14.45) 更能代表"典型票价"。

### Common Mistakes（常见错误）
| Mistake | Why Wrong | Correct Approach |
|---------|-----------|------------------|
| Reporting mean for heavily skewed `fare` | Mean inflated by outliers → misrepresents "typical" value | → Report **median (£14.45) + IQR (£7.91–£31.00)** |
| Using median for symmetric distribution | Loses efficiency (mean has smaller standard error) | → Use **mean** for symmetric distributions |
| Ignoring bimodality | Hides subgroups (e.g., two salary tiers) | → Use **histogram** to detect multiple modes |

## Concept 2: Measures of Spread（离散程度度量）

### Definition（定义）
| English | Français | 中文 | Formula |
|---------|----------|------|---------|
| **Range** | Étendue | 极差 | $\text{max} - \text{min}$ |
| **Variance** | Variance | 方差 | $s^2 = \frac{\sum (x_i - \bar{x})^2}{n-1}$ |
| **Standard Deviation** | Écart-type | 标准差 | $s = \sqrt{s^2}$ |
| **IQR (Interquartile Range)** | Écart interquartile | 四分位距 | $Q_3 - Q_1$ |

### Formulas & Rules（公式与规则）

#### Range（极差）
- Max(最大值) - Min(最小值)
- **缺点**: 仅依赖两个极端值，**对异常值极度敏感**

#### Variance & Standard Deviation（方差与标准差）
- **Variance**: 平均平方偏差（单位：原始单位²）
- **Standard Deviation**: 标准差（单位：与原始数据相同）
- **适用条件**: 对称分布（与均值配套使用）
- **敏感性**: **受异常值影响**（平方放大极端值影响）

#### IQR（四分位距）
- $Q_1$ = 25th percentile（第25百分位数）
- $Q_3$ = 75th percentile（第75百分位数）
- **IQR = $Q_3 - Q_1$ (outlier value)**
- **适用条件**: 偏斜分布或含异常值（与中位数配套使用）
- **稳健性**: **对异常值不敏感**（仅依赖中间50%数据）

### Titanic Examples（泰坦尼克号实例）

| Variable | Range | Std Dev | IQR | Interpretation（解读） |
|----------|-------|---------|-----|------------------------|
| **`age`** | 0.42 – 80.0 yrs<br>(79.6 yrs) | 14.5 years | 17.875 years | 轻度右偏 → **IQR 更稳健**（不受 80 岁老人影响） |
| **`fare`** | £0 – £512.33<br>(£512.33) | £49.69 | £23.09 | 严重右偏 + 极端异常值 → **Std Dev 失真**（£49.69 过大），**IQR 更可靠** |
| **`sibsp`** | 0 – 8 | 1.1 | 1.0 | 离散计数 → 两者均可，但 **IQR 更易解释**（"中间50%乘客有0-1个兄弟姐妹"） |

> **Critical Insight**:  
> EN: For `fare`, std dev (£49.69) is **inflated by outliers** → suggests huge spread that doesn't reflect typical passengers. IQR (£23.09) better captures spread of middle 50%.  
> FR: Pour `fare`, l'écart-type (£49.69) est **gonflé par les valeurs aberrantes** → suggère une dispersion énorme non représentative. L'IQR (£23.09) capture mieux la dispersion des 50% centraux.  
> ZH: `fare` 的标准差 (£49.69) **被异常值夸大** → 暗示的离散度远超典型乘客。IQR (£23.09) 更好地捕捉中间50%的离散度。

### Common Mistakes（常见错误）
| Mistake | Why Wrong | Correct Approach |
|---------|-----------|------------------|
| Using std dev for skewed `fare` | Inflated by outliers → misleading spread measure | → Use **IQR** for skewed distributions |
| Reporting only range | Ignores distribution shape (e.g., bimodal) | → Always pair with **histogram/box plot** |
| Using variance instead of std dev | Units are squared → hard to interpret | → Report **std dev** (same units as data) |

---
## Concept 3: Distribution Shape（分布形态）

### 📖 Definition（定义）
| Shape | English | Français | 中文 | Visual Cue | Skewness Coefficient |
|-------|---------|----------|------|------------|----------------------|
| **Symmetric** | Symmetric | Symétrique | 对称 | Bell-shaped, mean ≈ median | ≈ 0 |
| **Right-skewed** | Right-skewed (positive skew) | Asymétrie positive | 右偏（正偏） | Long tail right, mean > median | > +0.5 |
| **Left-skewed** | Left-skewed (negative skew) | Asymétrie négative | 左偏（负偏） | Long tail left, mean < median | < -0.5 |

### Rules（规则）
- **Pearson's Skewness Coefficient**: $\frac{3(\bar{x} - \text{median})}{s}$
- **OpenIntro Rule of Thumb**:
  - $|\text{skewness}| < 0.5$ → Approximately symmetric
  - $0.5 \leq |\text{skewness}| < 1$ → Moderately skewed
  - $|\text{skewness}| \geq 1$ → Highly skewed

### Titanic Examples（泰坦尼克号实例）

| Variable | Skewness | Shape | Mean vs Median | Why? |
|----------|----------|-------|----------------|------|
| **`age`** | +0.42 | Slightly right-skewed | 29.7 > 28.0 | Few elderly passengers (max=80) pull tail right |
| **`fare`** | +4.37 | **Highly right-skewed** | 32.20 ≫ 14.45 | Extreme outliers (£512 ticket) create long right tail |
| **`sibsp`** | +1.61 | Moderately right-skewed | 0.52 > 0.0 | Most passengers travel alone (sibsp=0), few have many siblings |

> **Visualization Guide**:  
> - **Histogram**: Shows overall shape + modality  
> - **Box Plot**: Reveals skewness via whisker length + outlier positions  
> - **Q-Q Plot**: Formal test for normality (beyond Ch 2 scope)

### Common Mistakes（常见错误）
| Mistake | Why Wrong | Correct Approach |
|---------|-----------|------------------|
| Assuming normality without checking | Many real-world variables are skewed | → Always **visualize first** (histogram/box plot) |
| Using mean/std dev for highly skewed data | Violates assumptions of many statistical tests | → Transform data (log) or use **median/IQR** |

---
## Concept 4: Outlier Detection（异常值检测）

### Definition（定义）
An **outlier** is an observation that appears extreme relative to the rest of the data.

### IQR Method（IQR 方法 — OpenIntro Ch 2.1.5）
1. Calculate $Q_1$ (25th percentile) and $Q_3$ (75th percentile)
2. Compute IQR = $Q_3 - Q_1$
3. Define bounds:
   - Lower bound = $Q_1 - 1.5 \times \text{IQR}$
   - Upper bound = $Q_3 + 1.5 \times \text{IQR}$
4. **Outlier**: Any value < lower bound OR > upper bound

> **Why 1.5?**  
> EN: Empirical rule — captures extreme values while minimizing false positives  
> FR: Règle empirique — capture les valeurs extrêmes tout en minimisant les faux positifs  
> ZH: 经验法则 — 捕捉极端值同时最小化误报

### Titanic Examples（泰坦尼克号实例）

#### **`fare` Outlier Detection** 
```python
Q1 = df['fare'].quantile(0.25)  # £7.91
Q3 = df['fare'].quantile(0.75)  # £31.00
IQR = Q3 - Q1                    # £23.09

lower_bound = Q1 - 1.5 * IQR     # -£26.73 (no lower outliers)
upper_bound = Q3 + 1.5 * IQR     # £65.64

outliers = df[df['fare'] > upper_bound]  # 78 passengers
max_fare = outliers['fare'].max()        # £512.33 (first-class ticket)
```
| Statistic | Value | Interpretation |
|-----------|----------|---------|
|Q1|£7.91|25% paid ≤ £7.91|
|Q3|£31.00|75% paid ≤ £31.00|
|IQR|£23.09|Middle 50% paid between £7.91–£31.00|
|Upper bound|£65.64|78 passengers (8.8%) paid > £65.64 → outliers|
|Max fare|£512.33|Extreme outlier (first-class luxury suite)|

>**Business Insight:**  
>EN: Outliers are not errors — they reflect socioeconomic reality (wealthy first-class passengers). Never remove without investigation!  
>FR: Les valeurs aberrantes ne sont pas des erreurs — elles reflètent la réalité socio-économique. Ne jamais supprimer sans enquête !  
>ZH: 异常值不是错误 — 它们反映社会经济现实（富裕的头等舱乘客）。切勿未经调查直接删除！  

### **age Outlier Detection** 
```python
Q1 = df['age'].quantile(0.25)  # 20.125 years
Q3 = df['age'].quantile(0.75)  # 38.0 years
IQR = Q3 - Q1                  # 17.875 years

lower_bound = Q1 - 1.5 * IQR   # -6.69 years → no lower outliers (age ≥ 0)
upper_bound = Q3 + 1.5 * IQR   # 64.81 years

outliers = df[df['age'] > upper_bound]  # 21 passengers (2.4%)
max_age = outliers['age'].max()         # 80.0 years
```   
**Conclusion: age has mild outliers (elderly passengers) but no extreme outliers like fare.**
### Common Mistakes（常见错误）  
|Mistake|Why Wrong|Correct Approach|
|----|-----|-----|
|Automatically removing outliers|Loses important signal (e.g., fraud detection)|Investigate cause first (data error vs real phenomenon)|
|Using 3×IQR without justification|Too strict for many real-world datasets|Start with 1.5×IQR (OpenIntro standard)|
|Ignoring context|Outliers may be valid (e.g., CEO salary)|Domain knowledge essential for interpretation|||||

### Concept 5: Choosing Appropriate Summaries（选择适当的摘要统计量）
### Decision Framework（决策框架 — OpenIntro Ch 2.1.4）

|Distribution Shape|Center|Spread|Visualization|Titanic Example|
|----|----|----|----|----|
|Symmetric|Mean|Std Dev|Histogram (symmetric)|sibsp (mild skew) → mean=0.52, std dev=1.1|
|Skewed|Median|IQR|Histogram (skewed) + Box plot|age (right-skew) → median=28.0, IQR=17.875|
|Skewed + Outliers|Median|IQR|Box plot (shows outliers)|fare (heavy right-skew) → median=£14.45, IQR=£23.09|
|Bimodal|Report both modes|Range|Histogram (two peaks)|Hypothetical salary data → modes at $3k & $6k|

### Titanic Decision Tree（泰坦尼克号决策树）

Start: Summarize numerical variable
│
├─ Is distribution symmetric? (|skewness| < 0.5)
│   ├─ YES → Use MEAN + STD DEV
│   │        Example: sibsp (skewness=+0.6 → borderline, but acceptable)
│   │
│   └─ NO → Is distribution skewed? (|skewness| ≥ 0.5)
│           ├─ YES → Use MEDIAN + IQR
│           │        Example: age (skewness=+0.42 → slight skew → median preferred)
│           │        Example: fare (skewness=+4.37 → heavy skew → median essential)
│           │
│           └─ Are there extreme outliers?
│                   ├─ YES → Use MEDIAN + IQR + report outliers separately
│                   │        Example: fare → median=£14.45, IQR=£23.09, 78 outliers >£65.64
│                   │
│                   └─ NO → Use MEDIAN + IQR

### Why This Matters（为什么重要） 
>EN: Using mean/std dev for skewed fare suggests "typical fare = £32.20" — misleading because 75% paid ≤ £31.00. Median (£14.45) correctly states "half paid ≤ £14.45".
>FR: Utiliser moyenne/écart-type pour fare asymétrique suggère "tarif typique = £32.20" — trompeur car 75% ont payé ≤ £31.00. La médiane (£14.45) indique correctement "la moitié a payé ≤ £14.45".
>ZH: 对偏斜的 fare 使用均值/标准差暗示"典型票价=£32.20" — 具有误导性，因为75%乘客支付≤£31.00。中位数 (£14.45) 正确表明"一半乘客支付≤£14.45"。

### Concept 6: Summarizing Categorical Variables（分类型变量汇总）
**Definition（定义）**
For categorical variables, frequencies and proportions (not mean/median) are appropriate summaries.

### Rules（规则）
|Variable Type|Summary Method|Visualization|Titanic Example|
|---|---|---|---|
|Binary|Proportion (e.g., 38.4% survived)|Bar plot / Pie chart|survived: 38.4% yes, 61.6% no|
|Nominal|Frequency table + proportions|Bar plot (unordered)|embarked: S=72.4%, C=18.9%, Q=8.7%|
|Ordinal|Frequency table + proportions|Bar plot (ordered)|pclass: 1st=24.2%, 2nd=20.7%, 3rd=55.1%|

### Titanic Examples（泰坦尼克号实例）
**Binary Variable: survived**
```python
df['survived'].value_counts(normalize=True) * 100
# Output:
# 0    61.6%
# 1    38.4%
```
### Correct summary: "38.4% of passengers survived"
**Wrong summary: "Mean survival = 0.384" (mathematically correct but conceptually misleading)**
**Ordinal Variable: pclass**
```python
df['pclass'].value_counts(normalize=True).sort_index() * 100
# Output:
# 1    24.2%  (First class)
# 2    20.7%  (Second class)
# 3    55.1%  (Third class)
```
**Correct summary: Bar plot with ordered categories (1st → 2nd → 3rd) to show socioeconomic gradient**
**Wrong summary: Pie chart (hides ordinal relationship)**
   
### **Common Mistakes（常见错误**   

|Mistake|Why Wrong|Correct Approach|
|-------|---|---|    
|Calculating "mean sex"|Mathematically possible but meaningless|Report proportions (64.8% male, 35.2% female)|
|Using pie chart for ordinal data|Hides natural ordering|Use ordered bar plot|
|Ignoring missing values in proportions|Biases results|Always report missing % (e.g., age: 19.9% missing)|

### **Concept 7: Robustness vs Efficiency（稳健性 vs 效率）** 
**Definition（定义）**  
|Property|English|Français|中文|Best For|
|-----|-------|------|-----|-------|
|Robustness|Resistant to outliers/skewness|Résistant aux aberrations/asymétrie|对异常值/偏斜稳健|Skewed distributions|
|Efficiency|Smaller standard error (more precise)|Plus faible erreur-type (plus précis)|标准误更小（更精确）|Symmetric distributions|

**Trade-off（权衡）**  
|Statistic|Robustness|Efficiency|When to Use|
|-----|----|----|-----|
|Mean|Low|High|Symmetric distributions|
|Median|High|Lower|Skewed distributions / outliers|
|Std Dev|Low|High|Symmetric distributions|
|IQR|High|Lower|Skewed distributions / outliers|

**Titanic Illustration（泰坦尼克号说明）** 
|Variable|Distribution|Robust Summar|Efficient Summary|Which to Report?|
|----|----|-----|-----|-----|
|age|Slight right-skew|Median=28.0, IQR=17.875|Mean=29.7, Std Dev=14.5|Both (median primary, mean secondary)|
|fare|Heavy right-skew|Median=£14.45, IQR=£23.09|Mean=£32.20, Std Dev=£49.69|Median + IQR only (mean/std dev misleading)|
|sibsp|Mild right-skew|Median=0, IQR=1|Mean=0.52, Std Dev=1.1|Mean + Std Dev (skew mild, efficiency preferred)|

**OpenIntro Principle:** 
>"When in doubt, report both robust and efficient summaries — let the reader decide which is more appropriate for their purpose"
>存疑时同时报告稳健与高效摘要 —— 让读者根据用途自行判断

### Concept 8: Data Transformations（数据变换 — Preview for Ch 3+）
**Purpose（目的**
>To reduce skewness and make distributions more symmetric → enables use of mean/std dev.

**Common Transformations（常见变换）**
|Transformation|Formula|Best For|Titanic Example|
|-----|-----|----|-----|
|Log|log(x)|Right-skewed positive data|fare → log(fare) reduces skewness from +4.37 → +0.85|
|Square Root|xx​|Mild right-skew|sibsp → sqrt(sibsp) slightly reduces skew|
|Reciprocal|1/x|Severe right-skew|Rarely used for Titanic data|

**Caveats（注意事项）**
>Only for positive values (log(0) undefined)  
>Interpretation changes: "1 unit increase in log(fare)" ≠ "£1 increase in fare"   
>Not covered in Ch 2 — introduced later for regression (Ch 8)  

