#From https://towardsdatascience.com/docker-for-python-dash-r-shiny-6097c8998506

FROM python:3.8.6-slim-buster

LABEL maintainer "Joshua, test@hotmail.com"

# set working directory in container
WORKDIR /dash-app

# Copy and install packages
COPY requirements.txt .
RUN pip install --upgrade pip

RUN pip install -r ./requirements.txt    

# Copy app folder to app folder in container
COPY ./app ./app

# Changing to non-root user
RUN useradd -m appUser
USER appUser


# Change directory into app folder 
# Run locally, first parameter is app.py file, next is server variable
CMD gunicorn --chdir ./app --bind 0.0.0.0:8050 app:server