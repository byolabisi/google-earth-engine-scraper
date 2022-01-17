# Google places scraper

## Introduction
This project was created to create a tool
that will allow to grab information about surrounding places of a certain point and store it in a structure from which we can easily take conclusion.
It can be used for data science, machine learning and .

Using this tool it is possible to enter a radius variable in which places should be checked and get information such as addresses, population by , security, ratings of restaurants and other interesting information.

## How to use it?
There are three methods to run this application:
#### 1) Running service with app image and database image with default configuration using `docker-compose` command
__NOTE__: You must have Docker and docker-compose installed.
1) Build images from docker-compose file from project folder
2) Run app with cords, radius and api_key arguments

```
docker-compose build
docker-compose run --rm scrapy scrapy crawl GooglePlacesSpider -a cords='53.4284953,14.5494097' -a radius=100 -a api_key="your api key"
```

#### 2) Running app on host machine
__NOTE__: To use this correctly you must have your own PostgreSQL database and modify settings file to use that database.
Also you must have python and pip installed.
1) Install all packages from requirements file
2) Start app locally (use the same parameters like before)
```
pip install -r requirements.txt
python -m scrapy crawl GooglePlacesSpider -a cords='53.4284953,14.5494097' -a radius=100 -a api_key="your api key"
```

#### 3) Running docker container with existing database
__NOTE__: You must have Docker installed.
1) Build image with specific name
2) Run container with database parameters that will set up connection to PostgreSQL 
(All connection params - host/port/user/pass - are supported)
```
docker build -t google-earth-engine-scraper .
docker run -e DB_NAME=db --rm google-earth-engine-scraper scrapy crawl GooglePlacesSpider -a cords='53.4284953,14.5494097' -a radius=100 -a api_key="your api key"
```
Above methods will result in scraped data into PostgreSQL database which is connected with geo-scrapper by default or by yourself.