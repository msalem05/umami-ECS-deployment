#Build Stage

FROM node:22-slim AS build
WORKDIR /app
COPY package*.json pnpm-lock.yaml ./
RUN npm install -g pnpm 
RUN pnpm run build-docker

EXPOSE 3000
CMD [ "pnpm" , "start-docker"]







