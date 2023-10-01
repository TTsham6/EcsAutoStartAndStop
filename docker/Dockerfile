FROM nginx:1.25.0-alpine

COPY ./default.conf /etc/nginx/conf.d/default.conf
COPY ./index.html /var/www/index.html

EXPOSE 80
CMD [ "nginx", "-g", "daemon off;" ]
