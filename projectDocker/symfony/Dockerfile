FROM ubuntu

RUN echo "Europe/paris" > /etc/timezone
RUN apt-get update 
RUN DEBIAN_FRONTEND=noninteractive
RUN apt-get install -y -q tzdata
RUN apt-get install -y -q apt-utils \
    && apt-get install -y -q php-cli \
    && apt-get install -y -q apache2 php libapache2-mod-php \
    && apt-get install -y -q curl \ 
    && apt-get install -y -q git \
    && apt-get install -y -q php-xml \
    && apt-get install -y -q libapache2-mod-php \
  php-cli \
  php-common \
  php-mbstring \
  php-gd \
  php-intl \
  php-xml \
  php-mysql \
  php-zip 

WORKDIR /var/www/symfony_docker

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony5/bin/symfony /usr/local/bin/symfony
RUN git config --global user.email "you@example.com" \ 
    && git config --global user.name "Your Name"
ADD . .  

RUN composer install
ENTRYPOINT ["/usr/sbin/apache2", "-k", "start"]