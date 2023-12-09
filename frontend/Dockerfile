# Stage 1: Build Angular app
FROM node:21-alpine as build
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build --prod

# Stage 2: Use Nginx to serve the build
FROM nginx:1.25.3-alpine

RUN rm -rf /usr/share/nginx/html/*
COPY --from=build /app/dist/angular-16-crud /usr/share/nginx/html
EXPOSE 80
ENTRYPOINT ["nginx", "-g", "daemon off;"]