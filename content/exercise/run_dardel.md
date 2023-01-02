## Build instruction for dardel.pdc.kth.se

### Build with amdflang
ml rocm/5.0.2
amdflang -fopenmp -fopenmp-targets=amdgcn-amd-amdhsa -Xopenmp-target=amdgcn-amd-amdhsa -march=gfx90a ex00.F90 -o ex00amdflang.x

### Build with CCE
ml rocm/5.0.2
ml craype-accel-amd-gfx90a
ftn -fopenmp ex00.F90 -o ex00cce.x

### Build with GNU. Need GCC 13 to build for gfx90a? Can run the executable, but it does not find the GPU.
ml rocm/5.0.2
ml craype-accel-amd-gfx90a
ml PrgEnv-gnu
ftn -fopenmp ex00.F90 -o ex00gnu.x

### Build with AOCC. Gives error: unknown target CPU 'gfx90a'
ml rocm/5.0.2
ml craype-accel-amd-gfx90a
ml PrgEnv-aocc
ftn -fopenmp ex00.F90 -o ex00aocc.x

### Build with Intel. Gives remark #8711: OpenMP* directive disabled via command line.
ml rocm/5.0.2
ml craype-accel-amd-gfx90a
ml PrgEnv-intel
ftn -fopenmp ex00.F90 -o ex00aocc.x

### Run
./ex00.x

### Display name of device
rocminfo | grep gfx
