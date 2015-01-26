FROM centos

MAINTAINER Kamesh Sampath, kamesh.sampath@hotmail.com

# clean repo
RUN yum -y clean all

#
RUN yum -y makecache fast

# Update 
RUN yum -y update

# Install JRE 7
RUN yum -y install java-1.7.0-openjdk-headless
