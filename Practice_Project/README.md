Scenario
Your organization is consolidating different platforms and wants to store customer communication records in a central location. As a software engineer, you are tasked to develop this Customer360 application using Django.

A communication record stores Channel, Direction (inbound or outbound) and Summary.

Objectives
Develop a screen to capture communication record
Display interaction in last 30 days
Provide professional customer management

The outline the instructions I followed to complete the project:
Ensure pip is installed.
python3.11 -m ensurepip

Install Django.
python3.11 -m pip install Django
Create a project.
django-admin startproject customer360

Change the directory so that it works in the lab.
cd customer360

Run migration before running the application for the first time.
python3.11 manage.py migrate

Run the server successfully this time.
python3.11 manage.py runserver

Changing Settings:
ALLOWED_HOSTS=["*"]
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'customer360'
]
CSRF_TRUSTED_ORIGINS = ['https://*.cognitiveclass.ai']
from pathlib import Path
import os
STATICFILES_DIRS = (
    os.path.join(BASE_DIR,"static/"),
)

Models created in Models.py:
A model is the single, definitive source of information about your data. It contains the essential fields and behaviors of the data you're storing. Generally, each model maps to a single database table.

Created Templates
add.html,base.html , index.html, interact.html, summary.html

Created views

Create URLs

Add styling

Run Application:
python3.11 manage.py makemigrations customer360
python3.11 manage.py migrate
python3.11 manage.py runserver

open on port 8000

extra changes:
add social media field to customer

