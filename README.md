# python-achievement-2

### Table of Contents

[Exercise 1](https://github.com/brett-ranieri/python-achievement-2/tree/main#exercise-1)

[Exercise 2](https://github.com/brett-ranieri/python-achievement-2/tree/main#exercise-2)


## Exercise 1

#### Install Python/Verify version

Install Python 3.8.7 and check for appropriate version by running `python --version`

#### Create virtual environment

Create virutal environment by running `mkvirtualenv achievement2-practice`

#### Install Django/Verify version

Install Django by running `py -m pip install Django` 

Confirm install and check version by running `django-admin --version`


## Exercise 2

#### Create Django project named "recipe_project"

While in desired directory, run the following command `django-admin.exe startproject recipe_project`

#### Run migration to create necessary database tables

While in src directory, run the following command `py manage.py migrate`
*This will also need to be done for any future changes to database once created.*

#### Run server to deploy project to localhost

While in src directory, run the following command `py manage.py runserver`

#### Create a superuser

While in src directory, run the following command `py manage.py createsuperuser`
*You will be prompted to provide a username, email (optional), and password (will not appear as you are typing it).*

#### Login as superuser

After redeploying project to localhost, add "/admin" to end of URL. This will bring you to admin login page where you will be prompted to provide your username/password for access.


