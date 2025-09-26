# ---- Build Stage ----
FROM node:20 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# ---- Run Stage ----
FROM nginx:alpine
WORKDIR /usr/share/nginx/html
COPY --from=build /app/dist .   # React (Vite) build goes to dist/
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
