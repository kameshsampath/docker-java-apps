FROM kameshsampath/openjdk-jre-7

MAINTAINER Kamesh Sampath, kamesh.sampath@hotmail.com

# clean repo
RUN yum -y clean all

#
RUN yum -y makecache fast

#Update
RUN yum -y update

#Update
RUN yum -y install unzip wget net-tools

# Update the sysctl.conf file

RUN sed -i.bak '$ i \ fs.file.max = 300000' /etc/sysctl.conf

# Update the limits.conf file

RUN sed -i.bak '$ i \
\*             hard     nofile         8192\n \*             soft     nofile         8192' /etc/security/limits.conf

# Dowload Liferay Portal 6.2.x Community Edition
RUN wget -nv -Oliferay-portal-tomcat-6.2-ce-ga3-20150103155803016.zip  http://sourceforge.net/projects/lportal/files/Liferay%20Portal/6.2.2%20GA3/liferay-portal-tomcat-6.2-ce-ga3-20150103155803016.zip/download

# Uncomment this if you dont want to download from external servers (adjust your local server)
# RUN wget -nv -Oliferay-portal-tomcat-6.2-ce-ga3-20150103155803016.zip  http://192.168.157.1/liferay/files/liferay-portal-tomcat-6.2-ce-ga3-20150103155803016.zip

# Unzip the Portal Tomcat Bundle
RUN unzip -qq liferay-portal-tomcat-6.2-ce-ga3-20150103155803016.zip

# Add the Portal related property files
ADD ./conf/liferay/portal-ext.properties /liferay-portal-6.2-ce-ga3/tomcat-7.0.42/webapps/ROOT/WEB-INF/classes/portal-ext.properties

# Remove the bundle
RUN rm liferay-portal-tomcat-6.2-ce-ga3-20150103155803016.zip ;\
   sed -i.bak '/CATALINA_OPTS\=/ c \CATALINA_OPTS\="$CATALINA_OPTS -server -Duser.timezone\=GMT -Djava.awt.headless\=true -Dfile.encoding\=UTF-8 -Xms1024m -Xmx1024m -XX:NewSize\=256m -XX:MaxNewSize\=256m -XX:PermSize\=256m -XX:MaxPermSize\=256m -XX:+DisableExplicitGC  -Dorg.apache.catalina.loader.WebappClassLoader.ENABLE_CLEAR_REFERENCES\=false"' /liferay-portal-6.2-ce-ga3/tomcat-7.0.42/bin/setenv.sh

# Liferay Home Dir
VOLUME ["/liferay"]

WORKDIR /liferay-portal-6.2-ce-ga3

# Expose the ports
EXPOSE 22 8080

# Start Liferay
ENTRYPOINT ["tomcat-7.0.42/bin/catalina.sh"]
CMD ["run"]

