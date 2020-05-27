FROM alpine:3.9.6

LABEL maintainer="anatoliy.dutchak@gmail.com"

# The below tasks should be executed under root user
USER root

# Installing nginx from apk repository
RUN apk update && apk add --no-cache nginx && \
    mkdir  /var/www/html && \
    mkdir /run/nginx && \
    chown -R nginx:nginx /var/www/html && \
    chown nginx:nginx /run/nginx

# A sinple copy of default nginx.conf + section listening on port 80
COPY nginx.conf /etc/nginx/nginx.conf

# Copying application content
COPY web/ /var/www/html/

EXPOSE 80

# Starting Nginx when spinning up the container
CMD ["nginx", "-g", "daemon off;"]