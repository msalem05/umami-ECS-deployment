#Build Stage

FROM node:22-alpine AS build
WORKDIR /app

RUN apt-get update && apt-get install -y --no-install-recommends openssl ca-certificates \
  && rm -rf /var/lib/apt/lists/*

COPY package*.json pnpm-lock.yaml ./
RUN npm install -g pnpm && pnpm install --frozen-lockfile
COPY . .

ARG DATABASE_TYPE=postgresql
ENV DATABASE_TYPE=$DATABASE_TYPE
ENV NEXT_TELEMETRY_DISABLED=1

RUN pnpm run build-docker

EXPOSE 3000
CMD [ "pnpm" , "start-docker"]







