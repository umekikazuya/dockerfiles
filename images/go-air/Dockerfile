ARG GO_VERSION=1.26-alpine
FROM golang:${GO_VERSION}

RUN apk add --no-cache wget

ARG AIR_VERSION=v1.63.5
RUN go install github.com/air-verse/air@${AIR_VERSION}

WORKDIR /app

CMD ["air", "-c", ".air.toml"]