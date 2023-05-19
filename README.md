# Opperation repo for the Remla project
Here you can find the files for starting the project using helm and kubernetes. It is also possible to use docker-compose using the docker-compose.yml


## Using k8s
First start a kubernetes cluster using `minikube start` and start up prometheus if this is not running already.
To create a tunnel we first have to enable the ingress addon using the following command:
```
minikube addons enable ingress
```
Then run `minikube tunnel`

### Manual start up using kubectl
Add all services to the running cluster by using the command:
```
kubectl apply -f .\operations.yml
```
This also automaticly exposes the grafana dashboard at http://grafana.localhost
To view the prometheus page you have to expose the port manualy using the following command:
```
minikube service myprom-kube-prometheus-sta-prometheus --url
```
You should be able to acces the webservice at http://localhost and the grafana dashboard at http://grafana.localhost

A template grafana dashboard can be imported with the json file: `/grafana/RestaurantSentiment.json`. 

### Start up using helm
You can then install the helm chart using:
```
helm install sentiment oci://ghcr.io/remla23-team01/operation/charts/sentimentchart
```
You should be able to acces the webservice at http://localhost and the grafana dashboard at http://grafana.localhost


## Start up using docker compose

Using docker compose the backend and frontend of the application are pulled from the docker registry and runs them.

To run the application use `docker-compose up -d`

You can then classify restaurant reviews at http://localhost:8081
