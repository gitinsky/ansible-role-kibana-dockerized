FROM gitinsky/baseimage:0.1.4
MAINTAINER Git In Sky <support@gitinsky.com>

RUN \
  apt-add-repository ppa:chris-lea/node.js && apt-get update && \
  apt-get -y install nodejs git nginx && \
  cd / && \
  git clone https://github.com/elasticsearch/kibana.git /kibana && \
  cd /kibana && git checkout v3.1.2 && npm install && npm install -g grunt-cli && grunt && grunt build && \
  grunt release --force

#COPY config.js /kibana/config.js

ADD ./default /etc/nginx/sites-available/default

EXPOSE 80
