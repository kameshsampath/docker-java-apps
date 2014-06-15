FROM ubuntu:precise

MAINTAINER Kamesh Sampath, kamesh.sampath@hotmail.com

# Update the APT cache
RUN apt-get update --fix-missing
RUN apt-get upgrade -y

# Install some common tools
RUN apt-get install -y --fix-missing curl unzip wget

# Install JRE 6
RUN apt-get -q -y --fix-missing install openjdk-6-jre-headless
