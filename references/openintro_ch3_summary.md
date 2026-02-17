# OpenIntro Statistics (4th Ed) — Chapter 3 Summary  
## Probability / Probabilité / 概率

> 📚 **Source**: Diez, D. M., Barr, C. D., & Çetinkaya-Rundel, M. (2019). *OpenIntro Statistics* (4th ed.), Chapter 3  
> 💡 **Golden Rule**: *"Probability quantifies uncertainty — foundation of statistical inference"*

---

## 🔑 Core Concepts at a Glance

| Concept | English | Français | 中文 | Titanic Example |
|---------|---------|----------|------|-----------------|
| **Probability** | Long-run relative frequency | Fréquence relative à long terme | 长期相对频率 | $P(\text{survived}) = 342/891 = 0.384$ |
| **Conditional Probability** | $P(A \mid B) = P(A \cap B)/P(B)$ | $P(A \mid B) = P(A \cap B)/P(B)$ | $P(A \mid B) = P(A \cap B)/P(B)$ | $P(\text{survived} \mid \text{female}) = 233/314 = 0.742$ |
| **Bayes' Theorem** | $P(A \mid B) = \frac{P(B \mid A)P(A)}{P(B)}$ | Théorème de Bayes | 贝叶斯定理 | $P(\text{female} \mid \text{survived}) = \frac{0.742 \times 0.352}{0.384} = 0.681$ |
| **Independence** | $P(A \cap B) = P(A)P(B)$ | Indépendance | 独立性 | `sex` & `pclass` NOT independent ($0.106 \neq 0.085$) |
| **Random Variable** | Numeric outcome of random process | Variable aléatoire | 随机变量 | $X = \text{survived}$ (discrete binary) |
| **Expected Value** | $E(X) = \sum x \cdot P(X=x)$ | Espérance | 期望值 | $E(\text{survived}) = 0.384$ |
| **Law of Large Numbers** | $\bar{x} \to \mu$ as $n \to \infty$ | Loi des grands nombres | 大数定律 | Sample survival rate → 38.4% as $n$ increases |

---

## 💡 Critical Principles (OpenIntro Ch 3)

| # | Principle | EN | FR | ZH |
|---|-----------|----|----|----|
| 1 | **Conditional ≠ Reverse** | $P(A \mid B) \neq P(B \mid A)$ | $P(A \mid B) \neq P(B \mid A)$ | $P(A \mid B) \neq P(B \mid A)$ |
| 2 | **Bayes' Theorem** | Updates beliefs with evidence | Met à jour les croyances | 用证据更新信念 |
| 3 | **Independence Rare** | Most variables associated in observational data | Variables souvent associées | 观察性数据中变量多关联 |
| 4 | **LLN Foundation** | Larger samples → more reliable estimates | Échantillons plus grands → estimations plus fiables | 样本越大 → 估计越可靠 |

---

## ⚠️ Common Mistakes to Avoid

| Mistake | Why Wrong | Correct Approach |
|---------|-----------|------------------|
| Confusing $P(A \mid B)$ with $P(B \mid A)$ | Different denominators → prosecutor's fallacy | → Always write full formula: $P(A \mid B) = P(A \cap B)/P(B)$ |
| Assuming independence without testing | $P(A \cap B) \neq P(A)P(B)$ for dependent events | → Test: $P(A \cap B) \stackrel{?}{=} P(A)P(B)$ |
| Ignoring base rates in Bayes' Theorem | High $P(B \mid A)$ ≠ high $P(A \mid B)$ if $P(A)$ small | → Always include $P(A)$ (prior) in calculation |
| Treating sample as population | Sample statistics vary due to randomness | → Acknowledge sampling variability (Ch 5) |

---

## 🌊 Titanic Probability Cheat Sheet

| Question | Formula | Calculation | Answer |
|----------|---------|-------------|--------|
| What % survived? | $P(\text{survived})$ | $342/891$ | **38.4%** |
| What % of females survived? | $P(\text{survived} \mid \text{female})$ | $233/314$ | **74.2%** |
| What % of males survived? | $P(\text{survived} \mid \text{male})$ | $109/577$ | **18.9%** |
| Among survivors, what % female? | $P(\text{female} \mid \text{survived})$ | $233/342$ | **68.1%** |
| Are sex & class independent? | $P(\text{female} \cap \text{1st}) \stackrel{?}{=} P(\text{female})P(\text{1st})$ | $0.106 \neq 0.085$ | **NO** |

> 💡 **Key Insight**:  
> EN: $P(\text{survived} \mid \text{female}) = 74.2\%$ ≠ $P(\text{female} \mid \text{survived}) = 68.1\%$  
> FR: $P(\text{survécu} \mid \text{femme}) = 74.2\%$ ≠ $P(\text{femme} \mid \text{survécu}) = 68.1\%$  
> ZH: $P(\text{生还} \mid \text{女性}) = 74.2\%$ ≠ $P(\text{女性} \mid \text{生还}) = 68.1\%$

---


## 🔗 Connection to Chapter 2

| Ch 2 Concept | Ch 3 Application |
|--------------|------------------|
| Proportions | → $P(A)$ = proportion of outcomes in event $A$ |
| Frequency tables | → Joint/marginal/conditional probabilities |
| Categorical summaries | → Foundation for probability models (Ch 4) |

> 💡 **Golden Thread**:  
> *"Descriptive statistics (Ch 2) → Probability models (Ch 3) → Statistical inference (Ch 5+)"*  
> → 描述性统计（第2章）→ 概率模型（第3章）→ 统计推断（第5章+）

---

## 🔗 Preview of Chapter 4

Chapter 4 applies Ch 3 foundations to specific distributions:
- **Binomial**: Counts of successes (e.g., survivors in sample of size $n$)
- **Normal**: Continuous symmetric variables (e.g., `age` after transformation)
- **Key bridge**: Ch 3 rules → Ch 4 distributions → Ch 5 inference

> 📌 **Memory Aid**:  
> *"Probability is the language of uncertainty — master it to speak statistics fluently"*  
> → 概率是不确定性的语言 —— 掌握它才能流利地说统计学