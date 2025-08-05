# Stage 1: Build the Angular app
FROM node:20 AS builder

WORKDIR /app
COPY . .

RUN npm install
RUN npm run build -- --configuration production

# Stage 2: Serve using Nginx
FROM nginx:alpine

COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/dist/ticketing-application/browser /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
