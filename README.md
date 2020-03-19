# .NET Interactive Docker

[.NET Interactive](https://github.com/dotnet/interactive) allows the execution of .NET (C#, F#, PowerShell) in a [Jupyter Notebook](https://jupyter.org/).

This repository contains a Dockerfile to allow users to run a *Jupyter* instance with a *.NET* kernel without the need install the tools locally.

## Run .NET Interactive

**Windows**:

```powershell
docker run -it --rm -p 8888:8888 -v ${PWD}:/home/user/local secana/dotnet-interactive:latest
```

**Linux**:

```bash
docker run -it --rm -p 8888:8888 -v $pwd:/home/user/local secana/dotnet-interactive:latest
```

This mounts your current working directory to the *local* folder in the *Jupyter* instance. The output will look like below. To open the notebook, click on the link in the last line.

```bash
...
[C 21:30:03.210 NotebookApp]

    To access the notebook, open this file in a browser:
        file:///home/user/.local/share/jupyter/runtime/nbserver-1-open.html
    Or copy and paste one of these URLs:
        http://193b0d4a4821:8888/?token=315f63eee4f367bfe27aa340547a0493f9880ff0521e78d8
     or http://127.0.0.1:8888/?token=315f63eee4f367bfe27aa340547a0493f9880ff0521e78d8
```

## Build container

To build the container yourself, run:

```powershell
docker build --squash -t jupyter .
```

An image is build locally with the name *jupyter*.

### Push to Docker Hub

```powershell
docker login
docker tag jupyter secana/dotnet-interactive
docker tag jupyter secana/dotnet-interactive:latest
docker tag jupyter secana/dotnet-interactive:latest
docker push secana/dotnet-interactive:latest
```
