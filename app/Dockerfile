FROM golang:1.12.0-alpine3.9 as build

ENV GO111MODULE=on

WORKDIR /app

RUN apk add --no-cache git

COPY go.mod .
COPY go.sum .

RUN go mod download
RUN go get gopkg.in/urfave/cli.v2@master && go get github.com/oxequa/realize
COPY . .

RUN go build -o app

FROM alpine:3.9

WORKDIR /app

COPY --from=build /go/app/app .

RUN set -x && \
  addgroup go && \
  adduser -D -G go go && \
  chown -R go:go /app/app

CMD ["./app"]