```shell
$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
alpine/git   latest    b8f176fa3f0d   2 months ago   25.1MB
```

Generally image format is `[image-id]:[tag]` for example - `busybox:1.24`

```shell
$ docker run busybox
Unable to find image 'busybox:latest' locally
latest: Pulling from library/busybox
b71f96345d44: Pulling fs layer
b71f96345d44: Verifying Checksum
b71f96345d44: Download complete
b71f96345d44: Pull complete
Digest: sha256:0f354ec1728d9ff32edcd7d1b8bbdfc798277ad36120dc3dc683be44524c8b60
Status: Downloaded newer image for busybox:latest
```
```shell
$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
busybox      latest    69593048aa3a   2 months ago   1.24MB
alpine/git   latest    b8f176fa3f0d   2 months ago   25.1MB
```
```shell
$ docker run busybox echo "hello world"
hello world
```
```shell
Abhinav@HEISENBERG MINGW64 ~
$ docker run busybox ls
bin
dev
etc
home
proc
root
sys
tmp
usr
var
```

To open an interactive terminal inside the container:

```bash
$ winpty docker run -i -t busybox
/ # ls -lrt
total 36
drwxr-xr-x    2 root     root         12288 Jun  7 17:34 bin
drwxrwxrwt    2 root     root          4096 Jun  7 17:34 tmp
drwxr-xr-x    4 root     root          4096 Jun  7 17:34 var
drwxr-xr-x    3 root     root          4096 Jun  7 17:34 usr
drwxr-xr-x    2 nobody   nobody        4096 Jun  7 17:34 home
dr-xr-xr-x   11 root     root             0 Aug 19 17:02 sys
dr-xr-xr-x  272 root     root             0 Aug 19 17:02 proc
drwxr-xr-x    1 root     root          4096 Aug 19 17:02 etc
drwxr-xr-x    5 root     root           360 Aug 19 17:02 dev
drwx------    1 root     root          4096 Aug 19 17:02 root
```

* `-i, --interactive` - interactive mode
* `-t, --tty` - Allocate a pseudo-TTY
* `winpty` is only required for windows

Get low level information about the docker container:

```bash
$ docker inspect busybox
[
    {
        "Id": "sha256:69593048aa3acfee0f75f20b77acb549de2472063053f6730c4091b53f2dfb02",
        "RepoTags": [
            "busybox:latest"
        ],
        "RepoDigests": [
            "busybox@sha256:0f354ec1728d9ff32edcd7d1b8bbdfc798277ad36120dc3dc683be44524c8b60"
        ],
        "Parent": "",
        "Comment": "",
        "Created": "2021-06-07T20:20:29.305375985Z",
        "Container": "6dd2b340ed3c81fb1f73ff1c7cfa6fde88cf6dd4b0d35f2e7045f2c93ca71481",
        "ContainerConfig": {
            "Hostname": "6dd2b340ed3c",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/sh",
                "-c",
                "#(nop) ",
                "CMD [\"sh\"]"
            ],
            "Image": "sha256:34dd1172b5b26c557e72a400b1c9aaf26746efe34ce01023f605cdb4d5870ad3",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {}
        },
        "DockerVersion": "19.03.12",
        "Author": "",
        "Config": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "sh"
            ],
            "Image": "sha256:34dd1172b5b26c557e72a400b1c9aaf26746efe34ce01023f605cdb4d5870ad3",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": null
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 1235821,
        "VirtualSize": 1235821,
        "GraphDriver": {
            "Data": {
                "MergedDir": "/var/lib/docker/overlay2/c180c3512a53767640d4b301bc8dd7ddfa2d4af6d33cf5bd55636bbe4dfad6fc/merged",
                "UpperDir": "/var/lib/docker/overlay2/c180c3512a53767640d4b301bc8dd7ddfa2d4af6d33cf5bd55636bbe4dfad6fc/diff",
                "WorkDir": "/var/lib/docker/overlay2/c180c3512a53767640d4b301bc8dd7ddfa2d4af6d33cf5bd55636bbe4dfad6fc/work"
            },
            "Name": "overlay2"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:5b8c72934dfc08c7d2bd707e93197550f06c0751023dabb3a045b723c5e7b373"
            ]
        },
        "Metadata": {
            "LastTagTime": "0001-01-01T00:00:00Z"
        }
    }
]
```
