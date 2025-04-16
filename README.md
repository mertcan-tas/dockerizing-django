# Dockerize Your Django Project

This repository provides a boilerplate setup to Dockerize your Django project using PostgreSQL, Redis, and Nginx. This configuration helps you create a consistent and isolated environment for your development and production needs.

**Key Features:**

* **Django:** A popular, high-level Python web framework.
* **PostgreSQL:** A powerful, open-source relational database system.
* **Redis:** A high-performance, key-value in-memory data structure store (often used for caching and queueing).
* **Nginx:** A lightweight and high-performance web server and reverse proxy.
* **Docker Compose:** A tool for defining and running multi-container Docker applications.

**Setup:**

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/mertcan-tas/dockerizing-django.git
    ```

    This command will download the boilerplate code to your local machine.

2.  **Run the script to generate the .env file:**

    ```bash
    python genenv.py .env-copy > .env
    ```

    This script creates a copy of the `.env-copy` file and saves it as `.env`. The `.env` file contains your environment variables such as database connection details, secret keys, etc. Please edit this file according to your needs.

3.  **Running the Project:**

    ```bash
    docker-compose build
    docker-compose up -d
    ```

    * `docker-compose build`: Builds the Docker images based on the instructions defined in the Dockerfiles. This process includes installing necessary dependencies and configurations for the Django application, PostgreSQL, Redis, and Nginx.
    * `docker-compose up -d`: Starts the containers in the background (`-d` flag stands for detached mode) using the built images.

4.  **Collect Static Files:**

    ```bash
    docker-compose exec web python manage.py collectstatic --noinput
    ```

    This command collects all the static files (CSS, JavaScript, images, etc.) from your Django application into a central location. `docker-compose exec web` ensures that this command is executed inside the `web` service's container (where your Django application is running). The `--noinput` flag prevents any prompts and allows the process to complete automatically.

After completing these steps, your Django project will be running inside Docker containers. You can usually access your project in your browser at [http://0.0.0.0:8000/](http://0.0.0.0:8000/) (this might vary depending on your Nginx configuration).

This boilerplate provides a solid foundation for Dockerizing your Django projects. You can customize the Dockerfiles, `docker-compose.yml` file, and other configuration files according to your specific requirements.
