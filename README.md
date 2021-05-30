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
![Stylesheet](Images/stylesheet.png):
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

