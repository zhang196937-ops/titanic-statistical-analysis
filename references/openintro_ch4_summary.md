# OpenIntro Statistics (4th Ed) — Chapter 4 Summary  
## Distributions of Random Variables (Exact Textbook Order)

> 📚 **Official Structure**: 4.1 Normal → 4.2 Geometric → 4.3 Binomial → **4.4 Negative Binomial** → 4.5 Poisson  
> 💡 **Golden Rule**: *"Match the random process to the distribution model"*

---

## 🔑 Core Concepts at a Glance (Exact Ch 4 Order)

| Sec | Distribution | English | Français | 中文 | Key Formula | Titanic Example |
|-----|--------------|---------|----------|------|-------------|-----------------|
| **4.1** | Normal | Symmetric continuous | Continue symétrique | 对称连续 | $z=\frac{x-\mu}{\sigma}$ | 68% ages in [15.2, 44.2] |
| **4.2** | Geometric | Trials until 1st success | Essais jusqu'au 1er succès | 首次成功前试验 | $P(X=k)=(1-p)^{k-1}p$ | $E(X)=2.6$ to find survivor |
| **4.3** | Binomial | Successes in fixed $n$ | Succès en $n$ fixe | 固定$n$次成功数 | $P(X=k)=\binom{n}{k}p^k(1-p)^{n-k}$ | $P(4/10 \text{ survive})=0.260$ |
| **4.4** | **Negative Binomial** | **Trials until $r$ successes** | **Essais jusqu'à $r$ succès** | **$r$次成功前试验** | $P(X=k)=\binom{k-1}{r-1}p^r(1-p)^{k-r}$ | $E(X)=7.81$ to find 3 survivors |
| **4.5** | Poisson | Rare events in interval | Événements rares | 固定区间稀有事件 | $P(X=k)=\frac{\lambda^k e^{-\lambda}}{k!}$ | $P(0 \text{ siblings})=0.593$ |

---

## 💡 Critical Relationships (OpenIntro Ch 4)

| Relationship | EN | FR | ZH |
|--------------|----|----|----|
| **Geometric → Negative Binomial** | Geometric = Negative Binomial with $r=1$ | Géométrique = Binomiale négative avec $r=1$ | 几何 = 负二项 ($r=1$) |
| **Negative Binomial → Poisson** | As $r \to \infty$, $p \to 1$ with $r(1-p)=\lambda$ | Quand $r \to \infty$, $p \to 1$ | $r \to \infty$, $p \to 1$ 时趋近泊松 |
| **Binomial vs Negative Binomial** | Binomial: fixed $n$, variable successes<br>NegBin: fixed $r$, variable trials | Binomiale: $n$ fixe<br>Binomiale négative: $r$ fixe | 二项：固定$n$<br>负二项：固定$r$ |
| **Poisson Limitation** | Assumes variance = mean (equidispersion) | Suppose variance = moyenne | 假设方差=均值（等离散） |
| **Negative Binomial Advantage** | Handles overdispersion (variance > mean) | Gère la surdispersion | 处理过离散（方差>均值） |

---

## ✅ Self-Assessment Checklist (Exact Ch 4 Coverage)

- [ ] **4.1**: Apply 68-95-99.7 rule; convert values to Z-scores
- [ ] **4.2**: Calculate $P(X=k)$ for geometric; explain memoryless property
- [ ] **4.3**: Verify 4 binomial conditions; compute probabilities
- [ ] **4.4**: **Calculate negative binomial probabilities**; explain $r=1$ → geometric
- [ ] **4.5**: Identify Poisson scenarios; recognize when overdispersion requires negative binomial
- [ ] **All**: Choose correct distribution for given scenario (process → model)

---

## 🔗 Why Negative Binomial Matters (Critical Addition)

| Distribution | Variance Formula | Limitation | Solution |
|--------------|------------------|------------|----------|
| **Poisson** | $\sigma^2 = \lambda$ | Assumes variance = mean | ❌ Fails for overdispersed data |
| **Negative Binomial** | $\sigma^2 = \lambda + \frac{\lambda^2}{r}$ | **Handles overdispersion** | ✅ Variance > mean allowed |

> 💡 **Real-World Insight**:  
> EN: Most count data (e.g., insurance claims, disease cases) are **overdispersed** → Negative binomial preferred over Poisson  
> FR: La plupart des données de comptage sont **surdispersées** → Binomiale négative préférée  
> ZH: 大多数计数数据（如保险索赔）**过离散** → 负二项分布优于泊松

---

## 📌 Memory Aid: Distribution Decision Tree
        Random Process?
        │
        ├─ Continuous measurement? → Normal (4.1)
        │
        ├─ Counting trials until success?
        │ ├─ Until 1st success? → Geometric (4.2)
        │ └─ Until r-th success? → Negative Binomial (4.4) ← NEW
        │
        ├─ Counting successes in fixed n trials? → Binomial (4.3)
        │
        └─ Counting rare events in fixed interval?
        ├─ Variance ≈ mean? → Poisson (4.5)
        └─ Variance > mean? → Negative Binomial (4.4) ← CRITICAL


> 📚 **OpenIntro Official Path**:  
> *"Master this sequence: Normal → Geometric → Binomial → Negative Binomial → Poisson"*  
> → 掌握此顺序：正态 → 几何 → 二项 → **负二项** → 泊松









