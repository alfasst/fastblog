---
toc: true
layout: post
comments: true
title: "One Jupyter - Three Languages" 
image: images/092020/notebooks.png
categories: [jupyter, R, julia, python]
description: "How to setup JupyterLab for Python, R and Julia."
---
I use Python for my coding work usually and R occasionally. And I'm currently learning Julia. Spyder (for Python), Juno (for Julia) and RStudio (obviously for R) were my usual editors. But now I use Jupyter for all three languages. So I would like to explain the process of integrating R and Julia into JupyterLab because Python is the default in Jupyter.

I use elementary OS. Thus Python 3 comes pre-installed. Otherwise you have to install Python along with pip and need to add both binaries' locations to PATH. Following things are for Gnu/Linux distributions based on Ubuntu/Debian. Change commands to your system accordingly.

## Install JupyterLab
JupyterLab can be installed using pip:<br/>
`$ sudo pip3 install jupyterlab`

Running `jupyterlab` in terminal will open JupyterLab in a browser window.


## Install R & Support for Jupyter
R binaries for Gnu/Linux, Windows & Mac are available at [CRAN](https://cloud.r-project.org/index.html). Download and install R. Add the installation path to PATH if required.

For Gnu/Linux distros, there is a better way.
1. Add GPG key:<br/> 
`$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9`
2. Add R repo:<br/>
`$ sudo add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran40/'`
If you are not using bionic (Ubuntu 18.04), change the above code according to your version.
3. Update repos and install R:<br/>
`$ sudo apt update && sudo apt install r-base`

### Setting Up Jupyter for R
Running `R` in terminal, will open R interactive shell. But if you are using Gnu/Linux, you have to do `sudo R` to install packages. Anyway, open R shell. Then:
1. Install IRkernel:<br/>
`> install.packages('IRkernel')`
2. Make the kernel available to Jupyter:<br/>
`> IRkernel::installspec(user = FALSE)`<br/>
Setting `user=TRUE` will limit installation only for the current user.
After doing these, Jupyter can be used to create R notebooks.

## Install and Set Up Julia
Julia binaries are available at [julialang.org](https://julialang.org/downloads/). For Gnu/Linux, don't use *snap* as it provides older version. Julia shows significant changes over versions. After installation/extraction, add Julia executable to PATH. 

### Install & Set Up IJulia
IJulia provides Jupyter support to Julia. To install IJulia, open Julia by typing `julia` in shell. Switch to Pkg mode by hitting `]`.<br/>
`(@v1.5) pkg> add IJulia`
After installation, to make Julia available in Jupyter, build IJulia.<br/>
`(@v1.5) pkg> build IJulia`

So Jupyter is ready to use with Python, R and Julia.

## References
* [Using R on Jupyter Notebook - DZone Big Data](https://dzone.com/articles/using-r-on-jupyternbspnotebook)
* [How To Install R on Ubuntu 18.04 - Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-install-r-on-ubuntu-18-04-quickstart)
