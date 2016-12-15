# Docker image for *moon-buggy*

The Dockerfile in this repository compiles into a Docker image that includes the famous [moon-buggy game](http://www.seehuhn.de/pages/moon-buggy)!
The main purpose of this project is of course fun, but I also use it for demonstrating Docker...

![docker image for moon-buggy](https://binfalse.de/assets/media/pics/2016/moon-buggy.png)

## Get the image

To get this image you may either clone this repository and run:

    git clone https://github.com/binfalse/docker-moon-buggy.git
    docker build -t binfalse/moon-buggy docker-moon-buggy

Or you take the precompiled image from the DockerHub at [binfalse/moon-buggy](https://hub.docker.com/r/binfalse/moon-buggy/):

    docker pull binfalse/moon-buggy

In both cases you'll end up with a new image `binfalse/moon-buggy:latest`:

    # docker images
    REPOSITORY            TAG      IMAGE ID       CREATED          SIZE
    binfalse/moon-buggy   latest   201d81d426de   15 minutes ago   57.49 MB

**Yes, you're correct! The image is less than 60MB in size!**


## Run a container

To run the image as a Docker container you would call something like this:

    # docker run --rm -it binfalse/moon-buggy

and it will immediatelly throw you into the moon-buggy game!
The commandline options will automatically clean the environment for you when you stop the game (`--rm`) and will give you an interactive tty for the running container (`-it`).

However, that means you'll loose the high-score everytime you stop the container!
To presistenly keep the high-scores you need to store them outside the container, e.g. in `/srv/moon-buggy-scores` of your machine.
You can then mount them to `/var/games/moon-buggy/mbscore` and moon-buggy will use and update that file.
Run the following to mount the file into the container:

    # docker run --rm -it -v /srv/moon-buggy-scores:/var/games/moon-buggy/mbscore binfalse/moon-buggy



