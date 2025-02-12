# Vikunja Docker Setup

This repository contains the Docker setup for **Vikunja**, a self-hosted task management system. Follow the instructions below to clone the repo, configure the environment variables, and start the application using Docker.

## **Steps to Set Up Vikunja Docker**

### 1. **Clone the Repository**

Start by cloning the repository to your local machine.

```bash
git clone https://github.com/kahnu044/vikunja-docker.git
cd vikunja-docker
```

### 2. **Update the `.env` File**

Create a `.env` file in the root directory of the cloned repository or modify the existing `.env` file.

Here is a template for the `.env` file:

```ini
# Vikunja Configuration
VIKUNJA_SERVICE_PUBLICURL=http://localhost:3456
VIKUNJA_DATABASE_HOST=db
VIKUNJA_DATABASE_TYPE=mysql
VIKUNJA_DATABASE_USER=vikunja
VIKUNJA_DATABASE_PASSWORD=changeme
VIKUNJA_DATABASE_DATABASE=vikunja
VIKUNJA_SERVICE_JWTSECRET=super-secure-random-secret

# Vikunja API Port (Change if needed)
VIKUNJA_PORT=3456

# MariaDB Configuration
MYSQL_ROOT_PASSWORD=supersecret
MYSQL_USER=vikunja
MYSQL_PASSWORD=changeme
MYSQL_DATABASE=vikunja
```

Update the following in your `.env` file:
- **VIKUNJA_SERVICE_PUBLICURL:** The public URL where Vikunja will be reachable (typically `http://localhost:3456` for local setups).
- **VIKUNJA_SERVICE_JWTSECRET:** A randomly generated secret key to secure your Vikunja API.
- **VIKUNJA_PORT:** The port on which Vikunja API will be accessible. The default is `3456`.
- **Database credentials:** Make sure to update `MYSQL_ROOT_PASSWORD`, `MYSQL_USER`, `MYSQL_PASSWORD`, and `MYSQL_DATABASE` for MariaDB as per your requirements.

### 3. **Start the Services**

Once the `.env` file is updated, you can start the Docker services.

Run the following command to start Vikunja and the database:

```bash
docker-compose up -d
```

This will:
- Pull the required images for Vikunja and MariaDB.
- Start the Vikunja API service on the specified port.
- Start MariaDB and initialize the database with the provided credentials.

### 4. **Access Vikunja**

Once the services are up and running, you can access Vikunja by navigating to:

```
http://localhost:3456
```

You should be able to see the Vikunja web interface.

### 5. **Stop the Services**

If you need to stop the services, run the following command:

```bash
docker-compose down
```

This will stop and remove the containers.

## **Additional Configuration**

### **Changing Ports**

To change the port Vikunja is running on, simply modify the `VIKUNJA_PORT` in the `.env` file and restart the services:

```bash
docker-compose down
docker-compose up -d
```
