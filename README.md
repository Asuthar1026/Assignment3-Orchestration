# Assignment3-Orchestration

### 1. Project Structure
Ensure that the project directory contains the following structure:



```
/loadbal
  - nginx.conf
  - Dockerfile

/web
  - index.html
  - Dockerfile

/docker-compose.yml
```

- **`index.html`**: This is the static HTML file served by the web service.
- **`Dockerfile` (for web service)**: Defines the Nginx web service image and configuration.
- **`nginx.conf`**: Configuration file for the Nginx load balancer.
- **`Dockerfile` (for load balancer)**: Defines the Nginx load balancer image.
- **`docker-compose.yml`**: The Docker Compose file orchestrates both services.

### 2. How to Run the Application

1. **Navigate to the project directory** on your local machine (where `docker-compose.yml` is located).

2. **Build and start the containers** by running the following command:
   ```bash
   docker-compose up --build
   ```

   This will build the Docker images for both the web service and the load balancer, and then start the containers.

### 3. Accessing the Services

- **Direct Access to Web Service**: Open your browser and navigate to:
  ```
  http://localhost:8084
  ```
  This is the direct access to the Nginx web service serving the static HTML page.

- **Access through Load Balancer**: Open your browser and navigate to:
  ```
  http://localhost:9091
  ```
  This is the access point where the Nginx load balancer forwards traffic to the web service.

### 4. Configuration

- **HTML Content**: The HTML response served by the web service is defined in the `web/index.html` file. You can modify this file to change the content.
  
- **Nginx Load Balancer**: The load balancer behavior is defined in `loadbal/nginx.conf`. You can modify the upstream or proxy settings in this file to scale the setup or change routing behavior.

### 5. Stopping the Application

To stop the running containers, use the following command:
```bash
docker-compose down

or 

docker-compose down --volumes --remove-orphans

```

This will stop and remove the containers but leave the images intact.

### 6. Modifications

- **Changing Ports**: If you'd like to expose the services on different ports, modify the `ports` section in the `docker-compose.yml` file.
- **Scaling**: To scale the web service (e.g., adding more replicas), you can modify the `docker-compose.yml` and specify multiple instances for the web service.

## Project Details

- **Web Service**: The web service is a simple Nginx container serving a static `index.html` page.
- **Load Balancer**: The Nginx load balancer forwards incoming requests to the web service. It listens on port 9091 (externally) and forwards traffic to the web service running on port 8084.
