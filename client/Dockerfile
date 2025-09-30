# FROM node:20-alpine

# WORKDIR /app

# COPY package*.json ./

# RUN npm install 

# COPY . .

# RUN npm run build

# EXPOSE 5173

# CMD ["npm", "run", "preview"]


# Build stage
FROM node:20-alpine AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Production stage
FROM node:20-alpine

WORKDIR /app

# Install serve to run the built app
RUN npm install -g serve

# Copy built files from builder stage
COPY --from=builder /app/dist ./dist

EXPOSE 5173

CMD ["serve", "-s", "dist", "-l", "5173"]