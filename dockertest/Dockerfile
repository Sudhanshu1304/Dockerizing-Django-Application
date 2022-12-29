# first line is to get the required os
FROM python:3.8-slim-buster
# in here we can specify the name and path to folder where we will keep all files inside docker image
WORKDIR /newapp
# now we will copy path to requirements.txt indise the workdir
COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt