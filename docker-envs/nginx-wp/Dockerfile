FROM nginx:stable-alpine as build

LABEL maintainer="joellr17@gmail.com"
LABEL description="Secure WordPress FPM Docker image"

RUN apk update --no-cache && \
    chown -R nginx:nginx /etc/nginx/ && \
    chown -R nginx:nginx /var/cache/nginx && \
    chown -R nginx:nginx /var/log/nginx && \
    chown -R nginx:nginx /etc/nginx/conf.d && \
    touch /var/run/nginx.pid && \
    chown -R nginx:nginx /var/run/nginx.pid && \
    rm /etc/nginx/conf.d/default.conf

COPY nginx.conf /etc/nginx/nginx.conf
COPY wordpress.conf /etc/nginx/conf.d/wordpress.conf
COPY node.conf /etc/nginx/conf.d/node.conf

USER nginx
FROM build as main
USER nginx
