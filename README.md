# chatapp

An example chat application

## Usage
The [`chatapp.yaml`](./chatapp.yaml) file describes the Kubernetes objects for the application. Please use the following commands to deploy the chat application to the namespace `chatapp` on a Kubernetes cluster. 

```
kubectl create namespace chatapp
kubectl apply -f chatapp.yaml -n chatapp
```
The frontend service has a NodePort value of `30222`. You can access the application by going to the address `http://MASTER_IP:30222`

Please note that you need to replace `MASTER_IP` with the IP of your master node.

## Artifacts
### Backend
The [chatapp-backend](./chatapp-backend) directory contains the source code for the backend service, which implements a WSGI web application served by uWSGI and is containerized with Docker. The WSGI application implements backend logics and binds to a TCP socket on port `14222`.

You can use the following commands to build the Docker image.
```
cd chatapp-backend
docker build -t harbor.pacslab.ca/eecs4222/chatapp-backend .
```

### Frontend
The [chatapp-frontend](./chatapp-frontend) directory contains the source code for the frontend service, which containerizes and leverages NGINX as both a web server to serve static files and a uWSGI (WebSocket) proxy. The web server listens on port `4222`.

You can use the following commands to build the Docker image.
```
cd chatapp-frontend
docker build -t harbor.pacslab.ca/eecs4222/chatapp-frontend .
```

## Note
*Important*: This is an example program that is intentionally minimalist and by no means guaranteed to be complete, robust, or follow the best practice.
