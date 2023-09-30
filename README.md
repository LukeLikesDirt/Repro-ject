# Repro-ject

A repository designed to enhance the management and reproducibility of your research by integrating Visual Studio Code (VS Code), High-Performance Computing (HPC), GitHub, and Conda environments into your project setup workflow.

### The tutorial is composed of four main sections:
1. How to install VS Code and configure it to connect to HPC.
2. How to integrate VS Code with GitHub to enhance project management and reproducibility.
3. How to create a Conda or Mamba environment to improve reproducibility.
4. How to configure R to take advantage of R tools within VS Code, such as code completion and code debugging. Also, learn how to install R packages so they can be run by Slurm batch scripts on the HPC.

### Prerequisite:
To complete the tasks in this tutorial, you will need an OpenSSH-compatible SSH client, such as `OpenSSH client`, as well as `git` installed on your computer. These are included by default in MacOS and Linux operating systems. To access them on Windows, you will need to install the Linux Bash Shell. You can do this by installing [Windows Subsystem for Linux (WSL)](https://apps.microsoft.com/store/detail/windows-subsystem-for-linux/9P9TQF7MRM4R) followed by [Ubuntu](https://apps.microsoft.com/store/detail/ubuntu/9PDXGNCFSCZV) from the Microsoft Store. Alternatively, you can follow a [dedicated tutorial](https://itsfoss.com/install-bash-on-windows/) or the instructions below:

1. Search for `PowerShell` in the Windows start menu.
2. *Open PowerShell as an administrator* by clicking the `Run as administrator` icon.
3. Inside PowerShell, type `WSL --install` and then press `Enter` to install WSL along with all necessary features and the default Linux distribution, which is `Ubuntu`.
4. Once completed, you will need to *reboot your computer* for the changes to be applied.
5. Next, open Ubuntu by searching for `Ubuntu` in the Windows start menu.
6. Ubuntu will prompt you to *enter a new Unix username and password*. Provide these details and then press the `Enter` key to continue.
7. Once logged in, update the installed Ubuntu by running the `sudo apt update` command followed by `sudo apt full-upgrade`.
8. *You are now ready to complete this tutorial*.
