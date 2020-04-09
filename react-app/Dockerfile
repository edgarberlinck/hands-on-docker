FROM node:12 as build
WORKDIR /usr/src/app
COPY . /usr/src/app

RUN npm install
RUN npm rebuild

ENV NODE_ENV=production
# ARG API_BASE_URL=https://consultaspublicas.mpes.mp.br/api
# ARG ELASTICSEARCH_API=https://elastic.mpes.mp.br/public/ws
# ARG BANCOPECAS_API_URL=https://bancopecas-ws.mpes.mp.br/public/ws

RUN npm run build

FROM nginx:alpine
COPY --from=build /usr/src/app/build/ /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/conf.d/default.conf
