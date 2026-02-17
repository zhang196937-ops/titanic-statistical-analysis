# OpenIntro Statistics (4th Ed) — Chapter 3 Core Concepts  
## Probability / Probabilité / 概率

> 📚 **Source**: Diez, D. M., Barr, C. D., & Çetinkaya-Rundel, M. (2019). *OpenIntro Statistics* (4th ed.), Chapter 3  
> 🔗 **Dataset**: Titanic passenger records (`sns.load_dataset('titanic')`, n=891)  
> 💡 **Golden Rule**: *"Probability quantifies uncertainty — it is the foundation of statistical inference"*

---

## 🔑 Concept 1: Defining Probability（概率定义）

### 📖 Definition（定义）
| English | Français | 中文 |
|---------|----------|------|
| **Probability** | Probabilité | 概率 |
| **Random Process** | Processus aléatoire | 随机过程 |
| **Outcome** | Issue / Résultat | 结果 |
| **Sample Space** | Espace d'échantillonnage | 样本空间 |
| **Event** | Événement | 事件 |

### 📐 Formal Definition（形式化定义）
For a random process with sample space $S$ and event $A \subseteq S$:
$$P(A) = \lim_{n \to \infty} \frac{\text{Number of times } A \text{ occurs}}{n}$$

**Key Properties**（关键性质）:
1. $0 \leq P(A) \leq 1$ for any event $A$
2. $P(S) = 1$ (certainty)
3. $P(A^c) = 1 - P(A)$ (complement rule/概率的补集法则)

### 🌊 Titanic Examples（泰坦尼克号实例）

| Event $A$ | Description | Calculation | Probability |
|-----------|-------------|-------------|-------------|
| `survived=1` | Passenger survived | $342/891$ | $0.384$ (38.4%) |
| `sex='female'` | Passenger is female | $314/891$ | $0.352$ (35.2%) |
| `pclass=1` | Passenger in 1st class | $216/891$ | $0.242$ (24.2%) |
| `survived=0` | Passenger died | $549/891$ | $0.616$ (61.6%) |
| `survived=0` complement | Passenger survived | $1 - 0.616$ | $0.384$ (38.4%) |

> 💡 **Critical Insight**:  
> EN: Probability is **long-run relative frequency** — not a guarantee for any single passenger  
> FR: La probabilité est une **fréquence relative à long terme** — pas une garantie pour un passager individuel  
> ZH: 概率是**长期相对频率** —— 不是对单个乘客的保证

### ⚠️ Common Misconceptions（常见误解）
| Misconception | Correction |
|---------------|------------|
| "Probability = certainty for this passenger" | → Probability describes **population-level patterns**, not individual outcomes(概率描述的是群体层面的模式，而非个体结果) |
| "38.4% survival means exactly 384 of 1000 will survive" | → It's an **expectation** — actual count varies due to randomness(这是一种预期——实际数量会因随机性而有所不同) |
| "If 10 males died in a row, next must be female" | → **Gambler's fallacy** — each passenger's survival is independent (in simple models)(赌徒谬误——每个乘客的生存都是独立的（在简单模型中）) |

---

## 🔑 Concept 2: Conditional Probability（条件概率）

### 📖 Definition（定义）
The probability of event $A$ **given that** event $B$ has occurred:
$$P(A \mid B) = \frac{P(A \text{ and } B)}{P(B)}, \quad \text{provided } P(B) > 0$$

| English | Français | 中文 |
|---------|----------|------|
| **Conditional Probability** | Probabilité conditionnelle | 条件概率 |
| **Given** | Sachant que / Étant donné | 给定 |
| **Joint Probability** | Probabilité conjointe | 联合概率 |

### 📐 Venn Diagram Interpretation（维恩图解释）
   ```
     S (Sample Space)
  
┌──────────────────────┐
│        ┌──────┐      │
│   B    │ A∩B  │      │  P(A|B) = Area(A∩B) / Area(B)
│ ┌──────┼──────┘      │
│ │      │             │
│ └──────┘             │
└──────────────────────┘
```

### 🌊 Titanic Examples（泰坦尼克号实例）

