FROM golang:1.21-alpine AS builder

RUN apk update && apk add --no-cache git

WORKDIR /build

COPY go.mod go.sum ./

RUN go mod download

COPY . .

# Сборка бинарного файла main
RUN go build -o main main.go

FROM alpine:latest

WORKDIR /root/

COPY --from=builder /build/main .

EXPOSE 8080

CMD ["./main"]

#решение от разработчиков
#FROM golang:1.22-alpine3.20 AS builder

#WORKDIR /build

#COPY . .

# Сборка бинарного файла main
#RUN go build -o main main.go

#FROM alpine:3.20

#COPY --from=builder /build/main /main

#EXPOSE 8080

#CMD ["/main"]