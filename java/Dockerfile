FROM centos:latest
MAINTAINER pranitha
#RUN apt-get update -y
#RUN apt-get install figlet -y
#RUN ["apt-get", "update"]
#RUN ["apt-get", "install", "figlet"]
RUN mkdir -p /home/user/hello && \
    useradd -c "this is a test user" -d /home/user/hello -s /bin/bash hello && \
    groupadd java && \
    gpasswd -a hello java && \
    echo -e "linuxpassword\nlinuxpassword" | passwd hello
ARG USER_NAME
RUN useradd ${USER_NAME}
USER root
WORKDIR /home/user/hello
ADD test /home/user/hello
COPY test2 /home/user/hello/
RUN chmod 755 -R /home/user/hello/ && \
    chown root:hello /home/user/hello
VOLUME  /home/user/hello/
#ADD ["http://www-us.apache.org/dist/tomcat/tomcat-9/v9.0.0.M20/bin/apache-tomcat-9.0.0.M20.tar.gz","."]
#RUN ["tar","-xvf","apache-tomcat-9.0.0.M20.tar.gz"]
#ADD http://download.oracle.com/otn-pub/java/jdk/8u131-b11/d54c1d3a095b4ff2b6607d096fa80163/jdk-8u131-linux-x64.tar.gz .
#RUN tar -xvf jdk-8u131-linux-x64.tar.gz
RUN yum install wget* -y && \
    wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u5-b13/jdk-8u5-linux-x64.tar.gz" && \
    tar -xvf jdk-8u5-linux-x64.tar.gz
ENV CATALINA_HOME /home/user/hello/apache-tomcat-8.5.14 && \
    JAVA_HOME /home/user/hello/jdk1.8.0_05/ && \
    PATH $PATH:$JAVA_HOME/bin:$CATALINA_HOME/bin
EXPOSE 8080
EXPOSE 8009
EXPOSE 8005
