# Stage 1 - Build Stage
FROM node:24-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm ci --omit=dev

COPY . .

# Stage 2 - Runtime Stage
FROM node:24-alpine

LABEL maintainer="Rahul Sharma"
LABEL project="SMAITIC DevOps Assignment"
LABEL version="3.0"

WORKDIR /app

COPY --from=builder /app /app

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

USER appuser

EXPOSE 3000

HEALTHCHECK --interval=30s --timeout=5s --start-period=10s --retries=3 \
CMD wget --spider -q http://localhost:3000/health || exit 1

CMD ["npm","start"]