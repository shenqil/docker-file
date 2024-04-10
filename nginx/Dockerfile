FROM nginx:alpine

COPY ./dist /usr/share/nginx/html
COPY ./conf/nginx.conf /etc/nginx/nginx.conf
COPY ./conf/conf.d /etc/nginx/conf.d

EXPOSE 8080