## Inheritance
```Dockerfile
FROM debian:latest
```

## Initialization
```Dockerfile
RUN apt update
WORKDIR /opt/myapp
VOLUME ["/data"]
ADD file.xyz /file.xyz
ADD http://host/path/file.txt /tmp/file.txt
COPY --chown=user:group host_file.xyz /path/container_file.xyz
```

## Entrypoint
Container that runs as an executable:
```Dockerfile
ENTRYPOINT ["executable", "param1", "param2"]
ENTRYPOINT command param1 param2
```

Use shell processing to substitute shell vars.
ignores CMD directives or `docker run` args
```Dockerfile
ENTRYPOINT exec top -b
```

## Variables
```Dockerfile
ENV APP_HOME /myapp
RUN mkdir $APP_HOME
# ---
ARG APP_HOME=""
RUN mkdir $APP_HOME
```

## Onbuild
```Dockerfile
ONBUILD RUN bundle install
```

## Commands
```Dockerfile
EXPOSE 5900
CMD ["bundle", "exec", "rails", "server"]
```

## Metadata
```Dockerfile
LABEL version="1.0"
LABEL "com.example.vendor"="ACME Inc."
LABEL com.example.label-with-value="foo"

LABEL dexcription="This is a multiline label \
escaped with a backslash."
```

## Reducing Container Size

- Use minimal base images
	- Prefer Alpine and smaller images rather than full distros when possible.
	- Distroless images exist that don't even have a shell, and use a separate variant for debugging which you can build in parallel.
- Multistage builds
	- Use different Dockerfiles for building and packaging application code. 
	- Intermediate images (build stages) are used to compile code, install dependencies, and package files to eliminate unwanted layers.
	- Necessary runtime files are copied into another image with only the required libraries.
- Minimize number of layers
	- Each RUN, COPY, FROM, etc. instruction creates a separate layer.
	- Combine commands and consider the order in which they're run.
- Understand caching
	- Intermediate images are cached and saved.
	- Place instructions that are likely to change after heavy operations
		- e.g. place COPY of files that might change after a RUN of os updates, package installs, compiles, etc.
- Use Dockerignore
	- Use a `.dockerignore` file to ignore files in the build directory that do not belong in the image.
- Keep Application Data Elsewhere
	- Keep application data out of the container


### Image Optimization Tools
[GitHub - wagoodman/dive: A tool for exploring each layer in a docker image](https://github.com/wagoodman/dive)
[GitHub - docker-slim/docker-slim: DockerSlim (docker-slim): Don't change anything in your Docker container image and minify it by up to 30x (and for compiled languages even more) making it secure too! (free and open source)](https://github.com/docker-slim/docker-slim)

----
# Sources
[How To Reduce Docker Image Size: 5 Optimization Methods](https://devopscube.com/reduce-docker-image-size/)
[Exploring Docker - YouTube](https://www.youtube.com/playlist?list=PLillGF-Rfqbb6vZqT-Lzi9Al_noaY5LAs)

