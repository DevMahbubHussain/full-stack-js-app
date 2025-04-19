# Use a lightweight Node.js image
FROM node:14.16.0-alpine3.13

# Create app user and group
RUN addgroup -S app && adduser -S app -G app

# Set working directory
WORKDIR /app

# Install dependencies first to leverage Docker layer caching
COPY package*.json ./
RUN npm install

# Copy rest of the code
COPY . .

# Change to non-root user
RUN chown -R app:app /app
USER app

# Expose app port (React default is 3000)
EXPOSE 3001

# Set environment variable
ENV NODE_ENV=development

# Start the app using development script (e.g. for React: `npm start`)
CMD ["npm", "start"]