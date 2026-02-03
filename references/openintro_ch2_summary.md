# OpenIntro Statistics (4th Ed) — Chapter 2 Core Concepts  
## Summarizing Data / Résumé des données / 数据汇总

> **Source**: Diez, D. M., Barr, C. D., & Çetinkaya-Rundel, M. (2019). *OpenIntro Statistics* (4th ed.), Chapter 2  
> **Dataset**: Titanic passenger records (`sns.load_dataset('titanic')`, n=891)  
> **Golden Rule**: *"The shape of a distribution determines which summaries are appropriate"* — OpenIntro Ch 2.1   
> **Notebook**: [02_summarizing_data.ipynb](../notebooks/02_summarizing_data.ipynb)

---

## Concept 1: Measures of Center（中心趋势度量）

### Definition（定义）
| English | Français | 中文 |
|---------|----------|------|
| **Mean (Arithmetic Average)** | Moyenne arithmétique | 算术平均数 |
| **Median** | Médiane | 中位数 |
| **Mode** | Mode | 众数 |

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
- The value with the highest frequency/出现频率**最高**的值
- There may be multiple modes/可能有多个众数（bimodal/multimodal）
- **Applicable conditions/适用条件**: Categorical variables or identification of multimodal distributions/分类型变量或识别多峰分布

### Titanic Examples（泰坦尼克号实例）

| Variable | Mean | Median | Mode | Interpretation（解读） |
|----------|------|--------|------|------------------------|
| **`age`** | 29.7 years | 28.0 years | 24.0 years | Mild right deviation/轻度右偏（mean > median ->The median is more representative of "typical age"/中位数更能代表"典型年龄" |
| **`fare`** | £32.20 | £14.45 | £8.05 | Severely skewed to the right/严重右偏（mean ≫ median）-> **The median is a more robust summary/中位数是更稳健的摘要** |
| **`survived`** | 0.38（比例） | — | 0（死亡） | 二元变量：mean/均值 = Survival rate/生还比例（38.4%） |
| **`pclass`** | 2.3 | 3.0 | 3（三等舱） | Categorical ordinal/有序分类：median/中位数=3 -> Typical passengers are in third class/表示"典型乘客是三等舱" |

> **Critical Insight**:  
> EN: For `fare`, mean (£32.20) is **misleading** — pulled up by extreme outlier (£512 first-class ticket). Median (£14.45) better represents "typical passenger fare".  
> FR: Pour `fare`, la moyenne (£32.20) est **trompeuse** — tirée vers le haut par une valeur aberrante (£512). La médiane (£14.45) représente mieux le "tarif typique".  
> ZH: `fare` 的均值 (£32.20) **misleading/具有误导性** — Driven up by extreme outliers (£512 first-class ticket price)/被极端异常值 (£512 头等舱票价) 拉高。The median price (£14.45) is more representative of the "typical ticket price"./中位数 (£14.45) 更能代表"典型票价"。

### Common Mistakes（常见错误）
| Mistake | Why Wrong | Correct Approach |
|---------|-----------|------------------|
| Reporting mean for heavily skewed `fare` | Mean inflated by outliers → misrepresents "typical" value | → Report **median (£14.45) + IQR (£7.91–£31.00)** |
| Using median for symmetric distribution | Loses efficiency (mean has smaller standard error) | → Use **mean** for symmetric distributions |
| Ignoring bimodality | Hides subgroups (e.g., two salary tiers) | → Use **histogram** to detect multiple modes |

---

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
- Maximum value - Minimum value/最大值 - 最小值
- **Disadvantages:** It relies solely on two extreme values, making it extremely sensitive to outliers./**缺点**: 仅依赖两个极端值，**对异常值极度敏感**

#### Variance & Standard Deviation（方差与标准差）
- **Variance**: 平均平方偏差（单位：原始单位²）
- **Standard Deviation**: 标准差（单位：与原始数据相同）
- **适用条件**: 对称分布（与均值配套使用）
- **敏感性**: **受异常值影响**（平方放大极端值影响）

#### IQR（四分位距）
- $Q_1$ = 25th percentile（第25百分位数）
- $Q_3$ = 75th percentile（第75百分位数）
- **IQR = $Q_3 - Q_1$**
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

### Definition（定义）
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

#### `fare` Outlier Detection
```python
Q1 = df['fare'].quantile(0.25)  # £7.91
Q3 = df['fare'].quantile(0.75)  # £31.00
IQR = Q3 - Q1                    # £23.09

lower_bound = Q1 - 1.5 * IQR     # -£26.73 (no lower outliers)
upper_bound = Q3 + 1.5 * IQR     # £65.64

outliers = df[df['fare'] > upper_bound]  # 78 passengers
max_fare = outliers['fare'].max()        # £512.33 (first-class ticket)