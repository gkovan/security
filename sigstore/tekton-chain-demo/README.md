
# Tekton chains demo


## Steps to setup and run the demo

Install OpenShift pipelines
```
From Operator Hub install OpenShift Pipelines 1.2.3 (this is the version for OCP 4.6)
```

Create a new project
```
oc new-project tekton-chains-demo
```

Create a docker registry secret
```
kubectl create secret docker-registry registry-credentials --docker-server=https://index.docker.io/v2/  --docker-username=gkovan --docker-email=gkovan@hotmail.com --docker-password=my-fake-passwoord -n tekton-chains-demo
```

Create a service account
```
kubectl create sa -n tekton-chains-demo build-bot
```

Patch the service account
```
kubectl patch serviceaccount build-bot -p '{"secrets": [{"name": "registry-credentials"}]}'
```

Create the pipeline resources
```
oc apply -f ./pipeline-resources
```

Create the task
```
oc apply -f ./tasks
```

Run the task
```
tkn task start -n tekton-chains-demo build-app   --serviceaccount=build-bot --inputresource='source=git-source' --outputresource='builtImage=tekton-tutorial-greeter-image' --showlog
```

Verify the image is signed
```
cosign verify -key cosign.pub docker.io/gkovan/greeter
```

## Issues
