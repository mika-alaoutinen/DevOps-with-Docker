FROM golang:1.16-alpine AS build-env
WORKDIR /app
EXPOSE 8080
COPY . .
RUN go build

FROM golang:1.16-alpine
WORKDIR /usr/src/app
COPY --from=build-env /app/server /usr/src/app/

# Add non-root user. The useradd command is not available on Alpine.
RUN addgroup -g 1001 -S appuser
RUN adduser -u 1001 -S appuser -G appuser
USER appuser

ENV PORT=8080
ENV REQUEST_ORIGIN=http://localhost:5000

CMD [ "./server" ]
