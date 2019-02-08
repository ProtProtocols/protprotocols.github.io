---
permalink: /documentation/isoprot/save_analysis
title: Save and Restore IsoProt Settings
---

This tutorial explains how to save and re-use an IsoProt analysis' settings.

## Save parameters

IsoProt stores all settings used for the search and the statistical analysis in two text files:

protocol_parameters.json
: Stores all parameters entered into the graphical user interface. These include all search related parameters (for example, precursor and fragment ion tolerance), as well as the statistical settings from the `Quantitative analysis` tab.

exp_design.tsv
: A tab-delimited text file containing table representing the complete experimental design. This includes all sample labels as well as the sample groups (and their names).

**Tip:** You can submit the `exp_design.tsv` file together with your raw / peaklist files to a repository to record which samples belong to which channel. `exp_design.tsv` files can easily be viewed in, for example, Excel.
{: .notice--info}

These files are created automatically when an analysis is started and are located in the specified result directory.

**Warning:** These two files only capture the settings entered in the user interface. Any changes to the R code contained in the Jupyter notebook is not archived using this method (see below).
{: .notice--warning}

## Reuse parameters

![Loaded settings dialog](/assets/images/isoprot_settings_loaded.png)

To **reuse settings** simply copy the `protocol_parameters.json` and `exp_design.tsv` files from the result directory of your previous analysis into the result directory of your new analysis (as selected in the [docker-launcher](./documentation/docker_launcher) tool). The IsoProt Juypter notebook will automatically recognize them and show them in the respective inputs of the graphical user interface.

**Warning:** Whenever you click the "Run my search" or "Save design" buttons, these files are overwritten. Also, if you click "Reset design", the `exp_design.tsv` is deleted.
{: .notice--warning}

## Save complete workflow

The `protocol_parameters.json` and  the `exp_desin.tsv` file do not include changes made to the notebook itself, like modifying R code etc. Luckily, the notebook itself can  be easily saved by choosing **File/Download as/Notebook (.ipynb)**:

![Save notebook dialog](/assets/images/isoprot_save_notebook.png)

It is also possible to save just the graphical presentation of a notebook by choosing **File/Download as/HTML (.html)** option. This makes it easy to view and share analyses results and setup without the need to have Jupyter installed.

**Warning:** Do not use the `PDF vi LaTeX (.pdf)` option. Unfortunately, this option does not work correctly and does not contain the complete text and code found in the notebook. This is not caused by us but by how Jupyter notebooks use LaTeX to create PDF files. We hope that this will be fixed in a future version of Jupyter notebook.
{: .notice--warning}

**Tip:** If your add you analysis results as Supplementary Materials to a manuscript, we recommend that you include the `HTML` and the `Notebook (.ipynb)` version of your notebook. This makes it easy for reviewers to view your protocol as well as for future readers to repeat your analysis.
{: .notice--info}
