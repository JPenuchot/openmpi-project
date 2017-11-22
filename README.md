# openmpi-project

Just a simple base for OpenMPI projects.

## Build

Simply run `./build.sh` and the executable will be built and moved to `bin/prog`.

## Run

Use OpenMPI to run your executable like so `mpirun bin/prog`.

You can add arguments like the number of processes you want to launch (ex. `mpirun -n 4 bin/prog` to run 4 instances).