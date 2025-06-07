FROM node:20-alpine
ENV NODE_ENV=development
RUN npm install -g pnpm

WORKDIR /app

COPY ["package.json", "pnpm-lock.yaml", "pnpm-workspace.yaml", "./"]
COPY frontend/package.json ./frontend/

RUN pnpm install --frozen-lockfile

COPY . .

CMD pnpm run --filter frontend dev