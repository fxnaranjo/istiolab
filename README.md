# istiolab

## Download the Guestbook app and create the Redis database

- `git clone https://github.com/fxnaranjo/istiolab.git` --> Download the assets
- `cd guestbook/v2`
- `oc create -f redis-master-deployment.yaml`
- `oc create -f redis-master-service.yaml`
- `oc create -f redis-slave-deployment.yaml`
- `oc create -f redis-slave-service.yaml`
- `oc get deployments` ---> CHECK STATUS
- `oc get pods` ---> CHECK STATUS

## Create the Guestbook Application
- `cd guestbook/v1`
- `oc create -f guestbook-deployment.yaml`
- `cd guestbook/v2`
- `oc create -f guestbook-deployment.yaml`
- `oc create -f guestbook-service.yaml`

## Create a Basic Virtual Service for Guestbook Application
- `cd workshop/plans`
- `oc create -f guestbook-gateway.yaml`  ----> THE FIRST VIRTUAL SERVICE POINTS TO THE K8S SERVICE
- `oc create -f guestbook-destination.yaml`
- Test the Application and Kiali interface

## Test different routing configurations
- `oc apply -f virtualservice-50-50.yaml` --> 50%-50% Load
- `oc apply -f virtualservice-all-v1.yaml` --> All Requests routed to V1
- `oc apply -f virtualservice-80-20.yaml` --> 80%-20% Load to V1 and V2
- `oc apply -f virtualservice-testBrowser.yaml` --> Requests routed by browser

