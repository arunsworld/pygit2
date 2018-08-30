This repo contains the binary for pygit2.

Source: https://github.com/libgit2/pygit2
Depends on: https://github.com/libgit2/libgit2

## How to use


## How to compile

* Clone the libgit2 repo: `git clone https://github.com/libgit2/libgit2.git`
* `cd libgit2`
* Use `arunsworld/builder:latest` docker image to build it
* `docker run --rm -it --name builder -v "$PWD":/app arunsworld/builder:latest`
* `cd /app`
* `mkdir build && cd build`
* `cmake ..`
* `cmake --build .`

This produces libgit2.so.0.27.0 same as libgit2.so and libgit2.so.27. This is part of the repo that goes into the conda lib folder. Also git2.h and git2 from `include` folder in libgit2 should be deployed in `/opt/conda/include/python3.6m`

* Now clone out the pygit2 repo: `git clone https://github.com/libgit2/pygit2.git`
* `cd pygit2`
* Use `arunsworld/builder:latest` docker image alongwith conda volume (refer: https://github.com/arunsworld/docker-builder/blob/master/README.md)
* `docker run --rm -it --name builder -v "$PWD":/app -v conda:/opt/conda arunsworld/builder:latest`
* `. /opt/conda/etc/profile.d/conda.sh`
* `conda activate base`
* `cd /app`
* Ensure libgit2* is copied to `/opt/conda/lib` and git2.h & git2 are copied to `/opt/conda/include/python3.6m`
* `python setup.py build`
* `python setup.py install`

This produces `dist/pygit2-0.27.1-py3.6-linux-x86_64.egg`. THis is part of the repo that can be installed via `easy_install`

