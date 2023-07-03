# Docker mvn package - initialization failed

While studying for the `DevOps & SRE` course from the Linux Foundation, 
I had forked the `eeganlf/LFS261-example-voting-app` repo to work on the
exercises.

I spinned up a maven container using:

    $ docker run -idt --name build maven:3.6.1-jdk-8-slim sh

Copied the content of the `worker` folder inside the container and then jumped inside:

    $ docker container cp . build:/app
    $ docker exec -it build sh

There, I was trying to build the app running `mvn package` from the `/app` folder.
Yet, the build failed with the following error:

    # mvn package
    [INFO] Scanning for projects...
    [INFO] 
    [INFO] ---------------------------< worker:worker >----------------------------
    [INFO] Building worker 1.0-SNAPSHOT
    [INFO] --------------------------------[ jar ]---------------------------------
    library initialization failed - unable to allocate file descriptor table - out of memoryAborted (core dumped)

## Dockerd service file -- Not working
I tried to solve this I had to increment the dockerd resource quota with `systemctl`:

   $ sudo systemctl edit docker

   [Service]
   ExecStart=
   ExecStart=/usr/bin/dockerd --default-ulimit nofile=65536:65536 -H fd://

Reload and restart:

   $ sudo systemctl daemon-reload && sudo systemctl restart docker


## The docker-flag way

Simply, spinning up the memory via a docker run flag: `--ulimit nofile=65536:65536 -m 3G`, did the trick.


## Sources
- https://github.com/eeganlf/LFS261-example-voting-app
- https://stackoverflow.com/questions/68776387/docker-library-initialization-failed-unable-to-allocate-file-descriptor-tabl
