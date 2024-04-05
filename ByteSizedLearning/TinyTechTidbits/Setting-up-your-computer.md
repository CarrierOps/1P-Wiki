# Set up

To get working on the data infrastructure and any of its components, you will need to have a few things installed. Some of which will require you to open up a ticket with IT.

This document will list out all the needed software (the full list as well as the absolute necessary to have, and the nice to have), and will walk you through how to install each of them and test that the installation was successful.

The [first section](#list-of-requirements) will list all requirements and the [second section](#installation-guide) will be an installation guide for each thing in the list

## List of Requirements

All items with an asterisk require IT to install.

### Necessary

- Python
- Git
- gcloud \*
- WSL2 \*
- Docker \*

### Nice to have/Optional

- VS Code
- Terraform \*
- NodeJS \*
- GO \*
- Windows longpath \*
- Poetry \*
- GitHub Desktop app
- Windows Terminal

## Installation guide

### Python

1. open up the software center. ![](../../imgs/softwarecenter.png)
2. Search for python. ![](../../imgs/softwarecenter_python.png)
3. Click on python and click "Install".
4. Once the install is done, open up a new command prompt and type in `python --version`. You should see a new line appear saying 'python 3.10.8' like in the screen shot right here: ![](../../imgs/python_version.png)

- Troubleshooting
  - If you see this message `'python' is not recognized as an internal or external command, operable program or batch file.` when entering the command `python -V` it means something went wrong with your installation
  - Open up a ticket with IT. Tell them the problem is most likely that python wasn't added as an environment variable on your system. Tell them to locate the python.exe file and create a variable that points to its path.

### git

Go to [this link](https://git-scm.com/download/win) and download '64-bit Git for Windows Setup.'. This will download an .exe, run it once the download is finish. This will run you through the installation of git as well ask you about configuration preferences. You can leave everything set as the default option (you can always change your settings later).

Once installed, you can check 2 things.

1. You should have git bash installed
   1. Search for 'git' in the windows search bar and look for this app ![](../../imgs/git_bash.png)
   2. If it's there and you can open it, then that's good if not, contact IT.
2. From your command prompt type `git --version`.
   1. You should see something similar to this (don't worry if your version is different than the one in the screenshot): ![](../../imgs/git_version.png)
   2. If you get something else, such as `'git' is not recognized as an internal or external command, operable program or batch file.` then open up a ticket with IT

### gcloud

1. Navigate to [this website](https://cloud.google.com/sdk/docs/install)
2. go to the Windows section and click on 'gcloud cli installer': ![](../../imgs/gcloud_windows.png)
3. Run the .exe file downloaded in the previous step. It may take a while for the installation to complete, don't worry

To verify that the installation worked, run the command `gcloud --version`. You should see something like this pop up: ![](../../imgs/gcloud_version.png)

If instead you get a message along the lines of `'gcloud' is not recognized as an internal or external command, operable program or batch file.` or another kind of message, reach out to Thomas & IT.

### WSL2

### Docker

### VS Code

### Terraform

### NodeJS

### GO

### Windows longpath

### Poetry

### GitHub Desktop app

### Windows Terminal
