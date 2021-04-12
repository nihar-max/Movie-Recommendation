# Movie-Recommendation System
![image](https://user-images.githubusercontent.com/61958476/114347101-17115e00-9b82-11eb-8179-9fb40d1ce3e5.png)

Data Source: https://grouplens.org/datasets/movielens/100k/

### How the Recommendation system works ?
![image](https://user-images.githubusercontent.com/61958476/114347180-2d1f1e80-9b82-11eb-864e-efc56a5e913a.png)

#### As in given eg: Here User 1 & User 2 purchase apples and Oranges so it his higher chance that we can also recommend our next user (User 3) to buy apple/orange

## Steps to do:
### Import Libraries & Load Datasets
### Exploratory Data Analysis
### Create Recommendation System


### Import Libraries & Load Dataset

import pandas as pd
import numpy as np
import warnings
warnings.filterwarnings("ignore")

col_names = ["user_id","item_id","rating","timestamp"]

df = pd.read_csv("ml-100k/u.data",sep = "\t",names = col_names)
