FROM php:7.0
MAINTAINER chenchuangjie <ccj@sd-zeus.com>

RUN apt-get update && apt-get install -y git curl libfreetype6-dev \
  && rm -rf /var/lib/apt/lists/* \
  && docker-php-ext-install zip \
  && docker-php-ext-enable zip

RUN git config --global user.name "ccj" \
  && git config --global user.email "1019242086@qq.com"


RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php -r "if (hash_file('sha384', 'composer-setup.php') === '48e3236262b34d30969dca3c37281b3b4bbe3221bda826ac6a9a62d6444cdb0dcd0615698a5cbe587c3f0fe57a54d8f5') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
  && php composer-setup.php \
  && php -r "unlink('composer-setup.php');" \
  && mv composer.phar /usr/local/bin/composer \
  && echo 'export PATH="$PATH:$HOME/.composer/vendor.bin"' >> /.bashrc \
  && . ~/.bashrc \
  && composer config -g repo.packagist composer https://packagist.phpcomposer.com
