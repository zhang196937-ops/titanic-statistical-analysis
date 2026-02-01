# 变量类型与可视化图表映射指南
## Variable Type → Visualization Mapping Guide

> 📚 **依据**: OpenIntro Statistics 4th Ed, Ch 1-2  
> 💡 **核心原则**: *"Match chart type to variable type — mismatched charts mislead interpretation"*

## 📊 推荐映射表

| 变量类型 | 英文 | 中文 | 推荐图表 | Seaborn 函数 | Titanic 示例 |
|----------|------|------|----------|--------------|--------------|
| **Binary** | Categorical-Binary | 二元分类型 | 条形图 | `countplot(x=var)` | `survived`, `alone` |
| **Ordinal** | Categorical-Ordinal | 有序分类型 | 有序条形图 | `countplot(x=var, order=[...])` | `pclass` (order=[1,2,3]) |
| **Nominal** | Categorical-Nominal | 名义分类型 | 条形图 | `countplot(x=var)` | `sex`, `embarked` |
| **Discrete** | Numerical-Discrete | 离散数值型 | 条形图 (唯一值≤10) | `countplot(x=var)` | `sibsp`, `parch` |
| **Continuous** | Numerical-Continuous | 连续数值型 | 直方图 + 箱线图 | `histplot(x=var)` + `boxplot(y=var)` | `age`, `fare` |

## ⚠️ 常见错误

| 错误做法 | 问题 | 正确做法 |
|----------|------|----------|
| 用直方图展示 `sex` | 无意义分箱 | → 条形图 (`countplot`) |
| 用条形图展示 `age` | 200+个条形 → 信息过载 | → 直方图 (`histplot`) |
| `pclass` 不指定 `order` | 按字母序 (3rd,1st,2nd) → 掩盖趋势 | → `order=[1,2,3]` |
| 仅用直方图展示 `fare` | 难以识别异常值 | → 直方图 + 箱线图组合 |