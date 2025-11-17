## App Components
- MySQL database container (ashokry32/cinemarates:latest)
- Two backend app containers (ashokry32/webcinema:latest)
- Nginx load balancing container (ashokry32/nginlb:latest)

The nginx load balancer container port 80 is mapped to the host port 8000. This container receives http traffic and forward it to the backend containers.
docker-compose file defines two replicas of the backend app. The `db-data` directory is used as a persistent storage for the MySQL container, so the data 
is not lost when containers are removed.

The backend container is a python flask app that accesses the database to display the rates and add new rates entered by users (and new movies).

docker compose file defines two bridge networks, front-end network for communication between the load balancer and the backend python app, and another 
a back-end container for the backend and MySQL containers.
