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


## Exploratory Data Analysis

#### Q1: Observe Movies with highest Average rating as well as with less Average rating
>>> mean_ratings = df.groupby("title")["rating"].mean().sort_values(ascending = False)

![image](https://user-images.githubusercontent.com/61958476/114348905-d109c980-9b84-11eb-8c38-2d41c65f8d6f.png)


#### Q2: How many times a movie have been watched by the critics ?
>>> df.groupby("title")['rating'].count().sort_values(ascending = False)

![image](https://user-images.githubusercontent.com/61958476/114348942-df57e580-9b84-11eb-9f12-96afdbd25973.png)

### Conclusion:
Star wars which was released in 1977 was one the highest grossing movies of all time with box-office of 777 Milion $, So it is highly watched by critics and similar to that we can observe some movies like Return of Jedi , Liar Liar , Fargo ... These all are Popular highest grossing films¶


### Q3: Now There might be Some movies that have 5 Average rating but watched by very few and some movies with less rating but watched by many peoples so how to deal with these problem ?

#### Distributions for how_many_times_movie_watched

![image](https://user-images.githubusercontent.com/61958476/114348013-94899e00-9b83-11eb-9333-18c3c1fd69fb.png)

#### Observation: So as we discused earlier that very few movies like Star wars , Liar Liar etc etc are movies which watched more than [400-500] times as we can see in histogram,and mostly movies which are flop/boaring watched very less time as we can see in graph range from (0-50)

#### Distributions for Ratings

![image](https://user-images.githubusercontent.com/61958476/114348070-ac612200-9b83-11eb-9169-582c51f36c78.png)

#### Observation: So here we can see Symmetric Distribution with most of the people are likely to give movies 3 rating as can see in given hsitogram

#### So lets combine both features and observe results

![image](https://user-images.githubusercontent.com/61958476/114348124-bf73f200-9b83-11eb-984b-805621384348.png)

#### Conclusion:
1] Here we can see some Monotonous relationship as views inc with rating inc.
2] In given plot with rating 1.0 have [0-10] views and also rating of 5.0 with [0-10] views. these movies comes under the category of Flop films.
3] In given Plot we can see that one point with 4.3 with around [550-600]. These follows monotonic relationship.eg:Highest grossing films like Aliens,Godfather,Star Wars etc etc....


### Create Movie Recommendation

def predict_movie(movie_name):
    # First step : Enter a movie name you want to find similar with
    movie_ratings = movie[movie_name]
    # Step 2 : Find Correlation of that movie
    similar_to_movie = movie.corrwith(movie_ratings)
    
    #Step 3 Create DataFrame
    corr_movie = pd.DataFrame(similar_to_movie,columns = ['Correlation'])
    #Step 4 Drop NA values
    corr_movie.dropna(inplace = True)
    
    #Step 5 Join
    corr_movie = corr_movie.join(ratings['how_many_times_movie_watched'])
    
    #Step 6: Prediction
    predictions = corr_movie[corr_movie['how_many_times_movie_watched']>100].sort_values(by = "Correlation",ascending = False)
    
    return predictions

predictions = predict_movie("Star Wars (1977)")


![image](https://user-images.githubusercontent.com/61958476/114348796-a455b200-9b84-11eb-9638-6797e5f8a76e.png)








