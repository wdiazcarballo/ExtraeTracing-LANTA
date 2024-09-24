# ExtraeTracing-LANTA

# Build step
1. Build Extrae from git repository
```shell
git clone https://github.com/bsc-performance-tools/extrae.git
cd extrae
#to get libtool in the right toolchain
module restore
module load libxml2/2.11.4-cpeCray-23.03
module load libtool/2.4.7
./bootstrap
```
  
2. Configure command
```bash
   CC=cc CXX=CC ./configure \
   --build=x86_64-suse-linux \
   --host=x86_64-suse-linux   \
   --prefix=/project/lt200291-ignite/local/extrae-cray   \
   --enable-pthread  \
   --with-mpi=/opt/cray/pe/mpich/8.1.25/ofi/crayclang/10.0   \
   --with-binary-type=64   \
   --with-xml-prefix=/lustrefs/disk/modules/easybuild/software/libxml2/2.11.4-cpeCray-23.03   \
   --enable-sampling \
   --enable-shared  \
   --enable-openmp  \
   --with-binutils=/lustrefs/disk/modules/easybuild/software/binutils/2.40 \
   --with-papi=/opt/cray/pe/papi/7.0.1.1  \
   --with-boost=/lustrefs/disk/modules/easybuild/software/Boost/1.82.0-cpeCray-23.03  \
   --without-unwind \
   --without-dyninst
```
3. Make and Install
   ```bash
   make -j4
   make install
   ```
# Build environment
```bash
Currently Loaded Modules:
  1) craype-x86-milan                        7) cray-dsmml/0.2.2        13) cpeCray/23.03
  2) libfabric/1.15.2.0                      8) cray-libsci/23.02.1.1   14) XZ/5.4.3-cpeCray-23.03
  3) craype-network-ofi                      9) cray-mpich/8.1.25       15) zlib/1.2.13
  4) xpmem/2.6.2-2.5_2.27__gd067c3f.shasta  10) craype/2.7.20           16) libxml2/2.11.4-cpeCray-23.03
  5) PrgEnv-cray/8.3.3                      11) perftools-base/23.03.0  17) M4/1.4.19
  6) cce/15.0.1                             12) cpe-cuda/23.03_quiet    18) libtool/2.4.7
```

# Obtain list of PAPI counters
```bash
/project/lt200291-ignite/local/extrae-cray/bin/papi_best_set  omnipresent {PAPI_TOT_INS,PAPI_TOT_CYC},PAPI_L1_DCM,PAPI_L2_DCM,PAPI_L3_TCM,PAPI_BR_INS,PAPI_BR_MSP,RESOURCE_STALLS,PAPI_VEC_SP,PAPI_SR_INS,PAPI_LD_INS,PAPI_FP_INS
```
