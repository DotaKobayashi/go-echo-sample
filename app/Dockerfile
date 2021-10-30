FROM golang:1.17.2-alpine3.14 as build

WORKDIR /app

COPY go.mod go.sum ./

RUN go mod download

COPY . .

RUN go build -o app

FROM alpine:3.14

RUN apk --no-cache add ca-certificates

WORKDIR /root/

COPY --from=build /app/app .

CMD ["./app"]
