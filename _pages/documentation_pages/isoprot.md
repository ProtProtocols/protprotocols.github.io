---
permalink: /documentation/isoprot_manual
title: Manually run IsoProt
---

IsoProt is a fully reproducible one-stop-shop for the analysis of iTRAQ/TMT data. 

<i class="far fa-file-alt"></i> Read the IsoProt manuscript on [bioRxiv](https://doi.org/10.1101/446070)

## Installation

The easiest way to install and run IsoProt is by using our [docker-launcher](/documentation/docker_launcher) tool. For more information on how to install a ProtProtocol image like IsoProt using [docker-launcher](https://github.com/ProtProtocols/docker-launcher) have a look at [this documentation](/documentation/docker_launcher).

The rest of this document only refers to running the IsoProt image **without** using docker-launcher. All of these steps are otherwise automatically taken care of by docker-launcher.

## Manual installation

IsoProt is a [Docker](https://www.docker.com) image and can also manually be installed using the `docker` command line tool. As a prerequestite, [Docker](https://www.docker.com) needs to be installed on the system. For more information, please have a look at our [help pages on installing Docker](/documentation/install_docker).

**Note:** The following instructions refer to your operating system's command line.
{: .notice--info}

Download the image:

```bash
# Download version 0.1 of the image
docker pull veitveit/isoprot:release-0.1

# Download the latest version of the image
docker pull veitveit/isoprot:latest
```

## Manually run the image

```bash
docker run -it -p 8888:8888 veitveit/isoprot:release-0.1
```

**Note:** Replace the `release-0.1` portion with the version of the image you downloaded and want to launch.
{: .notice--info}

This will launch the image and make it available to access on [http://localhost:8888](http://localhost:8888).

In order to directly access your computer's folders through the docker image (recommended option) map local directories to the containers /data (for input data) and OUT (for output data) folders:

```bash
docker run -it -p 8888:8888 -v /path/to/my/mgf/files:/data/ -v /path/to/my/result/folder:/home/biodocker/OUT veitveit/isoprot
```

**Note:** When running Docker Toolbox (ie. only available version on Windows 7), local paths must be below C:\Users. Additionally, paths need to specified in the following format:
{: .notice--info}

```bash
# to map C:\Users\Johannes\Downloads
docker run -it -p 8888:8888 -v /c/users/johannes/downloads:/data/ -v /c/users/johannes/results:/home/biodocker/OUT veitveit/isoprot
```

## Access the Notebook

If you launched the image as described above, the [Jupyter](https://jupyter.org) notebook is available at [http://localhost:8888](http://localhost:8888). Simply open the link and access the [Jupyter](https://jupyter.org) server.

You can start with the example use case by clicking on the file Isobaric_Workflow.ipynb
