FROM ubuntu

MAINTAINER Kamesh Sampath, kamesh.sampath@hotmail.com

# Update the APT cache
RUN apt-get update --fix-missing
RUN apt-get upgrade -y --fix-missing

# Install some common tools
RUN apt-get install -y curl unzip wget

# Install JRE 6
RUN apt-get -q -y --fix-missing install openjdk-6-jre-headless
