# Install Apache Airflow with Docker
### Service definitions
- **airflow-scheduler** - The scheduler monitors all tasks and DAGs, then triggers the task instances once their dependencies are complete.
- **airflow-webserver** - The webserver available at http://localhost:8080.
- **airflow-worker** - The worker that executes the tasks given by the scheduler.
- **airflow-init** - The initialization service.
- **flower** - The flower app for monitoring the environment. It is available at http://localhost:5555.
- **postgres** - The database.
- **redis** - The redis - broker that forwards messages from scheduler to worker.

### Prerequisite 
- Install **Docker Community Edition (CE)** on your workstation. Depending on the OS, you may need to configure your Docker instance to use 4.00 GB of memory for all containers to run properly. 
- Install **Docker Compose v1.29.1 and newer** on your workstation.

##### Below directories in the container are mounted, which means that their contents are synchronized between your computer and the container.
- **./dags** - you can put your DAG files here.
- **./logs** - contains logs from task execution and scheduler.
- **./plugins** - you can put your custom plugins here.

Manually create the  **_.env_** file in the same folder your docker-compose.yaml is placed. In this file add the following lines
```sh
 AIRFLOW_IMAGE_NAME=apache/airflow:2.3.0
 AIRFLOW_UID=50000
```

## Start Airflow
```sh
docker-compose up
Or
docker-compose up -d
```
## Access the web portal
- The webserver is available at: **_http://localhost:8080_** The default account has the login **airflow** and the password **airflow**
- 
## Stop Airflow
```sh
docker-compose down
```

## Clean up
- Run below mentioned command to **stop and delete containers, delete volumes with database data and download images**
```sh
docker-compose down --volumes --rmi all
```
