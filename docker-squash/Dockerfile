FROM centos:7

WORKDIR /var/www

#Adding nginx repo
COPY ./files/nginx.repo /etc/yum.repos.d/

#Installin Epel Release repo
RUN yum -y install curl epel-release

RUN yum -y install curl nginx gcc-c++ make

#Installing nodejs
RUN curl --silent --location https://rpm.nodesource.com/setup_9.x | bash -
RUN yum -y install nodejs

#Cleaning base image 
RUN yum -y remove epel-release python-pip

#Copy nginx configuration
RUN rm -f /etc/nginx
RUN mkdir -p /run/nginx

ADD . .

RUN mkdir -p /var/www/hml
RUN mkdir -p /var/www/prd

ENTRYPOINT [ "/usr/sbin/nginx", "-g", "daemon off;" ]

