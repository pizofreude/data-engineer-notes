# Lab Notes

Since I'm using Windows, Docker Desktop, and have local PostgreSQL with PGAdmin, I had to make a few adjustments to the lab instructions:
- I had to use `host portnumber=5433` instead of `host portnumber=5432` to avoid conflicts with the default port between Docker and my local PostgreSQL.
- File changes:
  - Make a copy of `example.env` and name it `.env` and set the `HOST_PORT=5433` instead of `5432`.
  - Make changes to `docker-compose.yml` to set pgadmin container name to `pgadmin3` instead of `pgadmin` to avoid conflict with my other pgadmin instance:
    ```yaml
    container_name: pgadmin3
    ```
## Lab 0 Solution

### Running Docker Compose

In the correct directory, run:

```bash
docker-compose up -d
```

### pgAdmin Server Setup

Once the docker container is up and running, open pgAdmin in your browser and set up a new server connection via `localhost:5050`.
Then, configure the database server by Servers > Register > Server:
- General -> Name: data_expert_data_modeling
- Connection:
  -  Host name/address: host.docker.internal
  -  Port: 5433
  -  Maintenance database: postgres
  -  Username: postgres
  -  Password: postgres
             
### Tables not showing up in pgAdmin

#### 🐳 For Docker Users

Get your running containers:

```bash
docker ps
```

Copy the name of your Postgres container (e.g., `my-postgres-container`)

Open a bash terminal inside it:

```bash
docker exec -it my-postgres-container bash
```

Run the restore manually from inside the container:

```bash
pg_restore -U $POSTGRES_USER -d $POSTGRES_DB /docker-entrypoint-initdb.d/data.dump
```

✅ Replace `$POSTGRES_USER` and `$POSTGRES_DB` with actual values from your `.env` file if needed.

Optionally check if tables are loaded:

```bash
psql -U postgres -d postgres -c '\dt'
```

This shows all the tables in the current schema. [Reference](https://github.com/DataExpert-io/data-engineer-handbook/tree/main/bootcamp/materials/1-dimensional-data-modeling#-for-docker-users).

