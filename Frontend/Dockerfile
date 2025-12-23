# Build stage
FROM node:18-alpine AS builder
WORKDIR /app

# Copy lockfile and package manifest first to leverage layer caching
COPY package*.json ./
COPY tsconfig.json tsconfig.node.json vite.config.ts ./

# Use npm ci for reproducible installs if lockfile exists, otherwise fallback to npm install
ARG NODE_ENV=production
ENV NODE_ENV=${NODE_ENV}
RUN if [ -f package-lock.json ]; then npm ci --production=false; else npm install; fi

COPY src ./src
COPY index.html ./

RUN npm run build

# Production stage
FROM nginx:stable-alpine AS runner

# Remove default nginx content and copy built site
RUN rm -rf /usr/share/nginx/html/*
COPY --from=builder /app/dist /usr/share/nginx/html

# Use a lightweight healthcheck
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
    CMD wget --no-verbose --tries=1 --spider http://localhost/ || exit 1

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
