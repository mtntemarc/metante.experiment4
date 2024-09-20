# PA4 - Data Wrangling and Data Visualization

# I. Intended Learning Outcomes:
1. To identify the codes and functions needed in cleaning and visualizing data
   
2. To be able to apply and use the different codes and functions in creating a Python program that will be used in data wrangling and data visualization

# II. Instructions:
Download the ECE Board Exam 2 dataset found on this link: bit.ly/ECEBoardExamDataset and write a Python script/code in the Jupyter Notebook to do the given problems. You may submit your Jupyter notebook in the dedicated submission bin.

# ECE BOARD EXAM PROBLEM: 
Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.
1. Create the following data frames based on the format provided: Example: Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as Visayas
   
   A. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon
   
   B. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female

____________________________________________________________________________________________________________________________________________________

1. Create the following data frames based on the format provided:

```
# Start Program

# Import pandas library
import pandas as pd 


# Load the .csv file into the data frame
board = pd.read_csv('board2.csv')
```

   A. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon
```
# Filter rows where the 'Hometown' column contains 'Luzon' and the 'Track' column contains 'Instrumentation'.
# Extract all entries where the 'Electronics' score is greater than 70.

data = board.loc[(board['Hometown']=='Luzon')&(board['Track']=='Instrumentation')&(board['Electronics'] > 70)]

# Output 
Instru = data[['Name','GEAS','Electronics']]
Instru
```

Output: 


![image](https://github.com/user-attachments/assets/cec87c9d-da9d-4995-a958-b2a15ef14438)

   B. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female
```
#B. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female


# Filter rows where the 'Hometown' column has the value 'Mindanao'. Extract rows where the 'Gender' column contains 'Female'.
data2 = board.loc[(board['Hometown']=='Mindanao')&(board['Gender']=='Female')].copy() #use .copy() in order to create a duplicate dataframe

# Calculate the mean of all subject scores and create a new column in the DataFrame named 'Average'.
data2['Average'] = data2[['Math', 'Electronics', 'Communication','GEAS']].mean(axis=1)

# Retrieve all entries where the 'Average' value is 55 or higher.
Mindy = data2.loc[data2['Average']>=55]

# Output 
Mindy[['Name', 'Track', 'Electronics', 'Average']]
```
Output:


![image](https://github.com/user-attachments/assets/1e058279-303c-46e6-87d1-7722a7b97f71)


________________________________________________________________________________________________________________________________________________________________________________________
2. Create a visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?
```

# Import necessary libraries
import matplotlib.pyplot as plt
import seaborn as sns

# Calculate the mean of the specified subjects and create a new 'Average' column in the DataFrame
board['Average'] = board[['Math', 'Electronics', 'Communication', 'GEAS']].mean(axis=1)

# Set up the figure for visualizing the relation of different features to the 'Average' grade
plt.figure(figsize=(20, 10))

# Plot 1: Average Grade by Track
plt.subplot(1, 3, 1)  # First subplot in a 1x3 grid (position 1)
sns.boxplot(x='Track', y='Average', data=board, hue='Track', palette='Set2')
plt.title('Average Grade by Track')
plt.xticks(rotation=45)  # Rotate x-axis labels for better fit

# Plot 2: Average Grade by Gender
plt.subplot(1, 3, 2)  # Second subplot in a 1x3 grid (position 2)
sns.boxplot(x='Gender', y='Average', data=board, hue='Gender', palette='Set1')
plt.title('Average Grade by Gender')

# Plot 3: Average Grade by Hometown
plt.subplot(1, 3, 3)  # Third subplot in a 1x3 grid (position 3)
sns.boxplot(x='Hometown', y='Average', data=board, hue='Hometown', palette='Set3')
plt.title('Average Grade by Hometown')

# Adjust layout to prevent overlap
plt.tight_layout()

# Display the plots
plt.show()

```
Output:



![image](https://github.com/user-attachments/assets/068d3a46-ae21-49b4-9855-04dfea92ba3c)




















