
**General Notes**

An `onlinecourse` app has already been provided in this repo upon which you will be adding a new assesement feature.

- If you want to develop the final project on Theia hosted by [IBM Developer Skills Network](https://labs.cognitiveclass.ai/), you will need to create the same project structure on Theia workspace and save it everytime you close the browser
- Or you could develop the final project locally by setting up your own Python runtime and IDE
- Hints for the final project are left on source code files
- You may choose any cloud platform for deployment (default is IBM Cloud Foundry)
- Depends on your deployment, you may choose any SQL database Django supported such as SQLite3, PostgreSQL, and MySQL (default is SQLite3)

**ER Diagram**
For your reference, we have prepared the ER diagram design for the new assesement feature.

![Onlinecourse ER Diagram](https://github.com/ibm-developer-skills-network/final-cloud-app-with-database/blob/master/static/media/course_images/onlinecourse_app_er.png)

Final Project: Add a New Assessment Feature to an Online Course Application

As a newly onboarded full-stack developer, your lead developer has entrusted you with implementing a new course assessment feature. To successfully deliver this feature, you will use your Django full-stack skills to design and develop the necessary models, templates, and views. Finally, you will run and thoroughly test your online course application to ensure its functionality.

Set-up: Create an Application
Run the following command to clone the Git repository that contains the starter code needed for this project, if the Git repository doesn't already exist.
[ ! -d 'tfjzl-final-cloud-app-with-database' ] && git clone https://github.com/ibm-developer-skills-network/tfjzl-final-cloud-app-with-database.git

set up a virtual environment to contain all the packages we need.
pip install --upgrade distro-info
pip3 install --upgrade pip==23.2.1
pip install virtualenv
virtualenv djangoenv
source djangoenv/bin/activate

Set up the Python runtime and test the template project.
pip install -U -r requirements.txt

Create the initial migrations and generate the database schema:

Migrations are Django's way of propagating changes you make to your models (adding a field, deleting a model, etc.) into your database schema. They are designed to be mostly automatic, but you will need to know when to make migrations, when to run them, and the common problems you might run into. There are several commands which you will use to interact with migrations and Django's handling of database schema:

migrate, which is responsible for applying and unapplying migrations
makemigrations, which is responsible for creating new migrations based on the changes you have made to your models
sqlmigrate, which displays the SQL statements for a migration
showmigrations, which lists a project's migrations and their status

python3 manage.py makemigrations
python3 manage.py migrate

Run server:
python3 manage.py runserver

Build new Models:

A Question model will save the questions of an exam with the following characteristics:
Used to persist questions for a course
Has a Many-To-One relationship with the course
Has question text
Has a grade point for each question

A Choice model saves all of the choices of a question:
Many-To-One relationship with Question model
The choice text
Indicates if this choice is the correct one or not

You are provided with commented out Submission model, which has:
Many-to-One relationships with Exam Submissions, for example, multiple exam submissions could belong to one course enrollment.
Many-to-Many relationship with choices or questions. For simplicity, you could relate the submission with the Choice model

Run migrations
1
2
python3 manage.py makemigrations onlinecourse
python3 manage.py migrate

Make changes to admin.py:
Import new models
At the moment, you are only importing Course, Lesson, Instructor, and Learner in onlinecourse/admin.py

You need to add Question, Choice, and Submission
Create QuestionInline and ChoiceInline
Create QuestionInline and ChoiceInline classes so that you could edit them together on one page in the admin site.
Create QuestionAdmin class
Register Question, Choice, and Submission
After you register the new models, you could create a new course with lessons, questions, and question choices using the admin site.

The register decorator: register(*models, site=django.contrib.admin.sites.site)
reate an admin user
Let's create an admin user with the following details:

Username: admin
Email address: leave blank by pressing enter
Password: Your choice, or use p@ssword123
1
python3 manage.py createsuperuser

ask 3: Update the Course Detail Template
You will now update the course detail template to create an exam section with a list of questions and choices.

One exam contains multiple questions, and each should have more than one correct answer (multiple-selection).
he changes will be made in templates/onlinecourse/course_details_bootstrap.html
