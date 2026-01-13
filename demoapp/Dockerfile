# Build stage
FROM node:20-alpine AS build

WORKDIR /app

# Copy dependency files first (cache-friendly)
COPY package*.json ./
RUN npm install

# Copy the rest of the Vite project
COPY . .

# Build the Vite app
RUN npm run build


# Production stage
FROM nginx:alpine

# Copy Vite build to Nginx
COPY --from=build /app/dist /usr/share/nginx/html

# Expose web port
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
