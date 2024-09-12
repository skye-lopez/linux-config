# Pipe the build output to a log file. (By default the output is only errors and will not show things like ls, etc)

`docker build --no-cache --progress=plain  . &> build.log`

Credit: https://forums.docker.com/t/capture-ouput-of-docker-build-into-a-log-file/123178
