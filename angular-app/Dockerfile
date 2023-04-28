FROM node:18.16.0-alpine

WORKDIR '/app'
COPY package*.json ./
RUN npm ci
COPY . .

RUN npx ng build --prod angular-app
FROM nginx
EXPOSE 80

COPY --from=builder /app/dist/angular-app /usr/share/nginx/html