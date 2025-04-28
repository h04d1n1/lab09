$ export GITHUB_USERNAME=h04d1n1

$ cd ${GITHUB_USERNAME}/workspace
$ pushd .
~/h04d1n1/workspace ~/h04d1n1/workspace
$ source scripts/activate

$ git clone https://github.com/${GITHUB_USERNAME}/lab07 lab08
Cloning into 'lab08'...
remote: Enumerating objects: 282, done.
remote: Counting objects: 100% (282/282), done.
remote: Compressing objects: 100% (134/134), done.
remote: Total 282 (delta 115), reused 278 (delta 114), pack-reused 0 (from 0)
Receiving objects: 100% (282/282), 174.99 KiB | 1.38 MiB/s, done.
Resolving deltas: 100% (115/115), done.
$ cd lab08
$ git submodule update --init
Submodule 'tools/polly' (https://github.com/ruslo/polly) registered for path 'tools/polly'
Cloning into '/home/freeman/h04d1n1/workspace/lab08/tools/polly'...
Submodule path 'tools/polly': checked out 'ef7e79c2c297d456f2742fd0b976f555d058d4e0'
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab08

$ cat > Dockerfile <<EOF
FROM ubuntu:20.04
EOF

$ cat >> Dockerfile <<EOF

RUN apt update
RUN apt install -yy gcc g++ cmake
EOF

$ cat >> Dockerfile <<EOF

COPY . print/
WORKDIR print
EOF

$ cat >> Dockerfile <<EOF

RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
RUN cmake --build _build
RUN cmake --build _build --target install
EOF

$ cat >> Dockerfile <<EOF

ENV LOG_PATH /home/logs/log.txt
EOF

$ cat >> Dockerfile <<EOF

VOLUME /home/logs
EOF

$ cat >> Dockerfile <<EOF

WORKDIR _install/bin
EOF

$ cat >> Dockerfile <<EOF

ENTRYPOINT ./demo
EOF

$ sudo docker build -t logger .
DEPRECATED: The legacy builder is deprecated and will be removed in a future release.
            Install the buildx component to build images with BuildKit:
            https://docs.docker.com/go/buildx/

Sending build context to Docker daemon  6.871MB
Step 1/12 : FROM ubuntu:20.04
 ---> b7bab04fd9aa
Step 2/12 : RUN apt update
 ---> Using cache
 ---> cc2969c637d0
Step 3/12 : RUN apt install -yy gcc g++ cmake
 ---> Using cache
 ---> 1143fe95b467
Step 4/12 : COPY . print/
 ---> Using cache
 ---> 7e6d9c7aa222
Step 5/12 : WORKDIR print
 ---> Using cache
 ---> 0f6a4ae3a78c
Step 6/12 : RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
 ---> Using cache
 ---> 56002176ccc1
Step 7/12 : RUN cmake --build _build
 ---> Using cache
 ---> 16abc4459559
Step 8/12 : RUN cmake --build _build --target install
 ---> Using cache
 ---> 5142dfee7b88
Step 9/12 : ENV LOG_PATH /home/logs/log.txt
 ---> Using cache
 ---> a6ad5ffcf3fa
Step 10/12 : VOLUME /home/logs
 ---> Using cache
 ---> 29787253717f
Step 11/12 : WORKDIR _install/bin
 ---> Using cache
 ---> d834e69a2503
Step 12/12 : ENTRYPOINT ./demo
 ---> Using cache
 ---> 966a71717d56
Successfully built 966a71717d56
Successfully tagged logger:latest

$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
logger       latest    966a71717d56   54 seconds ago   431MB
<none>       <none>    6ceb5803f087   9 minutes ago    340MB
<none>       <none>    d9faf192ecb4   55 minutes ago   340MB
ubuntu       20.04     b7bab04fd9aa   2 weeks ago      72.8MB
ubuntu       18.04     f9a80a55f492   23 months ago    63.2MB

$ mkdir logs
$ docker run -it -v "$(pwd)/logs/:/home/logs/" logger
text1
text2
text3
<C-D>

$ docker inspect logger
[
    {
        "Id": "sha256:966a71717d562ed704f29270415d49e247be718e940885adac8d37d5d21b78d8",
        "RepoTags": [
            "logger:latest"
        ],
        "RepoDigests": [],
        "Parent": "sha256:d834e69a2503fb5a5818be229ca3235a17377fd845e5460a68dbe09b0996dce4",
        "Comment": "",
        "Created": "2025-04-28T09:48:15.594284869Z",
        "DockerVersion": "28.1.1",
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
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "LOG_PATH=/home/logs/log.txt"
            ],
            "Cmd": null,
            "Image": "sha256:d834e69a2503fb5a5818be229ca3235a17377fd845e5460a68dbe09b0996dce4",
            "Volumes": {
                "/home/logs": {}
            },
            "WorkingDir": "/print/_install/bin",
            "Entrypoint": [
                "/bin/sh",
                "-c",
                "./demo"
            ],
            "OnBuild": null,
            "Labels": {
                "org.opencontainers.image.ref.name": "ubuntu",
                "org.opencontainers.image.version": "20.04"
            }
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 431393692,
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/535647d4f466ddc56179388979a7ce8df906292d2a9885ca9ba7f91144b805d6/diff:/var/lib/docker/overlay2/b6b61b4f4550dc8f4409a2cd77015fafa7ef467ebbdc3a5a8e60e9f4d59e768c/diff:/var/lib/docker/overlay2/d08a4efb122c6d79e0a285f047a13daa82cd8887b1a4a4f0ed8d2dd5c8fc4eea/diff:/var/lib/docker/overlay2/c94596d03cd79ec71d93c10995879620c6a4053b89926e12dff3192a7bc7b604/diff:/var/lib/docker/overlay2/ab1f44a2ec6ab4948cd5ae2b4b7839656ee96b14b832883cb5caf3a7c403669f/diff:/var/lib/docker/overlay2/66d4545933bd7a75d25e33eea8f5daea982a91c23e5edbc0a628e98510289387/diff",
                "MergedDir": "/var/lib/docker/overlay2/7a7a32fa3dfd35c7db4d33d18cd76734792b13d4cdff1566ef44d7717b6e3c7b/merged",
                "UpperDir": "/var/lib/docker/overlay2/7a7a32fa3dfd35c7db4d33d18cd76734792b13d4cdff1566ef44d7717b6e3c7b/diff",
                "WorkDir": "/var/lib/docker/overlay2/7a7a32fa3dfd35c7db4d33d18cd76734792b13d4cdff1566ef44d7717b6e3c7b/work"
            },
            "Name": "overlay2"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:470b66ea5123c93b0d5606e4213bf9e47d3d426b640d32472e4ac213186c4bb6",
                "sha256:3188d1f559adbd8cb797a696dc15e3fe1e91d2eeff319960360d60db92d710ae",
                "sha256:d60df692e99a9f267cb9d38cf339f8629f372c763d70fa071136688b30aad1bf",
                "sha256:cee242d7db70b2896fd3cd12a8501bf02da7fd8e588adfba577da62b5975ba31",
                "sha256:a94821ff798f6398d74eb749f24675c43a589169f83aff89caef1e85ca8c3616",
                "sha256:a960c8217d7fb620799e22f639304d011dd18f150e2d2b7ec980003828782593",
                "sha256:0b6745f78b9f5d85f91d550588ede6fbd34c8ec91d092486bc9a3aec1b7b993e"
            ]
        },
        "Metadata": {
            "LastTagTime": "2025-04-28T12:48:19.082568005+03:00"
        }
    }
]

$ cat logs/log.txt
text1
text2
text3

$ gsed -i 's/lab07/lab08/g' README.md

$ vim .travis.yml
/lang<CR>o
services:
- docker<ESC>
jVGdo
script:
- docker build -t logger .<ESC>
:wq

$ git add Dockerfile
$ git add .travis.yml
$ git commit -m"adding Dockerfile"
[main 37b4032] adding Dockerfile
 4 files changed, 26 insertions(+), 13 deletions(-)
 create mode 100644 Dockerfile
 create mode 100644 logs/log.txt
$ git push origin master
Enumerating objects: 289, done.
Counting objects: 100% (289/289), done.
Delta compression using up to 8 threads
Compressing objects: 100% (138/138), done.
Writing objects: 100% (289/289), 175.65 KiB | 35.13 MiB/s, done.
Total 289 (delta 117), reused 281 (delta 115), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (117/117), done.
To https://github.com/h04d1n1/lab08
 * [new branch]      main -> main
