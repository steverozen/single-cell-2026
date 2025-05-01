# Run the "rsinglecell"" container on Windows

If you encounter problems please email Steve Rozen, [sr110@duke.edu](mailto:sr110@duke.edu) with a copy of the error message.

### IMPORTANT: you need admin rights on your PC for installing Docker Desktop

## 1 Download and install Docker Desktop

Go to [Docker Desktop: The #1 Containerization Tool for Developers | Docker](https://www.docker.com/products/docker-desktop) and download and install Docker Desktop. Click the "Download Docker Desktop" button and the website will automatically detect that you're on Windows.

Make sure to enable WSL 2 (Windows Subsystem for Linux) during the installation process, which will be recommended by the Docker Desktop installer.

### If you get an error, first install WSL separately

Documentation at [Install WSL | Microsoft Learn](https://learn.microsoft.com/en-us/windows/wsl/install)

The key is to run powershell in administrator mode, by typing the windows (start) key and them typing `powershell`, the right-click on the "Windows PowerShell" app and select "Run as administrator".

*'Open PowerShell or Windows Command Prompt in **administrator** mode by right-clicking and selecting "Run as administrator", enter the wsl --install command, then restart your machine.'*

After that, try running the Docker Desktop installer again.

## 2 Open WSL and get the "rsinglecell" Docker image

You can open the WSL shell from the start menu.

Open WSL and download the Docker image for the workshop:

```bash
docker pull steverozen/rsinglecell
```

Check to see if rsinglecell got installed:

```bash
docker images
```

## 3 Start the Docker image

In your WSL terminal, create a folder for the workshop information and change your working directory there. We'll call the directory `proj`, but you can use any name without spaces.

```bash
mkdir proj
cd proj
docker run -d -e PASSWORD=xx -p 8787:8787 -v $(pwd):proj steverozen/rsinglecell
```

This will start an Rstudio server process in the background.

## 4 Connect to the Rstudio server

In your browser, open http://localhost:8787/

**Important**: That is http://, **not** https://

Log in with:

- Username: rstudio
- Password: xx (the password you set in the docker run command)