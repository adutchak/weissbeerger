FROM alpine:3.9.6

LABEL maintainer="anatoliy.dutchak@gmail.com"

USER root

RUN apk update && apk add --no-cache nginx && \
    mkdir  /var/www/html && \
    mkdir /run/nginx && \
    chown -R nginx:nginx /var/www/html && \
    chown nginx:nginx /run/nginx

COPY nginx.conf /etc/nginx/nginx.conf
COPY web/ /var/www/html/

CMD ["nginx", "-g", "daemon off;"]