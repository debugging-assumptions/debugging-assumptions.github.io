# Using the Docker Image

We provide a Docker image based on Debian Bullseye that already contains all benchmarks and tools required to run the experiments. For Angelix and Prophet, we use separate Docker images that are called through a Docker-in-Docker setup in the main image by sharing the Docker daemon of the host machine. The Angelix and Prophet Docker images need to be built before the main Docker image.

## Building and running the Docker Image

To run all APR tools, the Docker image needs a Docker-In-Docker setup with the Docker daemon of the host system shared with the Docker image. There needs to be a named Docker bind mount that contains the results and that is shared between all Docker images. This mount must be named `corebench-results` and needs to be created as follows, you may replace `$(pwd)/results` with the full absolute path to your results folder:

```bash
docker volume create --name corebench-results --opt type=none --opt device=$(pwd)/results --opt o=bind
```

To build the docker image, first make sure you have pulled all submodules of this repository, by cloning it with
`git clone --recurse-submodules`. Then, you can build the docker images by executing

```bash
docker build -t corebench-angelix --build-arg USER_UID=$(id -u) -f docker/Angelix .
docker build -t corebench --build-arg DOCKER_GID=$(getent group docker | cut -d: -f3) --build-arg USER_UID=$(id -u) -f docker/Dockerfile .
```

<p style="color: #666666">The Dockerfile unfortunately cannot be build with the supplied PyCharm build configuration, as of right now.
<i>This does currently not work since PyCharm for some reason completely ignores the .dockerignore file. (bug in PyCharm)</i>
</p>

You can then start the docker image using the commands below:

```bash
docker run -v /var/run/docker.sock:/var/run/docker.sock -v corebench-results:/home/corebench/results -h corebench -it corebench
```

This will launch an interactive ZSH shell with autocompletion and history enabled. To run experiments inside this shell, please see instructions in [the README file](README.md)

## Troubleshooting

### Delete all results

To delete (reset) all previous results from inside the docker image, run the following command in the home directory of the Docker image:

```bash
rm -rf results/Co* results/IntroClass* results/SIR*
```

Alternatively, you can also archive all results by executing the following commands in order:

```bash
cd results
tar -c -v --remove-files -I 'xz -9 -e -v -C sha256 --threads=4 --memlimit=12GiB' -f old_results_$(date '+%Y%m%d%H%M').tar.xz Codeflaws* Corebench* IntroClass* SIR* log out zshhistory
```

This will create an archive with maximum compression and delete all results afterwards (Use with care and never interrupt the running `tar` command! To keep the files, remove the `--remove-files` flag from the command above).

### Delete the ZSH History

To delete the ZSH history of recently-executed commands, just delete the `zshhistory` file inside the `results` folder.

### Why is my `docker build` command taking so long?

This is perfectly normal - On our test system, building Angelix alone took about 8 hours. Building all required Docker images will take a very long time.

### I am getting a `Permission Denied` error on `/var/run/docker.sock`

Please make sure the `docker` group exists on the host system and its GID can be queried by running `getent group docker | cut -d: -f3`. If the previous command does not work on your machine, please manually supply the `docker run` command with the appropriate GID.
