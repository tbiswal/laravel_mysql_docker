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

COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

# Set working directory
WORKDIR /var/www

# Set working directory
COPY ../app/composer.lock ../app/composer.lock/composer.json /var/www/

# Add user for laravel application
RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

# Copy existing application directory contents
COPY ../laravel-app /var/www

# Copy existing application directory permissions
COPY --chown=www:www . /var/www

# Change current user to www
USER www

COPY entrypoint.sh /sbin/entrypoint.sh
RUN chmod 755 /sbin/entrypoint.sh

# Expose apache.
EXPOSE 80

CMD ["/sbin/entrypoint.sh"]
