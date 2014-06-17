FROM ubuntu

MAINTAINER Kamesh Sampath, kamesh.sampath@hotmail.com

# Update the APT cache
RUN apt-get update 
RUN apt-get upgrade -y

# Install JRE 7
RUN apt-get -q -y --fix-missing install openjdk-7-jre-headless
