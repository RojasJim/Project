# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here : [2.Skills_count.ipynb] (Python Project\2.Skills_count.ipynb)

### Visualize data

```python
fig, ax = plt.subplots(len(job_titles), 1)

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)[::-1]
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')

plt.show()
```
# Results 
[Visualization of top skills for Data Roles]

![alt text](image.png)

# Insights
- SQL is the most requested skill for Data Analysts and Data Scientists, with it in over half the job postings for both roles. For Data Engineers, Python is the most sought-after skill, appearing in 68% of job postings.
- Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists who are expected to be proficient in more general data management and analysis tools (Excel, Tableau).
- Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists (72%) and Data Engineers (65%).

## 2. How are in-demand skills trending for Data Analysts?

To find how skills are trending in 2023 for Data Analysts, I filtered data analyst positions and grouped the skills by the month of the job postings. This got me the top 5 skills of data analysts by month, showing how popular skills were throughout 2023.

View my notebook with detailed steps here: [3.Skills_Trend.ipynb] (Python Project\3.Skills_Trend.ipynb)

```python
sns.set_theme(style='ticks')
plot = df_percentage.iloc[:, :5]
sns.lineplot(data=plot, dashes=False, palette='tab10')
plt.title('Top 5 Skill Trends for Data Analyst in USA')
plt.xlabel('2023')
plt.ylabel('Percentage of Job Postings')
plt.xticks(rotation=45)
plt.legend().remove()
plt.gca().yaxis.set_major_formatter(mtick.PercentFormatter(decimals=0))
offsets = {
    'tableau': 0.8,
    'python': -0.8 
}
for col in plot.columns:
    last_val = plot[col].iloc[-1]
    y_pos = last_val + offsets.get(col, 0) 
    plt.text(11.1, y_pos, col, va='center')
plt.xlim(right=12.5) 
sns.despine()
plt.tight_layout()
plt.show()

```
### Results
![alt text](image-1.png)

