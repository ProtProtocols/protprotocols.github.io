---
layout: splash
permalink: /
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/markus-spiske-507983-unsplash.jpg
  actions:
    - label: "<i class='fa fa-download'></i> Get docker-launcher"
      url: "https://github.com/ProtProtocols/docker-launcher"
  caption: "Photo by [Markus Spiske](https://unsplash.com/photos/466ENaLuhLY?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/science?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)"
excerpt: "Easy-to-use, reproducible bioinformatics workflows for MS/MS based proteomics approaches."
intro: 
  - excerpt: '**ProtProtocols** use Docker containers to distribute easy-to-use, reproducible bioinformatics workflows for MS/MS based proteomics approaches. This allows you to install complex bioinformatics workflows with a single command - or even at the click of a button through our [docker-launcher](https://github.com/ProtProtocols/docker-launcher) application.'
docker_launcher:
  - image_path: assets/images/dockerlauncher.svg
    alt: "docker-launcher"
    title: "docker-launcher"
    excerpt: "The **docker-launcher** tool is the simplest way to install and run ProtProtocol images. It is a lightweight Java application that provides a simple user interface to download and run ProtProtocols. It supports Windows, Mac OS X and Linux. Its only requirements are Java and Docker to be installed."
    url: "https://github.com/ProtProtocols/docker-launcher"
    btn_label: "<i class='fab fa-github'></i> Visit Project"
    btn_class: "btn--primary"
iso_protocol:
  - image_path: /assets/images/iso_protocol.svg
    alt: "ProtProtocol icon"
    title: "IsoProt"
    excerpt: "A ProtProtocol to analyse isobarically labelled (iTRAQ / TMT) quantitative proteomics experiments. The **IsoProt** provides sophisticated statistical methods to analyse complex experimental designs at the click of a button. Like all ProtProtocols the protocol is run as a [Jupyter](https://jupyter.org) notebook. Starting with peak list files as input (mgf format) it performs everything from the search of the spectra until the statistical analysis of the quantified proteins."
    url: "https://github.com/ProtProtocols/IsoProt"
    btn_label: "<i class='fab fa-github'></i> Visit Project"
    btn_class: "btn--primary"
eubic:
  - image_path: /assets/images/eubic_logo.png
    title: "EuBIC"
    excerpt: "**ProtProtocols** was launched under the umbrella of the European Bioinformatics Community (EuBIC). The EuBIC initiative aims to bring together the bioinformatics community and tackle bioinformatics problems in proteomics collectively."
    url: "https://www.proteomics-academy.org"
    btn_label: "Visit EuBIC"
    btn_class: "btn--primary"
funding:
  - image_path: /assets/images/eu_logo.png
    title: "Acknowledgments"
    excerpt: "This project has received funding from the European Research Council (ERC) under the European Union's Horizon 2020 research and innovation programme under grant agreement No 788042."
template_image:
  - image_path: /assets/images/template_protocol.svg
    title: "Template Image"
    excerpt: "The **ProtProtocols template** provides a basic docker image to start the development of a new ProtProtocol. It contains a system with Jupyter including an R kernel installed. To start a new ProtProtocol, simply *clone* the image and adapt it to your needs."
    url: https://github.com/ProtProtocols/protprotocols_template
    btn_label: "<i class='fab fa-github'></i> Visit Project"
    btn_class: "btn--primary"
---

{% include feature_row id="intro" type="center" %}

{% include feature_row id="docker_launcher" type="left" %}

{% include feature_row id="iso_protocol" type="right" %}

{% include feature_row id="template_image" type="left" %}
