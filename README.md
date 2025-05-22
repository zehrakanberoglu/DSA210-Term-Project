# DSA210-Term-Project
I am Zehra Kanberoğlu, a student at Sabanci University. In my DSA210 term project I decided to analyze my daily screen time data from both of my phone and computer, particularly the types of applications I use, such as social media and entertainment apps. In the second part, I will analyze my study habits, including total daily study time, the number of study sessions, and how frequently I check my devices while studying.  I will track my screen time on both my phone and computer, but I will manually collect all the data using an Excel format.

## CONTENTS
- [Motivation](#motivation)
- [Project Goal](#project-goal)
- [Data Source](#data-source)
- [Google Collab Link](#google-collab-link)
- [Files](#files)
- [Findings and Visualizations](#findings-and-visualizations)

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
- The data is recorded in `raw_data.2.xlsx`.

## GOOGLE COLLAB LINK
You can directly open and run this project on Google Collab using [this link](https://colab.research.google.com/drive/1VJFyATZyOmFEAIA3LrCj_uQbVdfqWod7?usp=drive_link).

## FILES
- `DSA210.ipynb`: Python code for data cleaning, exploratory data analysis (EDA), and hypothesis testing.
- `raw_data.2.xlsx`: Manually collected data.


## FINDINGS AND VISUALIZATIONS
In the code I write in the below creates different kind of graphs to support my hypothesis. 

1) LINE PLOT: Displays daily trends of phone time vs. study time.


2) BAR PLOT: Shows total phone screen time across days.


3) SCATTER PLOT:


4) HEATMAP:
## HYPOTHESIS TESTING AND INTERPRETATION
1) Phone Time vs Study Time:
   - Hypothesis: Increse of phone time negatively effects the study time.
   - r=0.0016, p=0.897
   - No statistically significant correlation
   - Conclusion: Daily phone screen time does not meaningfully affect study duration.
     
2) Phone Distractions vs Study Time:
   - Hypothesis: Increase the amount of study leads to more checking the phone during study time.
   - r=0.780, p<0.00001
   - Statistically significant strong correlation.
   - Interpretation: Days with longer study time may naturally involve more for distraction; this shoud not be misinterpreted as distraction increasing study time.
     
3) Weekly Exam Count vs Study Time:
   - Hypothesis: Number of weekly exams increase the study time.
   - r=0.428 , p=0.00027
   - Statistically significant moderate positive correlation
   - Interpretation: More weekly exams are associated with increased study time, supporting the hypothesis that exam number on that week leads to more study time.

5) Phone Time vs Phone Distractions:
   - Hypothesis: Higher phone screen time is associated with more frequent distractions.
   - r=0.008, p=0.946
   - No statistically significant correlation.
   - Conclusion: The amount of phone usage does not predict how frequently I check my phone during study sessions.

## MACHINE LEARNING MODEL: PREDICTING STUDY SESSIONS
In addition to hypothesis testing, a linear regression model was built to predict the number of daily study sessions using behavioral and contextual features:
- Features used: Phone Time/min, Phone Distractions, Study Time/min, Weekly Exam Count.
- Target variable: Study Sessions
Model Results:
- Mean Absolute Error (MAE): 0.336
- R² Score: 0.715
Interpretation:
This model explains approximately 71.5% of the variance in daily study session count and predicts the outcome with an average error of just 0.34 sessions. This indicates a strong predictive power, showing that screen and study behaviors, along with academic pressure, are useful indicators of study habits.
   




 
