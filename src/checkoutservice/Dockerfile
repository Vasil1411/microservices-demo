# Етап 1: Компилиране на Go приложението
FROM golang:1.25-alpine AS builder
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -o /server .

# Етап 2: Финален лек образ
FROM alpine:latest
WORKDIR /app
COPY --from=builder /server /app/server
EXPOSE 5050
ENTRYPOINT ["/app/server"]