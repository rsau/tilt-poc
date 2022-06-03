FROM govcms.api/drupal

# Install GovCMS.
COPY --from=govcms/govcms:9.x-latest /app /app
COPY --from=drupal:9-php8.1 /opt/drupal/web/core/install.php /app/web/core/install.php

WORKDIR /app

RUN set -eux; \
  rm -rf /opt/drupal; \
  ln -sf /app/web /var/www/html;

ENV COMPOSER_ALLOW_SUPERUSER=1
ENV COMPOSER_MEMORY_LIMIT=-1
RUN composer config -g github-oauth.github.com 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
