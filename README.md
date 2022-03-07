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
## Concept

A way to personalize the concepts of containers. This came in the mail: [Johnnie's Selected Seeds](https://www.johnnyseeds.com/on/demandware.static/-/Library-Sites-JSSSharedLibrary/default/dw293a81b5/assets/information/2022-digital-master-catalog.pdf) catalog

The catalog (repository) lists all the seeds (images) you might want to use.

Seeds (images) include everything required to grow what’s contained in them. But seeds (images) alone don’t do anything on their own.

They need a `container` and resources to live and grow.

The DNA (Dockerfile) are the instructions that create the seed (image)