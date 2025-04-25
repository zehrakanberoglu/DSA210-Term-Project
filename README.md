# DSA210-Term-Project
I am Zehra Kanberoğlu, a student at Sabanci University. In my DSA210 term project I decided to analyze my daily screen time data from both of my phone and computer, particularly the types of applications I use, such as social media and entertainment apps. In the second part, I will analyze my study habits, including total daily study time, the number of study sessions, and how frequently I check my devices while studying.  I will track my screen time on both my phone and computer, but I will manually collect all the data using an Excel format.

## CONTENTS
- [Motivation](##motivation)
- [Project Goal](##projectgoal)
- [Data Source](##datasource)
- [Files](##files)
- [Requirements](##requirements)
- [Code](##code)
- [Findings and Visualizations](##findingsandvisualizations)

## MOTIVATION
As a university student who struggles to balance academic responsibilities with digital distractions, I often find myself thinking how my device usage affects my study habits. With increasing screen time, I suspect that my focus and productivity are being negatively impacted. My aim in maintaining this project is to gain a deeper understanding of how my daily screen time influence my study behavior. Specifically, I want to determine if increased screen time correlates with reduced study duration, fewer study sessions, or increased phone-checking frequency during study periods. 

## PROJECT GOAL
The goal of this project is to explore relatioship between screen time and study efficiency. I want to determine and create a balance between device spending time and studying time. I will collect the screen time and study behaviour data manually. By analyzing this data, I hope to identify patterns that could help optimize study habits and manage digital distractions effectively.

## DATA SOURCE
All sata was manually collected by me over a few weeks. I tracked:
-Daily phone screen time
-Daily computer screen time
-Daily study time
-Daily number of study 
-Number of time I checked my phone during study
The data is recorded in `raw_data.2.xlsx`.
All project file is directly included below under the ##CODE section.

## FILES
- `raw_data.2.xlsx`: Manually collected data.

## REQUIREMENTS
This project requires the following Python Libraries:
-pandas
-matplotlib
-seaborn
-scipy
-openpyxl
You can install all required libraries manually by running the following command:
pip install pandas matplotlib seaborn scipy openpyxl


## CODE

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from scipy.stats import pearsonr

# Load data
df_raw = pd.read_excel('raw_data.2.xlsx', engine='openpyxl')

# Set proper headers
new_header = df_raw.iloc[0]
df = df_raw[1:].copy()
df.columns = new_header

# Rename columns
df.rename(columns={
    'Date': 'Date',
    'Phone Time/minute': 'Phone_Time_min',
    'Computer Time/minute': 'Computer_Time_min',
    'Study Time/minute': 'Study_Time_min',
    'Distraction by Phone': 'Phone_Distractions',
    'Study Session': 'Study_Sessions'
}, inplace=True)

# Convert date
df['Date'] = pd.to_datetime(df['Date'], dayfirst=True)

# Convert numeric columns
for col in ['Phone_Time_min', 'Computer_Time_min', 'Study_Time_min', 'Phone_Distractions', 'Study_Sessions']:
    df[col] = pd.to_numeric(df[col], errors='coerce')

# Total screen time
df['Total_Screen_Time_min'] = df['Phone_Time_min'] + df['Computer_Time_min']

# EDA
print(df.describe())
print(df.isnull().sum())

plt.figure(figsize=(12,6))
plt.plot(df['Date'], df['Phone_Time_min'], label='Phone Time')
plt.plot(df['Date'], df['Computer_Time_min'], label='Computer Time')
plt.plot(df['Date'], df['Study_Time_min'], label='Study Time')
plt.legend()
plt.xlabel('Date')
plt.ylabel('Minutes')
plt.title('Screen Time and Study Time Over Time')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

#bar plot
plt.figure(figsize=(12,6))
sns.barplot(x=df['Date'].dt.strftime('%d-%m'), y=df['Total_Screen_Time_min'])
plt.xticks(rotation=45)
plt.title('Daily Total Screen Time')
plt.xlabel('Date')
plt.ylabel('Minutes')
plt.show()


# Scatter plot: Computer Time vs Study Time
plt.figure(figsize=(8,6))
sns.scatterplot(x=df['Computer_Time_min'], y=df['Study_Time_min'])
plt.title('Computer Time vs Study Time')
plt.xlabel('Computer Time (min)')
plt.ylabel('Study Time (min)')
plt.show()


# Correlation matrix
plt.figure(figsize=(10,8))
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
plt.title('Correlation Matrix')
plt.show()

# Hypothesis Tests
r1, p1 = pearsonr(df['Total_Screen_Time_min'], df['Study_Time_min'])
r2, p2 = pearsonr(df['Phone_Distractions'], df['Study_Time_min'])
r3, p3 = pearsonr(df['Phone_Time_min'], df['Study_Sessions'])

print(f"Total Screen Time vs Study Time: r = {r1:.3f}, p-value = {p1:.4f}")
print(f"Phone Distractions vs Study Time: r = {r2:.3f}, p-value = {p2:.4f}")
print(f"Phone Time vs Study Sessions: r = {r3:.3f}, p-value = {p3:.4f}")
```

## FINDINGS AND VISUALIZATIONS
In the code I write in the below creates different kind of graphs to support my hypothesis. 

1) Screen Time and Study Time (LINE PLOT):
We can see in the Line Plot which shows the relationship between Phone-Computer Time and Study Time over the data collection period. There are some noticeable fluctuations across days. On some days, when screen time increased especially phone time, study time tended to decrease. This visual supports the hypothesis that increased screen time negatively affects study efficiency. The inverse relationship between screen time and study time is visible through these trends.

2) Daily Total Screen Time (BAR PLOT):
This bar graph illustrates the total screen time (phone + computer) for each recorded day. Certain days stand out with significantly higher total screen time, highlighting periods of heavier digital device usage. By identifying high screen time days and comparing them with corresponding study time, it is possible to observe patterns that support the idea that more screen time reduces available time and focus for studying.

3) Computer Time vs. Study Time (SCATTER PLOT):
This scatter plot shows the relationship between daily computer screen time and study time. There appears to be a mild positive trend: on days when computer time increases, study time often increases as well. This suggests that some of the computer usage might be study-related rather than purely for entertainment. Unlike phone usage, computer time does not seem to purely distract from studying. Instead, moderate to high computer usage might correlate with more study activity, possibly because students (including myself) often study using their computers for assignments, readings, or coding tasks. In this graph we can see that device screen time being increased does not always negatively correlated with the study time.

4) CORRELATION MATRIX (HEATMAP):
This heatmap shows the correlation coefficients between all numerical variables in the dataset. It visually represents how strongly two variables are linearly related, with values ranging from -1 (strong negative correlation) to +1 (strong positive correlation). There is a moderate to strong negative correlation between Total Screen Time and Study Time, indicating that as screen time increases, study time tends to decrease. There is a positive correlation between Computer Time and Study Time, which may suggest that computer usage is often linked to studying activities. Phone Distractions show a negative relationship with Study Time, implying that frequent checking of the phone is associated with reduced study time. This visual directly supports the project's main hypothesis. Additionally, it refines the hypothesis by revealing that not all screen time is equally distracting: Phone usage appears more harmful (due to stronger negative correlation), while computer usage may sometimes be study-related, as shown by its positive relationship with study time.


 
