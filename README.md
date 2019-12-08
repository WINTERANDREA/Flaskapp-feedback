#CREATE A PYTHON VIRTUAL ENVIRONMENT
pip install pipenv

#RUN THE VIRTUAL ENVIRONMENT
pipenv shell

#INSTALL ALL THE PACKAGES WE NEED
pipenv install flask
pipenv install request
pipenv install psycopg2 (database adaptor in order to work with Postgres)
pipenv install flask-sqlalchemy (abstract layer allows to work with db model similar to mangoose)
pipenv install gunicorn (http server needed to deploy to Heroku)

#SELECT VS PYTHON INTERPRETER
python 3.8 flaskapp_feedback

#CREATE FOLDERS AND FILES
static (logo.png, css.style)
template (index.html, success.html)

#CREATE APP.PY FILE
from flask import Flask, render_template (renderhtml file), request (deal with request parameter)

#INITIALIZE FLASK APP
<!-- app=Flask(__name__) -->

#CREATE ROUTE AND DEFINE FUNCTION

#RUN SERVER WITH IF STATEMENT 
<!-- 
if __name__ == '__main__':
app.run() 
-->

#ADD DEBUG MODE TO KEEP RELOADING SERVER (ONLY DURING DEVELOPMENT)
<!-- 
if __name__ == '__main__':
app.debug= True
app.run()
-->


#SQL ALCHEMY
from flask_sqlalchemy import SQLAlchemy

#INSTALL POSTGRESQL AND CREATE NEW DATABASE

#CREATE DB VARIABLE TO DIFFERENTATE DEV DB TO PRODUCTION DB

#CREATE DATABASE OBJECT 
<!-- 
db = SQLAlchemy(app)

class Feedback(db.Model):
    __tablename__ = 'feedback'
    id = db.Column(db.Integer, primary_key=True)
    customer = db.Column(db.String(200), unique=True)
    dealer = db.Column(db.String(200))
    rating = db.Column(db.Integer)
    comments = db.Column(db.Text())

    def __init__(self, customer, dealer, rating, comments):
        self.customer = customer
        self.dealer = dealer
        self.rating = rating
        self.comments = comments
 -->

 #CREATE DB TABLE BASED ON APP MODEL
<!--  
open up python terminal
 >>> from app import db
 >>> db.create_all()
 >>> exit() 
 -->

#EMAIL DB DATA
<!-- 
create new file send_mail.py
add to app.py -> from send_mail import send_mail 
-->

#DEPLOY ON HEROKU
<!-- create an account on heroku.com
install on your machine heroku cli
create a new file .gitignore
initialize within the terminal a git repository:
1) git init
2) check heroku is installed -> heroku --version
3) heroku login 
4) create heroku application -> heroku create flaskapp-feedback
5) create postgresql database on heroku -> heroku addons:create heroku-postgresql:hobby-dev --app flaskapp-feedback
6) get heroku database url -> heroku config --app flaskapp-feedback
7) paste the url inside app.py file in the app.config variable (production database)
8) change dev mode to production
9) create a new file -> Procfile and insert -> web: gunicorn app:app
10) create a new file to tell which python version use -> runtime.txt and insert -> python-3.8.0
11) create requirements.txt to include all the packages needed by the application -> pip freeze > requirements.txt
12) add all to git repository -> git add . && git commit -m 'Initial deploy'
-->


