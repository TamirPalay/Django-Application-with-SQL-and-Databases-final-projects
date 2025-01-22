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