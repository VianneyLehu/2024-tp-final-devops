# Étape de construction
FROM node:23 AS build

WORKDIR /app

COPY package.json yarn.lock ./
RUN yarn install

COPY . .


RUN yarn build




FROM node:23-alpine

WORKDIR /app


RUN addgroup --system appgroup && adduser --system --ingroup appgroup appuser

COPY --from=build /app /app

RUN apk update && apk add iputils

RUN chown -R appuser:appgroup /app


USER appuser


EXPOSE 3000

CMD ["yarn", "start"]