#### Example 1: Survival given female
$$P(\text{survived=1} \mid \text{sex=female}) = \frac{P(\text{survived=1 and sex=female})}{P(\text{sex=female})} = \frac{233/891}{314/891} = \frac{233}{314} = 0.742$$

| Calculation | Value |
|-------------|-------|
| $P(\text{sex=female(女性占总乘客的比例)})$ | $314/891 = 0.352$ |
| $P(\text{survived=1 and sex=female}(获救的女性占总乘客的比例))$ | $233/891 = 0.261$ |
| $P(\text{survived=1} \mid \text{sex=female}(获救的女性占总获救乘客的比例))$ | $0.261 / 0.352 = 0.742$ (74.2%) |

#### Example 2: Survival given male
$$P(\text{survived=1} \mid \text{sex=male}) = \frac{109/891}{577/891} = \frac{109}{577} = 0.189 \text{ (18.9%)}$$

#### Example 3: 1st class given survived
$$P(\text{pclass=1} \mid \text{survived=1}) = \frac{136/891}{342/891} = \frac{136}{342} = 0.398 \text{ (39.8%)}$$

> 💡 **Critical Insight**:  
> EN: $P(A \mid B) \neq P(B \mid A)$ in general — confusing these causes **prosecutor's fallacy**  
> FR: $P(A \mid B) \neq P(B \mid A)$ en général — cette confusion cause le **sophisme du procureur**  
> ZH: 一般情况下 $P(A \mid B) \neq P(B \mid A)$ —— 混淆二者导致**检察官谬误**

| Conditional Probability | Value | Interpretation |
|-------------------------|-------|----------------|
| $P(\text{survived} \mid \text{female})$ | 74.2% | Among females, 74.2% survived |
| $P(\text{female} \mid \text{survived})$ | 68.1% | Among survivors, 68.1% were female |
| **Difference** | 6.1% | These are **different questions** with different answers! |

### ⚠️ Common Mistakes（常见错误）
| Mistake | Why Wrong | Correct Approach |
|---------|-----------|------------------|
| Confusing $P(A \mid B)$ with $P(B \mid A)$ | Different denominators (B vs A) | → Always write full formula: $P(A \mid B) = P(A \cap B)/P(B)$ |
| Assuming independence when not true | $P(A \mid B) \neq P(A)$ for dependent events | → Test: $P(A \mid B) \approx P(A)$? If not, dependent |
| Ignoring base rates | High $P(\text{disease} \mid \text{positive test})$ requires high base rate | → Always consider $P(B)$ in denominator |

---

## 🔑 Concept 3: Bayes' Theorem（贝叶斯定理）

### 📖 Definition（定义）
A rearrangement of the conditional probability formula to "reverse" conditioning:
$$P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B)}$$

Where $P(B)$ can be expanded using the **Law of Total Probability**:
$$P(B) = P(B \mid A) \cdot P(A) + P(B \mid A^c) \cdot P(A^c)$$

贝叶斯定理：条件概率的“反转”通常，我们知道 $P(B|A)$（即在 $A$ 发生的情况下 $B$ 发生的概率），但如果我们想要求 $P(A|B)$（即在 $B$ 发生的情况下 $A$ 发生的概率），我们就需要用到贝叶斯定理。1. 数学公式 (LaTeX)$$P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}$$


### 📐 Derivation（推导）
$$
\begin{align*}
P(A \mid B) &= \frac{P(A \cap B)}{P(B)} & \text{(definition)} \\
&= \frac{P(B \mid A) \cdot P(A)}{P(B)} & \text{(since } P(A \cap B) = P(B \mid A) P(A)\text{)} \\
&= \frac{P(B \mid A) \cdot P(A)}{P(B \mid A) P(A) + P(B \mid A^c) P(A^c)} & \text{(Law of Total Probability)}
\end{align*}
$$

### 🌊 Titanic Examples（泰坦尼克号实例）

#### Example: Probability passenger is female given survived
We want $P(\text{female} \mid \text{survived})$.

