# istiolab

## Download the Guestbook app and create the Redis database

git clone https://github.com/fxnaranjo/istiolab.git --> Download the assets
cd guestbook/v2
oc create -f redis-master-deployment.yaml
oc create -f redis-master-service.yaml
oc create -f redis-slave-deployment.yaml
oc create -f redis-slave-service.yaml
oc get deployments ---> CHECK STATUS
oc get pods ---> CHECK STATUS

