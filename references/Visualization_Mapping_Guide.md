## Variable Type → Visualization Mapping Guide

> **Source**: OpenIntro Statistics 4th Ed, Ch 1-2  
> **core principles**: *"Match chart type to variable type — mismatched charts mislead interpretation"*

## Mapping Table

| Type Variable  | English/中文          | Recommended chart                                | Seaborn function|
|----------------|----------------------|-----------|--------------------------------------|--------------------------------------|
| **Binary**     | Categorical-Binary   | 二元分类型 | bar chart/条形图                     | `sns.barplot`                        | 
| **Ordinal**    | Categorical-Ordinal  | 有序分类型 | Ordered bar chart/有序条形图         | `sns.countplot`                      |
| **Nominal**    | Categorical-Nominal  | 名义分类型 | bar chart/条形图                     | `sns.barplot`                        | 
| **Discrete**   | Numerical-Discrete   | 离散数值型 | bar chart/条形图 (唯一值≤10)         | ``sns.barplot``                       |
| **Continuous** | Numerical-Continuous | 连续数值型 | Histogram + Box Plot/直方图 + 箱线图 | `sns.histplot` + `sns.boxplot(y=var)` |


