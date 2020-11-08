FROM node:latest  as frontend-image
WORKDIR /app
COPY frontend/package*.json ./
RUN npm install --production
COPY frontend/ ./
RUN npm run build

FROM nginx:stable-alpine
COPY --from=frontend-image /app/dist /app
COPY ../nginx.conf /etc/nginx/nginx.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;" ]
