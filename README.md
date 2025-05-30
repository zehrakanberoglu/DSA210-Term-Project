# DSA210-Term-Project
I am Zehra Kanberoğlu, a student at Sabanci University. In my DSA210 term project I decided to analyze my daily screen time data from my phone and how it affects my study behaviours. In the second part, I will analyze my study habits, including total daily study time, the number of study sessions,how frequently I check my devices while studying and the number of exams each week.  I will track my screen time from my phone, but I will manually collect all the data using an Excel format.

## CONTENTS
- [Motivation](#motivation)
- [Project Goal](#project-goal)
- [Data Source](#data-source)
- [Google Collab Link](#google-collab-link)
- [Files](#files)
- [Methods and Analysis](#methods-and-analysis)
- [Hypothesis Testing and Interpretation](#hypothesis-testing-and-interpretation)
- [Findings and Visualizations](#findings-and-visualizations)
- [Machine Learning Model](#machine-learning-model)
- [Limitations](#limitations)
- [Future Work](#future-work)
- [Conclusion](#conclusion)

## MOTIVATION
As a university student who struggles to balance academic responsibilities with digital distractions, I often find myself thinking how my device usage affects my study habits. With increasing screen time, I suspect that my focus and productivity are being negatively impacted. My aim in maintaining this project is to gain a deeper understanding of how my daily screen time influence my study behavior. Specifically, I want to determine if increased screen time correlates with reduced study duration, fewer study sessions, or increased phone-checking frequency during study periods. 

## PROJECT GOAL
The goal of this project is to explore relatioship between screen time and study efficiency. I want to determine and create a balance between device spending time and studying time. I will collect the screen time and study behaviour data manually. By analyzing this data, I hope to identify patterns that could help optimize study habits and manage digital distractions effectively.

## DATA SOURCE
All data was manually collected by me.
- Date: Dates that i have been collected.
- Phone Time/minute:  It represents daily phone screen time.
- Weekly Exam Count: It represents the exam number in current week.
- Study time/minute: It represents daily study time
- Study Session: It represents daily number of study sessions. 
- Distraction by Phone: It represents the number of time I checked my phone during study.
- The data is recorded in `screen_study_data_full.3.csv`.

## GOOGLE COLLAB LINK
You can directly open and run this project on Google Collab using [this link](https://colab.research.google.com/drive/1WeyEwItQatVwGk-qOQ72qjR4GQq7LniN?usp=drive_link).

## FILES
- `DSA210/project.ipynb`: Python code for data cleaning, exploratory data analysis (EDA),hypothesis testing and machine learning model.
- `screen_study_data_full.3.csv`: Manually collected data.

## METHODS AND ANALYSIS
1) DATA CLEANING:
   - Converted the Date column to datetime format using pd.to_datetime
   - Converted the numeric fields to proper float values
   - Checked for and removed missing values to ensure valid correlation and modeling
   
2) EXPLORATORY DATA ANALYSIS (EDA):
   - Line Plot: Visiualized daily trends of Phone Time and Study Time to examine possible inverse patterns.
   - Bar Graph: Displayed daily Phone Time to identify high-usage days and potential distraction patterns.
   - Correlation Matrix Heatmap: Examined linear relationships among key variables: Study Time, Phone Distractions, Exam Count, Phone Time.

3) HYPOTHESIS TESTING
4) MACHINE LEARNING-PREDICTIVE ANALYSIS

## HYPOTHESIS TESTING AND INTERPRETATION
1) Phone Time vs Study Time:
   - Hypothesis: Increse of phone time negatively effects and reduces the study time.
   - r=0.007, p=0.947
   - No statistically significant correlation
   - Conclusion: Daily phone screen time does not meaningfully affect study duration.
     
2) Phone Distractions vs Study Time:
   - Hypothesis: The increased amount of study time leads to looking at the phone more while studying.
   - r=0.703, p<0.00001
   - Statistically significant strong correlation.
   - Interpretation: Days with longer study time may naturally involve more for distraction; this shoud not be misinterpreted as distraction increasing study time.
     
3) Weekly Exam Count vs Study Time:
   - Hypothesis: Increse of weekly exam numbers increase the study time.
   - r=0.426 , p=0.00001
   - Statistically significant moderate positive correlation
   - Interpretation: More weekly exams are associated with increased study time, supporting the hypothesis that exam number on that week leads to more study time.

## FINDINGS AND VISUALIZATIONS 

1) LINE PLOT: Displays daily trends of phone time vs. study time. The lines help visiulize if there is a noticable trend between the two variables. In this case, there is no consistent inverse pattern-some days with high phone time do not always correspond to low study time and vice versa. This supports statistical test which found no significant correlation between these two variables. It supports the hypothesis 1 which is overall phone usage does not strongly or directly predict how much you study on a given day.

![image](https://github.com/zehrakanberoglu/DSA210-Term-Project/blob/3ce66ccf483effb2a5e7bfde830a3a2db53a5cb2/lineplot.png)


2) BAR PLOT: This bar graph shows the total amount of phone screen time for each recorded day. It highlights which days involved the most phone usage. While it does not directly indicate how study time was affected, these high-usage days might be represent periods of higher distraction or less focus. This graph helps you visually spot possible outliers or patterns in your daily phone habits. However, as with the line plot, the lack of strong statistical correlation means we should be cautious in assuming a direct negative impact.

![image](https://github.com/zehrakanberoglu/DSA210-Term-Project/blob/9c2b0cd188a49b577bec4029785191a0ef42bc0c/bargraph.png)


3) CORRELATION MATRIX HEATMAP: This heatmap shows the strength of linear relationships between all pairs of numerical variables using correlation coefficients. The most notable finding here is a strong positive correlation between Study Time and Phone Distractions. This might initially seem counterintuitive, but it could be that the more time you spend studying, the more chances there are to get distracted. A moderate positive correlation is seen between Weekly Exam Count and Study Time, which supports the hypothesis 3, suggesting that weekly exam number increases your study effort. Phone Time itself does not have strong correlations with the study-related variables, reinforcing earlier findings.

![image](https://github.com/zehrakanberoglu/DSA210-Term-Project/blob/a7507574802a10a0231eefd05bc337d642260aae/heatmap.png)

## MACHINE LEARNING MODEL: PREDICTING STUDY SESSIONS
In addition to hypothesis testing, a Random Forest regression model was built to predict the number of daily study sessions using behavioral and contextual features:
- Features used: Phone Time/min, Phone Distractions, Study Time/min, Weekly Exam Count.
- Target variable: Study Sessions
- Model Results:
- Mean Squared Error (MSE): 0.723
- R² Score: 0.362
- Interpretation:
This model explains approximately 36.2% of the variance in daily study session count. On average, the prediction deviates by less than one session per day, which is reasonably accurate given the limited range of possible session values. While the predictive power is moderate, the results suggest that behavioral patterns, especially related to screen time and study duration, are meaningful indicators of study session frequency.
   
![image](https://github.com/zehrakanberoglu/DSA210-Term-Project/blob/e98ec860ac61e88c7fffa084dbad7a38e9fd3105/ml.png)

## LIMITATIONS
- The data was manually collected and thus subject to recall bias or human error.
- The dataset is small and covers a short time window, limiting generalizability.
- The concept of screen time was not app-specific; future data collection could benefit from tracking app categories (e.g., social media, productivity) for clearer insights.

## FUTURE WORK
- Automate screen and distraction tracking through mobile phone.
- Differentiate between productive and non-productive screen activities.
- Include contextual data (e.g., environment) to better understand distraction dynamics.

## CONCLUSION
- This project set out to examine how daily phone usage interacts with study habits among university students. Through manual data collection and exploratory analysis, key behavioral patterns were identified:
- Phone distractions during study sessions are strongly associated with longer study durations. However, this correlation should not be misinterpreted as causation—longer study periods naturally offer more chances for distraction.
- Contrary to initial assumptions, overall daily phone screen time did not significantly correlate with either study duration or the number of distractions during study. This highlights the importance of distinguishing between active distraction and passive usage when analyzing screen time.
- The number of weekly exams was moderately and positively associated with increased study time. This confirms the expectation that academic workload drives longer study efforts.
- Interestingly, no meaningful relationship was found between phone time and distraction frequency, suggesting that high screen time alone doesn't necessarily lead to more interruptions during focused work.
- A simple machine learning model was also implemented to predict daily study sessions based on behavioral and contextual factors. The model demonstrated strong predictive power, reinforcing the idea that phone usage, study duration, and exam number can together serve as reliable indicators of study behavior.

 
