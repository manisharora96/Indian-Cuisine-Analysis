# Indian-Cuisine-Analysis
This Project comprises of some interesting facts and observations that people might not know about Indian cuisine.



Indian Cuisine Analysis
indianfood.jpg

Indian Cuisine consists of a variety of regional and traditional cuisines native to the Indian Subcontinent. Given the diversity in soil, climate, culture, ethnic groups, and occupations, these cuisines vary substantially and use locally available spices, herbs, vegetables, and fruits. Indian food is also heavily influenced by religion, cultural choices and traditions. Historical events such as invasions, trade relations, and colonialism have played a role in introducing certain foods to this country.

The cuisine of India is one of the world's most diverse cuisines, characterized by its sophisticated and subtle use of the many spices, vegetables, grains and fruits grown across India. The cuisine of each geographical region includes a wide assortment of dishes and cooking techniques reflecting the varied demographics of the ethnically diverse Indian subcontinent.

This notebook comprises of some interesting facts and observations that people might not know about Indian cuisine.

Table of Contents
Proportion of Vegetarian and Non-Vegetarian dishes
Number of dishes based on regions
State-wise Distribution of Indian Sweets
Number of dishes based on courses of meal
Proportion of Flavor Profiles
Ingredients used in Indian desserts
Ingredients used in South-Indian cuisine
List of Indian dishes that are sweet in flavor but not desserts
Ingredients used in North-Indian cuisine
Overall Ingredients used in Indian cuisine
Comparing preparation time and cooking time for Veg and Non Veg dishes
Maharashtra Food - Mini Infograph
Punjab Food - Mini Infograph
South Indian Cuisine Food-Mini Infograph
Ingredients used in Vegetarian food
Ingredients used in Non Vegetarian food
Top 10 snacks with shortest cooking time
Top 10 snacks with longest cooking time
Top 10 main courses with shortest cooking time
Top 10 main courses with longest cooking time
import numpy as np
import pandas as pd
import geopandas as gpd
import matplotlib.pyplot as plt
%matplotlib inline
import random
from plotly.offline import download_plotlyjs, init_notebook_mode, plot, iplot
import plotly.express as px
import plotly.graph_objects as go
import plotly.figure_factory as ff
from plotly.colors import n_colors
from plotly.subplots import make_subplots
init_notebook_mode(connected=True)
import cufflinks as cf
cf.go_offline()
from wordcloud import WordCloud , ImageColorGenerator
from PIL import Image
!python3.7 -m pip install --upgrade pip
!pip install pywaffle
from pywaffle import Waffle 
Requirement already satisfied: pip in /opt/conda/lib/python3.7/site-packages (20.3.3)
Requirement already satisfied: pywaffle in /opt/conda/lib/python3.7/site-packages (0.6.1)
Requirement already satisfied: matplotlib in /opt/conda/lib/python3.7/site-packages (from pywaffle) (3.2.1)
Requirement already satisfied: cycler>=0.10 in /opt/conda/lib/python3.7/site-packages (from matplotlib->pywaffle) (0.10.0)
Requirement already satisfied: pyparsing!=2.0.4,!=2.1.2,!=2.1.6,>=2.0.1 in /opt/conda/lib/python3.7/site-packages (from matplotlib->pywaffle) (2.4.7)
Requirement already satisfied: numpy>=1.11 in /opt/conda/lib/python3.7/site-packages (from matplotlib->pywaffle) (1.18.5)
Requirement already satisfied: kiwisolver>=1.0.1 in /opt/conda/lib/python3.7/site-packages (from matplotlib->pywaffle) (1.2.0)
Requirement already satisfied: python-dateutil>=2.1 in /opt/conda/lib/python3.7/site-packages (from matplotlib->pywaffle) (2.8.1)
Requirement already satisfied: six in /opt/conda/lib/python3.7/site-packages (from cycler>=0.10->matplotlib->pywaffle) (1.14.0)
df = pd.read_csv('../input/indian-food-101/indian_food.csv')
df=df.replace(-1,np.nan)
df=df.replace('-1',np.nan)
df.head()
name	ingredients	diet	prep_time	cook_time	flavor_profile	course	state	region
0	Balu shahi	Maida flour, yogurt, oil, sugar	vegetarian	45.0	25.0	sweet	dessert	West Bengal	East
1	Boondi	Gram flour, ghee, sugar	vegetarian	80.0	30.0	sweet	dessert	Rajasthan	West
2	Gajar ka halwa	Carrots, milk, sugar, ghee, cashews, raisins	vegetarian	15.0	60.0	sweet	dessert	Punjab	North
3	Ghevar	Flour, ghee, kewra, milk, clarified butter, su...	vegetarian	15.0	30.0	sweet	dessert	Rajasthan	West
4	Gulab jamun	Milk powder, plain flour, baking powder, ghee,...	vegetarian	15.0	40.0	sweet	dessert	West Bengal	East
df.shape
(255, 9)
The dataset consists of about 255 Indian dishes and 9 columns associated with each of them.

The 9 columns are as follows:-

name : name of the dish

ingredients : main ingredients used

diet : type of diet - either vegetarian or non vegetarian

prep_time : preparation time

cook_time : cooking time

flavor_profile : flavor profile includes whether the dish is spicy, sweet, bitter, etc

course : course of meal - starter, main course, dessert, etc

state : state where the dish is famous or is originated

region : region where the state belongs

All the observations in this notebook are based on these 255 dishes. There are many more dishes in Indian Cuisine!
