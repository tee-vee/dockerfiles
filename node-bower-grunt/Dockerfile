FROM node:latest
MAINTAINER Will Price <will.price94@gmail.com>

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

RUN npm install -g bower grunt json


ONBUILD COPY package.json /usr/src/app/
ONBUILD COPY bower.json /usr/src/app/
ONBUILD COPY bowerrc.json /root/.bowerrc
ONBUILD RUN  json -I -f /root/.bowerrc -e 'this.allow_root=true'

ONBUILD COPY . /usr/src/app
ONBUILD RUN rm -rf bower_components
ONBUILD RUN rm -rf node_modules

ONBUILD RUN npm install
ONBUILD RUN bower install
ONBUILD RUN grunt build
