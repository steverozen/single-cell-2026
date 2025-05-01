# Run rsinglecell container on Windows

(Need testers for these instructions)

## 1 Download and install Docker Desktop

Go to [Docker Desktop: The #1 Containerization Tool for Developers | Docker](https://www.docker.com/products/docker-desktop) and download and install Docker Desktop. Click the "Download Docker Desktop" button and the website will automatically detect that you're on Windows.

Make sure to enable WSL 2 (Windows Subsystem for Linux) during the installation process, which will be recommended by the installer.

## 2 Choose your environment (Recommended: WSL)

You have two options for running Docker on Windows:

### Option A: Using WSL (Recommended)

The recommended approach is to use the Windows Subsystem for Linux (WSL):

1. Open your WSL shell (or Ubuntu terminal if you have Ubuntu installed)
2. Follow the same instructions as Mac users from step 2 onwards
3. This provides a more consistent experience with the Mac instructions and better Docker performance

### Option B: Using Windows Command Prompt or PowerShell

Alternatively, you can use native Windows tools:

1. Open either Command Prompt or PowerShell
2. Follow the Windows-specific instructions below

## 2a Get the Docker image using WSL (Recommended)

1. Open WSL (or Ubuntu terminal)
2. Pull the Docker image:

```bash
docker pull steverozen/rsinglecell
```

Test to see if rsinglecell got installed:

```bash
docker images
```

## 3a Start the Docker image using WSL (Recommended)

In your WSL terminal, create a folder for the workshop information and change your working directory there. We'll call the directory `proj`, but you can use any name without spaces.

```bash
mkdir proj
cd proj
docker run -e PASSWORD=xx -p 8787:8787 -v $(pwd):proj steverozen/rsinglecell &
```

This will start an Rstudio server process in the background.

## 2b Get the Docker image using Windows (Alternative Option)

Open Command Prompt or PowerShell and run:

```cmd
docker pull steverozen/rsinglecell
```

Test to see if rsinglecell got installed:

```cmd
docker images
```

## 3b Start the Docker image using Windows (Alternative Option)

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

## 4 Connect to the Rstudio server (Same for both WSL and Windows)

In your browser, open http://localhost:8787/

**Important**: That is http://, **not** https://

Log in with:

- Username: rstudio
- Password: xx (the password you set in the docker run command)

## Windows-Specific Notes

- If using WSL, make sure Docker Desktop is configured to integrate with your WSL 2 installation (this should be automatic but can be verified in Docker Desktop settings)
- The WSL option provides better performance and a more Unix-like experience similar to Mac and Linux environments
- If you encounter any issues with WSL, you can always fall back to the native Windows commands using Command Prompt or PowerShell