# Variable Type → Visualization Mapping Guide

> **Source**: OpenIntro Statistics 4th Ed, Ch 1-2  
> **Core principal**: *"Match chart type to variable type — mismatched charts mislead interpretation"*

## 1 Univariate Analysis (Visualizing One Variable at a time)
>Goal:to understand the distribution,central tendency, and frequency of a single column
| Variable type | Chart name | Seaborn fuction | Explanation |
|----------|------|------|----------|
| Categorical-Binary |Bar chart(Count)  |sns.countplot() | Shows the frequency of two outcomes (e.g., Male vs Female). |
| Categorical-Nominal |Bar chart(Count)| sns.countplot()|Shows the count for each category. No natural order (e.g., Port S, C, Q).|
| Categorical-Ordinal |Ordered Bar chart|sns.countplot()|Shows counts while maintaining the rank (e.g., Class 1 > 2 > 3).|
|Numerical-Discrete|Frequency Plot|sns.histplot()|Shows how often specific whole numbers occur (e.g., # of Siblings).|
|Numerical-Continuous|Histogram|sns.histplot()|Groups data into "bins" to show the shape of the distribution (Skewed/Symmetric).|
|Numerical-Continuous|Boxplot|sns.boxplot()|Visualizes the Median, Quartiles, and detects Outliers.|
|Numerical-Continuous|Density Plot|sns.kdeplot()|Provides a smooth curve showing where values are most concentrated.|


## 2.Bivariate Analysis (Visualizing the Relationship between Two Variables)
>Goal: To see if one variable(variables explanatary) influences another(variable response) (Association vs. Causation).

| Variable type | Chart name | Seaborn function |Explanation|
|----------|------|----------|----------|
| Numerical vs Numerical | Scatter Plot | sns.scatterplot() |Checks for correlation or patterns between two numbers (e.g., Age vs. Fare).|
|Categorical vs. Numerical|Boxplot|sns.boxplot()|Compares the distribution of a number across groups (e.g., Age by Sex).|
|Categorical vs. Numerical|Bar Chart (Mean)|sns.barplot()|Shows the average value for each category (e.g., Average Fare per Class).|
|Categorical vs. Categorical|Heatmap|sns.heatmap()|Visualizes a "Contingency Table" to see overlap (e.g., Class vs. Survival).|

## 3. Multivariate Analysis (Adding a 3rd Variable)##
>Goal: To see how a third factor (often Binary) affects a relationship.
| Variable type | Chart name | Seaborn function |Explanation|
|----------|------|----------|----------|
|Multiple Variables|Clustered Bar Chart|sns.countplot(hue=...)|Compares groups within groups (e.g., Survival counts split by Sex).|
|Multiple Variables|Faceted Boxplot|sns.boxplot(hue=...)|Sees how a grouping variable shifts the median (e.g., Age vs Class, colored by Sex).|
|Entire Dataset|Pair Plot|sns.pairplot()|Generates a grid of charts for every numerical pair in the data at once.|












