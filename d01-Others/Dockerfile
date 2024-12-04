### BUILD STAGE
FROM node:16.0.0-alpine as build

# Set custom labels
LABEL maintainer="KMS Healthcare"
LABEL version="1.0"
LABEL description="A simple web application"

# Sets the working directory inside the container
WORKDIR /app

# Copy the dependencies config files to WORKDIR
# This is done BEFORE npm install for optimal caching
# Dependencies installation
COPY package*.json ./
RUN npm install

# Copy necessary files/directories to WORKDIR for build step
COPY . .

# Build artifact
RUN npm run build

### RUN STAGE
FROM nginx:1.23.3-alpine as production

# Copy artifact to nginx directory
COPY --from=build /app/dist /usr/share/nginx/html

RUN rm -f /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d/

# Expose necessary port
EXPOSE 80

# Start nginx
ENTRYPOINT ["nginx", "-g", "daemon off;"]
