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

* Dan Lorenc built a kube admission controller
https://github.com/dlorenc/cosigned

* Integration of sigstore with connaisseur (a kubernetes admission controller)
https://blog.sigstore.dev/verify-oci-container-image-signatures-in-kubernetes-33663a9ec7d8
https://github.com/sse-secure-systems/connaisseur

* Maven Central requires PGP signing for artifacts
- https://kotlinlang.org/docs/security.html
- https://github.com/junit-team/junit5/commit/729ffce00cfb57a08815f4e5844aa79230704cda
- https://docs.gradle.org/current/userguide/dependency_verification.html

# Integrity Enforcer to run only secure apps on Kubernetes / OpenShift

https://ibm.github.io/integrity-enforcer/README_OVERVIEW.html (need to investigate this)

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


# Miscellaneous

* https://certificate.transparency.dev/howctworks/

* Security in Development The IBM Secure Engineering Framework
https://www.redbooks.ibm.com/redpapers/pdfs/redp4641.pdf

* Thread modeling in the context of microservice architectures (Stride Model)
https://developer.ibm.com/articles/threat-modeling-microservices-openshift-4/

* GitHub deploy keys are more secure then github personal access tokens when used in a pipeline (jenkins, tekton etc.)
https://docs.github.com/en/developers/overview/managing-deploy-keys

