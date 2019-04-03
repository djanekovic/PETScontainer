Bootstrap: docker
From: debian:stable

%help
Debian container with configured and installed petsc.

%labels
    Author Darko Janekovic <darko.janekovic@fer.hr>
    PETSc_version 3.11.0

%post
    apt-get update
    apt-get upgrade -y
    apt-get install git wget gcc g++ gfortran make cmake            \
                    curl python pkg-config build-essential          \
                    valgrind openssh-client openssh-server          \
                    libopenblas-dev libopenblas-base bison flex -y
    wget http://ftp.mcs.anl.gov/pub/petsc/release-snapshots/petsc-3.11.0.tar.gz
    gunzip -c petsc-3.11.0.tar.gz | tar -xof -
    cd petsc-3.11.0/

    ./configure --with-blaslapack-lib=-lopenblas --download-openmpi \
                --download-hypre --download-superlu --download-superlu_dist \
                --download-parmetis --download-metis --download-ptscotch \
                --download-triangle --download-ctetgen --download-hdf5 \
                --with-cc=gcc --with-fc=gfortran --with-cxx=c++ \
                --with-cxx-dialect=C++11 --with-debugging=0
    make
    make test
