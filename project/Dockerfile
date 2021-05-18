#From https://towardsdatascience.com/docker-for-python-dash-r-shiny-6097c8998506

FROM python:3.8.6-slim-buster

LABEL maintainer "Robin Opdam, robinopdam@hotmail.com"

# set working directory
WORKDIR /usr/src/app

# install system dependencies
RUN apt-get update \
  && apt-get -y install netcat gcc \
  && apt-get clean

# install python dependencies
RUN pip install --upgrade pip
COPY requirements.txt /
RUN pip install -r /requirements.txt

# copy app
COPY . /usr/src/app/

# add entrypoint.sh
COPY ./entrypoint.sh .
RUN chmod +x /usr/src/app/entrypoint.sh

# run entrypoint.sh
ENTRYPOINT ["/usr/src/app/entrypoint.sh"]