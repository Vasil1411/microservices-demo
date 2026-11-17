# Етап 1: Компилиране с Gradle и Java (JDK)
FROM eclipse-temurin:21-jdk-alpine AS builder

WORKDIR /app
RUN apk add --no-cache libc6-compat
COPY . .
RUN chmod +x gradlew
RUN ./gradlew installDist

# Етап 2: Финален лек образ само с Java Runtime (JRE)
FROM eclipse-temurin:21-jre-alpine

WORKDIR /app
# Използваме wildcard (*), за да вземе директорията без значение точното име от Gradle
COPY --from=builder /app/build/install/*/ /app/

EXPOSE 9555
ENTRYPOINT ["/app/bin/AdService"]