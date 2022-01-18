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
3. open the browser and go to http://localhost:3000, you should see the express app running
4. make any changes to the helm chart and redeploy:
   helm upgrade nodeserver chart/nodeserver

tips: restart the docker client a few times if the kubernetes cluster could not be connected.
