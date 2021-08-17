# See https://github.com/chemidy/smallest-secured-golang-docker-image for more examples

# Building the executable binary
FROM golang:1.16-alpine as builder

WORKDIR /build

# Install git + SSL ca certificates.
# Git is required for fetching the dependencies.
# Ca-certificates is required to call HTTPS endpoints.
RUN apk update && apk add --no-cache git ca-certificates tzdata && update-ca-certificates

# Add non-root user.
RUN addgroup -g 1001 -S appuser
RUN adduser -u 1001 -S appuser -G appuser
USER appuser

COPY . .

# Fetch dependencies
RUN go get -d -v

# Build the binary
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build \
  -ldflags='-w -s -extldflags "-static"' -a \
  -o /go/bin/server .

# STEP 2 build an image
FROM scratch

# Import from builder
COPY --from=builder /usr/share/zoneinfo /usr/share/zoneinfo
COPY --from=builder /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/
COPY --from=builder /etc/passwd /etc/passwd
COPY --from=builder /etc/group /etc/group
COPY --from=builder /go/bin/server /go/bin/server

USER appuser:appuser

ENTRYPOINT ["/go/bin/server"]
