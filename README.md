bash
investment_website/
(link unavailable)
(link unavailable)
(link unavailable)
templates/
base.html
home.html
login.html
register.html
invest.html
static/
css/
js/
img/
requirements.txt
(link unavailable)
database.db

(link unavailable) (Flask App):

from flask import Flask, render_template, request, redirect, url_for
from flask_sqlalchemy import SQLAlchemy
from models import User, Investment

app = Flask(name)
app.config.from_object('config')
db = SQLAlchemy(app)

@app.route('/')
def home():
    return render_template('home.html')

@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        # Login logic
        pass
    return render_template('login.html')

@app.route('/register', methods=['GET', 'POST'])
def register():
    if request.method == 'POST':
        # Registration logic
        pass
    return render_template('register.html')

@app.route('/invest', methods=['GET', 'POST'])
def invest():
    if request.method == 'POST':
        # Investment logic
        pass
    return render_template('invest.html')

if name == 'main':
    app.run(debug=True)

(link unavailable) (Database Models):

from flask_sqlalchemy import SQLAlchemy

db = SQLAlchemy(app)

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(64), unique=True, nullable=False)
    email = db.Column(db.String(120), unique=True, nullable=False)
    password = db.Column(db.String(128), nullable=False)

class Investment(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    user_id = db.Column(db.Integer, db.ForeignKey('(link unavailable)'), nullable=False)
    investment_type = db.Column(db.String(64), nullable=False)
    amount = db.Column(db.Float, nullable=False)

(link unavailable) (URL Routing):

from app import app
from models import User, Investment

@app.route('/user/<int:user_id>')
def user_profile(user_id):
    user = User.query.get(user_id)
    return render_template('user_profile.html', user=user)

@app.route('/investment/<int:investment_id>')
def investment_details(investment_id):
    investment = Investment.query.get(investment_id)
    return render_template('investment_details.html', investment=investment)

templates (HTML Files):

Create the following HTML files in the templates directory:

1. base.html (layout)
2. home.html (homepage)
3. login.html (login page)
4. register.html (registration page)
5. invest.html (investment page)
6. user_profile.html (user profile page)
7. investment_details.html (investment details page)

Static Files (CSS, JS, Images):

Create the following directories and files in the static directory:

1. css/
    - style.css
2. js/
    - script.js
3. img/
    - logo.png

(link unavailable) (Configuration File):

import os

SECRET_KEY = os.urandom(24)
SQLALCHEMY_DATABASE_URI = 'sqlite:///database.db'
SQLALCHEMY_TRACK_MODIFICATIONS = False

Database Setup:

Run the following commands to create the database:

bash
flask db init
flask db migrate
flask db upgrade
