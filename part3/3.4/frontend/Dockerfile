FROM node:14-alpine
EXPOSE 5000
WORKDIR /usr/src/app

COPY package*.json ./

# Install dependencies
RUN npm i -g serve
RUN npm i

# Build application
COPY . .
RUN npm run build

# Add non-root user. The useradd command is not available on Alpine.
RUN addgroup -g 1001 -S appuser
RUN adduser -u 1001 -S appuser -G appuser
USER appuser

CMD [ "serve", "-s", "-l", "5000", "build" ]
