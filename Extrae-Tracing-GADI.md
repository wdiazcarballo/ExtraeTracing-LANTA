# ExtraeTracing-GADI

# Build step
1. Build Extrae from git repository
```shell
git clone https://github.com/bsc-performance-tools/extrae.git
cd extrae

#libtool is installed and loaded by default at GADI
./bootstrap
```

2. Load the following module

```bash
 1) pbs                        3) intel-mkl/2024.2.0    5) binutils/2.36.1   7) intel-tbb/2021.13.0
 2) intel-compiler/2021.10.0   4) intel-mpi/2021.13.0   6) papi/7.0.1 7) cuda/12.5.1
```

2. Configure command
```bash
CC=icc CXX=icpc ./configure \
   --build=x86_64-suse-linux \
   --host=x86_64-suse-linux   \
   --prefix=/scratch/jq90/app/extrae-intel \
   --enable-sampling \
   --enable-shared  \
   --enable-openmp  \
   --enable-pthread \
   --with-binary-type=64 \
   --with-mpi=$INTEL_MPI_ROOT  \
   --with-xml=/lib64 \
   --with-binutils=$BINUTILS_ROOT \
   --with-papi=$PAPI_ROOT \
   --with-boost=$BOOST_ROOT \
   --with-tbb=$INTEL_TBB_ROOT \
   --with-cuda=$CUDA_ROOT \
   --without-unwind \
   --without-dyninst
```