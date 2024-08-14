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


==========================================



To create a `docker-compose.yml` file that avoids conflicts between two GeoNode apps on the same server and ensures they can be accessed through Nginx without issues, you'll need to set up each app with its own separate service and configure Nginx to properly route requests to the correct app. Here’s a step-by-step guide to help you achieve this:

### 1. Directory Structure

Assuming you have the following directory structure:

```
/path/to/geonode-app1
/path/to/geonode-app2
```

### 2. Docker Compose File

Create a `docker-compose.yml` file in the root directory of your project (or wherever you prefer). The file should look something like this:

```yaml
version: '3.8'

services:
  geonode-app1:
    image: geonode/geonode:latest
    container_name: geonode_app1
    environment:
      - DEBUG=False
      - DATABASE_URL=postgres://user:password@db1:5432/geonode1
    volumes:
      - /path/to/geonode-app1:/usr/src/app
    networks:
      - geonode_network

  geonode-app2:
    image: geonode/geonode:latest
    container_name: geonode_app2
    environment:
      - DEBUG=False
      - DATABASE_URL=postgres://user:password@db2:5432/geonode2
    volumes:
      - /path/to/geonode-app2:/usr/src/app
    networks:
      - geonode_network

  db1:
    image: postgres:13
    container_name: geonode_db1
    environment:
      - POSTGRES_DB=geonode1
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=password
    networks:
      - geonode_network
    volumes:
      - geonode_db1_data:/var/lib/postgresql/data

  db2:
    image: postgres:13
    container_name: geonode_db2
    environment:
      - POSTGRES_DB=geonode2
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=password
    networks:
      - geonode_network
    volumes:
      - geonode_db2_data:/var/lib/postgresql/data

  nginx:
    image: nginx:latest
    container_name: nginx
    ports:
      - "80:80"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
    networks:
      - geonode_network

networks:
  geonode_network:
    driver: bridge

volumes:
  geonode_db1_data:
  geonode_db2_data:
```

### 3. Nginx Configuration

Create an `nginx.conf` file in the same directory as your `docker-compose.yml`. Configure Nginx to handle requests for both GeoNode apps by setting up server blocks. Here’s an example:

```nginx
events {}

http {
    server {
        listen 80;
        server_name localhost;

        location /app1/ {
            proxy_pass http://geonode-app1:8000/;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }

        location /app2/ {
            proxy_pass http://geonode-app2:8000/;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
    }
}
```

In this configuration:

- Requests to `http://localhost/app1/` are proxied to `geonode-app1`.
- Requests to `http://localhost/app2/` are proxied to `geonode-app2`.

### 4. Running the Setup

1. **Place the `docker-compose.yml` and `nginx.conf` files in the same directory.**
2. **Navigate to that directory and run:**

   ```bash
   docker-compose up -d
   ```

This command will start the services in the background. Nginx will now route requests to the appropriate GeoNode application based on the URL path.

### Notes

- **Ensure that the ports specified in the `docker-compose.yml` file do not conflict with other services on your server.**
- **Adjust the `DATABASE_URL` environment variables as needed to match your database configuration.**
- **Customize Nginx configuration further if needed to handle specific application requirements or security considerations.**

This setup should provide a clear separation between the two GeoNode applications and allow you to access them without conflicts.



========================================



If each GeoNode application has its own `docker-compose.yml` file, you can manage them by setting up a reverse proxy with Nginx to route traffic to the correct application based on the URL path or subdomain. Here’s how to configure it:

### 1. Folder Structure

Assume your folders are structured like this:

```
/path/to/geonode-app1
/path/to/geonode-app2
```

Each folder has its own `docker-compose.yml` file:

```
/path/to/geonode-app1/docker-compose.yml
/path/to/geonode-app2/docker-compose.yml
```

### 2. Nginx Configuration

You will need a separate `nginx.conf` file to configure the reverse proxy. This file should be placed in a directory where Nginx can read it. Let’s assume you put it in `/path/to/nginx/nginx.conf`.

Here's an example `nginx.conf` that routes traffic to different GeoNode instances based on URL paths:

```nginx
events {}

http {
    upstream geonode_app1 {
        server 127.0.0.1:8001;
    }

    upstream geonode_app2 {
        server 127.0.0.1:8002;
    }

    server {
        listen 80;
        server_name localhost;

        location /app1/ {
            proxy_pass http://geonode_app1/;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }

        location /app2/ {
            proxy_pass http://geonode_app2/;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
    }
}
```

### 3. Docker Compose for Each GeoNode App

#### For GeoNode App 1:

Create or update `/path/to/geonode-app1/docker-compose.yml`:

```yaml
version: '3.8'

services:
  geonode:
    image: geonode/geonode:latest
    container_name: geonode_app1
    ports:
      - "8001:8000"  # Maps container port 8000 to host port 8001
    environment:
      - DEBUG=False
      - DATABASE_URL=postgres://user:password@db1:5432/geonode1
    volumes:
      - /path/to/geonode-app1:/usr/src/app
    networks:
      - geonode_network

  db1:
    image: postgres:13
    container_name: geonode_db1
    environment:
      - POSTGRES_DB=geonode1
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=password
    volumes:
      - geonode_db1_data:/var/lib/postgresql/data

networks:
  geonode_network:
    driver: bridge

volumes:
  geonode_db1_data:
```

#### For GeoNode App 2:

Create or update `/path/to/geonode-app2/docker-compose.yml`:

```yaml
version: '3.8'

services:
  geonode:
    image: geonode/geonode:latest
    container_name: geonode_app2
    ports:
      - "8002:8000"  # Maps container port 8000 to host port 8002
    environment:
      - DEBUG=False
      - DATABASE_URL=postgres://user:password@db2:5432/geonode2
    volumes:
      - /path/to/geonode-app2:/usr/src/app
    networks:
      - geonode_network

  db2:
    image: postgres:13
    container_name: geonode_db2
    environment:
      - POSTGRES_DB=geonode2
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=password
    volumes:
      - geonode_db2_data:/var/lib/postgresql/data

networks:
  geonode_network:
    driver: bridge

volumes:
  geonode_db2_data:
```

### 4. Running the Applications

1. **Start GeoNode App 1:**

   ```bash
   cd /path/to/geonode-app1
   docker-compose up -d
   ```

2. **Start GeoNode App 2:**

   ```bash
   cd /path/to/geonode-app2
   docker-compose up -d
   ```

3. **Configure and Start Nginx:**

   - Create a Docker container for Nginx or install Nginx on your server.
   - Ensure Nginx has access to the `nginx.conf` file you created.
   - If using Docker for Nginx, create a `docker-compose.yml` for Nginx in a separate directory:

     ```yaml
     version: '3.8'

     services:
       nginx:
         image: nginx:latest
         container_name: nginx
         ports:
           - "80:80"
         volumes:
           - /path/to/nginx/nginx.conf:/etc/nginx/nginx.conf
         networks:
           - geonode_network

     networks:
       geonode_network:
         external: true
     ```

   - **Start Nginx:**

     ```bash
     cd /path/to/nginx
     docker-compose up -d
     ```

### Summary

- **Each GeoNode app runs on its own port** (e.g., 8001 and 8002).
- **Nginx** listens on port 80 and routes traffic based on the URL path.
- **Docker Compose files** for each app specify different ports and configurations.

This setup ensures that each GeoNode application can be accessed without conflict, with Nginx handling the routing based on the URL path. Adjust paths and configuration as needed for your specific environment and requirements.

