Django Project | djblogger from youtube  https://www.youtube.com/playlist?list=PLOLrQ9Pn6cawJ9CbY-o_kQC4GOWfhCFHq video 1- 13 
first commit to git hub This is my attempt to create a blog using Django and htmx. 
using VScode I will use the blog to details my journey into the world of cybersecurity. this is an introduction. 
I have run into a few challeng that i manage to overcome with stack overflow and github as resources. I
Ireally like this course, even though it is technical, the help is great. Lets continue to learn
When trying to use github for the first time i manage to delete some file, had to redo the process a few time. glad all works.




Vscode
Python -m venv blog	Create environment blog

PS c:\ set-ExecutionPolicy Unrestricted -Scope Process	Change Powershell to have virtual environment
PS c: \ Set-ExecutionPolicy Unrestricted -Force	Complete the change
.\blog\scripts\activate	Run virtual environment
.\blog\scripts\deactivate	Terminate environment, but must restart VScode
.
Vscode 
Ctrl wheel	Zoom
Ctrl `	Terminal

In virtual environment
Pip install django	Install the django files
django-admin startproject djblogger	Start project djblogger with manage.py outside folder
django-admin startproject djblogger .	Start project djblogger with manage.py inside folder djblogger + folder djblogger
Python ./manage.py runserver 	Start server at 127.0.0.1:8000
CTRl C to break out	

Setting files
Settings.py	In djblogger folder

Create a settings folder in djblogger
Create a __init__.py in settings
Copy settings.py to /settings

Edit manage.py 
os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'djblogger.settings') 
to
os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'djblogger.settings.settings')

Rename settings to base.py
And create local.py in setting folder

from .base import *

Do the same for production.py

Add a condition in manage.py to chose either local or production depending on debug

from djblogger.settings import base


if base.DEBUG:
        os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'djblogger.settings.local')
    else:
        os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'djblogger.settings.production')

When setting manage.py  DEBUG to False, we need to add ALLOWED HOST ['*']

Setting up  a Secret key  (Cap letter screws the copy paste in the shell)
Python ./manage.py shell	Enter django shell
From django.core.management.utils import get_random_secret_key	Open the tools
Print(get_random_secret_key)	Return a function
Print(get_random_secret_key())	Get secret key

Copy the key to the base.py SECRET_KEY

In the environment
Pip Intall python-dotenv	Install dotenv 

Create a file name .env in the djblogger folder (next to manage.py)

Add to .env

SECRET_KEY=1&2bhao9vjp5f9v1&mk(l^acdzd-7_a(5t=tr1bg7#*cb1f=@)	Secret key generated to base.py
DEBUG=True	Debug settomg

Now add and replace base.py with

from dotenv import load_dotenv
import os
load_dotenv()

SECRET_KEY = os.environ.get('SECRET_KEY')	Get secret key from .env file
DEBUG = os.environ.get('DEBUG') == 'True'	See if debug is set to true. When getting a string, if non null it is true, that is why we need to compare.

Installing pytest
pip install pytest-django	Installing pytest
Pytest	Runs test

Create a file pytest.ini in the manage.py folder

[pytest]
DJANGO_SETTINGS_MODULE = djblogger.settings.local
python_files = test_*.py

In the djblogger folder make a tests folder
Let's create an example
Make test_example.py

def test_example():
    assert 1 == 1

Run pytest to check the test

Video 13 was how to setup a github repository. I had to recreate the project twice because of folder mixup…


![image](https://github.com/SylvainK1/Django-project-djblogger-local/assets/161142973/9cb88cf1-3bff-45ef-be54-0c724c26745a)
