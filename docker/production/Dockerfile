FROM node:20-alpine

RUN npm install -g pnpm

WORKDIR /app

COPY ["package.json", "pnpm-lock.yaml", "pnpm-workspace.yaml", "./"]
COPY frontend/package.json frontend/

RUN pnpm install --frozen-lockfile

COPY . .

RUN pnpm run -r build

FROM nginx:1.28-alpine

COPY --from=0 /app/frontend/dist /usr/share/nginx/html
COPY docker/production/nginx.conf /etc/nginx/conf.d/default.conf
