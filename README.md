# Opperation repo for the Remla project
Here you can find the files for starting the project using helm and kubernetes. It is also possible to use docker-compose using the docker-compose.yml


## Start up using helm
First make sure you have a kubernetes cluster running using `minikube start` and enabled the ingress addon using `minikube addons enable ingress`

You can then install the helm chart using:
```
helm install sentiment oci://ghcr.io/remla23-team01/operation/charts/sentimentchart
```
After setting up a tunnel using `minikube tunnel` you should be able to acces the webservice at http://localhost

If you want to have a look at the flask api using swagger go to http://localhost:8080/apidocs

## Start up using docker compose

Using docker compose the backend and frontend of the application are pulled from the docker registry and runs them.

To run the application use `docker-compose up -d`

You can then classify restaurant reviews at http://localhost:8081
