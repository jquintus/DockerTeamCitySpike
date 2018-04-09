# Docker

## Compose

Prep:

```batch
mkdir .\teamcity-server\logs
mkdir .\teamcity-server\data

mkdir .\teamcity-agent01\conf
mkdir .\teamcity-agent01\work

mkdir .\teamcity-agent02\conf
mkdir .\teamcity-agent02\work
```

* [Source](https://github.com/JetBrains/teamcity-docker-samples)
* To run: `docker-compose up -d`
* To shutdown `docker-compose down`

* Server will be available on [http://127.0.0.1:8111/](http://127.0.0.1:8111/)
* Login info:
  * Username:  `username`
  * Password: `password`

## Agent Docker File

```cmd
cd Agent
docker build -t tc-agent:latest -m 2GB .
docker run -it tc-agent
```

1. Go to the agent folder
2. Use `docker build` to build the image
3. Use `docker run` to run the image

For the docker file, I copied the example from [docs.microsoft](https://docs.microsoft.com/en-us/visualstudio/install/build-tools-container).  I pretty much just got lucky that they were doing the same thing I needed to do.

If it was anything more complicated, I would have had to look into [getting chocolatey installed](https://github.com/StefanScherer/dockerfiles-windows/blob/master/chocolatey/Dockerfile) into the contianer and then using that to install anything else I need.

## sample-src

The `sample-src` folder contains a simple sample .net framework C# solution and a [cake build script](https://cakebuild.net/).  This is the repo that will be build from our Team City deployment.