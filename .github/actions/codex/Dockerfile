FROM node:lts-alpine

# Add build argument for API key
ARG OPENAI_API_KEY
ENV OPENAI_API_KEY=${OPENAI_API_KEY}

WORKDIR /usr/src/app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application code
COPY . .

# Expose port
EXPOSE 3000

# Set proper permissions
RUN chown -R node /usr/src/app
USER node

# Start the application
CMD ["npm", "start"]
