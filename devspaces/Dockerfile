FROM ubuntu:16.04

LABEL description="Devspaces implementation for LanguageTool"

RUN apt-get update \
 && apt-get install -y build-essential \
    	curl \
        dialog \
        git \    	
    	mc \
    	sudo \ 
        vim \  	
        wget \ 
        openjdk-8-jdk \
  && apt-get clean

# Installing Maven
RUN cd /usr/local \
 && wget http://www-eu.apache.org/dist/maven/maven-3/3.5.4/binaries/apache-maven-3.5.4-bin.tar.gz \
 && tar xzf apache-maven-3.5.4-bin.tar.gz \
 && ln -s apache-maven-3.5.4 apache-maven \
 && rm -f apache-maven-3.5.4-bin.tar.gz \
 && echo '/etc/profile.d/apache-maven.sh' >> ~/.bashrc 

COPY apache-maven.sh /etc/profile.d/apache-maven.sh

RUN chmod 755 /etc/profile.d/apache-maven.sh

WORKDIR /data

CMD tail -f /dev/null  