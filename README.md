# Netflix Content Growth Analysis

## 项目简介 | Project Overview

本项目基于 Kaggle Netflix 数据集，使用 Python、SQL 和 Power BI 对 Netflix 平台内容增长情况进行数据分析。

项目主要分析：

- Netflix 内容增长趋势
- 年增长率变化
- 电影与电视剧数量对比
- 平台发展趋势洞察

该项目主要用于展示数据分析能力，包括：

- Python 数据清洗
- SQL 数据分析
- 数据可视化
- 数据业务分析能力

---

# 数据来源 | Dataset

数据来源：Kaggle Netflix Movies and TV Shows Dataset

数据字段包括：

- show_id
- type
- title
- director
- cast
- country
- date_added
- rating
- duration
- listed_in

---

# 使用工具 | Tools

- Python
- Pandas
- Matplotlib
- SQL (SQLite)
- Power BI
- Kaggle Notebook

---

# 项目流程 | Project Workflow

## 1. 数据清洗（Python）

主要清洗内容：

- 处理缺失值
- 转换日期格式
- 提取年份信息
- 创建分析字段

```python
df['date_added'] = pd.to_datetime(
    df['date_added'].astype(str).str.strip(),
    errors='coerce'
)

df['year_added'] = df['date_added'].dt.year
```

---

## 2. SQL 增长分析

使用 SQL 对 Netflix 每年新增内容数量进行统计，并计算年度增长率。

使用到：

- GROUP BY
- COUNT()
- LAG()
- Window Function

```sql
WITH yearly_content AS (

    SELECT
        year_added,
        COUNT(show_id) AS total_content

    FROM netflix

    GROUP BY year_added
)

SELECT

    year_added,

    total_content,

    LAG(total_content) OVER (
        ORDER BY year_added
    ) AS previous_year

FROM yearly_content
```

---

## 3. Python 数据可视化

使用 Matplotlib 绘制：

- 内容增长趋势图
- 年增长率趋势图
- 电影 vs 电视剧分析

---

# 项目分析 | Analysis

## 1. Netflix 内容增长趋势分析

Netflix 平台内容数量在 2015 年后快速增长。

尤其在 2017-2019 年期间，新增内容数量明显提升，说明平台开始大规模扩张内容库。

增长趋势表明：

- 平台用户需求快速增长
- Netflix 开始全球化内容布局
- 原创内容投入增加

---

## 2. 年增长率分析

通过 SQL Window Function 中的 LAG() 函数计算年度增长率。

分析发现：

- 前期增长率较高
- 后期增长逐渐稳定
- 平台进入成熟发展阶段

说明 Netflix 已从高速扩张进入稳定运营阶段。

---

## 3. 电影 vs 电视剧分析

数据中电影数量明显高于电视剧数量。

说明：

- 电影内容上线成本较低
- 电影更适合快速扩充内容库
- 电视剧更偏向精品化运营

---
# 项目成果 | Key Insights

- Netflix 在 2015 年后进入高速增长阶段
- 平台后期增长趋于稳定
- 电影仍是主要内容形式
- 美国是核心内容来源国家
- Netflix 正逐渐推进全球化内容布局

---

# 项目截图 | Screenshots

## 内容增长趋势图

![增长趋势图](content_growth.png)

---

## 年增长率趋势图

![增长率趋势图](content_growth_rate.png)

---

## 电影 vs 电视剧分析

![电影电视剧分析](tv_vs_movie.png)

---

# 技能展示 | Skills Demonstrated

- Python 数据分析
- SQL 数据查询
- Window Function
- 数据清洗
- 数据可视化
- Power BI Dashboard
- 增长分析
- 业务分析能力

---

# 作者 | Author

HENGYIN Mai

GitHub Portfolio Project for Data Analyst
