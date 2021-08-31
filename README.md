# security

This repo will contain info about various security related projects and information in order to build, deploy and manage apps in a secure way.

* Software supply chain security

https://github.com/sigstore

* Understand your dependencies

https://deps.dev/

* How does HTTPS work? What's a CA? What's a self-signed Certificate?
* 
https://www.youtube.com/watch?v=T4Df5_cojAs


# Zero trust supply chains (sigstore)

https://docs.google.com/document/d/1CRvANkYu0fxJjEZO4KTyyk_1uZm2Q9Nr0ibxplakODg/edit?ts=60b8f2cd&resourcekey=0-nGnWnCni8IpiXim-WreYMg#heading=h.fyy27kd27z1r

* Dan Lorenc video on Sigstore tools and cosign
https://www.youtube.com/watch?v=gCi9_4NYyR0

* CNCF Security TAG Supply Chain WG 2021-06-10
https://www.youtube.com/watch?v=TVNyL2_ljtg

* OCB: Secure your Open Source Supply Chain with Sigstore
https://www.youtube.com/watch?v=yKrbUGSwrEw

https://sigstore.dev/

https://github.com/sigstore

* Cosign image signatures
https://blog.sigstore.dev/cosign-image-signatures-77bab238a93

* Dan Lorenc built a kube admission controller
https://github.com/dlorenc/cosigned

* Integration of sigstore with connaisseur (a kubernetes admission controller)
https://blog.sigstore.dev/verify-oci-container-image-signatures-in-kubernetes-33663a9ec7d8
https://github.com/sse-secure-systems/connaisseur

* Maven Central requires PGP signing for artifacts
- https://kotlinlang.org/docs/security.html
- https://github.com/junit-team/junit5/commit/729ffce00cfb57a08815f4e5844aa79230704cda
- https://docs.gradle.org/current/userguide/dependency_verification.html

# Kubernetes Admission Controller

https://kubernetes.io/docs/reference/access-authn-authz/admission-controllers/

# Integrity Shield - Integrity Enforcer to run only secure apps on Kubernetes / OpenShift
* https://github.com/IBM/integrity-shield
* https://github.com/IBM/integrity-shield/tree/main/admission-controller
* https://ibm.github.io/integrity-enforcer/README_OVERVIEW.html (need to investigate this)
* https://operatorhub.io/operator/integrity-shield-operator
* https://cloud.redhat.com/blog/k8s-integrity-shield-tech-preview-protecting-the-integrity-of-kubernetes-resources-with-signature

* https://cloud.redhat.com/blog/better-kubernetes-security-with-open-policy-agent-opa-part-1
* https://cloud.redhat.com/blog/better-kubernetes-security-with-open-policy-agent-opa-part-2


# Open Policy Agent Gatekeeper

* https://github.com/open-policy-agent/gatekeeper
* https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/2.3/html/governance/governance#managing-gatekeeper-operator-policies

# Dan Lorenc sample admission contoller

* https://github.com/dlorenc/cosigned

# Connaisseur Admission Controller has support for sigstore cosign

* https://sse-secure-systems.github.io/connaisseur/v2.0.0/

# Kyverno Admission Controller has support for sigstore cosign

* https://github.com/kyverno/kyverno/
* https://docs.google.com/document/d/1d2Qm47wjjoyGDT8v3_ijB1Q4mGYV5cncAQoQniiR414/edit#heading=h.s8qsd3dl8lqi
* https://nirmata.com/2021/08/12/kubernetes-supply-chain-policy-management-with-cosign-and-kyverno/

# Portieris Admission Controller

* https://github.com/IBM/portieris
* https://www.ibm.com/cloud/blog/trusted-workloads-signing-container-images-in-your-kubernetes-workflow

# Issue to track work on Deployment policies (i.e. admission controller to verify container image is signed)
https://github.com/sigstore/cosign/issues/196

# ArgoCD integration with Sigstore
* https://github.com/IBM/argocd-interlace

# Web Security Tools

* OWASP ZAP (open source tool)

https://owasp.org/www-project-zap/

* Burp suite (commercial paid product used by professional hackers)

https://portswigger.net/burp

* dvws-node

Damn Vulnerable Web Service (example web app of what not to do - contains many vulnerabilities)

https://github.com/snoopysecurity/dvws-node

# OpenShift/Kubernetes Security

* https://developer.ibm.com/learningpaths/secure-context-constraints-openshift/
* https://developer.ibm.com/learningpaths/secure-context-constraints-openshift/scc-tutorial/
* https://docs.openshift.com/container-platform/4.1/authentication/using-service-accounts-in-applications.html
* To disble the service account secrets being mounted into a pod
```
apiVersion: v1
kind: ServiceAccount
metadata:
  name: {{ .Values.name }}
automountServiceAccountToken: false
```
The `automountServiceAccountToken: false` will ensure that the service account secret does not get mounted.
As a best practice, create a service account per app.


# Miscellaneous

* https://certificate.transparency.dev/howctworks/

* Security in Development The IBM Secure Engineering Framework
https://www.redbooks.ibm.com/redpapers/pdfs/redp4641.pdf

* Thread modeling in the context of microservice architectures (Stride Model)
https://developer.ibm.com/articles/threat-modeling-microservices-openshift-4/

* GitHub deploy keys are more secure then github personal access tokens when used in a pipeline (jenkins, tekton etc.)
https://docs.github.com/en/developers/overview/managing-deploy-keys

* SLSA (pronounced Salsa) - Supply-chain Levels for Software Artifacts
* https://slsa.dev/

