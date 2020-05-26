FROM jenkins/jenkins:2.238-alpine

LABEL maintainer="anatoliy.dutchak@gmail.com" 

USER root

COPY jenkins-home/ /var/jenkins_home

RUN apk update && apk add --no-cache docker
RUN addgroup jenkins docker