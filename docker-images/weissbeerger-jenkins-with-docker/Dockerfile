FROM jenkins/jenkins:2.238-alpine

LABEL maintainer="anatoliy.dutchak@gmail.com" 

# The below tasks should be executed under root user
USER root

# This folder was temporarily exposed during Initial Jenkins configuration via web interface.
# After the basic configuration was completed, I've excluded it from Git.
COPY jenkins-home/ /var/jenkins_home

# Docker needed for Jenkins to build images
RUN apk update && apk add --no-cache docker

EXPOSE 8080

# Adding jenkins used into docker group
RUN addgroup jenkins docker