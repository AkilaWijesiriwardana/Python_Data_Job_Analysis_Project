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

![Visualization of most Demanded Skills of Top Data Roles](2_Project\images\Skill_Demand.png)

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