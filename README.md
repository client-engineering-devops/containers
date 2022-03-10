# J0hnnieWa1ker does Containers
I am testing these steps on:

[Fedora 35 Workstation](https://getfedora.org/en/workstation/)
```
sudo dnf -y install podman
```

[Red Hat Enterprise Linux 8 (RHEL)](https://developers.redhat.com/rhel8)
```
sudo yum module enable -y container-tools:rhel8
sudo yum module install -y container-tools:rhel8
```
## Jump right in with an Introduction
```
podman run --name ceevee --rm -d -p 8083:80 quay.io/j0hnniewa1ker/ceevee
```
open http://localhost:8083 in a browser
## Concept

A way to personalize the concepts of containers. This came in the mail: [Johnnie's Selected Seeds](https://www.johnnyseeds.com/on/demandware.static/-/Library-Sites-JSSSharedLibrary/default/dw293a81b5/assets/information/2022-digital-master-catalog.pdf) catalog

The catalog (repository) lists all the seeds (images) you might want to use.

Seeds (images) include everything required to grow what’s contained in them. But seeds (images) alone don’t do anything on their own.

They need a `container` and resources to live and grow.

The DNA (Dockerfile) are the instructions that create the seed (image)

## How did I get here?
- [Cloud Native Bootcamp](https://cloudnative101.dev)
  - `git clone https://github.com/ibm-cloud-architecture/learning-cloudnative-101.git`
- [Docker Essentials](https://cognitiveclass.ai/courses/docker-essentials/)
- [Red Hat Certified Specialist in Containers and Kubernetes Complete Video Course: Red Hat EX180](https://www.oreilly.com/videos/red-hat-certified/9780137442058/)
  - requires O’Reilly Subscription
  - free trial gives you unlimited learning for 10 days
- [DO180 - Red Hat OpenShift I: Containers & Kubernetes](https://rol.redhat.com/rol/app/)
  - requires Red Hat Learning Subscription
- [A Practical Introduction to Container Terminology](https://developers.redhat.com/blog/2018/02/22/container-terminology-practical-introduction)
- [Docker 101 Tutorial](https://www.docker.com/101-tutorial)
- Contributed to [add tekton and cloudnativetoolkit cli](https://github.com/cloud-native-toolkit/image-ibmcloud-dev/issues/9)
  - [ibmcloud-dev container image](https://github.com/cloud-native-toolkit/image-ibmcloud-dev) repo
  - [ibmgaragecloud/ibmcloud-dev](https://quay.io/repository/ibmgaragecloud/ibmcloud-dev) Quay.io image
- Contributed to [image-tensorflow-model-train](https://github.com/client-engineering-devops/image-tensorflow-model-train)
- Contributed to [IBM Cloud Garage Tekton Pipelines](https://github.com/client-engineering-devops/ibm-garage-tekton-tasks/tree/model-pipeline)
- Building this training material
  - focusing on how I might have learned containers faster 

## What images do I plan on showing?
Image | Demo | Description
----- | ----- | ----- 
[ceevee](https://quay.io/repository/j0hnniewa1ker/ceevee) | [ceevee.md](ceevee.md) | My version of Hello
[nexus3](https://hub.docker.com/r/sonatype/nexus3) |
[gitbucket](https://hub.docker.com/r/gitbucket/gitbucket) |
[alpine](https://hub.docker.com/_/alpine) |
[nginx](https://hub.docker.com/_/nginx) |
[alpine](https://hub.docker.com/_/alpine) |
[node](https://hub.docker.com/_/node) |
[oc-pwsh](https://quay.io/repository/j0hnniewa1ker/oc-pwsh) |
[ibmcloud-dev](https://quay.io/repository/ibmgaragecloud/ibmcloud-dev) |

### Ross's Helloworld_Fortran_rk
- https://github.ibm.com/TechGarageCode/Helloworld_Fortran_rk
- quay.io/kramerro_ibm/helloworld_fortran_rk

### [Modern Fortran](https://learning.oreilly.com/library/view/modern-fortran/9781617295287/)
- https://github.com/modern-fortran/modern-fortran-docker.git


### need to investigate these
- https://hub.docker.com/r/ibmcom/xlf-ce
- https://hub.docker.com/r/coredns/coredns
- https://hub.docker.com/r/dreamcat4/pxe

