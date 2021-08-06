
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

Verify TaskRun
```
export TASKRUN=<Name of your TaskRun> # Replace with your taskrun name
```

```
kubectl get taskrun $TASKRUN
```

```
$ export TASKRUN_UID=$(kubectl get taskrun $TASKRUN -o=json | jq -r '.metadata.uid')

$ kubectl get taskrun $TASKRUN -o=json | jq  -r ".metadata.annotations[\"chains.tekton.dev/payload-taskrun-$TASKRUN_UID\"]" | base64 --decode > payload

$ kubectl get taskrun $TASKRUN -o=json | jq  -r ".metadata.annotations[\"chains.tekton.dev/signature-taskrun-$TASKRUN_UID\"]" | base64 --decode > signature
```
```
cosign verify-blob -key cosign.pub -signature ./signature ./payload
```



## Issues

1. Tekton chains was not signing the image the was created and pushed to the registry.

I add the `digestfile` option in the buildah push command.
```
buildah --storage-driver=vfs push \
--tls-verify=$(inputs.params.tlsVerify) \
--digestfile /tekton/results/IMAGE_DIGEST \
$(inputs.params.destinationImage) \
docker://$(inputs.params.destinationImage)
```

I also add the results section in the task yaml as follows:
```
results:
  - description: Digest of the image just built.
    name: IMAGE_DIGEST
  - description: URL of the image just built.
    name: IMAGE_URL
```

-- Issue resolved.
   With OpenShift Pipelines v 1.2.3 it build-app.yaml works.
   With the newer versions of Pipelines it does not work.
See: https://github.com/tektoncd/chains/blob/main/docs/config.md#chains-type-hinting
