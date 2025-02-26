FROM golang:1.22-alpine AS builder

WORKDIR /usr/src/app

COPY . . 

RUN go mod download

RUN go build -o product-catalog . 

FROM alpine AS release

WORKDIR /usr/src/app

COPY ./products /products

COPY --from=builder=

EXPORT 8088

ENTRYPOINT [ "./product-catalog" ]