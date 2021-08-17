FROM node:14
EXPOSE 5000
WORKDIR /usr/src/app

COPY package*.json ./

# Install dependencies
RUN npm i -g serve
RUN npm i

COPY . .

# Run production build
# ENV REACT_APP_BACKEND_URL=http://localhost:8080
RUN npm run build

# Add non-root user
RUN useradd -u 1234 appuser
USER appuser

CMD [ "serve", "-s", "-l", "5000", "build" ]
