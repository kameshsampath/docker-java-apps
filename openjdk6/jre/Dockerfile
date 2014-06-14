FROM ubuntu

MAINTAINER Kamesh Sampath, kamesh.sampath@hotmail.com

# Update the APT cache
# RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list
RUN apt-get update
RUN apt-get upgrade -y

# Install some common tools
RUN apt-get install -y curl unzip wget

# Install JRE 6
RUN apt-get -q -y install openjdk-6-jre
