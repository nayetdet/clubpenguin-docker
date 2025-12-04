FROM node:20-slim
WORKDIR /app

ARG MYSQL_HOST
ARG MYSQL_USER
ARG MYSQL_PASSWORD
ARG MYSQL_DATABASE

COPY submodules/yukon-server/package*.json ./
RUN npm install
COPY submodules/yukon-server .
RUN apt-get update \
    && apt-get install -y jq \
    && mkdir -p ./config \
    && jq --arg host "$MYSQL_HOST" \
        --arg user "$MYSQL_USER" \
        --arg password "$MYSQL_PASSWORD" \
        --arg database "$MYSQL_DATABASE" \
        '.database.host = $host | .database.user = $user | .database.password = $password | .database.database = $database' \
        ./config/config_example.json > ./config/config.json ; \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN npm run secret-gen
EXPOSE 6111 6112
CMD ["npm", "run", "dev"]
