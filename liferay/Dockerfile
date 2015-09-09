# Liferay Portal 6.2 CE
#
# VERSION               0.0.1

FROM kameshsampath/openjdk-jre-7

MAINTAINER Kamesh Sampath, kamesh.sampath@hotmail.com

# Download Liferay Portal 6.2-ce-ga4  
RUN wget -q -oliferay-portal-tomcat-6.2-ce-ga4-20150416163831865.zip http://sourceforge.net/projects/lportal/files/Liferay%20Portal/6.2.3%20GA4/liferay-portal-tomcat-6.2-ce-ga4-20150416163831865.zip/download

# Unzip the Portal Tomcat Bundle
RUN unzip -qq liferay-portal-tomcat-6.2-ce-ga4-20150416163831865.zip

# Default customized portal-ext.properties that will enable the users
# to point the Liferay home to the mount volume
ADD ./conf/liferay/portal-ext.properties /liferay-portal-6.2-ce-ga4/tomcat-7.0.42/webapps/ROOT/WEB-INF/classes/portal-ext.properties

# Remove the bundle
RUN rm liferay-portal-tomcat-6.2-ce-ga4-20150416163831865.zip

# Setup Mount Volume Directories
RUN mkdir -p /liferay/deploy && mv liferay-portal-6.2-ce-ga4/data /liferay/data

# Liferay Home Dir
VOLUME  /liferay

# Liferay setenv.sh
VOLUME ["/liferay-portal-6.2-ce-ga4/tomcat-7.0.42/bin/setenv.sh”]

## Container Start

WORKDIR /liferay-portal-6.2-ce-ga4

# Expose the ports HTTP | OSGi console

EXPOSE 8080 

EXPOSE 11311

## Add points of extension
ONBUILD ADD ./deploy /liferay/deploy
ONBUILD ADD ./lib    /liferay-portal-6.2-ce-ga4/tomcat-7.0.42/lib

# Start Liferay
ENTRYPOINT ["tomcat-7.0.42/bin/catalina.sh"]
CMD ["run"]