
FROM golang:1.23 AS build


RUN useradd -m appuser


WORKDIR /app


COPY . .


RUN CGO_ENABLED=0 go build -o vote-api .


FROM alpine:latest


RUN addgroup -S appgroup && adduser -S appuser -G appgroup


WORKDIR /app

ENV PG_URL=postgresql://neondb_owner:hmYcEZnG7BN9@ep-shy-mode-a2l6ax5k.eu-central-1.aws.neon.tech/neondb?sslmode=require

COPY --from=build /app /app


EXPOSE 8080


CMD ["./vote-api"]
