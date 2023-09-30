# Repro-ject
A repository to enhance the management and reproducibility of your research by integrating Visual Studio Code (VS Code), High Performace Computing (HPC), GitHub and Conda environments into your project set-up workflow.

### The tutorial is composed of four main sections:
(1) How to install VS Code, and how to configure and connect VS Code to the HPC
(2) How to integrate VS Code and GitHub to enhanve project managment and repoducability
(3) How to create a conda or mamba environment to enhance reproducibility
(4) How to configure R to take advantage of R tools within VS Code, such as code completion and code debugging, as well as how to install R packages so that they can be run by Slurm batch scripts on the HPC.

### Prerequsite:
To complete to complete the tasks in this tutorial you will need to an OpenSSH compatible SSH client such as `OpenSSH client` as well as `git` installed on your computer. These come standard with MacOS and Linux operating systems. To access these on Windows you will need to install Linux Bash Shell. This can be done by installing [Windows Subsystem for Linux (WSL)](https://apps.microsoft.com/store/detail/windows-subsystem-for-linux/9P9TQF7MRM4R) followed by [Ubuntu](https://apps.microsoft.com/store/detail/ubuntu/9PDXGNCFSCZV) from the Microsoft Store. Or you can follow a [dedicated tutorial](https://itsfoss.com/install-bash-on-windows/) or follow the instructione bellow:

1. Search for <span style="color:blue;">`PowerShell`</span> in the Windows start menu.
2. Open PowerShell as an admiistratior by clicking the `<span style="color:blue;">Run as administator` icon.
3. Inside Powershell, type '<span style="color:red;">WSL --install</span>' and then press <span style="color:blue;"><Enter>,  to install WSL, along with all necessary features and the default Linux distribution, that is, Unbutu.