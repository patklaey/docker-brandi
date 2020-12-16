FROM nginx

ARG version=1.0

RUN apt-get update && \
    apt-get install -y wget curl vim git

WORKDIR /home/

RUN wget https://github.com/patklaey/brandiUi/archive/v${version}.tar.gz

RUN tar -zxf v${version}.tar.gz

RUN cp -r brandiUi-${version}/* /usr/share/nginx/html
