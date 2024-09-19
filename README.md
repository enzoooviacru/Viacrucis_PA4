# PA4 - Data Wrangling and Data Visualization

#### This repository serves as the submission for Programming Assignment#4 involving 2 problems to be solved used the following libraries PANDAS library and Matplotlib or Seaborn library.

## Dependencies
#### Please download the attached `board2.xlsx` excel file before running any of the codes
#### Import pandas as pd
#### Import matplotlib.pyplot as plt
#### Import seaborn as sns
```
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

## Load "board2.xlsx" excel file
#### Use `pd.read_excel()` function to load the excel file
```
#Store the dataframe into a variable
ece = pd.read_excel("board2.xlsx")
ece
```
## Output
<img width="275" alt="PA4 LOAD" src="https://github.com/user-attachments/assets/f3e5fbc4-f148-4b28-99fb-b6081b2646aa">

# Problem 1 
#### For the first problem, filter the dataframe by its rows and columns based on the given limitations of the problem
#### The first part limits the dataframe to rows and columns which have students under the track of instrumentation, hometown in Luzon, and an electronics score of >70

## Code
```python
#Setting "Instru" as dataframe "ece" but only limited to rows where track is instrumentation, hometown is luzon, and score at electronics is >70
Instru = ece[(ece['Track']=='Instrumentation') & (ece['Hometown']=='Luzon') & (ece['Electronics']>70)]

#Displaying rows with columns "Name", "GEAS", and "Electronics" with the restrictions of the previous line for "Instru"
Instru[['Name', 'GEAS', 'Electronics']]
```
## Output
<img width="300" alt="PA4 PROBLEM1 PART1" src="https://github.com/user-attachments/assets/01986c9e-2bf0-493d-a51a-03ac70d9659d">

#### The second part limits the dataframe to rows and columns which have students who have their hometown in Mindanao, gender female, and average score of >= 55
## Code
```python
#Adding a column for the average score of each student
ece['Average'] = ece[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)

#Setting "Mindy" as dataframe "ece" but only limited to rows where hometown is Mindanao, gender is female, and average score is >=55
Mindy = ece[(ece['Hometown']=='Mindanao') & (ece['Gender']=='Female') & (ece['Average']>=55)]

#Displaying rows with columns "Name", "Track", "Electronics", and "Average" with the restrictions of the previous line for "Mindy"
Mindy[['Name', 'Track', 'Electronics', 'Average']]
```
## Output
<img width="300" alt="PA4 PROBLEM1 PART2" src="https://github.com/user-attachments/assets/99403781-24f4-4ec4-8956-0fb98a32c2af">

# Problem 2
#### For problem 2, using the Matplot library, display in bar graphs how the different features contribute to the students average score.

## Code for bar graph of Average Score by Track
```python
import matplotlib.pyplot as plt

plt.figure(figsize=(10, 5)) #Setting the size of the output figure
plt.bar(ece['Track'], ece['Average']) #Bar graph will have "Track" as the x-axis and "Average" as the y-axis
plt.title('Average Score by Track') #Giving the bar graph a title for better readability
plt.ylabel('Average Score') #Labelling the y-axis for better readability
plt.xlabel('Track') #Labelling the x-axis for better readability
```
## Output
<img width="505" alt="PA4 PROBLEM2 PART1" src="https://github.com/user-attachments/assets/6163dc2e-1c71-47a6-8a37-7365cf48fec4">

#### From the bar graph generated, microelectronics has the highest average while instrumentation has the lowest average
## Code for bar graph of Average Score by Gender
```python
plt.figure(figsize=(10, 5)) #Setting the size of the output figure
plt.bar(ece['Gender'], ece['Average']) #Bar graph will have "Gender" as the x-axis and "Average" as the y-axis
plt.title('Average Score by Gender') #Giving the bar graph a title for better readability
plt.ylabel('Average Score') #Labelling the y-axis for better readability
plt.xlabel('Gender') #Labelling the x-axis for better readability
```
## Output
<img width="507" alt="PA4 PROBLEM2 PART2" src="https://github.com/user-attachments/assets/1a0fb70f-00e3-4339-93bb-489df56c996f">

#### From the bar graph generated, females have a higher average score than males
## Code for bar graph of Average Score by Hometown
```python
plt.figure(figsize=(10, 5)) #Setting the size of the output figure
plt.bar(ece['Hometown'], ece['Average']) #Bar graph will have "Hometown" as the x-axis and "Average" as the y-axis
plt.title('Average Score by Hometown') #Giving the bar graph a title for better readability
plt.ylabel('Average Score') #Labelling the y-axis for better readability
plt.xlabel('Hometown') #Labelling the x-axis for better readability
```
## Output
<img width="507" alt="PA4 PROBLEM2 PART3" src="https://github.com/user-attachments/assets/af00f1ed-9523-4f45-861e-376270c72833">

#### From the bar graph generated, Luzon has the highest average and Mindanao has the lowest

## Observations
#### From all of the graphs, track, gender, and hometown have little influence to the average score of the students. All of the results are found to be at a range of 70-80

## Author
### Lorenzo G. Viacrucis
### 2ECE-D
