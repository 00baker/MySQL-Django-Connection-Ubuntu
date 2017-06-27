# How to connect MySQL and Django Ubuntu

### Creating a new database in UBUNTU

1. Start MySQL using command `mysql -u root -p`. You will be prompted for the admin password.(to install MySQL go to [link](https://github.com/avmain/Acadview-Docs/blob/master/docs/How%20to%20install%20MySQL%20Server%20in%20Ubuntu.md))

![](/img/mysql-django1.png)

2. Create a new database using the command `CREATE DATABASE database_name;`.


3. Create a new user using command `CREATE USER user_name@localhost IDENTIFIED BY 'password';`.

![](/img/mysql-django2.png)

4. We need to give our user some database rights `GRANT ALL PRIVILEGES ON database_name.* TO user_name@localhost;`.

![](/img/mysql-django3.png)

### Connection to Django

1. Go the project directory. Using command `cd path/to/project`.

2. Activate virtualenviroment. Using command `source bin/active`.

![](/img/mysql-django4.png)

3. Download and install python-mysqlclient. Using command `pip install django mysqlclient`.

![](/img/mysql-django5.png)

4. Open settings.py file using command `gedit path/to/project/project_name`.

![](/img/mysql-django6.png)

5. Toward the bottom you will see DATABASES section that looks like.
```
...
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
...
```

6. Edit this file with following code:

```
...
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'test0', 
        'USER': 'user_name',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '',
    }
}
....
```
![](/img/mysql-django7.png)

7. Now on terminal use the following command. `python manage.py makemigrations'`

8. After that `python manage.py migrate`

9. Then `python manage.py runserver`





