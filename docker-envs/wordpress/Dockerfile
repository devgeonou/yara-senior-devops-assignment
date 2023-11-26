FROM wordpress:6-fpm-alpine

LABEL maintainer="joellr17@gmail.com"
LABEL description="Secure WordPress FPM Docker image"

RUN addgroup -g 1000 wordpress && \
    adduser -D -u 1000 -G wordpress wordpress
    
RUN chown -R wordpress:wordpress /var/www/html

COPY www.conf /usr/local/etc/php-fpm.d/www.conf

USER wordpress
