## Build instruction for dt0.pdc.kth.se

### Build
ml rocm/5.0.0-test
amdflang -fopenmp -fopenmp-targets=amdgcn-amd-amdhsa -Xopenmp-target=amdgcn-amd-amdhsa -march=gfx908 ex00.F90 -o ex00.x

### Run
./ex00.x

### Display name of device
rocminfo | grep gfx
