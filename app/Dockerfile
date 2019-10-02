FROM golang:1.12.0-alpine3.9

ENV GO111MODULE=on

WORKDIR /app

RUN apk add --no-cache git

COPY go.mod .
COPY go.sum .

RUN go mod download
RUN go get -u gopkg.in/urfave/cli.v2@master && go get -u github.com/oxequa/realize
COPY . .
