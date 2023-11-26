FROM nginx:stable-alpine as build
RUN  apk update --no-cache &&  \
     chown -R nginx:nginx /etc/nginx/ && \
     chown -R nginx:nginx /var/cache/nginx && \
     chown -R nginx:nginx /var/log/nginx && \
     chown -R nginx:nginx /etc/nginx/conf.d && \
     touch /var/run/nginx.pid && \
     chown -R nginx:nginx /var/run/nginx.pid && \
     rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/nginx.conf
USER nginx

FROM build as main
USER nginx