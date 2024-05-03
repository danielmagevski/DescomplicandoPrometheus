FROM golang:1.20.0-alpine3.16 AS buildando

WORKDIR /app
COPY . /app
RUN go build segundo-exporter.go

FROM alpine:3.16
LABEL maintainer Daniel Magevski <daniel_magevski@hotmail.com>
LABEL description "Executando o nosso segundo exporter"
COPY --from=buildando /app/segundo-exporter /app/segundo-exporter
EXPOSE 7788
WORKDIR /app
CMD ["./segundo-exporter"]