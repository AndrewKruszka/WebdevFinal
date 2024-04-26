# Use the official Node.js image to build the Angular project
FROM node:16 as build

# Set the working directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json (or yarn.lock) to the working directory
COPY package*.json ./

# Install project dependencies
RUN npm install

# Copy the Angular project files into the working directory
COPY . .

# Build the project for production
RUN npm run build

# Use the official nginx image as a base for the production environment
FROM nginx:alpine

# Copy the build output from the build stage to the nginx server
COPY --from=build /usr/src/app/dist/webdev_final /usr/share/nginx/html

# Expose the port nginx is reachable on
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
