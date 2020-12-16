FROM ubuntu:latest
LABEL maintainer="pat@247.ch"

ARG version=1.0

RUN apt-get update && \
    apt-get install -y python3-pip python3-dev wget curl vim

COPY requirements.txt /home/html/

RUN pip3 install -r /home/html/requirements.txt

# Set the locale
ENV LANG C.UTF-8
ENV LANGUAGE C.UTF-8
ENV LC_ALL C.UTF-8

WORKDIR /home/html

RUN wget https://github.com/patklaey/brandi-dog/archive/v${version}.tar.gz
RUN tar -zxf v${version}.tar.gz
RUN mv brandi-dog-${version} brandi-dog

WORKDIR /home/html/brandi-dog

COPY ./uwsgi.ini /home/html/brandi-dog/
RUN mkdir -p /var/log/uwsgi/ 

CMD uwsgi --ini /home/html/brandi-dog/uwsgi.ini

EXPOSE 5000
