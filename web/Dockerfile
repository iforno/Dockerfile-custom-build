FROM centos:7

# If PHP 7
RUN yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
RUN yum install -y http://rpms.remirepo.net/enterprise/remi-release-7.rpm
RUN yum install -y yum-utils
RUN yum-config-manager --enable remi-php72

RUN yum update -y
RUN yum install -y httpd php-fpm php php-mysql
COPY vhosts /etc/httpd/conf.d/
COPY www /var/www/html/
ADD scripts /scripts
RUN chmod +x /scripts/*.sh

ENV VIRTUAL_HOST=web.local
    
ENTRYPOINT [ "/scripts/init.sh" ]
EXPOSE 80
