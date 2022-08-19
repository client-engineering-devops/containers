# scratch
- [Create a simple parent image using scratch](https://docs.docker.com/develop/develop-images/baseimages/#create-a-simple-parent-image-using-scratch)
  - and you compiled it with the `-static` flag

- [How to Statically Link C and C++ Programs on Linux with gcc](https://www.systutorials.com/how-to-statically-link-c-and-c-programs-on-linux-with-gcc/)

## On a minimal linux host
`sudo dnf install gcc glibc-static podman -y`

compile `-static` and verify it is `not a dynamic executable`
```
gcc -static scratch.c -o scratch
ldd scratch
        not a dynamic executable
 ```
build with Dockerfile

`podman build -t scratch .` 

Run and verify 

`podman run --rm scratch`
```
scratch
```
`podman images`
```
REPOSITORY         TAG         IMAGE ID      CREATED         SIZE
localhost/scratch  latest      da41b49173f7  19 seconds ago  1.91 MB
``` 
`podman inspect scratch`
```json
[
    {
        "Id": "da41b49173f73e646817fd4a8c1d28c90e925a682eecef42a6e8535cdbb33027",
        "Digest": "sha256:e7b672b7fd995ae139b840193fc7a68434ad041097b90a7c9491ffead8f84b6b",
        "RepoTags": [
            "localhost/scratch:latest"
        ],
        "RepoDigests": [
            "localhost/scratch@sha256:e7b672b7fd995ae139b840193fc7a68434ad041097b90a7c9491ffead8f84b6b"
        ],
        "Parent": "c153a758fdbd0286cce271a6aa109aeb9215569fb024c3cc941e81adc720634d",
        "Comment": "",
        "Created": "2022-08-19T10:00:13.347640102Z",
        "Config": {
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/scratch"
            ],
            "Labels": {
                "io.buildah.version": "1.23.1"
            }
        },
        "Version": "",
        "Author": "",
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 1908851,
        "VirtualSize": 1908851,
        "GraphDriver": {
            "Name": "overlay",
            "Data": {
                "UpperDir": "/home/temp/.local/share/containers/storage/overlay/7aa36cc8acff133244222d5c0e8936de088fc4bcf1e170b32e7d5d7d0fcd72d0/diff",
                "WorkDir": "/home/temp/.local/share/containers/storage/overlay/7aa36cc8acff133244222d5c0e8936de088fc4bcf1e170b32e7d5d7d0fcd72d0/work"
            }
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:7aa36cc8acff133244222d5c0e8936de088fc4bcf1e170b32e7d5d7d0fcd72d0"
            ]
        },
        "Labels": {
            "io.buildah.version": "1.23.1"
        },
        "Annotations": {
            "org.opencontainers.image.base.digest": "sha256:f7db448f47b5e95c7350455b5c664b24e49cc7f41cb52f98a71d09181fc6f72f",
            "org.opencontainers.image.base.name": ""
        },
        "ManifestType": "application/vnd.oci.image.manifest.v1+json",
        "User": "",
        "History": [
            {
                "created": "2022-08-19T10:00:13.260536031Z",
                "created_by": "/bin/sh -c #(nop) ADD file:77484e94d4074131f9b0d8d901f40f8c929942a19570269e9ebdb5c32dbbc90a in / "
            },
            {
                "created": "2022-08-19T10:00:13.347811558Z",
                "created_by": "/bin/sh -c #(nop) CMD [\"/scratch\"]",
                "empty_layer": true
            }
        ],
        "NamesHistory": [
            "localhost/scratch:latest"
        ]
    }
]
```