Using Bayes' Theorem:
$$
\begin{align*}
P(\text{female} \mid \text{survived}) &= \frac{P(\text{survived} \mid \text{female}) \cdot P(\text{female})}{P(\text{survived})} \\
&= \frac{0.742 \times 0.352}{0.384} \\
&= \frac{0.261}{0.384} \\
&= 0.681 \text{ (68.1%)}
\end{align*}
$$

| Component | Value | Source |
|-----------|-------|--------|
| $P(\text{survived} \mid \text{female})$ | 0.742 | From conditional probability above |
| $P(\text{female})$ | 0.352 | Base rate (314/891) |
| $P(\text{survived})$ | 0.384 | Base rate (342/891) |
| **Result** | **0.681** | Matches direct calculation: 233/342 |

#### Why Bayes' Theorem Matters（为什么重要）
- **Medical testing**: $P(\text{disease} \mid \text{positive test})$ depends on disease prevalence (取决于疾病流行情况)
- **Spam filtering**: $P(\text{spam} \mid \text{"free offer"})$ updates with new evidence
- **Machine learning**: Naive Bayes classifiers use this principle

> 💡 **Critical Insight**:  
> EN: Bayes' Theorem formalizes **updating beliefs with evidence** — prior $P(A)$ → posterior $P(A \mid B)$  
> FR: Le théorème de Bayes formalise la **mise à jour des croyances avec des preuves** — prior $P(A)$ → posterior $P(A \mid B)$  
> ZH: 贝叶斯定理形式化了**用证据更新信念** —— 先验 $P(A)$ → 后验 $P(A \mid B)$

---

## 🔑 Concept 4: Sampling from a Population（从总体抽样）

### 📖 Definition（定义）
| English | Français | 中文 |
|---------|----------|------|
| **Population** | Population | 总体 |
| **Sample** | Échantillon | 样本 |
| **Sampling** | Échantillonnage | 抽样 |
| **Simple Random Sample (SRS)** | Échantillon aléatoire simple | 简单随机样本 |
| **Stratified Sample** | Échantillon stratifié | 分层样本 |

### 📐 Key Principles（关键原则）
1. **Representativeness(代表性)**: Sample should reflect population characteristics
2. **Randomness(随机性)**: Each member has known (often equal) chance of selection
3. **Independence(独立)**: Selection of one unit doesn't affect others (approximate for large populations)

### 🌊 Titanic Examples（泰坦尼克号实例）

| Sampling Method | Description | Titanic Application | Risk |
|-----------------|-------------|---------------------|------|
| **Simple Random Sample** | Randomly select 100 passengers | Select 100 rows uniformly from dataset | May underrepresent(低估) rare groups(稀有群体) (e.g., 1st class women) |
| **Stratified Sample** | Sample proportionally from strata(按比例从各层中抽样) | Sample 24% from 1st class, 21% from 2nd, 55% from 3rd | Ensures class representation |
| **Cluster Sample(聚类样本)** | Randomly select groups | Randomly select 10 cabins, include all occupants | Efficient but may have intra-cluster correlation(效率高，但可能存在组内相关性) |

> 💡 **Critical Insight**:  
> EN: Titanic dataset is a **census** (all passengers), not a sample — but we treat it as population for inference practice  
> FR: Le jeu de données Titanic est un **recensement** (tous les passagers), pas un échantillon — mais nous le traitons comme population pour pratique d'inférence  
> ZH: 泰坦尼克号数据集是**普查**（所有乘客），非样本 —— 但为推断练习，我们将其视为总体

### ⚠️ Sampling Bias Examples（抽样偏差示例）
| Bias Type | Description | Titanic Example |
|-----------|-------------|-----------------|
| **Survivorship bias(幸存者偏差)** | Only observing survivors(仅观察幸存者) | Analyzing only survivors → overestimating survival factors(仅分析幸存者 → 高估生存因素) |
| **Non-response bias(无应答偏差)** | Missing data not random(缺失数据并非随机发生)| Age missing for 20% — if missingness related to survival, bias introduced(
20% 的年龄数据缺失——如果缺失值与生存相关，则会引入偏差。) |
| **Convenience sampling方便取样** | Easy-to-reach units | Only analyzing passengers with known ages → biased toward adults(仅分析已知年龄的乘客 → 倾向于成年人) |

