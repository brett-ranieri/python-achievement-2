# python-achievement-2

### Table of Contents

[Exercise 1](https://github.com/brett-ranieri/python-achievement-2/tree/main#exercise-1)

[Exercise 2](https://github.com/brett-ranieri/python-achievement-2/tree/main#exercise-2)

[Exercise 3](https://github.com/brett-ranieri/python-achievement-2/tree/main#exercise-3)


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



## Exercise 3

#### Create apps

Run the following command while in the desired directory `py manage.py startapp APP_NAME`

#### Create Models

In `models.py` file, add the following code:

`class Recipe(models.Model):
    # define attributes of the class
    name = models.CharField(max_length=120)
    cooking_time = models.IntegerField(help_text="in minutes")
    ingredients = models.CharField(
        max_length=400, help_text="Ingredients must be seperated by commas"
    )
    difficulty = models.CharField(max_length=20)
    description = models.TextField()
    # define string representation od the class
    def __str__(self):
        return str(self.name)`

#### Register Model

Navigate to respective `admin.py` file and add the following code:

`from .models import User
     # register the class to Django admin - making it visible under Django site admin
admin.site.register(User)`

#### Migrate

While in src directory, run the following command `py manage.py make migrations` then run `py manage.py migrate`

#### Write tests

In the respective `tests.py` file add the following code:

`from .models import Recipe
class RecipeModelTest(TestCase):
    # setting up non-modified objects used by test methods
    def setUpTestData():
        Recipe.objects.create(
            name="Spaghetti and Meatballs",
            cooking_time=30,
            ingredients=["Spaghetti", "Ground meat", "Tomato Sauce", "Cheese", "Bread"],
            description="Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.",
        )
    def test_name_length(self):
        # get recipe to test
        recipe = Recipe.objects.get(id=1)
        # get metadata of name field and use to query its max_length
        max_length = recipe._meta.get_field("name").max_length
        # compare value to expected result
        self.assertEqual(max_length, 120)
    def test_name_label(self):
        recipe = Recipe.objects.get(id=1)
        # get metadata of name field and use to query its label
        recipe_name_label = recipe._meta.get_field("name").verbose_name
        # comparae value to expected result
        self.assertEqual(recipe_name_label, "name")
    def test_name(self):
        recipe = Recipe.objects.get(id=1)
        # compare name value to expected result
        self.assertEqual(recipe.name, "Spaghetti and Meatballs")
    def test_cooking_time(self):
        recipe = Recipe.objects.get(id=1)
        # compare name value to expected result
        self.assertEqual(recipe.cooking_time, 30)
    def test_ingredients_help_text(self):
        recipe = Recipe.objects.get(id=1)
        # get metadata of name field and use to query its label
        ing_help_text = recipe._meta.get_field("ingredients").help_text
        # comparae value to expected result
        self.assertEqual(ing_help_text, "Ingredients must be seperated by commas.")`


