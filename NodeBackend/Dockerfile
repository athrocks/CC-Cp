# Use a lightweight Node image
FROM node:14

# Create app directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of your app
COPY . .

# Expose the port your app runs on (adjust if needed)
EXPOSE 5000

# Start the app
CMD ["npm", "start"]
