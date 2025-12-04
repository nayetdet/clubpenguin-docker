FROM node:20-slim
WORKDIR /app
COPY submodules/yukon/package*.json ./
RUN npm install
COPY submodules/yukon .
COPY submodules/assets /tmp/assets
RUN mkdir -p ./assets \
    && cp -rn /tmp/assets/* ./assets/ \
    && rm -rf /tmp/assets

EXPOSE 8080
CMD ["npx", "webpack", "serve", "--host", "0.0.0.0", "--port", "8080"]
