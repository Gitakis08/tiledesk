FROM node:14.21.2-alpine AS builder

RUN npm install -g ionic cordova@8.0.0

WORKDIR /app

COPY . ./

RUN npm install

RUN mkdir -p ./www

RUN cordova platform add browser@latest

RUN ionic cordova build browser
RUN sed -i 's#<script src="cordova.js"></script>##g; s#<script src="cordova.js" defer></script>##g' /app/platforms/browser/www/index.html

FROM nginx:1.14.1-alpine AS setup

COPY nginx.conf /etc/nginx/nginx.conf

RUN rm -rf /usr/share/nginx/html/*

COPY --from=builder /app/platforms/browser/www/ /usr/share/nginx/html
COPY --from=builder /app/src/chat-config-template.json /usr/share/nginx/html
COPY --from=builder /app/src/firebase-messaging-sw-template.js /usr/share/nginx/html

RUN sed -i "s#<title>.*</title>#<title>Pobuca Converse</title>#g" /usr/share/nginx/html/index.html

WORKDIR /usr/share/nginx/html

CMD ["/bin/sh", "-c", "envsubst < /usr/share/nginx/html/chat-config-template.json > /usr/share/nginx/html/chat-config.json && envsubst < /usr/share/nginx/html/firebase-messaging-sw-template.js > /usr/share/nginx/html/firebase-messaging-sw.js && exec nginx -g 'daemon off;'"]
