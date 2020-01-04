FROM ubuntu:18.04

ARG N8N_VERSION

RUN if [ -z "$N8N_VERSION" ] ; then echo "The N8N_VERSION argument is missing!" ; exit 1; fi

RUN \
apt-get update && \
apt-get -y install graphicsmagick

# Set a custom user to not have n8n run as root
USER root

RUN apt-get install wget build-essential curl python python-pip -y

RUN pip install feedparser

RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -

RUN apt-get install nodejs -y

RUN npm_config_user=root npm install -g n8n@${N8N_VERSION}

WORKDIR /data

CMD "n8n"
