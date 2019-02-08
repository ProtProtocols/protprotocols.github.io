---
permalink: /documentation/development/docker_protocols
title: Creating New Protocols
---

This guide gives a brief overview of how to turn a workflow into a ProtProtocol Docker container. It will show you how to add a new tool to the existing `IsoProt` container.

**Tip:** In case your new workflow only requires a different type of statistical analysis, have a look at [creating a new Jupyter notebook ](/documentation/development/custom_notebooks) first.
{: .notice--info}

This guide assumes that the following terms mean something to you:

  * Docker
  * Dockerfile
  * Linux

## Setup

We will use the `IsoProt` container as a starting point. To clone the latest version from GitHub, execute:

```
git clone https://github.com/ProtProtocols/IsoProt.git
```

## Dockerfile

ProtProtocol protocols are shipped as Docker containers. Docker containers are created following a set of instructions found in a `Dockerfile`. Conveniently, `Dockerfiles` are by default named `Dockerfile`.

<i class='fas fa-book'></i> The official Dockerfile reference can be found [here](https://docs.docker.com/engine/reference/builder/).
{: .notice--info}

A `Dockerfile` starts with a `FROM` commend, telling the Docker builder which image to use as a starting point:

```Dockerfile
FROM protprotocols/protprotocols_template
```

We created our own `protprotocols_template` base image. It comes Jupyter notebook and several dependencies pre-installed and serves as a common ground for all ProtProtocol images.

## Installing software

Next, we change to the user `root` to install additionally required software for the `IsoProt` image:

```Dockerfile
USER root

RUN apt-get update \
 && apt-get install -y --no-install-recommends mono-complete libxml2-dev libnetcdf-dev \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*
```

**Tip:** The Docker builder creates a new layer for every command in the `Dockerfile`. Therefore, to reduce the total size of the image, it is a good idea to combine several commands in one and always cleanup afterwards. In the above case, this is achieved by combining several `apt-get` commands using the `&&` sign.
{: .notice--info}

Additional files from the current directory can be copied into the image using the `ADD` command:

```Dockerfile
# Setup R
ADD DockerSetup/install_packages.R /tmp/
RUN Rscript /tmp/install_packages.R && rm /tmp/install_packages.R
```

In the code above, we copy our `install_packages.R` script into the image to then use it through the `Rscript` command to install all required R packages.

As you saw, the commands in a `Dockerfile` are basic Linux commands executed in the containers shell. We use a bit more complex commands to install tools like SearchGUI and PeptideShaker:

```Dockerfile
RUN mkdir /home/biodocker/bin
RUN PVersion=1.16.27 && ZIP=PeptideShaker-${PVersion}.zip && \
    wget -q http://genesis.ugent.be/maven2/eu/isas/peptideshaker/PeptideShaker/${PVersion}/$ZIP -O /tmp/$ZIP && \
    unzip /tmp/$ZIP -d /home/biodocker/bin/ && rm /tmp/$ZIP && \
    bash -c 'echo -e "#!/bin/bash\njava -jar /home/biodocker/bin/PeptideShaker-${PVersion}/PeptideShaker-${PVersion}.jar $@"' > /home/biodocker/bin/PeptideShaker && \
    chmod +x /home/biodocker/bin/PeptideShaker
```

## Adding additional software

To add additional software, simply add the required `RUN` commands to the `Dockerfile`.

If the software you need is **available in the repository**, the easiest is to adapt the first `RUN` command used to install `mono` and related libraries. Simply add the packages you need to this command.

If the software you need is **available as a biocontainer image**, have a look at the respective `Dockerfile` in [Biodocker's GitHub repository](https://github.com/biocontainers/containers). The simplest method is to copy the install command from there.

Alternatively, you need to manually add the required files for your tool to the Docker image using the `ADD` or `COPY` commands and then execute the required shell commands using `RUN` statements.

**Tip:** Always delete temporary files at the end of a run statement to keep your image as small as possible.
{: .notice--info}

## Building your container

To build your container, execute the following command in the directory containing the `Dockerfile`:

```bash
sudo docker build -t yourname/my_container .
```

`sudo` is needed on most Linux distributions since the `docker` command can only be executed by `root`.

The `-t yourname/my_container` parameter assigns a tag to the new container. The format for these tags is `{username}/{container name}:{version}`. If `{version}` is ommitted, like in the above example, the default `:latest` version is automatically added to the tag. If launching or pulling a container without specifying the version, this also defaults to the `:latest` version.

**Warning:** Do not use the `:latest` version for your final workflows. These do not reference a stable version and will change in the future and do not provide a stable point of reference.
{: .notice--warning}

## Testing your container

To launch your container, simply call:

```bash
sudo docker run yourname/my_container
```

Since you will want to access the Jupyter web interface and don't want the container to exit immediately, you also need to map the respective port and enable an interactive session:

```bash
sudo docker run -p 8888:8888 -ti yourname/my_container
```

For more information on how to start a container using the `docker` command directly, have a look at [Run IsoProt without docker-launcher](/documentation/isoprot_manual).

## Debugging your container

Sometimes, you will want to access your container directly using a shell. There are two options to do this:

### Start the container to open a shell directly:

```bash
sudo docker run -ti -p 8888:8888 yourname/my_container bash
```

To have root access in the session:

```bash
sudo docker run -ti -p 8888:8888 -u root yourname/my_container bash
```

### Connect to a running container

Run `sudo docker container ls`  to find the appropriate container_id.
Then, run `sudo docker exec -ti -u root <container_id> bash`:

```bash
# Get the running container id
$> sudo docker container ls
CONTAINER ID        IMAGE                               COMMAND                  CREATED [...]
c4f023536c56        protprotocols/isoprot:release-0.2   "/bin/sh -c 'jupyter…"   [...]

# Open a session in this container
sudo docker exec -ti -u root c4f023536c56 bash
```
