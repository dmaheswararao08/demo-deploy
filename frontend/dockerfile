FROM node:14 as build

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json to the container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Build the React app
RUN npm run build

# Stage 2: Serve the React application with Node.js
FROM node:14-alpine

# Set the working directory
WORKDIR /app

# Copy build output from Stage 1 to Stage 2
COPY --from=build /app/build ./build

# Expose port 3000 to the outside world
EXPOSE 3000

# Command to run the React app
CMD ["node", "./build/index.js"]
