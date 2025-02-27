# Provide MATLAB as a Volume or Bind Mount

To provide a MATLAB installation to the container via a volume or bind mount, instead of installing MATLAB inside the image, follow the instructions below.

### Build the Docker Image

Build a Docker image called `matlab-notebook-nomatlab`, using the file `Dockerfile.mounted`:

```bash
docker build -f Dockerfile.mounted -t matlab-notebook-nomatlab .
```

### Start the Docker Container

Execute the command below to start a Docker container, bind mount the directory `/usr/local/MATLAB/R2020b` (which must contain a MATLAB R2020b or later 64 bit Linux installation) into the directory `/opt/matlab` inside the container, and bind port 8888 on the host to port 8888 of the container (by default, Jupyter's app-server runs on port 8888 inside the container):

```bash
docker run -it -v /usr/local/MATLAB/R2020b:/opt/matlab:ro -p 8888:8888 matlab-notebook-nomatlab
```

Access the Jupyter Notebook by following one of the URLs displayed in the output of the ```docker run``` command.
For instructions about how to use the integration, see [MATLAB Integration for Jupyter](https://github.com/mathworks/jupyter-matlab-proxy).
