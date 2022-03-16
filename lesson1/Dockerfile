FROM node:14.15.1 as building

WORKDIR /app

EXPOSE 3000

ENV PATH /app/node_modules/.bin:$PATH

COPY package.json package-lock.json ./

RUN npm install --silent && npm install react-scripts@3.3.0 -g --silent

COPY . ./

RUN npm run build

FROM nginx:1.20.1

WORKDIR /usr/share/nginx/html

RUN rm /etc/nginx/conf.d/default.conf

COPY --from=building /app/build /usr/share/nginx/html
COPY .nginx/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

ENTRYPOINT ["nginx", "-g", "daemon off;"]