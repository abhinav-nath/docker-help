```shell
$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
alpine/git   latest    b8f176fa3f0d   2 months ago   25.1MB
```

Generally image format is `[image-id]:[tag]` for example - `busybox:1.24`

```shell
Abhinav@HEISENBERG MINGW64 ~
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
Abhinav@HEISENBERG MINGW64 ~
$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
busybox      latest    69593048aa3a   2 months ago   1.24MB
alpine/git   latest    b8f176fa3f0d   2 months ago   25.1MB
```
```shell
Abhinav@HEISENBERG MINGW64 ~
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