---

## 🔑 Concept 5: Random Variables（随机变量）

### 📖 Definition（定义）
A **random variable** is a numeric variable whose value depends on the outcome(结果) of a random process.

| Type | English | Français | 中文 | Example |
|------|---------|----------|------|---------|
| **Discrete** | Discrete random variable | Variable aléatoire discrète | 离散随机变量 | `survived` (0/1), `sibsp` (0,1,2...) |
| **Continuous** | Continuous random variable | Variable aléatoire continue | 连续随机变量 | `age`, `fare` |

### 📐 Notation & Properties（符号与性质）
- Denoted by capital letters: $X$, $Y$, $Z$
- Specific outcomes denoted by lowercase: $x$, $y$, $z$
- **Probability mass function(概率质量函数) (PMF)** for discrete: $P(X = x)$
- **Probability density function(概率密度函数) (PDF)** for continuous: $f(x)$ where $P(a < X < b) = \int_a^b f(x)dx$

### 🌊 Titanic Examples（泰坦尼克号实例）

| Random Variable | Type | Possible Values | PMF Example |
|-----------------|------|-----------------|-------------|
| $X = \text{survived}$ | Discrete (binary) | $\{0, 1\}$ | $P(X=1) = 0.384$ |
| $Y = \text{sibsp}$ | Discrete | $\{0, 1, 2, ..., 8\}$ | $P(Y=0) = 0.682$ |
| $Z = \text{age}$ | Continuous | $[0.42, 80.0]$ | $P(20 < Z < 30) = 0.352$ |

> 💡 **Critical Insight**:  
> EN: Random variables **map outcomes to numbers** — essential for mathematical treatment of uncertainty  
> FR: Les variables aléatoires **associent des résultats à des nombres** — essentielles pour le traitement mathématique de l'incertitude  
> ZH: 随机变量**将结果映射为数字** —— 对不确定性进行数学处理的基础

---

## 🔑 Concept 6: Expected Value & Variance（期望值与方差）

### 📖 Definition（定义）
| Concept | English | Français | 中文 | Formula (Discrete) |
|---------|---------|----------|------|---------------------|
| **Expected Value** | Espérance mathématique | 期望值 | $E(X) = \sum x \cdot P(X = x)$ |
| **Variance** | Variance | 方差 | $\text{Var}(X) = \sum (x - E(X))^2 \cdot P(X = x)$ |
| **Standard Deviation** | Écart-type | 标准差 | $\sigma_X = \sqrt{\text{Var}(X)}$ |

### 📐 Properties（性质）
1. $E(aX + b) = aE(X) + b$
2. $\text{Var}(aX + b) = a^2 \text{Var}(X)$
3. For independent $X, Y$: $E(X+Y) = E(X) + E(Y)$ and $\text{Var}(X+Y) = \text{Var}(X) + \text{Var}(Y)$

### 🌊 Titanic Examples（泰坦尼克号实例）

#### Example 1: Expected value of `survived`
$$E(X) = 0 \cdot P(X=0) + 1 \cdot P(X=1) = 0 \cdot 0.616 + 1 \cdot 0.384 = 0.384$$
✅ **Interpretation**: Expected survival rate = 38.4% (matches sample proportion)

#### Example 2: Variance of `survived`
$$
\begin{align*}
\text{Var}(X) &= (0 - 0.384)^2 \cdot 0.616 + (1 - 0.384)^2 \cdot 0.384 \\
&= 0.147 \cdot 0.616 + 0.380 \cdot 0.384 \\
&= 0.091 + 0.146 \\
&= 0.237
\end{align*}
$$
Standard deviation: $\sigma_X = \sqrt{0.237} = 0.487$

#### Example 3: Expected family size
Define $F = \text{sibsp} + \text{parch} + 1$ (including self)
$$E(F) = E(\text{sibsp}) + E(\text{parch}) + 1 = 0.523 + 0.382 + 1 = 1.905$$
✅ **Interpretation**: Average family group size = 1.9 passengers

