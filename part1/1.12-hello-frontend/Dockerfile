FROM node:14
EXPOSE 5000
WORKDIR /usr/src/app

COPY package*.json ./

# Install dependencies
RUN npm i -g serve
RUN npm i

COPY . .

# Run production build
RUN npm run build

CMD [ "serve", "-s", "-l", "5000", "build" ]
