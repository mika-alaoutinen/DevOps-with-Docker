# Build layer
FROM node:14-alpine AS build-env
WORKDIR /app

COPY package*.json .
RUN npm i

COPY . .
RUN npm run build

# Application layer
FROM node:14-alpine
WORKDIR /usr/src/app

COPY package*.json .
RUN npm i
RUN npm i -g serve

COPY --from=build-env /app/build /usr/src/app/build
COPY --from=build-env /app/public /usr/src/app/public

RUN addgroup -g 1001 -S appuser
RUN adduser -u 1001 -S appuser -G appuser
USER appuser

EXPOSE 5000

CMD [ "serve", "-s", "-l", "5000", "build" ]
