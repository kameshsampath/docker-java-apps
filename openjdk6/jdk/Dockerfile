FROM kameshsampath/ubuntu

MAINTAINER Kamesh Sampath, kamesh.sampath@hotmail.com

# Update the APT cache
RUN apt-get update -y
RUN apt-get upgrade -y

# Install some common tools
RUN apt-get install -y curl unzip wget

# Install JDK 6
RUN apt-get -q -y install openjdk-6-jdk
