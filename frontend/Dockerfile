FROM node:24-alpine AS build

WORKDIR /app

COPY package.json ./
RUN npm install
COPY . .
EXPOSE 5173

ARG VITE_API_URL
ENV VITE_API_URL=$VITE_API_URL

RUN npm run build

# static for production
FROM nginx:1-alpine AS production
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]