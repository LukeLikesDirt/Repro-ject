# Repro-ject

A repository designed to enhance the management and reproducibility of your research by integrating Visual Studio Code (VS Code), High-Performance Computing (HPC), GitHub, and Conda environments into your project workflow.

### The tutorial is composed of four main sections:
1. How to install VS Code and configure HPC connection.
2. How to integrate VS Code with GitHub to enhance project documentaion, organisation and reproducibility.
3. How to create a Conda or Mamba environment to improve reproducibility.
4. How to configure R to take advantage of R tools within VS Code, such as code completion and debugging, as well as learn how to install R packages so they can be run by Slurm batch scripts on the HPC.

### Prerequisite:
To complete the tasks in this tutorial, you will need an OpenSSH-compatible client, such as `OpenSSH Client`, as well as the version control system `git` installed on your computer. These are default software on macOS and Linux operating systems. To access them on Windows, you will need to install the Linux Bash Shell. You can do this by installing [Windows Subsystem for Linux (WSL)](https://apps.microsoft.com/store/detail/windows-subsystem-for-linux/9P9TQF7MRM4R) followed by [Ubuntu](https://apps.microsoft.com/store/detail/ubuntu/9PDXGNCFSCZV) from the Microsoft Store. Alternatively, you can follow a [dedicated tutorial](https://itsfoss.com/install-bash-on-windows/) or the instructions below:

1. Search for `PowerShell` in the Windows start menu.
2. *Open PowerShell as an administrator* by clicking the `Run as administrator` icon.
3. Inside PowerShell, type `WSL --install` and then press `Enter` to install WSL along with all necessary features and the default Linux distribution, which is Ubuntu.
4. Once completed, you will need to *reboot your computer* for the changes to be applied.
5. Next, open Ubuntu by searching for `Ubuntu` in the Windows start menu.
6. Ubuntu will prompt you to *enter a new Unix username and password*. Provide these details and then press the `Enter` key to continue.
7. Once logged in, update the installed Ubuntu by running the `sudo apt update` command followed by `sudo apt full-upgrade`.
8. *You are now ready to complete this tutorial*.

## Connect VS Code to the HPC

To complete this section, you will need to have an [OpenSSH compatible SSH client](https://code.visualstudio.com/docs/remote/troubleshooting#_installing-a-supported-ssh-client) installed on your computer (PuTTY is not supported). This comes pre-installed on macOS and Linux. For Windows, see the instructions at the top of this page.

Steps 2 and 3 are summarised from a detailed [tutorial on configuring remote SSH in VS Code](https://code.visualstudio.com/docs/remote/ssh-tutorial). Follow the instructions in the link if you require a more detailed explanation.

### (1) Download and install VS Code
First, you will need to [download and install VS Code](https://code.visualstudio.com/) on [macOS](https://code.visualstudio.com/docs/setup/mac), [Linux](https://code.visualstudio.com/docs/setup/setup-overview), or [Windows](https://code.visualstudio.com/docs/setup/windows).

### (2) Configure remote SSH in VS Code
- To configure SSH in VS Code, you will need to [install the Remote - SSH extension](vscode:extension/ms-vscode-remote.remote-ssh). Once you have installed the `Remote - SSH extension`, a new green Status bar item will appear in the far bottom left corner of the VS Code window, just below the settings icon.

    ![Remote - SSH extension icon](https://code.visualstudio.com/assets/docs/remote/ssh-tutorial/remote-status-bar.png)

 - Click on the green Status bar item.
 - In the search bar at the top of the top of the window, selet `Connect to Host...` followed by `Add New SSH Host...`
 - Entre your SSH Host details, for example, `ssh -p 6022 ``<p><span style="color:blue;">your username><span></p>``@ltu-hpc.latrobe.edu.au`

### (3) Optional: Add a public SSH key to your HPC account for easier access to the HPC

- In the terminal, run the command `ssh-keygen -t ed25519`. This will generate the SSH key.
- Press `Enter` to use the default file name: "id_vscode."
- When prompted to enter a passphrase, press the "Enter Key" (don't create a passphrase).
- In VS Code, navigate to the `/Users/<p><span style="color:blue;">your username</span></p>/.ssh/` folder on your personal computer, and copy the public SSH key, e.g., "id_vscode.pub." This will be copied to the HPC in the following step.
- Alternatively, open a terminal and enter the command `nano /Users/username/.ssh/`. In VS Code, navigate to your home directory on the HPC and open the ".ssh" folder. Paste the public key into the "authorized_keys" document.
- DONE!