ARG aiida_base
FROM aiida_core_base:$aiida_base

ARG siesta_version
ENV SIESTA_VERSION=$siesta_version
ARG siesta=siesta-$siesta_version

WORKDIR /opt
ADD ./$siesta.tar.gz .

WORKDIR /opt/$siesta/Obj
ADD arch.make ./

# Install deps and SIESTA, cleanup
RUN apt-get -qq update \
    && apt-get install -y --no-install-recommends \
    openmpi-common openmpi-bin libopenmpi-dev libblacs-openmpi1 \
    libopenmpi1.6 libnetcdf-dev netcdf-bin \
    libscalapack-openmpi1 libscalapack-mpi-dev \
    libblas-common libblas-dev liblapack-dev libhdf5-dev \
    && ../Src/obj_setup.sh \
    && make \
    && cp siesta /usr/local/bin/siesta \
    && cd ../Util/STM/simple-stm \
    && make \
    && cp plstm /usr/local/bin/plstm \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /code
RUN export PYTHONPATH=/code:$PYTHONPATH \
    && rm -rf /opt/$siesta
