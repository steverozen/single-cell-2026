# Run rstudio container on Mac

(Need testers for these instructions)

## 1 Download and install Docker Desktop

Go to [Docker Desktop: The #1 Containerization Tool for Developers | Docker](https://www.docker.com/products/docker-desktop) and download and install Docker Desktop (Blue button "Download Docker Desktop" and select whether your mac is running an Apple Silicon chip or an Intel chip).

## 2 Open Terminal and get the Docker image for the workshop

The Docker image contains an Rstudio server plus the R packages needed for the workshop

`$ docker pull steverozen/rsinglecell`

Test to see if rsinglecell got installed

`$ docker images`

## 3 Start the Docker image

First, in Terminal create a folder for the workshop information and change your working directory there. We'll call the directory `proj`, but you can use any name without spaces.

`$ mkdir proj`

`$ cd proj`

`$ docker run -e PASSWORD=xx -p 8787:8787 -v $(pwd):proj singlecell &`

This will start an Rstudio server process in the background

## Connect to the the Rstudio server

In your broswer, open http://localhost:8787/. 

**Important**: that is http://, **not** https:///

Log in with:

- Username: rstudio
- Password: xx (the password you set in the docker run command)
