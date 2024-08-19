# Repro-ject

This repository provides an overview of how I have integrated Visual Studio Code (VS Code), High-Performance Computing (HPC), GitHub, and Conda environments into my project workflow. By integrating these tools into my workflow, I aim to enhance the management and reproducibility of my research.

### The tutorial is composed of four main sections:
1. How to install VS Code and how to configure a HPC connection.
2. How to integrate VS Code with GitHub to enhance project documentaion, organisation and reproducibility.
3. How to create a Conda or Mamba environment to improve reproducibility.
4. How to configure R to take advantage of R tools within VS Code, such as code completion and debugging, as well as learn how to install R packages so they can be run by Slurm batch scripts on the HPC.

### Prerequisite:
To complete the tasks in this tutorial, you will need an OpenSSH-compatible client, such as `OpenSSH Client`, as well as the version control system `git` installed on your computer. These are default software on macOS and Linux operating systems. To access them on Windows, you will need to install the Linux Bash Shell. You can do this by installing [Windows Subsystem for Linux (WSL)](https://apps.microsoft.com/store/detail/windows-subsystem-for-linux/9P9TQF7MRM4R) followed by [Ubuntu](https://apps.microsoft.com/store/detail/ubuntu/9PDXGNCFSCZV) from the Microsoft Store. Alternatively, you can follow a [dedicated tutorial](https://itsfoss.com/install-bash-on-windows/) or the instructions below:

##### Install Windows Subsystem for Linux (WSL) and Ubuntu
1. *Open PowerShell as an administrator* by searching for `PowerShell` in the Windows start menu and clicking the `Run as administrator` icon.
2. Inside PowerShell, type `WSL --install` and then press `Enter` to install WSL along with all necessary features and the default Linux distribution, which is Ubuntu.
3. Once completed, you will need to *reboot your computer* for the changes to be applied.
  ![Install Powershell](https://github.com/LukeLikesDirt/Repro-ject/blob/main/.pics/install_powershell.png)
##### Configure Ubuntu
1. Next, open Ubuntu by searching for `Ubuntu` in the Windows start menu.
  ![Search for Ubuntu](https://github.com/LukeLikesDirt/Repro-ject/blob/main/.pics/search_for_Ubuntu.png)
2. Ubuntu will prompt you to *enter a new Unix username and password*. Provide these details and then press `Enter` to continue.
  ![Username Password](https://github.com/LukeLikesDirt/Repro-ject/blob/main/.pics/username_password.png)
3. Once logged in, update the installed Ubuntu by running the `sudo apt update` command followed by `sudo apt full-upgrade`.
  ![Update Ubuntu](https://github.com/LukeLikesDirt/Repro-ject/blob/main/.pics/update_Ubuntu.png)
*You are now ready to complete this tutorial*.

## Connect VS Code to the HPC

To complete this section, you will need to have an [OpenSSH compatible SSH client](https://code.visualstudio.com/docs/remote/troubleshooting#_installing-a-supported-ssh-client) installed on your computer (PuTTY is not supported). This comes pre-installed on macOS and Linux. For Windows, see the instructions at the top of this page.

Steps 2 and 3 are summarised from a detailed [tutorial on configuring remote SSH in VS Code](https://code.visualstudio.com/docs/remote/ssh-tutorial). Follow the instructions in the link if you require a more detailed explanation.

### Download and install VS Code
First, you will need to [download and install VS Code](https://code.visualstudio.com/) on [macOS](https://code.visualstudio.com/docs/setup/mac), [Linux](https://code.visualstudio.com/docs/setup/setup-overview), or [Windows](https://code.visualstudio.com/docs/setup/windows).

### Configure remote SSH in VS Code
1. To configure SSH in VS Code, you will need to install the 'Remote - SSH extension' by search for `remote` in the `EXTENTIONS` tab to the left of the VS Code window.

   ![Remote - SSH extension icon](https://github.com/LukeLikesDirt/Repro-ject/blob/main/.pics/remote.png)

Once you have installed the `Remote - SSH extension`, a new green Status bar item will appear in the far bottom left corner of the VS Code window, just below the settings icon.

   ![gree Status bar item](https://code.visualstudio.com/assets/docs/remote/ssh-tutorial/remote-status-bar.png)

 - Click on the green Status bar item.
 - In the search bar at the top of the top of the window, selet `Connect to Host...` followed by `Add New SSH Host...`
 - Entre your SSH Host details, for example, `ssh -p 6022 username@ltu-hpc.latrobe.edu.au` and then press `Enter`
 - Select the `/User/username/.ssh/config` file to save the SSH Host details
 - Next we'll generate a pair of SSH keys to streamline HPC access via VS Code.

### (3) Generate a pair of SSH keys and add the public SSH key to your HPC account to link you personal computer to the HPC

- In the terminal, set the working directory to your .ssh subdirectory by running the command `cd /Users/lukeflorence/.ssh` 
- Next, entre the command `ssh-keygen -t ed25519`. This will generate a pair of SSH keys.
- Press `Enter` to use the default file name `id_ed25519)` or define a unique file name such as `id_vscode`.
- When prompted to enter a passphrase, press the `Enter` (don't create a passphrase).
- In VS Code, navigate to the `/Users/username/.ssh/` folder using the `EXPLORER` tab to the left of the window. Open the public SSH file, for example, the `id_vscode.pub` file, and copy its contents. Alternitivly, in the terminal  within VS Code, entre the command `nano /Users/username/.ssh/id_vscode.pub` and copy the contents of the file, then press `Ctrl + X` to exit nano. This public key will be copied to the HPC in the following step.
- Press the green Status bar item in VS Code followed by`Connect to Host...` to connect to the HPC. From your user home directory on the HPC, navigate to and open the `.ssh` folder using the `EXPLORER` tab to the left of the window. Open the `authorized_keys` file and paste your public key here. Alternatively, while connected to the HPC, open terminal and enter path to you `authorised_key` file using nano, for example `nano /home/ad/username/.ssh/authorized_keys`. Paste your key within the `authorised_key` file then press `Ctrl + X` to exit followed by `Y` to save and press `Enter` to continue. 
- Your personal computer and HPC now share a set of key to streamline your access to the HPC.

## Set up Conda envrionments to ensure the reproducability of your research

### (1) Install mambaforge

### (2) Create required environemnts 
In this examples, I create a `shell` environemnt to run my `bash` scripts and `R` environemnt to run `R`. 
    -

### (3) Install R packages into your project folder on the HPC

In this section I will explain how to install `R` packages so they can be accessed from within a 'slurm' script.

If you plan to run intensive jobs with `R` on the HPC, you will need to exicute `R` scripts via `bash`. To do this, `R` packages will need to be accessed by the HPC. However, `R` packages are installed within your within your home directory by default, and the HPC cannot access your home directrory within an `R` slurm because of the default privacy settings on the HPC. Therefore, when installing and requireing `R` packages they need to be saved and called from an accessable directory, such as you project directory.

## Configure R to take advantage of Visual Studio Code tools for R

In this section, we will Configuring the "R › Rpath: Linux" and "Rterm: Linux" settings in Visual Studio Code (VS Code).

Configurging these settings are essential to establishing effective communication between VS Code and your R installation on Linux. They ensure that VS Code can locate and interact with the R interpreter and, if desired, an alternative interactive R terminal, enabling you to write, run, and debug R code seamlessly within the VS Code environment, as well as to take advantage of tool such as R code completeion withn VS Code.

The follwing steps will explain how to configuring (1) the "R › Rpath: Linux" and (2) the "Rterm: Linux" settings in VS Code.

### Step 1
First we need to obtain the `R › Rpath: Linux`. You can obtain this from your R environment or from the R module on the HPC.

To use R from your R environment, type the follwoing commands one by one:
`conda activate R
which R`

You should use the output, for example `/data/group/"your_lab_name"/home/"your-username"/mambaforge/envs/R/bin/R`, for the "R › Rpath: Linux" setting in VS Code (Step 2).

Alternitivly, if you are not using an R environement, 


Once you have obtained the paths for both settings, you can configure them in Visual Studio Code:

 - Open VS Code on your computer.
 - Go to "File" > "Preferences" > "Settings" or use the keyboard shortcut Ctrl+, (Windows/Linux) or Cmd+, (macOS).
 - In the search bar at the top of the settings panel, type "Rpath" to quickly locate the "R › Rpath: Linux" setting.
 - In the "R › Rpath: Linux" setting, enter the path to the R executable you found in step 1.
 - Similarly, search for "Rterm" to locate the "Rterm: Linux" setting and enter the path to the interactive R terminal you want to use, either the R executable itself or the "radian" executable.
 - Save your settings.

With these paths configured correctly, VS Code should work properly with your R installation on Linux.
