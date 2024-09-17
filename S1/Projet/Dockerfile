FROM node:lts-alpine as build-stage
WORKDIR /app
COPY portfolio/package*.json ./
COPY portfolio/. .
RUN npm install
RUN npm run build

# production stage
FROM nginx:stable-alpine AS production-stage
COPY --from=build-stage ../dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]