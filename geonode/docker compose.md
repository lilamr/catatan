To set up a `docker-compose.yml` file for two apps that both use Nginx on the same server, you need to configure a multi-container Docker setup. Each app will run in its own container, and Nginx will be configured to proxy requests to the appropriate app based on the domain or path.

Here's a basic example of how you can set this up. In this example, we'll assume you have two apps: `app1` and `app2`, and we'll use Nginx as a reverse proxy to route traffic to each app based on the domain name.

1. **Directory Structure**:
   ```
   ├── docker-compose.yml
   ├── nginx
   │   └── nginx.conf
   ├── app1
   │   └── Dockerfile
   └── app2
       └── Dockerfile
   ```

2. **`docker-compose.yml`**:
   ```yaml
   version: '3.8'

   services:
     nginx:
       image: nginx:latest
       container_name: nginx
       ports:
         - "80:80"
       volumes:
         - ./nginx/nginx.conf:/etc/nginx/nginx.conf
       depends_on:
         - app1
         - app2

     app1:
       build:
         context: ./app1
       container_name: app1
       expose:
         - "8001"  # The port that the app listens on inside the container

     app2:
       build:
         context: ./app2
       container_name: app2
       expose:
         - "8002"  # The port that the app listens on inside the container
   ```

3. **`nginx/nginx.conf`**:
   ```nginx
   events {}

   http {
       server {
           listen 80;

           server_name app1.example.com;

           location / {
               proxy_pass http://app1:8001;
               proxy_set_header Host $host;
               proxy_set_header X-Real-IP $remote_addr;
               proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
               proxy_set_header X-Forwarded-Proto $scheme;
           }
       }

       server {
           listen 80;

           server_name app2.example.com;

           location / {
               proxy_pass http://app2:8002;
               proxy_set_header Host $host;
               proxy_set_header X-Real-IP $remote_addr;
               proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
               proxy_set_header X-Forwarded-Proto $scheme;
           }
       }
   }
   ```

4. **`app1/Dockerfile`**:
   ```Dockerfile
   # Use an appropriate base image for your app
   FROM node:14

   # Set working directory
   WORKDIR /usr/src/app

   # Copy application code
   COPY . .

   # Install dependencies
   RUN npm install

   # Expose the port your app runs on
   EXPOSE 8001

   # Start the application
   CMD ["npm", "start"]
   ```

5. **`app2/Dockerfile`**:
   ```Dockerfile
   # Use an appropriate base image for your app
   FROM node:14

   # Set working directory
   WORKDIR /usr/src/app

   # Copy application code
   COPY . .

   # Install dependencies
   RUN npm install

   # Expose the port your app runs on
   EXPOSE 8002

   # Start the application
   CMD ["npm", "start"]
   ```

### Notes:
- Adjust the `Dockerfile` configurations according to the technology stack used by your applications.
- Replace `app1.example.com` and `app2.example.com` with your actual domain names.
- Make sure to configure your DNS or `/etc/hosts` file to resolve these domain names to your server’s IP address.

This setup uses Nginx as a reverse proxy to forward traffic based on the `server_name` directive, directing requests to the correct application container. The `depends_on` option ensures that Nginx starts after the application containers are up.

=============================

To set up a `docker-compose.yml` file for two apps that use Nginx as a reverse proxy on the same server and can be accessed through `localhost`, you need to configure Nginx to route traffic to each app based on a URL path or port.

Here’s an example where Nginx routes traffic to `app1` and `app2` based on URL paths (`/app1` and `/app2`):

### Directory Structure
```
├── docker-compose.yml
├── nginx
│   └── nginx.conf
├── app1
│   └── Dockerfile
└── app2
    └── Dockerfile
```

### `docker-compose.yml`
```yaml
version: '3.8'

services:
  nginx:
    image: nginx:latest
    container_name: nginx
    ports:
      - "8080:80"  # Expose port 8080 on localhost
    volumes:
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf
    depends_on:
      - app1
      - app2

  app1:
    build:
      context: ./app1
    container_name: app1
    expose:
      - "8001"  # Port that the app listens on inside the container

  app2:
    build:
      context: ./app2
    container_name: app2
    expose:
      - "8002"  # Port that the app listens on inside the container
```

### `nginx/nginx.conf`
```nginx
events {}

http {
    server {
        listen 80;

        # Route requests to /app1 to app1 container
        location /app1/ {
            proxy_pass http://app1:8001/;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }

        # Route requests to /app2 to app2 container
        location /app2/ {
            proxy_pass http://app2:8002/;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
    }
}
```

### `app1/Dockerfile`
```Dockerfile
# Use an appropriate base image for your app
FROM node:14

# Set working directory
WORKDIR /usr/src/app

# Copy application code
COPY . .

# Install dependencies
RUN npm install

# Expose the port your app runs on
EXPOSE 8001

# Start the application
CMD ["npm", "start"]
```

### `app2/Dockerfile`
```Dockerfile
# Use an appropriate base image for your app
FROM node:14

# Set working directory
WORKDIR /usr/src/app

# Copy application code
COPY . .

# Install dependencies
RUN npm install

# Expose the port your app runs on
EXPOSE 8002

# Start the application
CMD ["npm", "start"]
```

### Notes:
- **Accessing Apps**: After running `docker-compose up`, you can access `app1` at `http://localhost:8080/app1` and `app2` at `http://localhost:8080/app2`.
- **Path Adjustments**: If your apps don’t handle paths (like `/app1` or `/app2`), you may need to adjust the configuration or app code to properly handle these paths. Alternatively, you can configure Nginx to route requests to different ports if you prefer not to use path-based routing.
- **DNS and Port Configuration**: Adjust the port and path configurations based on your needs. For example, if you want to use different ports instead of paths, modify the `nginx.conf` and `docker-compose.yml` accordingly.

This setup allows you to access both apps through `localhost` with Nginx acting as a reverse proxy to route traffic to the correct application.