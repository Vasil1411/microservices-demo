# --- ЕТАП 1: Компилиране (Builder) ---
FROM golang:1.25-alpine AS builder

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .

RUN CGO_ENABLED=0 GOOS=linux go build -o /server .


# --- ЕТАП 2: Финален лек образ ---
FROM alpine:latest

WORKDIR /app

COPY --from=builder /server /app/server
COPY --from=builder /app/templates /app/templates
COPY --from=builder /app/static /app/static

EXPOSE 8080

ENTRYPOINT ["/app/server"]