> 💡 **Critical Insight**:  
> EN: For binary variables, $E(X) = p$ and $\text{Var}(X) = p(1-p)$ — fundamental for proportion inference  
> FR: Pour variables binaires, $E(X) = p$ et $\text{Var}(X) = p(1-p)$ — fondamental pour l'inférence sur les proportions  
> ZH: 对二元变量，$E(X) = p$ 且 $\text{Var}(X) = p(1-p)$ —— 比例推断的基础

---

## 🔑 Concept 7: Law of Large Numbers（大数定律）

### 📖 Definition（定义）
As the number of independent observations $n$ increases, the sample mean $\bar{x}$ converges to the population mean $\mu$:
$$\bar{x} = \frac{1}{n}\sum_{i=1}^n X_i \xrightarrow{P} \mu = E(X) \quad \text{as } n \to \infty$$

### 🌊 Titanic Simulation Example（泰坦尼克号模拟示例）
```python
import numpy as np
import matplotlib.pyplot as plt

# Simulate sampling from Titanic survival distribution
np.random.seed(42)
population = np.random.choice([0, 1], size=10000, p=[0.616, 0.384])  # True p=0.384

sample_sizes = np.arange(1, 1001)
sample_means = [population[:n].mean() for n in sample_sizes]

plt.figure(figsize=(10, 5))
plt.plot(sample_sizes, sample_means, label='Sample mean')
plt.axhline(y=0.384, color='red', linestyle='--', label='True mean (μ=0.384)')
plt.xlabel('Sample size (n)')
plt.ylabel('Sample mean (x̄)')
plt.title('Law of Large Numbers: Sample Mean → Population Mean as n increases')
plt.legend()
plt.grid(alpha=0.3)
plt.show()
```
### ✅ Interpretation:###
Small samples (n<50): Sample mean varies widely (0.2 to 0.6)
Large samples (n>500): Sample mean stabilizes near true mean (0.384)
Practical implication: Larger samples → more reliable estimates
### 💡 Critical Insight:###
EN: LLN justifies using sample statistics to estimate population parameters — foundation of statistical inference  
FR: La LGN justifie l'utilisation des statistiques d'échantillon pour estimer les paramètres de population — fondement de l'inférence statistique 
ZH: 大数定律证明用样本统计量估计总体参数的合理性 —— 统计推断的基础  

## 🔑 Concept 8: Independence（独立性） 

### 📖 Definition（定义）
Events A and B are independent if:
P(A∣B)=P(A) or equivalently P(A and B) = P(A) ⋅ P(B)
P(A∣B)=P(A)or equivalentlyP(A and B)=P(A)⋅P(B)
Random variables X and Y are independent if knowledge of X provides no information about Y.

### 🌊 Titanic Examples（泰坦尼克号实例）
Test independence: sex and pclass 
||1st class|2nd class|3rd class|Total|
|-----|------|------|-----|-----|
|Female|94|76|144|314|
|Male|122|108|347|
|Total|216 184|491|891|

P(female)=314/891=0.352
P(1st class)=216/891=0.242
P(female and 1st class)=94/891=0.106
P(female)⋅P(1st class)=0.352×0.242=0.085
### ❌ Not independent because 
### ✅ Interpretation: Females were overrepresented in 1st class (43.5% of 1st class vs 35.2% overall)

Test independence: survived and alone
||Alone|Not alone|Total|
|----|-----|---|----|
|Survived|113|229|342|
|Died|209|340|549|
|Total|322|569|891|


P(survived)=0.384
P(alone)=322/891=0.361
P(survived and alone)=113/891=0.127
P(survived)⋅P(alone)=0.384×0.361=0.139
### ⚠️ Approximately independent (0.127≈0.139) — traveling alone had little effect on survival
### 💡 Critical Insight:  
EN: Independence is rare in observational data — most variables have some association (confounding)  
FR: L'indépendance est rare dans les données observationnelles — la plupart des variables ont une certaine association (confusion)  
ZH: 独立性在观察性数据中罕见 —— 大多数变量存在某种关联（混杂）  
