Bootstrap: docker
From: ubuntu:latest

%environment
    export OMPI_DIR=/opt/ompi
    export SINGULARITY_OMPI_DIR=$OMPI_DIR
    export SINGULARITYENV_APPEND_PATH=$OMPI_DIR/bin
    export SINGULAIRTYENV_APPEND_LD_LIBRARY_PATH=$OMPI_DIR/lib

%post
    apt-get update && apt-get install -y wget git bash gcc gfortran g++ make file

    # install MPI version 3.1.4
    export OMPI_DIR=/opt/ompi
    export OMPI_VERSION=3.1.4
    export OMPI_URL="https://download.open-mpi.org/release/open-mpi/v3.1/openmpi-3.1.4.tar.bz2"
    mkdir -p /tmp/ompi
    mkdir -p /opt
    cd /tmp/ompi && wget -O openmpi-$OMPI_VERSION.tar.bz2 $OMPI_URL && tar -xjf openmpi-$OMPI_VERSION.tar.bz2
    cd /tmp/ompi/openmpi-$OMPI_VERSION && ./configure --prefix=$OMPI_DIR && make install
    export PATH=$OMPI_DIR/bin:$PATH
    export LD_LIBRARY_PATH=$OMPI_DIR/lib:$LD_LIBRARY_PATH
    export MANPATH=$OMPI_DIR/share/man:$MANPATH

    # install python
    apt-get install -y python3 python3-pip