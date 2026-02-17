# OpenIntro Statistics (4th Ed) — Chapter 4 Core Concepts  
## Distributions of Random Variables / Distributions des variables aléatoires / 随机变量分布

> 📚 **Source**: Diez, D. M., Barr, C. D., & Çetinkaya-Rundel, M. (2019). *OpenIntro Statistics* (4th ed.), **Chapter 4 (Exact Order)**  
> 🔗 **Official Structure**:  
> 4.1 Normal Distribution → 4.2 Geometric → 4.3 Binomial → 4.4 Negative Binomial → 4.5 Poisson  
> 💡 **Golden Rule**: *"Each distribution models a specific random process — match the process to the model"* — OpenIntro Ch 4

---

## 🔑 Concept 4.1: Normal Distribution（正态分布）

### 📖 Definition（定义）
| English | Français | 中文 |
|---------|----------|------|
| **Normal Distribution** | Distribution normale | 正态分布 |
| **Bell Curve** | Courbe en cloche | 钟形曲线 |
| **68-95-99.7 Rule** | Règle 68-95-99.7 | 68-95-99.7法则 |
| **Z-score** | Score Z | Z分数 |

### 📐 Formal Definition（形式化定义）
$$f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}, \quad X \sim N(\mu, \sigma)$$
**Standard Normal**: $Z \sim N(0,1)$, $z = \frac{x - \mu}{\sigma}$

### 🌊 Titanic Example（泰坦尼克号实例）
`age` distribution ($\mu=29.7$, $\sigma=14.5$):
- 68% passengers: $29.7 \pm 14.5$ → [15.2, 44.2] years
- 95% passengers: $29.7 \pm 29.0$ → [0.7, 58.7] years
- Actual 95% interval: [0.8, 56.0] → **Close approximation** (slight right skew)

> 💡 **Critical Insight (OpenIntro 4.1)**:  
> EN: Normal distribution is **symmetric & unimodal** — inappropriate for skewed variables like `fare` (skewness=4.37)  
> FR: La normale est **symétrique et unimodale** — inappropriée pour `fare` asymétrique  
> ZH: 正态分布**对称且单峰** —— 不适用于偏斜变量如 `fare`（偏度=4.37）

---

## 🔑 Concept 4.2: Geometric Distribution（几何分布）

### 📖 Definition（定义）
Models **number of trials until first success** in independent Bernoulli trials.

### 📐 Formal Definition（形式化定义）
$$P(X = k) = (1-p)^{k-1} p, \quad k = 1, 2, 3, ...$$
- $X$ = trials until first success
- **Memoryless property**: $P(X > s+t \mid X > s) = P(X > t)$

### 🌊 Titanic Example（泰坦尼克号实例）
Survival rate $p = 0.384$:
- $E(X) = 1/p = 2.60$ → Expect to interview **2.6 passengers** to find first survivor
- $P(X=1) = 0.384$ (first passenger survived)
- $P(X=3) = (0.616)^2 \times 0.384 = 0.146$ (first two died, third survived)

> 💡 **Critical Insight (OpenIntro 4.2)**:  
> EN: Geometric is **special case of negative binomial** with $r=1$ (first success)  
> FR: La géométrique est un **cas particulier de la binomiale négative** avec $r=1$  
> ZH: 几何分布是**负二项分布的特例**（$r=1$，首次成功）

---

## 🔑 Concept 4.3: Binomial Distribution（二项分布）

### 📖 Definition（定义）
Models **number of successes in fixed $n$ independent trials**.

### 📐 Formal Definition（形式化定义）
$$P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, ..., n$$
**Conditions**: Fixed $n$, independent trials, binary outcome, constant $p$

### 🌊 Titanic Example（泰坦尼克号实例）
Sample of $n=10$ passengers, $p=0.384$:
- $P(X=4) = \binom{10}{4} (0.384)^4 (0.616)^6 = 0.260$
- $P(X \geq 6) = 0.128$ (only 12.8% chance ≥60% survival)
- Mean: $\mu = np = 3.84$, SD: $\sigma = \sqrt{np(1-p)} = 1.54$

> 💡 **Critical Insight (OpenIntro 4.3)**:  
> EN: Binomial requires **independence** — violated if sampling without replacement from small population  
> FR: La binomiale exige **l'indépendance** — violée si échantillonnage sans remise dans petite population  
> ZH: 二项分布要求**独立性** —— 无放回抽样小总体时被违反

---

## 🔑 Concept 4.4: Negative Binomial Distribution（负二项分布）← **NEWLY ADDED**

### 📖 Definition（定义）
| English | Français | 中文 |
|---------|----------|------|
| **Negative Binomial** | Binomiale négative | 负二项分布 |
| **Trials until r successes** | Essais jusqu'à r succès | 直到r次成功所需的试验次数 |
| **Overdispersion** | Surdispersion | 过离散 |

