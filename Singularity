Bootstrap: docker
From: debian:stable

%help
Debian container with configured and installed petsc.

%labels
    Darko Janekovic <darko.janekovic@fer.hr>
    PETSc version 3.9.4

%post
    apt-get update
    apt-get upgrade -y
    apt-get install git wget gcc g++ gfortran make \
                    curl python pkg-config build-essential \
                    valgrind openssh-client openssh-server -y
    wget http://ftp.mcs.anl.gov/pub/petsc/release-snapshots/petsc-3.9.4.tar.gz
    gunzip -c petsc-3.9.4.tar.gz | tar -xof -
    cd petsc-3.9.4/
    ./configure --with-cc=gcc --with-cxx=g++ --with-fc=gfortran --with-cxx-dialect=C++11 \
                --download-fblaslapack --download-mpich --download-triangle \
                --download-ctetgen --download-hypre
