# Use Nginx base image
FROM nginx:alpine

# Set working directory
WORKDIR /usr/share/nginx/html

# Remove default content
RUN rm -rf ./*

# Copy Angular build output
COPY dist/frontend/ .

# Optional: replace default nginx config to support Angular routing
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]

