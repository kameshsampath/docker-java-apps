FROM kameshsampath/openjdk8

MAINTAINER Kamesh Sampath, kamesh.sampath@hotmail.com

RUN apk add --update curl && \
    rm -rf /var/cache/apk/* && \
    curl -sL https://github.com/jpm4j/jpm4j.installers/raw/master/dist/biz.aQute.jpm.run.jar >jpm4j.jar && \
    java -jar jpm4j.jar -g init && \
    jpm install bnd

CMD ["bnd","version"]