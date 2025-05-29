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
   - Hypothesis: Increse of phone time negatively effects the study time.
   - r=0.007, p=0.947
   - No statistically significant correlation
   - Conclusion: Daily phone screen time does not meaningfully affect study duration.
     
2) Phone Distractions vs Study Time:
   - Hypothesis: Increase the amount of study leads to more checking the phone during study time.
   - r=0.703, p<0.00001
   - Statistically significant strong correlation.
   - Interpretation: Days with longer study time may naturally involve more for distraction; this shoud not be misinterpreted as distraction increasing study time.
     
3) Weekly Exam Count vs Study Time:
   - Hypothesis: Number of weekly exams increase the study time.
   - r=0.426 , p=0.00001
   - Statistically significant moderate positive correlation
   - Interpretation: More weekly exams are associated with increased study time, supporting the hypothesis that exam number on that week leads to more study time.

## FINDINGS AND VISUALIZATIONS 

1) LINE PLOT: Displays daily trends of phone time vs. study time. The lines help visiulize if there is a noticable trend between the two variables. In this case, there is no consistent inverse pattern-some days with high phone time do not always correspond to low study time and vice versa. This supports statistical test which found no significant correlation between these two variables. t suggests that overall phone usage does not strongly or directly predict how much you study on a given day.


2) BAR PLOT: This bar graph shows the total amount of phone screen time for each recorded day. It highlights which days involved the most phone usage. While it does not directly indicate how study time was affected, these high-usage days might be represent periods of higher distraction or less focus. This graph helps you visually spot possible outliers or patterns in your daily phone habits. However, as with the line plot, the lack of strong statistical correlation means we should be cautious in assuming a direct negative impact.


3) CORRELATION MATRIX HEATMAP: This heatmap shows the strength of linear relationships between all pairs of numerical variables using correlation coefficients. The most notable finding here is a strong positive correlation between Study Time and Phone Distractions. This might initially seem counterintuitive, but it could be that the more time you spend studying, the more chances there are to get distracted. A moderate positive correlation is seen between Weekly Exam Count and Study Time, suggesting that exam pressure increases your study effort.
Phone Time itself does not have strong correlations with the study-related variables, reinforcing earlier findings.


## MACHINE LEARNING MODEL: PREDICTING STUDY SESSIONS
In addition to hypothesis testing, a Random Forest regression model was built to predict the number of daily study sessions using behavioral and contextual features:
- Features used: Phone Time/min, Phone Distractions, Study Time/min, Weekly Exam Count.
- Target variable: Study Sessions
- Model Results:
- Mean Squared Error (MSE): 0.723
- R² Score: 0.362
- Interpretation:
This model explains approximately 36.2% of the variance in daily study session count. On average, the prediction deviates by less than one session per day, which is reasonably accurate given the limited range of possible session values. While the predictive power is moderate, the results suggest that behavioral patterns, especially related to screen time and study duration, are meaningful indicators of study session frequency.
   




 
