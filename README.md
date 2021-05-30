# Tracking COVID-19 cases over time #
This tutorial guides users on how to plot COVID infections over time using the library [MatplotLib](https://matplotlib.org/) and how to make an animated map of COVID infections over time using [Kepler](https://kepler.gl/).

The first part walks users through plotting COVID cases using Matplotlib in [Google Colaboratory](https://colab.research.google.com/notebooks/intro.ipynb#recent=true) whereas the second one talks about making an animated map on Kepler.

## Part 1: Using Colab to Plot Covid Cases over time ##
The data obtained for Covid cases is obtained from [The Humanitarian Data Exchange](https://data.humdata.org/dataset/novel-coronavirus-2019-ncov-cases). The CSV data file is contained in the 'Part 1 Data' folder in this repo. 

First, we start off with installing the required libraries:
```
#install required libraries
import pandas as pd
from matplotlib import pyplot as plt
```
In order to choose different styles of plotting, we can check this [Style Sheets reference](https://matplotlib.org/stable/gallery/style_sheets/style_sheets_reference.html). Below is a snippet of this webpage:

![Stylesheet](Images/stylesheet.png)

I liked the dark background so I specified in the code that I wanted the dark background. You can do this for any background you like:
```
plt.style.use('dark_background')
```
Next, we import our CSV file for the data we want to plot:
```
#import data
from google.colab import files
uploaded = files.upload()
```
I manipulated the data from the original dataset. Since I wanted to track covid cases over time for selected European countries, I made another CSV file where I filtered the data for only European countries and changed the date column to days to track Covid-19. The time period if from Jan 22,2020 to May 28,2021. A snapshot of my data file is given below:

![Filtered-data](Images/filtered-data.png)

Then we write code allowing Pandas to read the csv file and do some operations on it:
```
#read csv file
data=pd.read_csv('covid.csv')
```
We can also change and shorten column names for our ease:
```
daycount=data['Day']
FIN=data['Finland']
FRA=data['France']
DEU=data['Germany']
ITA=data['Italy']
ESP=data['Spain']
SWE=data['Sweden']
```
Then we can make a plot of confirmed cases over time for these 6 countries:
```
plt.plot(daycount,FIN,label="Finland")
plt.plot(daycount,FRA,label="France")
plt.plot(daycount,DEU,label="Germany")
plt.plot(daycount,ITA,label="Italy")
plt.plot(daycount,ESP,label="Spain")
plt.plot(daycount,SWE,label="Sweden")
```

To prevent any scientific notation on the axis, we pass the code:
```
plt.ticklabel_format(style='plain') 
```
We can set the legend, title and customize our display of the axis using the following code:
```
plt.legend()
plt.title('COVID-19 cases in European Countries')
plt.ylabel('Number of Infections')
plt.xlabel('Number of Days')
```
The following code displays the graph:
```
plt.show()
```
The output of the graph is displayed below:

![Graph](Images/graph.png)


## Part 2: Using Kepler to make an animated map of COVID infections over time ##
The data obtained for Covid cases comes from [another GitHub repo about a tutorial on Kepler](https://github.com/leighhalliday/keplergl-demo). The data can be viewed from the 'Part 2 Data' folder in my repo.

The data consists of COVID cases in different countries over a three month period from Jan 22,2020 to March 24,2020. In order to make an animated map on Kepler, the Date column in this file had to be changed to date-time column
