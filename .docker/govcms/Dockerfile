FROM drupal:9-php8.1

RUN apt-get update && apt-get install -q -y ssmtp mailutils && rm -rf /var/lib/apt/lists/*

RUN echo "hostname=govcms.local" > /etc/ssmtp/ssmtp.conf
RUN echo "root=root@pgovcms.local" >> /etc/ssmtp/ssmtp.conf
RUN echo "mailhub=mailhog:1025" >> /etc/ssmtp/ssmtp.conf
RUN echo "sendmail_path=/usr/sbin/ssmtp -t" >> /usr/local/etc/php/conf.d/php-sendmail.ini

# Install Drush with the phar file.
RUN curl -fsSL -o /usr/local/bin/drush "https://github.com/drush-ops/drush-launcher/releases/latest/download/drush.phar" && \
  chmod +x /usr/local/bin/drush

# Install GovCMS.
COPY --from=govcms/govcms:9.x-latest /app /app
COPY --from=drupal:9-php8.1 /opt/drupal/web/core/install.php /app/web/core/install.php

WORKDIR /app

RUN set -eux; \
    rm -rf /opt/drupal; \
    ln -sf /app/web /var/www/html;
