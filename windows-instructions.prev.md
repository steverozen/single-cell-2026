# Run rsinglecell container on Windows

(Need testers for these instructions)

## 1 Download and install Docker Desktop

Go to [Docker Desktop: The #1 Containerization Tool for Developers | Docker](https://www.docker.com/products/docker-desktop) and download and install Docker Desktop. Click the "Download Docker Desktop" button and the website will automatically detect that you're on Windows.

Make sure to enable WSL 2 (Windows Subsystem for Linux) during the installation process, which will be recommended by the installer.

## 2 Open Command Prompt or PowerShell and get the Docker image for the workshop

The Docker image contains an Rstudio server plus the R packages needed for the workshop

```cmd
docker pull steverozen/rsinglecell
```

Test to see if rsinglecell got installed

```cmd
docker images
```

## 3 Start the Docker image

First, create a folder for the workshop information and change your working directory there. We'll call the directory `proj`, but you can use any name without spaces.

For Command Prompt:

```cmd
mkdir proj
cd proj
docker run -e PASSWORD=xx -p 8787:8787 -v "%cd%":proj steverozen/rsinglecell
```

For PowerShell:

```powershell
mkdir proj
cd proj
docker run -e PASSWORD=xx -p 8787:8787 -v "${pwd}":proj steverozen/rsinglecell
```

This will start an Rstudio server process.

**Note**: On Windows, you don't need the ampersand (&) at the end to run in the background - just leave it off.

## 4 Connect to the Rstudio server

In your browser, open http://localhost:8787/

**Important**: That is http://, **not** https://

Log in with:

- Username: rstudio
- Password: xx (the password you set in the docker run command)
