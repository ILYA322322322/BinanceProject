# Django binance project App - ASETT Project

Introducing the 3-part technical tutorial series on building a Django project that lets users manage their cryptocurrency portfolios. The app also offers a user registration system that enables users to create an account and build their own crypto portfolio with a password reset and referral system.

👉🏻 Follow along for a more guided learning:-  


[Tutorial Series Part 1](https://atharvashah.netlify.app/blog/django-crypto-app/part1/) 


[Tutorial Series Part 2](https://atharvashah.netlify.app/blog/django-crypto-app/part2/)  


[Tutorial Series Part 3](https://atharvashah.netlify.app/blog/django-crypto-app/part3/)


**TECHNOLOGIES USED:**

- Language: Python 3.10
- Framework: Django 4.0+
- Database: SQLite [Default]
- API USED: [CoinGecko](https://www.coingecko.com/en/api/documentation) - Public Version, No API Key. Rate Limit is 10-25 req/minute
- Frontend: Bootstrap 5.1.3
- Testing: Django Test Framework
- Test Coverage: 90%+
- Development Methodology: TDD (Test Driven Development)

## How I Set Up The Project

For instructions on how to run this project on YOUR PC, see below ↘️ [How To Run This Project](#how-to-run-this-project)  

>**All steps are for a Windows 10 machine.**
>I followed these steps to set up the project:

```py
# cd into the folder where you want to create the project
cd django-crypto-app

# create a virtualenv
python -m venv env 

# activate the virtualenv
env\Scripts\activate  

# install needed packages
pip install django
pip install requests
pip install coverage

# start the django project in the current folder
django-admin startproject crypto .

# create a django app
python manage.py startapp mainapp

# make migrations (i'm sticking to the default sqlite db for now)
python manage.py makemigrations

# perform migrations to populate the db
python manage.py migrate

# create a superuser, enter username, email and password to login to the admin panel
python manage.py createsuperuser

# start the server
python manage.py runserver

# Django will start the server on port 8000 so open the browser and go to http://localhost:8000/

# Visit http://localhost:8000/admin to login to the admin panel

# I generated requirements.txt using the following command
pip freeze > requirements.txt
```

## How To Run This Project

You need app password for your email account for emailing. To know more about how to get your app password, see this [link](https://support.google.com/accounts/answer/185833?hl=en)

```py

# clone the repo
git clone https://github.com/HighnessAtharva/django-crypto-app.git

# cd into the project folder
cd django-crypto-app

# create a virtualenv
python -m venv env

# activate the virtualenv
env\Scripts\activate

# install the needed packages
pip install -r requirements.txt

# make a .env file and add the following variables
# EMAIL_HOST_USER=<your-email-here>
# EMAIL_HOST_PASSWORD=<your-app-password-here>
# See .env-example for more info, structure it in the same way as the .env-example file

# make migrations
python manage.py makemigrations
python manage.py migrate

# delete existing database if necessary, overwrite and make your own migrations and users

# create a superuser to login to the admin panel
python manage.py createsuperuser

# start the server
python manage.py runserver

```

## Docker

```py

# Ensure you have Docker Desktop installed and running

# cd into the project folder

# build the image
docker-compose build

# run the container
docker-compose up

# visit http://localhost:8000/

# stop the container
docker-compose down
```

## Database Schema

![Database Schema](https://github.com/HighnessAtharva/django-crypto-app/blob/main/assets/DB-layout.png?raw=true)

## How to Run Tests

All tests are written in the `tests.py` file in the `mainapp` folder.

```py

# to run all tests
python manage.py test

# to run tests for a specific class
python manage.py test -k <class-name>

# start coverage
coverage run --source='.' --omit=mainapp\tests.py manage.py test mainapp

# generate coverage report
coverage html

# check the htmlcov folder and open the index.html file

```

#### Coverage Report

![Coverage Report](https://github.com/HighnessAtharva/django-crypto-app/blob/main/assets/coverage.png?raw=true)

## Folder Structure and Important Files

`crypto` - The main project folder. Contains the `settings.py` file and the `urls.py` file.

`crypto\static` - Contains the static files for the project such as css, js, images, etc.

`templates` - Contains the html templates for the project. I prefer to set up templates in the root folder and configure the `TEMPLATES` setting in the `settings.py` file to point to the templates folder.

`mainapp` - The main app folder.

`mainapp\urls.py` - Contains the urls for the main app.

`mainapp\views.py` - Contains the views for the main app.

`mainapp\tests.py` - Contains the tests for the main app.

`mainapp\models.py` - Contains the models for the main app such as `Crypto` and `Portfolio`.

`mainapp\forms.py` - Contains the forms for the main app such as `CustomUserCreationForm`

`mainapp\migrations` - Contains the migrations for the main app.

`mainapp\signals.py` - Contains the `create_profile` signal once a user is created.

## Available Endpoints [URLs]

```
localhost:8000/
localhost:8000/login
localhost:8000/logout
localhost:8000/signup
localhost:8000/signup/str:referral_code
localhost:8000/portfolio
localhost:8000/search
localhost:8000/add_to_portfolio
localhost:8000/delete_from_portfolio/int:pk
localhost:8000/password_reset
localhost:8000/password_reset_done
localhost:8000/password_reset_confirm/<uidb64>/<token>
localhost:8000/password_reset_complete 
localhost:8000/admin
```

