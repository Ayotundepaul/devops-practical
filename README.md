# Swimlane DevOps Practical

Create a Kubernetes Cluster using Rancher Desktop
Download and install Rancher Desktop from https://rancherdesktop.io/.
Open Rancher Desktop and follow the instructions to set up your Kubernetes cluster.

git clone https://github.com/swimlane/devops-practical.git
cd devops-practical

Create a Dockerfile in the root directory of the repository:

Build the Docker image 
docker build -t devops-practical .

create a docker-compose file that ensures:

The application (app) and MongoDB (mongo) are both running as Docker containers and can communicate with each other.

The two services are on the same custom bridge network (app-network), which allows them to communicate using their service names as hostnames. Your application can refer to MongoDB by using mongo as the hostname.

The ports are mapped so that you can access your application through port 3000 on your host machine, and if needed, access MongoDB through port 27017.

created mongo.yml file 

In Kubernetes pod, the application is expecting to connect to MongoDB on a host called mongo, just like it did in the Docker Compose environment. 

Kubernetes uses a different approach for service discovery. Instead of referring to other services by their container name, as you would in Docker Compose, you would refer to them by their service name.

Create a MongoDB service in the same namespace as the application, with the name mongo.

create the deployment and service using the kubectl apply -f mongo.yml, 

Helm 

helm create devops-practical 

helm install devops-practical ./devops-practical