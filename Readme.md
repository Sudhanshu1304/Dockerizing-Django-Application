# Dockerizing Django Application

<div align="center">
<img src = "Images\docker3.png"  height = "50%" >
</div>

## Step 1
---

> Create the django project <br>
~~~
    # Let's name the project to be Dockertest 
    django-admin startproject dockertest
~~~


The basic file structure after running above command will look like 

    dockertest
    |
    |-- dockertest
    |    |-- __init__.py
    |    |-- asgi.py
    |    |-- setting.py
    |    |-- urls.py
    |    |-- wsgi.py
    |
    |-- manage.py
    |-- db.sqlite3

## Step 2
---

Now create a requirements.txt file 
> This file will contain all the libraries to be installed to run the program
~~~
    # Run below command to create the requirements.txt
    pip freeze > requirements.txt
~~~

After running the above command the file structure should look like

    dockertest
    |
    |-- dockertest
    |    |-- __init__.py
    |    |-- asgi.py
    |    |-- setting.py
    |    |-- urls.py
    |    |-- wsgi.py
    |
    |-- manage.py
    |-- db.sqlite3
    |-- requirements.txt


## Step 3
---

Create the docker file in the dir where requirements.txt exists. Although the files can be kept at different locations
as well but then you have to prove the paths accordingly

~~~
    # Docker file content
    FROM python:3.8-slim-buster
    
    WORKDIR /app
    
    COPY requirements.txt requirements.txt
    
    RUN pip3 install -r requirements.txt
    
    COPY . .
    
    CMD [ "python3", "manage.py", "runserver" ,"0.0.0.0:8080" ]

~~~

## Step 4
---

Run the below commands to create and run the image in the bash/cmd
~~~
    # here you can name anything to the docker image and the ".(dot)" represents the location where the dockerfile is kept. This file will create the docker image.
    
    docker build --tag MydockerImage .

    # This line will create a container out of the docker image you created above and run it.
    docker run -it -p 8000:8000 MydockerImage

~~~







