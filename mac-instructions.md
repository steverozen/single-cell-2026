# Run the "rsinglecell" container on a Mac

If you encounter problems please email Steve Rozen, sr110@duke.edu with a copy of the error message.

## 1 Download and install Docker Desktop

Go to [Docker Desktop: The #1 Containerization Tool for Developers | Docker](https://www.docker.com/products/docker-desktop) and download and install Docker Desktop (Blue button "Download Docker Desktop" and select whether your mac is running an Apple Silicon chip or an Intel chip).

## 2 Open Terminal and get the Docker image for the workshop

Use `Terminal` to download the Docker image, which contains an Rstudio server plus the R packages needed for the workshop:

```bash
docker pull --platform linux/amd64 steverozen/rsinglecell
```

Check to see if rsinglecell got installed:

```bash
docker images
```

## 3 Start the Docker image

In `Terminal`, create a folder for the workshop information and change your working directory there. We'll call the directory `proj`, but you can use any name without spaces.

```bash
mkdir proj
cd proj
docker run -d -e PASSWORD=xx -p 8787:8787 -v $(pwd):proj steverozen/rsinglecell
```

This will start an Rstudio server process in the background

## Connect to the the Rstudio server

In your broswer, open http://localhost:8787/. 

**Important**: that is http://, **not** https://

Log in with:

- Username: rstudio
- Password: xx (the password you set in the docker run command)
