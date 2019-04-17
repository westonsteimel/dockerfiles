## dockerfiles

This repo was started from the excellent [dockerfiles](https://github.com/jessfraz/dockerfiles) of [@jessfraz](https://github.com/jessfraz).  
It holds various dockerfiles for tools I find useful.

**Table of Contents**

<!-- toc -->

- [About](#about)
- [Resources](#resources)
  * [My dotfiles](#my-dotfiles)
- [Contributing](#contributing)
  * [Using the `Makefile`](#using-the-makefile)

<!-- tocstop -->

## About

The ones I've added or customised live on dockerhub under [westonsteimel](https://hub.docker.com/u/westonsteimel).  
Any others which I haven't yet made any changes to probably still live under [jess](https://hub.docker.com/u/jess/) or 
[r.j3ss.co](https://r.j3ss.co/).

## Resources

### My dotfiles

You might potentially find my [dotfiles](https://github.com/westonsteimel/dotfiles) to be useful.  Most of the commands 
for launching the tools I use as docker containers live under [bin/](https://github.com/westonsteimel/dotfiles/blob/master/bin/).

These were also inspired by the [dotfiles](https://github.com/jessfraz/dotfiles) of [@jessfraz](https://github.com/jessfraz)

## Contributing

I try to make sure each Dockerfile has a command at the top to document running it,
if a file you are looking at does not have a command, please
pull request it!

### Using the `Makefile`

```
$ make help
build                          Builds all the dockerfiles in the repository.
dockerfiles                    Tests the changes to the Dockerfiles build.
image                          Build a Dockerfile (ex. DIR=telnet).
latest-versions                Checks all the latest versions of the Dockerfile contents.
run                            Run a Dockerfile from the command at the top of the file (ex. DIR=telnet).
shellcheck                     Runs the shellcheck tests on the scripts.
test                           Runs the tests on the repository.
```
