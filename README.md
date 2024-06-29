# Recipe-App-API
This is a REST API built using Python, Django, Django REST Framework, Docker, GitHub Actions, PostgreSQL and Test Driven Development.

This is a fully functioning REST API that can handle:
- User authentication.
- Creating objects.
- Filtering and sorting objects.
- Uploading and viewing images.

# Local Development
### Running the project
This project runs using Docker. It should work consistently on Windows, MacOS and Linux machines. 
Follow the steps below to run a local development environment
1. Ensure you have Docker Desktop or Docker CLI (Engine) installed. You can download Docker from https://www.docker.com/products/docker-desktop/
2. Clone the project, `cd` to it in the Terminal/Command Prompt and run the following:
```sh
docker compose up
```
3. Browse the project at http://127.0.0.1:8000/api/health-check/
4. Browse the documentation of all the endpoints at http://127.0.0.1:8000/api/docs/
### Creating a superuser
To create a superuser to access the Django admin follow these steps:
1. Run the below command and follow the in terminal instructions:
```sh
docker compose run --rm app sh -c "python manage.py createsuperuser"
```
2.  Browse the Django admin at http://127.0.0.1:8000/admin and login.
### Clearing Storage
To clear all storage (including the database) and start fresh:

```sh
docker compose down --volumes
docker compose up
```
## Running the deployment server locally
To run the deployment server locally,
1. Ensure port 80 is not being used by any process. To check for processes using port 80, run the following command on Linux or MacOS:
   ```sh
   sudo lsof -i :80
   ```
   On Windows, run the following command:
   ```sh
   netstat -ano | findstr :80
   ```
2. Cd into the project directory, then copy the sample environment values:
   ```sh
   cp .env.sample .env
   ```
3. Start the deployment server:
   ```sh
   docker compose -f docker-compose-deploy.yml up
   ```
4. Browse the documentation of all the endpoints at http://127.0.0.1/api/docs
### Creating a superuser
To create a superuser to access the Django admin, follow these steps:
1. Run the following command and follow the in terminal instructions:
   ```sh
   docker compose -f docker-compose-deploy.yml run --rm app sh -c "python manage.py createsuperuser"
2.  Browse the Django admin at http://127.0.0.1/admin and login.
### Clearing Storage
To clear all storage (including the database) and start fresh, run the following command:
```sh
docker compose -f docker-compose-deploy.yml down --volumes
docker compose -f docker-compose-deploy.yml up
```
