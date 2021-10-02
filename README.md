# TECH-A-THON-PREDICTOR

![Python](https://img.shields.io/badge/Python-3.8-blueviolet)
![Framework](https://img.shields.io/badge/Framework-Flask-red)
![Frontend](https://img.shields.io/badge/Frontend-HTML/CSS/JS-green)
![API](https://img.shields.io/badge/API-TMDB-fcba03)

This application provides all the details of the requested movie such as overview, genre, release date, rating, runtime, top cast, reviews, recommended movies, etc.

The details of the movies(title, genre, runtime, rating, poster, etc) are fetched using an API by TMDB, https://www.themoviedb.org/documentation/api, and using the IMDB id of the movie in the API, I did web scraping to get the reviews given by the user in the IMDB site using `beautifulsoup4` and performed sentiment analysis on those reviews.

## Link to the application

Check out the live demo: https://still-coast-69612.herokuapp.com/


## How to get the API key?

Create an account in https://www.themoviedb.org/, click on the `API` link from the left hand sidebar in your account settings and fill all the details to apply for API key. If you are asked for the website URL, just give "NA" if you don't have one. You will see the API key in your `API` sidebar once your request is approved.

## How to run the project?

1. Clone this repository in your local system.
2. Install all the libraries mentioned in the [requirements.txt](https://github.com/kishan0725/The-Movie-Cinema/blob/master/requirements.txt) file with the command `pip install -r requirements.txt`.
3. Replace YOUR_API_KEY in **both** the places (line no. 23 and 43) of `static/recommend.js` file.
4. Open your terminal/command prompt from your project directory and run the `main.py` file by executing the command `python main.py`.
5. Go to your browser and type `http://127.0.0.1:5000/` in the address bar.
6. Hurray! That's it.

### Sources of the datasets 

1. [IMDB 5000 Movie Dataset](https://www.kaggle.com/carolzhangdc/imdb-5000-movie-dataset)
2. [The Movies Dataset](https://www.kaggle.com/rounakbanik/the-movies-dataset)
3. [List of movies in 2018](https://en.wikipedia.org/wiki/List_of_American_films_of_2018)
4. [List of movies in 2019](https://en.wikipedia.org/wiki/List_of_American_films_of_2019)
5. [List of movies in 2020](https://en.wikipedia.org/wiki/List_of_American_films_of_2020)

## THIS MODALS CONSISTS OF FOLLOWING JUPYTER FILES:- 
### 1. Preprocessing 1.ipynb :- 
In this file we import movie data from (movie_metadata.csv(This file contains the data from the year <= 2016)) and we collecting only 'director_name','actor_1_name','actor_2_name','actor_3_name','genres','movie_title' from the csv file for comparision. 
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(245).png" align="centre">
and stores all this to data named named variable and also repalced the the null names of actors and directors to unknown and convets data to csv file.

### 2. Preprocessing 2.ipynb :- 
In this file we import two csv files (credits.csv and movies_metadata.csv) and the data of these files in two diffrent variables and takinfg the value of year from the movies_metadata.csv and storing the year in list form after that we taking the ('genres','id','title','year') from the movies_metadata.csv and storing these values in the variable having year <=2017 after which we merge the data of variables containes the credit and movies_metadata csv file on another variable(named data) with refrence of id.
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(259).png" align="centre">
After which we listing the genres values with refrence of name and also collecting actor_1,actor_2 and actor_3 name from cast and director_name from crew in data 
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(262).png" align="centre">
and listing all of them with refrence of names and then storing all these values('director_name','actor_1_name','actor_2_name','actor_3_name','genres_list','title') in another variable named (movie)
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(260).png" align="centre">
and in combining all these values to make a single column and appending this cloumn to previous variable movie
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(261).png" align="centre">
and after this we drop all duplicates from movie_title(which renamed from title column) and convert this to movie.csv.

### 3. Preprocessing 3.ipynb :- 
In this file we are collectiong the values of movie nme of year 2018 and 2019 seperately from wikipedia 
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(263).png" align="centre">
and the genres through API 
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(264).png" align="centre">
and mering 2018 and movie.csv file in 2019 year movies
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(265).png" align="centre"> 
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(266).png" align="centre">
and drop the null values then makes final_data.
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(267).png" align="centre">

### 4. Preprocessing 4.ipynb :- 
In this file we are doning the same thing for collection 2020 movies and appending all previous movies upto 2019
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(268).png" align="centre">
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(269).png" align="centre">
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(270).png" align="centre">
in this file and makes main_data.csv

### 5. Sentiment.ipynb :- 
this is our filnal file where we make our modal with maximum accuracy score of 
98.77167630057804 with the help of Multinomial naive bayes and completes our modal 
filename = 'nlp_model.pkl'.
<img src="https://github.com/nikhilGupta1209/Predictor/blob/main/notebook%20screenshots/Screenshot%20(271).png" align="centre">
filename = 'nlp_model.pkl'.
    
    
    
## FEASIBILITY AND APPLICABILITY:
### 1. USABILITY:
Search for a Movie and gain knowledge about the movie and its cast.
Get recommendations for the movies.
### 2. SPECIFY FEATURES:
The main feature of the app is that it shows all the movie recommendations related to our input given.
### 3. SCALABILITY:
This project can actually be used at a product-level scale and can come in handy. We can include more filters options which can make searching more extensive.
### 4. HOW REALISTIC TO ACHIEVE/MAKE:
Our app is not just a theoretical idea rather it a full scale app which can be put into production stage and everyone can use it.
### 5. ECONOMIC SUSTAINABILITY:
We have made our app in such a way so that it could be as economical as possible.
Till now the app is completely build without spending any money as we have used all free resources.
### 6. ENVIRONMENT SUSTAINABILITY:
Our project does not harm environment in any aspect and it totally user friendly as we don't take any information from our user or store their information.
### 7. ANY THREAT/RISK/PROBLEM THAT YOU CAN FORESEE?:
There are always controversies regarding the movie app but this app should not include any risk as we are just using information which are provided in an open to use API source. (https://www.themoviedb.org)
### 8. ANY IMPROVEMENT IN YOUR PROJECT YOU FORESEE TO IMPLEMENT IN FUTURE:
We are planning to add some additional features and make it more appealing in terms of UI.
We are planning to use dialouge flow as a chat bot which will be trained to help users. 

    
Please do ⭐ the repository, if it helped you in anyway.
