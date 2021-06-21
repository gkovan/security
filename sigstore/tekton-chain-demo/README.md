



kubectl logs -f deployment/tekton-chains-controller -n tekton-chains


tkn task start -n workspace-auth-demo build-app   --serviceaccount=build-bot   --inputresource='source=git-source'   --outputresource='builtImage=tekton-tutorial-greeter-image'   --showlog

cosign verify -key cosign.pub docker.io/gkovan/greeter
