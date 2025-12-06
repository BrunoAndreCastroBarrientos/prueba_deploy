# deploy/Dockerfile
FROM node:24-alpine AS runner
WORKDIR /app

ENV NODE_ENV=production \
    HOSTNAME=0.0.0.0 \
    PORT=3000

RUN addgroup -S nodejs \
    && adduser -S nextjs -G nodejs \
    && mkdir -p /app/logs \
    && chown -R nextjs:nodejs /app

# --------------------------
# Copiar la build subida
# --------------------------
COPY ./uploads/standalone ./        # server.js + node_modules
COPY ./uploads/static ./.next/static
COPY ./uploads/public ./public

USER nextjs
EXPOSE 3000

CMD ["node", "server.js"]
