# django-starter-template
Template code to start Django project with Heroku and Cloudinary

## How to use :

### Start Project
1.	Make project directory and cd to that directory
2.	Create virtual environment and activate
```
virtualenv venv & venv\Scripts\activate
```
3.	Download this zip code and rename to root
4.	Drag and drop the folder (at number 3) to project directory (at number 1)
5.	cd root & git init
6.	pip install -r requirements.txt (customize the version of each package as needed)
7.	Create local.py in settings folder
```
from .base import *
```
8.	Create templates folder in root directory
9.	python manage.py migrate & python manage.py createsuperuser

### Heroku Setup
10.	Change the python version on runtime.txt (optional)
11.	heroku login -i
12.	heroku create <name> (domain will be : <name>.herokuapp.com)
13.	Set allowed host (in production.py)
```
ALLOWED_HOSTS = ['<name>.herokuapp.com']
```
14.	heroku config:set DISABLE_COLLECTSTATIC=1
15.	git push heroku master
16.	heroku ps:scale web=1
17.	heroku addons:create heroku-postgresql:hobby-dev
18.	heroku run bash or heroku run <command>
```
heroku run python manage.py makemigrations & heroku run python manage.py migrate & heroku run python manage.py createsuperuser
```
note : create a superuser with a strong password because it's now live

### Setup Django Storage Cloudinary (Static Files)
19.	Set heroku env variable
```
heroku config:set CLOUD_NAME=<your_cloud_name>
heroku config:set CLOUD_API_KEY=<your_cloud_api_key>
heroku config:set CLOUD_API_SECRET=<your_cloud_api_secret>
```
20.	Set MEDIA_URL in settings/base.py file (this is the folder name to store your media in cloudinary) (optional)
21.	Set image field in model, and specify where you want to store your image (upload_to=’…/’)
22.	In cloudinary, your image will be saved on “media_url/upload_to/”
