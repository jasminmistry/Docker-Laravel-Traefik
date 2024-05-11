FROM php:8.3-fpm-alpine3.19
ADD --chmod=0755 https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer 

COPY --chown=nginx . /srv/app
RUN apk update && apk upgrade
RUN apk add --no-cache \
    nginx \
    supervisor


COPY docker/config/nginx.conf /etc/nginx/http.d/default.conf
COPY docker/config/supervisord.conf /etc/supervisor/conf.d/supervisord.conf
RUN chown -R nginx:nginx /srv/app

USER nginx

EXPOSE 80

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
