# Summary

## **Objective**

The primary goal of this session was to set up the local database environment required for the first exercise on Dimensional Data Modeling in the DataExpert.io Data Engineering Bootcamp.

## **Key Resources**

*   **The Data Engineering Handbook:** A free resource that contains the course materials.
*   **GitHub Repository:** Contains the necessary files and instructions for the setup.

## **Setup Options**

There were two primary methods for setting up the PostgreSQL database:
1.  **Local Installation:** Installing PostgreSQL directly on the host machine.
2.  **Docker Installation:** Running PostgreSQL inside a Docker container.

The speaker chose the Docker method to avoid cluttering their local machine and to allow for easy removal of the environment later.

## **Step-by-Step Setup Guide**

Here is a summary of the steps taken to get the environment up and running:

1.  **Clone the Repository:** The first step, completed before the stream, was to clone the course's GitHub repository to the local machine.

2.  **Environment Configuration:**
    *   The project uses an `.env` file to manage configuration variables like database credentials, ports, and container names.
    *   This file is created from the provided `example.env` template.

3.  **Docker Compose for PostgreSQL:**
    *   The `docker-compose.yml` file is used to define and run the multi-container Docker application.
    *   It defines the PostgreSQL service, specifying the official Postgres image, container name, and port mappings.
    *   The speaker initiated the service by running the `docker-compose up` command.

4.  **Customization: Adding pgAdmin:**
    *   The initial `docker-compose.yml` file did not include a database management tool.
    *   To avoid a local installation, the speaker decided to add a `pgAdmin` service directly to the `docker-compose.yml` file. 
    *   This involved adding new environment variables for the pgAdmin login credentials (`PGADMIN_DEFAULT_EMAIL`, `PGADMIN_DEFAULT_PASSWORD`) to the `.env` file. 

5.  **Troubleshooting:**
    *   After launching the services, the pgAdmin web interface was not immediately available.
    *   The speaker initially suspected a configuration error and began searching for solutions online. 
    *   However, the issue resolved itself after a short wait, indicating that the pgAdmin container simply needed more time to initialize. The speaker noted they were just being "impatient".

6.  **Verification:**
    *   The speaker successfully logged into the pgAdmin interface using the credentials defined in the `.env` file.
    *   From within pgAdmin, they connected to the PostgreSQL database instance.
    *   Finally, they confirmed that the required tables were created and populated in the database, verifying the setup was complete and successful.

## **Final Configuration Summary**

*   **Services:** The final environment consists of two services managed by Docker Compose: `postgres` and `pgadmin`.
*   **Persistence:** The speaker prefers containerized tools like pgAdmin over local installations to keep their machine clean and make teardown easier.
*   **Outcome:** The setup was successfully prepared for the upcoming lesson on data modeling.