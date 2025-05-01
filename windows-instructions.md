# Run the "rsinglecell"" container on Windows

(Need testers for these instructions)

### IMPORTANT: you need admin rights on your PC for installing Docker Desktop

## 1 Download and install Docker Desktop

Go to [Docker Desktop: The #1 Containerization Tool for Developers | Docker](https://www.docker.com/products/docker-desktop) and download and install Docker Desktop. Click the "Download Docker Desktop" button and the website will automatically detect that you're on Windows.

Make sure to enable WSL 2 (Windows Subsystem for Linux) during the installation process, which will be recommended by the installer.

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

## 4 Connect to the Rstudio server (Same for both WSL and Windows)

In your browser, open http://localhost:8787/

**Important**: That is http://, **not** https://

Log in with:

- Username: rstudio
- Password: xx (the password you set in the docker run command)
- 