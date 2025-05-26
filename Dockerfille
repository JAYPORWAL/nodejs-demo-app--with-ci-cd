# Use official Node.js base image
FROM node:18
# Create app directory
WORKDIR /usr/src/app
# Install dependencies
COPY package*.json ./
RUN npm install
# Bundle app source
COPY . .
# App runs on port 3000
EXPOSE 3000
# Run the app
CMD ["node", "index.js"]