### 📐 Formal Definition（形式化定义）
Models **number of trials $X$ until $r$-th success**:
$$P(X = k) = \binom{k-1}{r-1} p^r (1-p)^{k-r}, \quad k = r, r+1, r+2, ...$$
- **Alternative parameterization**: $Y = X - r$ = failures before $r$-th success  
  $P(Y = k) = \binom{k+r-1}{r-1} p^r (1-p)^k, \quad k = 0, 1, 2, ...$

### 📊 Key Properties（关键性质）
| Property | Formula | Interpretation |
|----------|---------|----------------|
| **Mean** | $\mu = \frac{r}{p}$ | Expected trials until $r$ successes |
| **Variance** | $\sigma^2 = \frac{r(1-p)}{p^2}$ | Larger than binomial (overdispersed) |
| **Special Case** | $r=1$ → Geometric distribution | 几何分布是 $r=1$ 的特例 |

### 🌊 Titanic Example（泰坦尼克号实例）
**Scenario**: How many passengers must we interview to find **$r=3$ survivors**? ($p=0.384$)
- $E(X) = r/p = 3/0.384 = 7.81$ trials
- $P(X=5)$ = Probability 5th passenger is **3rd survivor**:
  $$P(X=5) = \binom{4}{2} (0.384)^3 (0.616)^2 = 6 \times 0.0566 \times 0.379 = 0.128$$
- Interpretation: 12.8% chance exactly 5 interviews needed to find 3 survivors

**Why not binomial?**  
- Binomial: "In 10 interviews, how many survivors?" (fixed $n$)  
- Negative Binomial: "How many interviews to find 3 survivors?" (fixed $r$)

> 💡 **Critical Insight (OpenIntro 4.4)**:  
> EN: Negative binomial handles **overdispersed count data** (variance > mean) — common in real-world counts  
> FR: La binomiale négative gère les **données de comptage surdispersées** (variance > moyenne)  
> ZH: 负二项分布处理**过离散计数数据**（方差 > 均值）—— 真实计数数据常见  
>   
> 📌 **Connection**:  
> - $r=1$ → Geometric distribution (Ch 4.2)  
> - $r \to \infty$, $p \to 1$ → Poisson distribution (Ch 4.5)

### ⚠️ When to Use Negative Binomial（使用场景）
| Scenario | Why Negative Binomial? |
|----------|------------------------|
| Counting trials until $r$ successes | Fixed $r$, variable $n$ (opposite of binomial) |
| Overdispersed count data (variance > mean) | Binomial/Poisson underestimate variance |
| Modeling `sibsp` with excess zeros | Better fit than Poisson for Titanic family size |

---

## 🔑 Concept 4.5: Poisson Distribution（泊松分布）

### 📖 Definition（定义）
Models **number of rare events in fixed interval** (time/space).

### 📐 Formal Definition（形式化定义）
$$P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad k = 0, 1, 2, ...$$
- $\lambda$ = average rate (events per interval)
- **Connection to Binomial**: Limit as $n \to \infty$, $p \to 0$, $np = \lambda$

### 🌊 Titanic Example（泰坦尼克号实例）
`sibsp` (siblings/spouses) with $\lambda = 0.523$:
- $P(X=0) = e^{-0.523} = 0.593$ (59.3% travel alone)
- $P(X=1) = 0.523 \times e^{-0.523} = 0.310$
- **Problem**: Observed 68.2% have 0 siblings → **underestimates zeros**  
  → Better model: **Zero-inflated Poisson** (advanced topic)

> 💡 **Critical Insight (OpenIntro 4.5)**:  
> EN: Poisson assumes **equidispersion** (variance = mean) — often violated in real data  
> FR: La Poisson suppose **l'équidispersion** (variance = moyenne) — souvent violée  
> ZH: 泊松分布假设**等离散性**（方差=均值）—— 真实数据常被违反  
>   
> 📌 **Bridge to Negative Binomial**:  
> When variance > mean (overdispersion), **negative binomial** is preferred over Poisson

---

## 🔗 Chapter 4 Structure Summary（章节结构总结）

| Section | Distribution | Models | Key Parameter(s) | Titanic Application |
|---------|--------------|--------|------------------|---------------------|
| **4.1** | Normal | Continuous measurements | $\mu, \sigma$ | `age` distribution (approximate) |
| **4.2** | Geometric | Trials until **1st** success | $p$ | Interviews to find 1 survivor |
| **4.3** | Binomial | Successes in **fixed $n$** trials | $n, p$ | Survivors in sample of 10 |
| **4.4** | **Negative Binomial** | Trials until **$r$ successes** | $r, p$ | Interviews to find 3 survivors |
| **4.5** | Poisson | Rare events in fixed interval | $\lambda$ | `sibsp` counts (with limitations) |

> 💡 **Golden Progression (OpenIntro Ch 4)**:  
> *"Geometric ($r=1$) → Negative Binomial ($r$ successes) → Binomial (fixed $n$) → Poisson (rare events)"*  
> → 几何（$r=1$）→ 负二项（$r$次成功）→ 二项（固定$n$）→ 泊松（稀有事件）
