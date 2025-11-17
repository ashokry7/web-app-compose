## App Components
- MySQL database container
- Two backend app containers
- Nginx load balancing container

The nginx load balancer container port 80 is mapped to the host port 8000. This container receives http traffic and forward it to the backend containers.
docker-compose file defines two replicas of the backend app. The `db-data` directory is used as a persistent storage for the MySQL container, so the data 
is not lost when containers are removed.

The backend container is a python flask app that accesses the database to display the rates and add new rates entered by users (and new movies).
