---
permalink: /documentation/
title: ProtProtocol Documentation
toc: true
toc_label: "On this page"
header:
    overlay_image: /assets/images/alfons-morales-410757-unsplash.jpg
    overlay_filter: 0.5
    caption: "Photo by [Alfons Morales](https://unsplash.com/photos/YLSwjSy7stw?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/book?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)"
    actions:
        - label: "<i class='fas fa-question-circle'></i> Get help"
          url: "http://qa.proteomics-academy.org"
excerpt: "For additional help, simply post on the EuBIC bioinformatics mailing list."
sidebar:
    nav: doc_toc
---

The documentation pages are targeted at two audiences: **end-users** and **developers**. 

In case you **canot find the answer** to your question here, please post your question on the [EuBIC help mailing list](http://qa.proteomics-academy.org).

In case you **find a bug** in any of our tools, please do not hestitate to post an issue on the respective GitHub page.

## What are ProtProtocol images?

ProtProtcol images are bioinformatic workflows encapsulated in [Jupyter](https://jupyter.org) notebooks and installed in [Docker](https://www.docker.com) containers.

**Docker containers** are lightweight virtual machines. If you download any [Docker](https://www.docker.com) image, it is as if you were downloading a whole computer with all its installed software. [Docker](https://www.docker.com) makes these images considerably smaller and more efficient to run than real virtual machines. As a prerequesite to running ProtProtocol images, you therefore have to install the [Docker](https://www.docker.com) daemon to your system. 

**[Jupyter](https://jupyter.org) notebooks** is a software that allows you to combine text with analysis code in a single file. The, for example, resulting plots from your analysis code are automatically rendered with the text. Thereby, it creates an electronic notebook that contains both, the resulting plots and the code that generated them.

We use [Jupyter](https://jupyter.org) notebooks to encapsulate all workflows in a reproducible fashion. All steps of a ProtProtocol protocol are executed within such a notebook. This gives us the advantage that we can leverage [Jupyter's](https://jupyter.org) inbuilt functions to, for example, download the whole notebook as a HTML file which contains the complete documentation of our results. [Jupyter](https://jupyter.org) notebooks are web-applications. Therfore, they can be used on any operating system with a modern browser.

## Using ProtProtocol images

The easiest way to use ProtProtocol images is by installing our [docker-launcher](https://github.com/ProtProtocols/docker-launcher) tool. Once you have [Docker](https://www.docker.org) installed on your system, [docker-launcher](https://github.com/ProtProtocols/docker-launcher) takes care of downloading any ProtProtocol image and running it for you.

For more information see our [docker-launcher help page](/documentation/docker_launcher).
