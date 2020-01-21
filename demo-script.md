# OpenShift 4 Demo Script

## Prep

* Create App Project

* Deploy Jenkins (Ephemeral) in App project

## Steps

* Login

* Show homepage -list of projects, create project button.

* Create Project

* Show menu dividers for project context - Workloads, Networking, Builds. All dividers context sensitive. Mention RBAC.

* Developer Catalogue - list of capabilities. Deploy httpd S2I. Show route.

## JWS Project

* Go Home

* Use App project

* Select webserver5 from dev catalogue

* Show different base image versions - pin to 1.2, or follow latest to get patches and updates as they get pushed out.

* oc new-app

oc new-app webserver50-tomcat9-openshift~https://github.com/benemon/jws-fuse-example.git --name=hello-jws --build-env=MAVEN_ARGS='clean package -Dbuild.finalName=ROOT'

* Create app from https://github.com/benemon/jws-fuse-example.git

* Edit Build - add environment variables for Nexus if required:

```
MAVEN_MIRROR_URL    http://nexus-internal.shared-services.svc.cluster.local:8081/repository/maven-all-public/
MAVEN_ARGS          clean package -Dbuild.finalName=ROOT
```

* Run Build - Watch logs

* Watch deployment

* Check app through route

* Remove deployment image trigger from yaml

* Create pipeline - `oc create -f openshift/pipeline.yml` - copy yaml.

* Run pipeline
