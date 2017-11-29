# openmpi-project

This is a base project to automatically manage and build several programs (typically for exercises) using a single project.

## How-to

To create a project just create a folder named `src__[NAME]` where `[NAME]` is the name of the project and start writing your program.

## Build

Simply run `./build.sh` and the executables will be built and moved to `bin/`.

## Run

Use OpenMPI to run your executable like so `mpirun -n [NODE_AMOUNT] bin/prog-[NAME]`.

You can add arguments like the number of processes you want to launch (ex. `mpirun -n 4 bin/prog-hello-world` to run 4 instances).