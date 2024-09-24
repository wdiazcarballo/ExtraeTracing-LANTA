# ExtraeTracing-LANTA

# Build step
1. Build Extrae from git repository
'''shell
git clone https://github.com/bsc-performance-tools/extrae.git
cd extrae
#to get libtool in the right toolchain
module load libxml2/2.11.4-cpeCray-23.03
module load libtool/2.4.7
./bootstrap
'''
  
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
