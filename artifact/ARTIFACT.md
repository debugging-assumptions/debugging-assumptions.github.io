# ICSE 2023 Artifact README

# Setup and Installation

In order to set up the artifact, you need to extract the content of the `icse2023_artifact.zip` archive into a folder of your choice.
Inside this folder, you need to create a `results/` subfolder.
To include the results into the artifact, extract the content of the `icse2023_results.tar.xz` archive into the `results` folder.

To set up the environment to run the experiments, please build the docker image as described in
the [Docker Readme](DOCKER.md). You need to create a result folder on your machine and attach this folder as Docker
volume to the Docker image. This folder will contain all final and intermediate results from the experiments, as well as all generated graphs and tables.

# Running the experiments

Inside the running Docker image, the scripts for each benchmark (`SIR`, `IntroClass`, `Corebench` and `codeflaws`) are
in their respective subfolder called `{Benchmark}_scripts`, where `{Benchmark}` is replaced with the benchmark's name.
The Docker image contains a command-line alias to run all the scripts.
This alias can be called with the `debug_assumptions` command from the interactive Docker shell.

## Replicating the results

To replicate the results, the following commands need to be executed in order:

```bash
debug_assumptions IntroClass runme
debug_assumptions IntroClass analyze
debug_assumptions IntroClass slicing
debug_assumptions IntroClass statdbg

debug_assumptions SIR runme
debug_assumptions SIR analyze
debug_assumptions SIR slicing
debug_assumptions SIR statdbg

debug_assumptions Codeflaws runme
debug_assumptions Codeflaws analyze
debug_assumptions Codeflaws slicing
debug_assumptions Codeflaws statdbg

debug_assumptions Corebench runme
debug_assumptions Corebench statdbg
cd ~/src/Corebench_scripts
python 03DbgBench.py
cd ../..
debug_assumptions Corebench slicing
```

After running the experiments as shown above, for each benchmark, the APR experiments may be run with the following command:

```bash
debug_assumptions IntroClass genprog [--faults-from <experiment>]
```

The `--faults-from` argument determines what kind of fault localization strategy from the AFL experiments is used to tell the APR tool the fault locations. It may be one of `slicing`, `statistical-mod-kulczynski2`, `statistical-ord-jaccard`, `rootcause`, `perfectdiagnosis`, etc.

The intermediate and final results of the experiments will be generated in the result folder that has been bound to the Docker image. To compile the results into graphs and CSV tables, just run `BuildTables.py` inside the home directory of the Docker container, it will automatically create an `out` folder with the graphs inside the result directory.

By default, evaluations with existing result files will be skipped.
To re-evaluate and overwrite existing files, the argument `--re-evaluate` can be supplied to `debug_assumptions`, e.g., `debug_assumptions --re-evaluate IntroClass genprog`.

### Running the APR experiments

After running the AFL experimentsas described above, you may run the APR experiments.

#### GenProg

The GenProg experiments can be run inside the same Docker image as the AFL experiments.
These experiments can be run with the `genprog` command.
To supply the APR tools with faulty lines from the AFL experiments, add a `--faults-from <experiment>` flag to the command.
For example, you can run GenProg with faults from the Slicing experiment without PBU with the following command:

```bash
debug_assumptions IntroClass genprog --faults-from slicing-nopbu
```

#### Angelix

Since Angelix requires an old LLVM version which does not build on recent systems, Angelix requires a separate Dockerfile.
To build and run this Docker image, please see the [separate README for building and running the Docker images](DOCKER.md).
Angelix experiments can be run the same way as GenProg experiments, e.g.

```bash
debug_assumptions IntroClass angelix --faults-from statdbg-kulczynski2-mod-nopbu
```

will run Angelix APR with faults from the statistical debugging evaluation using the formula `Kulczynski2` and modified ranking without PBU.

# Generating the graphs and result tables

To generate the graphs and tables, please run the following command inside the Docker image:

```bash
debug_assumptions --generate-results
```

This will build all graphs and tables in the `out/` folder.

## Troubleshooting

#### Slicing fails with "Mismatch between GDB and Oracle"

Please re-run the analysis step, some GDB log files seem to be missing.
This may happen if a run is interrupted and continued which might leave the files in an unstable state.
