# Install Ubuntu 18.04
FROM ubuntu:18.04

# Resynchronize the packages available
RUN apt update

# Check Ubuntu version
RUN cat /etc/issue

# Install Apache2
RUN apt install -y apache2

RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata

RUN apt install -y php php-cli php-fpm php-json php-pdo php-mysql php-zip php-gd  php-mbstring php-curl php-xml php-pear php-bcmath

COPY entrypoint.sh /sbin/entrypoint.sh
RUN chmod 755 /sbin/entrypoint.sh

# Expose apache.
EXPOSE 80

CMD ["/sbin/entrypoint.sh"]
