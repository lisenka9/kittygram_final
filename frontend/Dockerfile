FROM node:18 as build

WORKDIR /app

COPY package.json package-lock.json ./
RUN npm ci

COPY . .
RUN npm run build

FROM alpine:latest

WORKDIR /build

COPY --from=build /app/build /build

RUN ls -la /build