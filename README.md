# cloud native express application

Cloud Native Development with Node.js, Docker, and Kubernetes

Steps to run(you should have docker installed and kubernetes enabled):

Run with docker:

1. cd myapp
2. build the app into a docker image:
   docker build -t nodeserver -f Dockerfile .
3. run a docker container from the image:
   docker run -ti -p 3000:3000 nodeserver
4. open the browser and go to http://localhost:3000, you should see the express app running

Run with kubernetes(Helm):
After finishing the previous steps running with docker:

1. cd myapp
2. deploy docker image to kubernetes and run the express app:
   helm install nodeserver chart/nodeserver
3. make any changes to the helm chart and redeploy:
   helm upgrade nodeserver chart/nodeserver
4. check and see if all three pods are running:
   kubectl get pods
5. check exposed port, eg. 30524, from the service:
   kubectl get services
6. open the browser and go to http://localhost:30524, you should see the express app running
7. use http://localhost:30524/ready or http://localhost:30524/live to check the readiness and liveness of the app
8. use http://localhost:30524/metrics to see the metrics of the app
9. install Prometheus and Grafana to see the metrics of the app: https://artifacthub.io/packages/helm/prometheus-community/prometheus | https://artifacthub.io/packages/helm/grafana/grafana
10. use zipkin for opentracing: https://artifacthub.io/packages/helm/carlosjgp/zipkin

tips: restart the docker client a few times if the kubernetes cluster could not be connected.
