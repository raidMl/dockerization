FROM node:20-alpine

# Create a user with permissions to run the app
RUN addgroup app && adduser -S -G app app

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json and set ownership
COPY package*.json ./

# Install dependencies as root
USER root
RUN npm install

# Change ownership of node_modules to app user
RUN chown -R app:app /app/node_modules

# Copy the rest of the files and set ownership
COPY --chown=app:app . .

# Expose port 5173
EXPOSE 5173

# Switch back to the app user
USER app
CMD ["npm", "run", "dev"]
