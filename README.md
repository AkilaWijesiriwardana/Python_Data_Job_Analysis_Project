# The Analysis

## 1. What are the most demanded skills for the top 3 popular data roles?

To identify the most in-demand skills, the top three most commonly posted data job roles were filtered based on job listing frequency. For each role, the five most frequently mentioned skills were extracted to get a better idea of what employers are really looking for. This makes it easier to focus on the right skills depending on the role being targeted.

Detailed steps and analysis can be found in the notebook: [2_Skill_Demand.ipynb](2_Project\2_Skill_Demand.ipynb)

### Visualizing Data
```python
fig, ax = plt.subplots(len(job_titles), 1)

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short']==job_title].head(5)
    sns.barplot(data=df_plot, y='job_skills',x='skills_percentage', ax=ax[i], hue='skills_percentage', palette='dark:r_r')
    sns.set_theme(style='ticks')
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].legend().remove()
    ax[i].set_xlim(0, 78)

    for n, v in enumerate(df_plot['skills_percentage']):
        ax[i].text(v + 1, n, f'{v:.0f}%', va = 'center')
    
    if i != len(job_titles) -1:
        ax[i].set_xticks([])
    
plt.suptitle('Likelihood of Skills Requested in Job Postings', fontsize = 15)
plt.tight_layout(h_pad=0.5)
plt.show()
```

### Results

![Visualization of most Demanded Skills of Top Data Roles](2_Project/images/Skill_Demand.png)
*Visualization of Most In-Demand skills of Top Data Roles.*

### Insights

#### *Core Skills Across All Roles*

**✅ SQL is the most consistently in-demand skill, appearing prominently for all three roles:**

* 51% for Analysts, 68% for Engineers, and 51% for Scientists.

**Python is essential across the board:**

* Particularly dominant in Data Science (72%) and Engineering (65%), and still relevant for Analysts (27%).

**These two skills (SQL + Python) form the foundational technical stack for data professionals.**


**📊 Data Analyst – Focus on Business Tools & Reporting**


* Strong emphasis on Excel (41%) and Tableau (28%), showing the importance of data visualization and reporting.

* Lower demand for advanced programming (Python 27%) and statistical tools (SAS 19%).

* *Key Takeaway: Analysts often serve as the bridge between data and business, relying more on tools that enable communication and insight presentation.*


**🛠️ Data Engineer – Focus on Infrastructure & Scalability**


*Strong technical requirements:*

* SQL (68%) and Python (65%) dominate

* Cloud platforms like AWS (43%) and Azure (32%)

* Big data tools like Spark (32%)

*Engineers need skills in data pipelines, cloud infrastructure, and distributed systems.*

*Key Takeaway: Data Engineers are builders, needing both programming and cloud ecosystem knowledge to manage large-scale data systems.*


**🧪 Data Scientist – Focus on Modeling & Analytics**


* Python (72%) is the top skill, showing its dominance in data science workflows

* R (44%) is notable for statistical modeling and research-heavy roles

* SQL (51%) remains important for querying data

* Tools like SAS (24%) and Tableau (24%) are less critical, but still present

*Key Takeaway: Data Scientists require strong programming and statistical skills to extract insights, build models, and contribute to decision-making.*


## 1. How are in-demand Skills trending for Data Analysts?

### Visualizing Data

``` python

df_plot = df_DA_US_percent.iloc[:, :5]
sns.set_theme(style='ticks')
sns.lineplot(data=df_plot, dashes = False, palette='tab10')
sns.despine()

plt.title('Trending Top Skills for Data Analysts in the US')
plt.ylabel('Likelihood in Job Posting')
plt.xlabel('2023')
plt.legend().remove()


from matplotlib.ticker import PercentFormatter
plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.text(11.4, df_plot.iloc[-1, 0],df_plot.columns[0])
plt.text(11.4, df_plot.iloc[-1, 1],df_plot.columns[1])
plt.text(11.4, df_plot.iloc[-1, 2],df_plot.columns[2])
plt.text(11.1, df_plot.iloc[-3, 3],df_plot.columns[3])
plt.text(11.4, df_plot.iloc[-1, 4],df_plot.columns[4])

plt.tight_layout()
plt.show()

```

### Results

![Trending Top-Skills for Data Analysts in the US](2_Project/images/Skill_Trend.png)
*Linegraph Visualizing the trending top skills for Data Analysts in the US in 2023.*

### Insights

* SQL remains the most in-demand skill throughout the year, maintaining above 50% likelihood in job postings, though slightly dipping in Q4.

* Excel stays consistently important, showing a steady presence around 40–42%, with a small dip in October–November and a bounce back in December.

* Tableau and Python trend closely together, with Tableau slightly leading for most of the year, except a crossover in late summer.

* Python maintains stable demand around 26–29%, showing its consistent value across the year.

* SAS remains the least requested skill, with likelihood hovering around 20%, showing a steady but lower relevance in the market.

**📈 Notable Changes**

* Excel shows a noticeable dip in October–November, possibly due to a shift in reporting tools or role requirements late in the year.

* August sees a temporary spike in Tableau demand, suggesting increased need for data visualization during that period.

* Python and Tableau converge in Q4, showing that either tool could be valuable depending on the job listing.