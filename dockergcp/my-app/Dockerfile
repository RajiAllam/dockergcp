# Stage 0 - Build Frontend Assets
FROM node:12.16.3-alpine as build

WORKDIR /app

COPY . ./
RUN npm install
RUN npm run build

# server environment
FROM nginx:alpine
COPY nginx.conf /etc/nginx/conf.d/configfile.template

COPY --from=build /app/build /usr/share/nginx/html

ENV PORT 8080
ENV HOST 0.0.0.0
EXPOSE 8080
CMD ["nginx", "-g", "daemon off;"]
