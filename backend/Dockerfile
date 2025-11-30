FROM node:24-alpine AS build

WORKDIR /app

COPY package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM node:24-alpine AS production
WORKDIR /app
COPY --from=build /app /app
EXPOSE 5000
CMD ["npm", "start"]