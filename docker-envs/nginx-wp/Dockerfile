FROM nginx:stable-alpine

LABEL maintainer="joellr17@gmail.com"
LABEL description="Secure Nginx Docker image"

RUN apk update --no-cache && \
    mkdir -p /var/cache/nginx && \
    mkdir -p /var/log/nginx && \
    mkdir -p /etc/nginx/conf.d && \
    touch /var/run/nginx.pid && \
    chown -R nginx:nginx /etc/nginx /var/cache/nginx /var/log/nginx /etc/nginx/conf.d /var/run/nginx.pid && \
    rm /etc/nginx/conf.d/default.conf

COPY nginx.conf /etc/nginx/nginx.conf
COPY wordpress.conf /etc/nginx/conf.d/wordpress.conf

USER nginx