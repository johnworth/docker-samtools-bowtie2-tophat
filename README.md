# Dockerized SAMtools, Bowtie2, and TopHat

This project is used to create a Docker image that comes with the samtools, bowtie2, and tophat commands installed.

The Vagrantfile was copied over from the Docker project at https://github.com/dotcloud/docker. You'll only need it if you're running on an OS that Docker doesn't (and/or can't) support.

The Dockerfile assumes that the following files are located in the local directory alongside of it:

* tophat-2.0.10.Linux_x86_64.tar.gz - http://tophat.cbcb.umd.edu/downloads/

* bowtie2-2.1.0-linux-x86_64.zip - http://sourceforge.net/projects/bowtie-bio/files/bowtie/1.0.0/

* samtools-0.1.19.tar.bz2 - http://sourceforge.net/projects/samtools/files/samtools/0.1.19/

SAMtools is built from source and the other two are using pre-built binaries. We'll switch over to packaged version in the future.

Tophat is installed in /tophat, bowtie2 is installed in /bowtie2, and samtools is installed in /samtools. All 3 directories have been added to the PATH.

The image is available at https://index.docker.io/u/quagbrain/tophat-bowtie2-samtools/.

You can get a shell into the container with a command like the following:

    docker run -i -t -v $(pwd):/output quagbrain/tophat-bowtie2-samtools /bin/bash

That will mount the local current working directory as /output in the container. If you copy any output files to /output in the container, they will be available in the local working directory when the container is destroyed.
