Sending build context to Docker daemon  1.281GB

Step 1/14 : ARG VERSION=latest
Step 2/14 : FROM smart-g-ray-plugin:$VERSION.step3
 ---> 223148b4fb24
Step 3/14 : MAINTAINER sobey/yuanqi
 ---> Using cache
 ---> 3a509bbc81c8
Step 4/14 : ENV LIBRARY_PATH $LIBRARY_PATH:/usr/local/cuda/lib64/stubs
 ---> Using cache
 ---> 424ba680ffb6
Step 5/14 : RUN pip install -U pip setuptools -i https://pypi.tuna.tsinghua.edu.cn/simple && 	pip --no-cache-dir --default-timeout 1000 install pysocks -i https://pypi.tuna.tsinghua.edu.cn/simple
 ---> Using cache
 ---> 5bcaf5f9c55f
Step 6/14 : RUN pip install --no-cache-dir --default-timeout 1000 typing_extensions numpy ninja pyyaml mkl mkl-include setuptools cmake cffi future six requests dataclasses --proxy socks5://172.16.135.61:7891
 ---> Using cache
 ---> 5970945b0818
Step 7/14 : ADD pytorch_nightly.tar.gz /pytorch/pytorch_build
 ---> Using cache
 ---> 81aac6bfed88
Step 8/14 : WORKDIR /pytorch/pytorch_build/nightly/pytorch_nightly
 ---> Running in b82bace4904d
Removing intermediate container b82bace4904d
 ---> 6f002b8c2574
Step 9/14 : RUN USE_CUDNN=1 python setup.py install && 	python setup.py clean
 ---> Running in 13f5a1b707ea
-- The CXX compiler identification is GNU 5.4.0
-- The C compiler identification is GNU 5.4.0
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Not forcing any particular BLAS to be found
-- Performing Test COMPILER_WORKS
-- Performing Test COMPILER_WORKS - Success
-- Performing Test SUPPORT_GLIBCXX_USE_C99
-- Performing Test SUPPORT_GLIBCXX_USE_C99 - Success
-- Performing Test CAFFE2_EXCEPTION_PTR_SUPPORTED
-- Performing Test CAFFE2_EXCEPTION_PTR_SUPPORTED - Success
-- std::exception_ptr is supported.
-- Performing Test CAFFE2_NEED_TO_TURN_OFF_DEPRECATION_WARNING
-- Performing Test CAFFE2_NEED_TO_TURN_OFF_DEPRECATION_WARNING - Failed
-- Turning off deprecation warning due to glog.
-- Performing Test CAFFE2_COMPILER_SUPPORTS_AVX2_EXTENSIONS
-- Performing Test CAFFE2_COMPILER_SUPPORTS_AVX2_EXTENSIONS - Success
-- Current compiler supports avx2 extension. Will build perfkernels.
-- Performing Test CAFFE2_COMPILER_SUPPORTS_AVX512_EXTENSIONS
-- Performing Test CAFFE2_COMPILER_SUPPORTS_AVX512_EXTENSIONS - Success
-- Current compiler supports avx512f extension. Will build fbgemm.
-- Performing Test COMPILER_SUPPORTS_HIDDEN_VISIBILITY
-- Performing Test COMPILER_SUPPORTS_HIDDEN_VISIBILITY - Success
-- Performing Test COMPILER_SUPPORTS_HIDDEN_INLINE_VISIBILITY
-- Performing Test COMPILER_SUPPORTS_HIDDEN_INLINE_VISIBILITY - Success
-- Performing Test COMPILER_SUPPORTS_RDYNAMIC
-- Performing Test COMPILER_SUPPORTS_RDYNAMIC - Success
-- Building using own protobuf under third_party per request.
-- Use custom protobuf build.
-- 
-- 3.11.4.0
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Failed
-- Check if compiler accepts -pthread
-- Check if compiler accepts -pthread - yes
-- Found Threads: TRUE  
-- Performing Test protobuf_HAVE_BUILTIN_ATOMICS
-- Performing Test protobuf_HAVE_BUILTIN_ATOMICS - Success
-- Caffe2 protobuf include directory: $<BUILD_INTERFACE:/pytorch/pytorch_build/nightly/pytorch_nightly/third_party/protobuf/src>$<INSTALL_INTERFACE:include>
-- Trying to find preferred BLAS backend of choice: MKL
-- MKL_THREADING = OMP
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of void*
-- Check size of void* - done
[91mCMake Warning (dev) at /usr/local/lib/python3.6/site-packages/cmake/data/share/cmake-3.18/Modules/FindPackageHandleStandardArgs.cmake:273 (message):
  The package name passed to `find_package_handle_standard_args` (OpenMP_C)
  does not match the name of the calling package (OpenMP).  This can lead to
  problems in calling code that expects `find_package` result variables
  (e.g., `_FOUND`) to follow a certain pattern.
Call Stack (most recent call first):
  cmake/Modules/FindOpenMP.cmake:565 (find_package_handle_standard_args)
  cmake/Modules/FindMKL.cmake:213 (FIND_PACKAGE)
  cmake/Modules/FindMKL.cmake:307 (CHECK_ALL_LIBRARIES)
  cmake/Dependencies.cmake:136 (find_package)
  CMakeLists.txt:485 (include)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Warning (dev) at /usr/local/lib/python3.6/site-packages/cmake/data/share/cmake-3.18/Modules/FindPackageHandleStandardArgs.cmake:273 (message):
  The package name passed to `find_package_handle_standard_args` (OpenMP_CXX)
  does not match the name of the calling package (OpenMP).  This can lead to
  problems in calling code that expects `find_package` result variables
  (e.g., `_FOUND`) to follow a certain pattern.
Call Stack (most recent call first):
  cmake/Modules/FindOpenMP.cmake:565 (find_package_handle_standard_args)
  cmake/Modules/FindMKL.cmake:213 (FIND_PACKAGE)
  cmake/Modules/FindMKL.cmake:307 (CHECK_ALL_LIBRARIES)
  cmake/Dependencies.cmake:136 (find_package)
  CMakeLists.txt:485 (include)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m-- Looking for cblas_sgemm
-- Looking for cblas_sgemm - found
-- MKL libraries: /usr/local/lib/libmkl_intel_lp64.so;/usr/local/lib/libmkl_gnu_thread.so;/usr/local/lib/libmkl_core.so;-fopenmp;/usr/lib/x86_64-linux-gnu/libpthread.so;/usr/lib/x86_64-linux-gnu/libm.so;/usr/lib/x86_64-linux-gnu/libdl.so
-- MKL include directory: /usr/local/include
-- MKL OpenMP type: GNU
-- MKL OpenMP library: -fopenmp
-- The ASM compiler identification is GNU
-- Found assembler: /usr/bin/cc
-- Brace yourself, we are building NNPACK
-- Performing Test NNPACK_ARCH_IS_X86_32
-- Performing Test NNPACK_ARCH_IS_X86_32 - Failed
-- Found PythonInterp: /usr/bin/python (found version "3.6.10") 
-- NNPACK backend is x86-64
-- Failed to find LLVM FileCheck
-- Found Git: /usr/bin/git (found version "2.7.4") 
[91m-- git Version: v1.4.0-505be96a
[0m[91m-- Version: 1.4.0
[0m-- Performing Test HAVE_CXX_FLAG_STD_CXX11
-- Performing Test HAVE_CXX_FLAG_STD_CXX11 - Success
-- Performing Test HAVE_CXX_FLAG_WALL
-- Performing Test HAVE_CXX_FLAG_WALL - Success
-- Performing Test HAVE_CXX_FLAG_WEXTRA
-- Performing Test HAVE_CXX_FLAG_WEXTRA - Success
-- Performing Test HAVE_CXX_FLAG_WSHADOW
-- Performing Test HAVE_CXX_FLAG_WSHADOW - Success
-- Performing Test HAVE_CXX_FLAG_WERROR
-- Performing Test HAVE_CXX_FLAG_WERROR - Success
-- Performing Test HAVE_CXX_FLAG_PEDANTIC
-- Performing Test HAVE_CXX_FLAG_PEDANTIC - Success
-- Performing Test HAVE_CXX_FLAG_PEDANTIC_ERRORS
-- Performing Test HAVE_CXX_FLAG_PEDANTIC_ERRORS - Success
-- Performing Test HAVE_CXX_FLAG_WSHORTEN_64_TO_32
-- Performing Test HAVE_CXX_FLAG_WSHORTEN_64_TO_32 - Failed
-- Performing Test HAVE_CXX_FLAG_WFLOAT_EQUAL
-- Performing Test HAVE_CXX_FLAG_WFLOAT_EQUAL - Success
-- Performing Test HAVE_CXX_FLAG_FSTRICT_ALIASING
-- Performing Test HAVE_CXX_FLAG_FSTRICT_ALIASING - Success
-- Performing Test HAVE_CXX_FLAG_WNO_DEPRECATED_DECLARATIONS
-- Performing Test HAVE_CXX_FLAG_WNO_DEPRECATED_DECLARATIONS - Success
-- Performing Test HAVE_CXX_FLAG_WSTRICT_ALIASING
-- Performing Test HAVE_CXX_FLAG_WSTRICT_ALIASING - Success
-- Performing Test HAVE_CXX_FLAG_WD654
-- Performing Test HAVE_CXX_FLAG_WD654 - Failed
-- Performing Test HAVE_CXX_FLAG_WTHREAD_SAFETY
-- Performing Test HAVE_CXX_FLAG_WTHREAD_SAFETY - Failed
-- Performing Test HAVE_CXX_FLAG_COVERAGE
-- Performing Test HAVE_CXX_FLAG_COVERAGE - Success
[91m-- Performing Test HAVE_STD_REGEX
-- Performing Test HAVE_STD_REGEX
[0m[91m-- Performing Test HAVE_STD_REGEX -- success
[0m[91m-- Performing Test HAVE_GNU_POSIX_REGEX
[0m[91m-- Performing Test HAVE_GNU_POSIX_REGEX
[0m[91m-- Performing Test HAVE_GNU_POSIX_REGEX -- failed to compile
[0m[91m-- Performing Test HAVE_POSIX_REGEX
-- Performing Test HAVE_POSIX_REGEX
[0m[91m-- Performing Test HAVE_POSIX_REGEX -- success
[0m[91m-- Performing Test HAVE_STEADY_CLOCK[0m[91m
[0m[91m-- Performing Test HAVE_STEADY_CLOCK[0m[91m
[0m[91m-- Performing Test HAVE_STEADY_CLOCK -- success
[0m-- Performing Test COMPILER_SUPPORTS_AVX512
-- Performing Test COMPILER_SUPPORTS_AVX512 - Success
[91mCMake Warning (dev) at /usr/local/lib/python3.6/site-packages/cmake/data/share/cmake-3.18/Modules/FindPackageHandleStandardArgs.cmake:273 (message):
  The package name passed to `find_package_handle_standard_args` (OpenMP_C)
  does not match the name of the calling package (OpenMP).  This can lead to
  problems in calling code that expects `find_package` result variables
  (e.g., `_FOUND`) to follow a certain pattern.
Call Stack (most recent call first):
  cmake/Modules/FindOpenMP.cmake:565 (find_package_handle_standard_args)
  third_party/fbgemm/CMakeLists.txt:59 (find_package)
This warning is for project developers.  Use -Wno-dev to suppress it.
[0m[91m
[0m-- Found OpenMP_C: -fopenmp (found version "4.0") 
[91mCMake Warning (dev) at /usr/local/lib/python3.6/site-packages/cmake/data/share/cmake-3.18/Modules/FindPackageHandleStandardArgs.cmake:273 (message):
  The package name passed to `find_package_handle_standard_args` (OpenMP_CXX)
  does not match the name of the calling package (OpenMP).  This can lead to
  problems in calling code that expects `find_package` result variables
  (e.g., `_FOUND`) to follow a certain pattern.
Call Stack (most recent call first):
  cmake/Modules/FindOpenMP.cmake:565 (find_package_handle_standard_args)
  third_party/fbgemm/CMakeLists.txt:59 (find_package)
This warning is for project developers.  Use -Wno-dev to suppress it.
[0m[91m
[0m-- Found OpenMP_CXX: -fopenmp (found version "4.0") 
-- Found OpenMP: TRUE (found version "4.0")  
[91mCMake Warning at third_party/fbgemm/CMakeLists.txt:61 (message):
  OpenMP found! OpenMP_C_INCLUDE_DIRS =

[0m[91m
[0m[91mCMake Warning at third_party/fbgemm/CMakeLists.txt:130 (message):
  ==========

[0m[91m
[0m[91mCMake Warning at third_party/fbgemm/CMakeLists.txt:131 (message):
  CMAKE_BUILD_TYPE = Release

[0m[91m
[0m[91mCMake Warning at third_party/fbgemm/CMakeLists.txt:132 (message):
  CMAKE_CXX_FLAGS_DEBUG is -g

[0m[91m
[0m[91mCMake Warning at third_party/fbgemm/CMakeLists.txt:133 (message):
  CMAKE_CXX_FLAGS_RELEASE is -O3 -DNDEBUG

[0m[91m
[0m[91mCMake Warning at third_party/fbgemm/CMakeLists.txt:134 (message):
  ==========

[0m[91m
[0m-- Performing Test __CxxFlag__fno_threadsafe_statics
-- Performing Test __CxxFlag__fno_threadsafe_statics - Success
-- Performing Test __CxxFlag__fno_semantic_interposition
-- Performing Test __CxxFlag__fno_semantic_interposition - Success
-- Performing Test __CxxFlag__fmerge_all_constants
-- Performing Test __CxxFlag__fmerge_all_constants - Success
[91m** AsmJit Summary **
   ASMJIT_DIR=/pytorch/pytorch_build/nightly/pytorch_nightly/third_party/fbgemm/third_party/asmjit
   ASMJIT_TEST=FALSE
   ASMJIT_TARGET_TYPE=STATIC
[0m[91m   ASMJIT_DEPS=pthread;rt
   ASMJIT_LIBS=asmjit;pthread;rt
   ASMJIT_CFLAGS=-DASMJIT_STATIC
   ASMJIT_PRIVATE_CFLAGS=-Wall;-Wextra;-fno-math-errno;-fno-threadsafe-statics;-fno-semantic-interposition;-DASMJIT_STATIC
   ASMJIT_PRIVATE_CFLAGS_DBG=
   ASMJIT_PRIVATE_CFLAGS_REL=-O2;-fmerge-all-constants
[0m-- Could NOT find Numa (missing: Numa_INCLUDE_DIR Numa_LIBRARIES) 
[91mCMake Warning at cmake/Dependencies.cmake:748 (message):
  Not compiling with NUMA.  Suppress this warning with -DUSE_NUMA=OFF
Call Stack (most recent call first):
  CMakeLists.txt:485 (include)

[0m[91m
[0m-- Using third party subdirectory Eigen.
-- Found PythonInterp: /usr/bin/python (found suitable version "3.6.10", minimum required is "3.0") 
-- Found PythonLibs: /usr/local/lib/libpython3.6m.a (found suitable version "3.6.10", minimum required is "3.0") 
-- Could NOT find pybind11 (missing: pybind11_DIR)
-- Found pybind11: /pytorch/pytorch_build/nightly/pytorch_nightly/torch/include  
-- System pybind11 found
-- pybind11 include dirs: /pytorch/pytorch_build/nightly/pytorch_nightly/torch/include
-- Could NOT find MPI_C (missing: MPI_C_LIB_NAMES MPI_C_HEADER_DIR MPI_C_WORKS) 
-- Could NOT find MPI_CXX (missing: MPI_CXX_LIB_NAMES MPI_CXX_HEADER_DIR MPI_CXX_WORKS) 
-- Could NOT find MPI (missing: MPI_C_FOUND MPI_CXX_FOUND) 
    Reason given by package: MPI component 'Fortran' was requested, but language Fortran is not enabled.  

[91mCMake Warning at cmake/Dependencies.cmake:1010 (message):
  Not compiling with MPI.  Suppress this warning with -DUSE_MPI=OFF
Call Stack (most recent call first):
  CMakeLists.txt:485 (include)


[0m[91mCMake Warning (dev) at /usr/local/lib/python3.6/site-packages/cmake/data/share/cmake-3.18/Modules/FindPackageHandleStandardArgs.cmake:273 (message):
  The package name passed to `find_package_handle_standard_args` (OpenMP_C)
  does not match the name of the calling package (OpenMP).  This can lead to
  problems in calling code that expects `find_package` result variables
  (e.g., `_FOUND`) to follow a certain pattern.
Call Stack (most recent call first):
  cmake/Modules/FindOpenMP.cmake:565 (find_package_handle_standard_args)
  cmake/Dependencies.cmake:1065 (find_package)
  CMakeLists.txt:485 (include)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Warning (dev) at /usr/local/lib/python3.6/site-packages/cmake/data/share/cmake-3.18/Modules/FindPackageHandleStandardArgs.cmake:273 (message):
  The package name passed to `find_package_handle_standard_args` (OpenMP_CXX)
  does not match the name of the calling package (OpenMP).  This can lead to
  problems in calling code that expects `find_package` result variables
  (e.g., `_FOUND`) to follow a certain pattern.
Call Stack (most recent call first):
  cmake/Modules/FindOpenMP.cmake:565 (find_package_handle_standard_args)
  cmake/Dependencies.cmake:1065 (find_package)
  CMakeLists.txt:485 (include)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m-- Adding OpenMP CXX_FLAGS: -fopenmp
-- Will link against OpenMP libraries: /usr/lib/gcc/x86_64-linux-gnu/5/libgomp.so;/usr/lib/x86_64-linux-gnu/libpthread.so
-- Found CUDA: /usr/local/cuda (found version "10.0") 
-- Caffe2: CUDA detected: 10.0
-- Caffe2: CUDA nvcc is: /usr/local/cuda/bin/nvcc
-- Caffe2: CUDA toolkit directory: /usr/local/cuda
-- Caffe2: Header version is: 10.0
-- Found CUDNN: /usr/lib/x86_64-linux-gnu/libcudnn.so  
-- Found cuDNN: v7.6.5  (include: /usr/include, library: /usr/lib/x86_64-linux-gnu/libcudnn.so)
-- Autodetected CUDA architecture(s):  7.5
-- Added CUDA NVCC flags for: -gencode;arch=compute_75,code=sm_75
-- Autodetected CUDA architecture(s):  7.5
[91mCMake Warning at cmake/External/nccl.cmake:65 (message):
  Objcopy version is too old to support NCCL library slimming
Call Stack (most recent call first):
  cmake/Dependencies.cmake:1237 (include)
  CMakeLists.txt:485 (include)


[0m-- Could NOT find CUB (missing: CUB_INCLUDE_DIR) 
[91mCMake Warning (dev) at third_party/gloo/CMakeLists.txt:21 (option):
  Policy CMP0077 is not set: option() honors normal variables.  Run "cmake
  --help-policy CMP0077" for policy details.  Use the cmake_policy command to
  set the policy and suppress this warning.

  For compatibility with older versions of CMake, option is clearing the
  normal variable 'BUILD_BENCHMARK'.
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m-- Found CUDA: /usr/local/cuda (found suitable version "10.0", minimum required is "7.0") 
-- CUDA detected: 10.0
[91mCMake Warning (dev) at /usr/local/lib/python3.6/site-packages/cmake/data/share/cmake-3.18/Modules/FindPackageHandleStandardArgs.cmake:273 (message):
  The package name passed to `find_package_handle_standard_args` (NCCL) does
  not match the name of the calling package (nccl).  This can lead to
  problems in calling code that expects `find_package` result variables
  (e.g., `_FOUND`) to follow a certain pattern.
Call Stack (most recent call first):
  third_party/gloo/cmake/Modules/Findnccl.cmake:45 (find_package_handle_standard_args)
  third_party/gloo/cmake/Dependencies.cmake:91 (find_package)
  third_party/gloo/CMakeLists.txt:75 (include)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m-- Found NCCL: /usr/include  
-- Determining NCCL version from the header file: /usr/include/nccl.h
-- NCCL_MAJOR_VERSION: 2
-- Found NCCL (include: /usr/include, library: /usr/lib/x86_64-linux-gnu/libnccl.so)
-- Performing Test UV_LINT_W4
-- Performing Test UV_LINT_W4 - Failed
-- Performing Test UV_LINT_WALL
-- Performing Test UV_LINT_WALL - Success
-- Performing Test UV_LINT_NO_UNUSED_PARAMETER
-- Performing Test UV_LINT_NO_UNUSED_PARAMETER - Success
-- Performing Test UV_LINT_STRICT_PROTOTYPES
-- Performing Test UV_LINT_STRICT_PROTOTYPES - Success
-- Performing Test UV_LINT_EXTRA
-- Performing Test UV_LINT_EXTRA - Success
-- Found uv: 1.38.1 (found version "1.38.1") 
[91mCMake Warning at cmake/Dependencies.cmake:1350 (message):
  Metal is only used in ios builds.
Call Stack (most recent call first):
  CMakeLists.txt:485 (include)


[0m[91mGenerated: /pytorch/pytorch_build/nightly/pytorch_nightly/build/third_party/onnx/onnx/onnx_onnx_torch-ml.proto
[0m[91mGenerated: /pytorch/pytorch_build/nightly/pytorch_nightly/build/third_party/onnx/onnx/onnx-operators_onnx_torch-ml.proto
[0m-- 
-- ******** Summary ********
--   CMake version         : 3.18.2
--   CMake command         : /usr/local/lib/python3.6/site-packages/cmake/data/bin/cmake
--   System                : Linux
--   C++ compiler          : /usr/bin/c++
--   C++ compiler version  : 5.4.0
--   CXX flags             :  -Wno-deprecated -fvisibility-inlines-hidden -DUSE_PTHREADPOOL -fopenmp -Wnon-virtual-dtor
--   Build type            : Release
--   Compile definitions   : TH_BLAS_MKL;ONNX_ML=1;ONNXIFI_ENABLE_EXT=1
--   CMAKE_PREFIX_PATH     : /usr/local/lib/python3.6/site-packages;/usr/local/cuda
--   CMAKE_INSTALL_PREFIX  : /pytorch/pytorch_build/nightly/pytorch_nightly/torch
--   CMAKE_MODULE_PATH     : /pytorch/pytorch_build/nightly/pytorch_nightly/cmake/Modules;/pytorch/pytorch_build/nightly/pytorch_nightly/cmake/public/../Modules_CUDA_fix
-- 
--   ONNX version          : 1.7.0
--   ONNX NAMESPACE        : onnx_torch
--   ONNX_BUILD_TESTS      : OFF
--   ONNX_BUILD_BENCHMARKS : OFF
--   ONNX_USE_LITE_PROTO   : OFF
--   ONNXIFI_DUMMY_BACKEND : OFF
--   ONNXIFI_ENABLE_EXT    : OFF
-- 
--   Protobuf compiler     : 
--   Protobuf includes     : 
--   Protobuf libraries    : 
--   BUILD_ONNX_PYTHON     : OFF
-- 
-- ******** Summary ********
--   CMake version         : 3.18.2
--   CMake command         : /usr/local/lib/python3.6/site-packages/cmake/data/bin/cmake
--   System                : Linux
--   C++ compiler          : /usr/bin/c++
--   C++ compiler version  : 5.4.0
--   CXX flags             :  -Wno-deprecated -fvisibility-inlines-hidden -DUSE_PTHREADPOOL -fopenmp -Wnon-virtual-dtor
--   Build type            : Release
--   Compile definitions   : TH_BLAS_MKL;ONNX_ML=1;ONNXIFI_ENABLE_EXT=1
--   CMAKE_PREFIX_PATH     : /usr/local/lib/python3.6/site-packages;/usr/local/cuda
--   CMAKE_INSTALL_PREFIX  : /pytorch/pytorch_build/nightly/pytorch_nightly/torch
--   CMAKE_MODULE_PATH     : /pytorch/pytorch_build/nightly/pytorch_nightly/cmake/Modules;/pytorch/pytorch_build/nightly/pytorch_nightly/cmake/public/../Modules_CUDA_fix
-- 
--   ONNX version          : 1.4.1
--   ONNX NAMESPACE        : onnx_torch
--   ONNX_BUILD_TESTS      : OFF
--   ONNX_BUILD_BENCHMARKS : OFF
--   ONNX_USE_LITE_PROTO   : OFF
--   ONNXIFI_DUMMY_BACKEND : OFF
-- 
--   Protobuf compiler     : 
--   Protobuf includes     : 
--   Protobuf libraries    : 
--   BUILD_ONNX_PYTHON     : OFF
-- Found CUDA with FP16 support, compiling with torch.cuda.HalfTensor
-- Adding -DNDEBUG to compile flags
-- MAGMA not found. Compiling without MAGMA support
-- Could not find hardware support for NEON on this machine.
-- No OMAP3 processor on this machine.
-- No OMAP4 processor on this machine.
-- Looking for cpuid.h
-- Looking for cpuid.h - found
-- Performing Test HAVE_GCC_GET_CPUID
-- Performing Test HAVE_GCC_GET_CPUID - Success
-- Performing Test NO_GCC_EBX_FPIC_BUG
-- Performing Test NO_GCC_EBX_FPIC_BUG - Success
-- Performing Test C_HAS_AVX_1
-- Performing Test C_HAS_AVX_1 - Failed
-- Performing Test C_HAS_AVX_2
-- Performing Test C_HAS_AVX_2 - Success
-- Performing Test C_HAS_AVX2_1
-- Performing Test C_HAS_AVX2_1 - Failed
-- Performing Test C_HAS_AVX2_2
-- Performing Test C_HAS_AVX2_2 - Success
-- Performing Test CXX_HAS_AVX_1
-- Performing Test CXX_HAS_AVX_1 - Failed
-- Performing Test CXX_HAS_AVX_2
-- Performing Test CXX_HAS_AVX_2 - Success
-- Performing Test CXX_HAS_AVX2_1
-- Performing Test CXX_HAS_AVX2_1 - Failed
-- Performing Test CXX_HAS_AVX2_2
-- Performing Test CXX_HAS_AVX2_2 - Success
-- AVX compiler support found
-- AVX2 compiler support found
-- Performing Test BLAS_F2C_DOUBLE_WORKS
-- Performing Test BLAS_F2C_DOUBLE_WORKS - Failed
-- Performing Test BLAS_F2C_FLOAT_WORKS
-- Performing Test BLAS_F2C_FLOAT_WORKS - Success
-- Performing Test BLAS_USE_CBLAS_DOT
-- Performing Test BLAS_USE_CBLAS_DOT - Success
-- Found a library with BLAS API (mkl).
-- Found a library with LAPACK API (mkl).
[91mdisabling ROCM because NOT USE_ROCM is set
[0m-- MIOpen not found. Compiling without MIOpen support
-- MKLDNN_CPU_RUNTIME = OMP
-- Intel MKL-DNN compat: set DNNL_ENABLE_CONCURRENT_EXEC to MKLDNN_ENABLE_CONCURRENT_EXEC with value `ON`
-- Intel MKL-DNN compat: set DNNL_BUILD_EXAMPLES to MKLDNN_BUILD_EXAMPLES with value `FALSE`
-- Intel MKL-DNN compat: set DNNL_BUILD_TESTS to MKLDNN_BUILD_TESTS with value `FALSE`
-- Intel MKL-DNN compat: set DNNL_LIBRARY_TYPE to MKLDNN_LIBRARY_TYPE with value `STATIC`
-- Intel MKL-DNN compat: set DNNL_CPU_RUNTIME to MKLDNN_CPU_RUNTIME with value `OMP`
[91mCMake Warning (dev) at /usr/local/lib/python3.6/site-packages/cmake/data/share/cmake-3.18/Modules/FindPackageHandleStandardArgs.cmake:273 (message):
  The package name passed to `find_package_handle_standard_args` (OpenMP_C)
  does not match the name of the calling package (OpenMP).  This can lead to
  problems in calling code that expects `find_package` result variables
  (e.g., `_FOUND`) to follow a certain pattern.
Call Stack (most recent call first):
  cmake/Modules/FindOpenMP.cmake:565 (find_package_handle_standard_args)
  third_party/ideep/mkl-dnn/cmake/OpenMP.cmake:61 (find_package)
  third_party/ideep/mkl-dnn/CMakeLists.txt:114 (include)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m-- Found OpenMP_C: -fopenmp (found version "4.0") 
[91mCMake Warning (dev) at /usr/local/lib/python3.6/site-packages/cmake/data/share/cmake-3.18/Modules/FindPackageHandleStandardArgs.cmake:273 (message):
  The package name passed to `find_package_handle_standard_args` (OpenMP_CXX)
  does not match the name of the calling package (OpenMP).  This can lead to
  problems in calling code that expects `find_package` result variables
  (e.g., `_FOUND`) to follow a certain pattern.
Call Stack (most recent call first):
  cmake/Modules/FindOpenMP.cmake:565 (find_package_handle_standard_args)
  third_party/ideep/mkl-dnn/cmake/OpenMP.cmake:61 (find_package)
  third_party/ideep/mkl-dnn/CMakeLists.txt:114 (include)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m-- Found OpenMP_CXX: -fopenmp (found version "4.0") 
-- GPU support is disabled
[91mfatal: Not a git repository: /pytorch/pytorch/.git/modules/third_party/ideep/modules/mkl-dnn
[0m-- Primitive cache is enabled
-- Found MKL-DNN: TRUE
-- Looking for clock_gettime in rt
-- Looking for clock_gettime in rt - found
-- Looking for mmap
-- Looking for mmap - found
-- Looking for shm_open
-- Looking for shm_open - found
-- Looking for shm_unlink
-- Looking for shm_unlink - found
-- Looking for malloc_usable_size
-- Looking for malloc_usable_size - found
-- Performing Test C_HAS_THREAD
-- Performing Test C_HAS_THREAD - Success
-- Version: 6.2.0
-- Build type: Release
-- CXX_STANDARD: 14
-- Performing Test has_std_14_flag
-- Performing Test has_std_14_flag - Success
-- Performing Test has_std_1y_flag
-- Performing Test has_std_1y_flag - Success
-- Performing Test SUPPORTS_USER_DEFINED_LITERALS
-- Performing Test SUPPORTS_USER_DEFINED_LITERALS - Success
-- Performing Test FMT_HAS_VARIANT
-- Performing Test FMT_HAS_VARIANT - Failed
-- Required features: cxx_variadic_templates
-- Looking for strtod_l
-- Looking for strtod_l - not found
-- GCC 5.4.0: Adding gcc and gcc_s libs to link line
-- Performing Test HAS_WERROR_FORMAT
-- Performing Test HAS_WERROR_FORMAT - Success
-- Looking for backtrace
-- Looking for backtrace - found
-- backtrace facility detected in default set of libraries
-- Found Backtrace: /usr/include  
-- don't use NUMA
[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


CMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/test/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


[0m[91mCMake Error at c10/test/CMakeLists.txt:10 (add_test):
  add_test given test NAME "c10_" which already exists in this directory.


[0m[91mCMake Error at c10/benchmark/CMakeLists.txt:8 (add_executable):
  add_executable cannot create target "c10_" because another target with the
  same name already exists.  The existing target is an executable created in
  source directory "/pytorch/pytorch_build/nightly/pytorch_nightly/c10/test".
  See documentation for policy CMP0002 for more details.


CMake Error at c10/benchmark/CMakeLists.txt:9 (target_link_libraries):
  Attempt to add link library "c10" to target "c10_" which is not built in
  this directory.

  This is allowed only when policy CMP0079 is set to NEW.


[0m-- Performing Test COMPILER_SUPPORTS_NO_AVX256_SPLIT
-- Performing Test COMPILER_SUPPORTS_NO_AVX256_SPLIT - Success
-- Using ATen parallel backend: OMP
[91mCMake Deprecation Warning at third_party/sleef/CMakeLists.txt:20 (cmake_policy):
  The OLD behavior for policy CMP0066 will be removed from a future version
  of CMake.

  The cmake-policies(7) manual explains that the OLD behaviors of all
  policies are deprecated and that a policy should be set to OLD only under
  specific short-term circumstances.  Projects should be ported to the NEW
  behavior and not rely on setting a policy to OLD.


[0m-- Found OpenSSL: /usr/lib/x86_64-linux-gnu/libcrypto.so (found version "1.0.2g")  
-- Check size of long double
-- Check size of long double - done
-- Performing Test COMPILER_SUPPORTS_LONG_DOUBLE
-- Performing Test COMPILER_SUPPORTS_LONG_DOUBLE - Success
-- Performing Test COMPILER_SUPPORTS_FLOAT128
-- Performing Test COMPILER_SUPPORTS_FLOAT128 - Success
-- Performing Test COMPILER_SUPPORTS_SSE2
-- Performing Test COMPILER_SUPPORTS_SSE2 - Success
-- Performing Test COMPILER_SUPPORTS_SSE4
-- Performing Test COMPILER_SUPPORTS_SSE4 - Success
-- Performing Test COMPILER_SUPPORTS_AVX
-- Performing Test COMPILER_SUPPORTS_AVX - Success
-- Performing Test COMPILER_SUPPORTS_FMA4
-- Performing Test COMPILER_SUPPORTS_FMA4 - Success
-- Performing Test COMPILER_SUPPORTS_AVX2
-- Performing Test COMPILER_SUPPORTS_AVX2 - Success
-- Performing Test COMPILER_SUPPORTS_AVX512F
-- Performing Test COMPILER_SUPPORTS_AVX512F - Failed
-- Performing Test COMPILER_SUPPORTS_OPENMP
-- Performing Test COMPILER_SUPPORTS_OPENMP - Success
-- Performing Test COMPILER_SUPPORTS_WEAK_ALIASES
-- Performing Test COMPILER_SUPPORTS_WEAK_ALIASES - Success
-- Performing Test COMPILER_SUPPORTS_BUILTIN_MATH
-- Performing Test COMPILER_SUPPORTS_BUILTIN_MATH - Success
-- Performing Test COMPILER_SUPPORTS_SYS_GETRANDOM
-- Performing Test COMPILER_SUPPORTS_SYS_GETRANDOM - Success
-- Configuring build for SLEEF-v3.4.0
-- Using option `-Wall -Wno-unused -Wno-attributes -Wno-unused-result -Wno-psabi -ffp-contract=off -fno-math-errno -fno-trapping-math` to compile libsleef
-- Building shared libs : OFF
-- MPFR : LIB_MPFR-NOTFOUND
-- GMP : LIBGMP-NOTFOUND
-- RT : /usr/lib/x86_64-linux-gnu/librt.so
-- FFTW3 : LIBFFTW3-NOTFOUND
-- OPENSSL : 1.0.2g
-- SDE : SDE_COMMAND-NOTFOUND
[91m   Target system: Linux-4.15.0-106-generic
   Target processor: x86_64
   Host system: Linux-4.15.0-106-generic
   Host processor: x86_64
   Detected C compiler: GNU @ /usr/bin/cc
[0m-- RUNNING_ON_TRAVIS : 0
-- COMPILER_SUPPORTS_OPENMP : 1
[91mAT_INSTALL_INCLUDE_DIR include/ATen/core
core header install: /pytorch/pytorch_build/nightly/pytorch_nightly/build/aten/src/ATen/core/TensorBody.h
[0m-- Include NCCL operators
-- Excluding FakeLowP operators
-- Including IDEEP operators
-- Excluding image processing operators due to no opencv
-- Excluding video processing operators due to no opencv
-- MPI operators skipped due to no MPI support
-- Include Observer library
-- /usr/bin/c++ /pytorch/pytorch_build/nightly/pytorch_nightly/torch/abi-check.cpp -o /pytorch/pytorch_build/nightly/pytorch_nightly/build/abi-check
-- Determined _GLIBCXX_USE_CXX11_ABI=1
-- Autodetected CUDA architecture(s):  7.5
[91mCMake Warning (dev) at /usr/local/lib/python3.6/site-packages/cmake/data/share/cmake-3.18/Modules/FindPackageHandleStandardArgs.cmake:273 (message):
  The package name passed to `find_package_handle_standard_args` (OpenMP_C)
  does not match the name of the calling package (OpenMP).  This can lead to
  problems in calling code that expects `find_package` result variables
  (e.g., `_FOUND`) to follow a certain pattern.
Call Stack (most recent call first):
  cmake/Modules/FindOpenMP.cmake:565 (find_package_handle_standard_args)
  caffe2/CMakeLists.txt:890 (find_package)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Warning (dev) at /usr/local/lib/python3.6/site-packages/cmake/data/share/cmake-3.18/Modules/FindPackageHandleStandardArgs.cmake:273 (message):
  The package name passed to `find_package_handle_standard_args` (OpenMP_CXX)
  does not match the name of the calling package (OpenMP).  This can lead to
  problems in calling code that expects `find_package` result variables
  (e.g., `_FOUND`) to follow a certain pattern.
Call Stack (most recent call first):
  cmake/Modules/FindOpenMP.cmake:565 (find_package_handle_standard_args)
  caffe2/CMakeLists.txt:890 (find_package)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m-- pytorch is compiling with OpenMP. 
OpenMP CXX_FLAGS: -fopenmp. 
OpenMP libraries: /usr/lib/gcc/x86_64-linux-gnu/5/libgomp.so;/usr/lib/x86_64-linux-gnu/libpthread.so.
-- Caffe2 is compiling with OpenMP. 
OpenMP CXX_FLAGS: -fopenmp. 
OpenMP libraries: /usr/lib/gcc/x86_64-linux-gnu/5/libgomp.so;/usr/lib/x86_64-linux-gnu/libpthread.so.
[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/aten/src/ATen/core/._List_test.cpp"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/aten/src/ATen/core/._TensorImpl_test.cpp"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/aten/src/ATen/core/boxing/._KernelFunction_test.cpp"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/aten/src/ATen/core/boxing/impl/._kernel_function_legacy_test.cpp"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/aten/src/ATen/core/boxing/impl/._kernel_function_test.cpp"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/aten/src/ATen/core/boxing/impl/._kernel_lambda_legacy_test.cpp"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/aten/src/ATen/core/boxing/impl/._kernel_lambda_test.cpp"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/aten/src/ATen/core/boxing/impl/._kernel_stackbased_test.cpp"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


[0m[91mCMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/aten/src/ATen/core/boxing/impl/._make_boxed_from_unboxed_functor_test.cpp"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/aten/src/ATen/core/dispatch/._CppSignature_test.cpp"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/aten/src/ATen/core/dispatch/._backend_fallback_test.cpp"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/aten/src/ATen/core/op_registration/._op_registration_test.cpp"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/aten/src/ATen/core/op_registration/._op_whitelist_test.cpp"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._blob_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._common_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._context_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._event_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.

[0m[91m
CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._graph_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._init_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._module_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


[0m[91mCMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._net_async_tracing_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._net_dag_utils_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


[0m[91mCMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._net_simple_refcount_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


[0m[91mCMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.

[0m[91m
[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._net_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


[0m[91mCMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._observer_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.

[0m[91m
[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._operator_schema_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._operator_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


[0m[91mCMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._parallel_net_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._plan_executor_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._stats_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._timer_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._transform_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._workspace_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


[0m[91mCMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/serialize/._inline_container_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/nomnigraph/tests/._AlgorithmsTest.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/nomnigraph/tests/._BinaryMatchImplTest.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/nomnigraph/tests/._GraphTest.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


CMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/nomnigraph/tests/._MatchTest.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.

[0m[91m
CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/nomnigraph/tests/._NeuralNetTest.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/nomnigraph/tests/._SubgraphMatcherTest.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/nomnigraph/tests/._TarjansImplTest.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/nomnigraph/tests/._TopoSortTest.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/observers/._time_observer_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/onnx/._ssa_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._batch_matmul_op_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._boolean_unmask_ops_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._conv_transpose_op_mobile_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._elementwise_op_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._generate_proposals_op_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._generate_proposals_op_util_boxes_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._generate_proposals_op_util_nms_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


[0m[91mCMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._half_float_ops_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._string_ops_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._text_file_reader_utils_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._utility_ops_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


[0m[91mCMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/opt/._backend_cutting_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/opt/._bound_shape_inference_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/opt/._converter_nomigraph_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/opt/._dead_code_elim_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


[0m[91mCMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


CMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/opt/._device_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/opt/._distributed_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/opt/._mobile_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/opt/._split_slss_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/transforms/._common_subexpression_elimination_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/transforms/._conv_to_nnpack_transform_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1236 (add_executable):
  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/transforms/._pattern_net_transform_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.


CMake Error at caffe2/CMakeLists.txt:1237 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1238 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1239 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1240 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1241 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._blob_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._context_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._event_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._net_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/core/._operator_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._conv_op_cache_cudnn_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._batch_matmul_op_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._batch_permutation_op_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._elementwise_op_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._generate_proposals_op_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._generate_proposals_op_util_nms_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._operator_fallback_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._reshape_op_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._roi_align_op_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


[0m[91mCMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m[91mCMake Warning (dev) at cmake/Modules_CUDA_fix/upstream/FindCUDA.cmake:1897 (add_executable):
  Policy CMP0037 is not set: Target names should not be reserved and should
  match a validity pattern.  Run "cmake --help-policy CMP0037" for policy
  details.  Use the cmake_policy command to set the policy and suppress this
  warning.

  The target name
  "/pytorch/pytorch_build/nightly/pytorch_nightly/caffe2/operators/._utility_ops_gpu_test.cc"
  is reserved or not valid for certain CMake features, such as generator
  expressions, and may result in undefined behavior.
Call Stack (most recent call first):
  caffe2/CMakeLists.txt:1254 (cuda_add_executable)
This warning is for project developers.  Use -Wno-dev to suppress it.

[0m[91mCMake Error at caffe2/CMakeLists.txt:1255 (target_link_libraries):
  INTERFACE library can only be used with the INTERFACE keyword of
  target_link_libraries


CMake Error at caffe2/CMakeLists.txt:1256 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1257 (target_include_directories):
  Cannot specify include directories for target "PRIVATE" which is not built
  by this project.


CMake Error at caffe2/CMakeLists.txt:1258 (add_test):
  add_test must be given non-empty NAME.


[0m-- Using lib/python3.6/site-packages as python relative installation path
[91mCMake Warning at CMakeLists.txt:739 (message):
  Generated cmake files are only fully tested if one builds with system glog,
  gflags, and protobuf.  Other settings may generate files that are not well
  tested.


[0m-- 
-- ******** Summary ********
-- General:
--   CMake version         : 3.18.2
--   CMake command         : /usr/local/lib/python3.6/site-packages/cmake/data/bin/cmake
--   System                : Linux
--   C++ compiler          : /usr/bin/c++
--   C++ compiler id       : GNU
--   C++ compiler version  : 5.4.0
--   BLAS                  : MKL
--   CXX flags             :  -Wno-deprecated -fvisibility-inlines-hidden -DUSE_PTHREADPOOL -fopenmp -DNDEBUG -DUSE_FBGEMM -DUSE_QNNPACK -DUSE_PYTORCH_QNNPACK -DUSE_XNNPACK -DUSE_VULKAN_WRAPPER -O2 -fPIC -Wno-narrowing -Wall -Wextra -Werror=return-type -Wno-missing-field-initializers -Wno-type-limits -Wno-array-bounds -Wno-unknown-pragmas -Wno-sign-compare -Wno-unused-parameter -Wno-unused-variable -Wno-unused-function -Wno-unused-result -Wno-unused-local-typedefs -Wno-strict-overflow -Wno-strict-aliasing -Wno-error=deprecated-declarations -Wno-psabi -Wno-error=pedantic -Wno-error=redundant-decls -Wno-error=old-style-cast -fdiagnostics-color=always -Wno-unused-but-set-variable -Wno-maybe-uninitialized -fno-math-errno -fno-trapping-math -Werror=format
--   Build type            : Release
--   Compile definitions   : TH_BLAS_MKL;ONNX_ML=1;ONNXIFI_ENABLE_EXT=1;ONNX_NAMESPACE=onnx_torch;IDEEP_USE_MKL;HAVE_MMAP=1;_FILE_OFFSET_BITS=64;HAVE_SHM_OPEN=1;HAVE_SHM_UNLINK=1;HAVE_MALLOC_USABLE_SIZE=1;USE_EXTERNAL_MZCRC;MINIZ_DISABLE_ZIP_READER_CRC32_CHECKS
--   CMAKE_PREFIX_PATH     : /usr/local/lib/python3.6/site-packages;/usr/local/cuda
--   CMAKE_INSTALL_PREFIX  : /pytorch/pytorch_build/nightly/pytorch_nightly/torch
-- 
--   TORCH_VERSION         : 1.7.0
--   CAFFE2_VERSION        : 1.7.0
--   BUILD_CAFFE2          : ON
--   BUILD_CAFFE2_OPS      : ON
--   BUILD_CAFFE2_MOBILE   : OFF
--   BUILD_BINARY          : OFF
--   BUILD_CUSTOM_PROTOBUF : ON
--     Link local protobuf : ON
--   BUILD_DOCS            : OFF
--   BUILD_PYTHON          : True
--     Python version      : 3.6.10
--     Python executable   : /usr/bin/python
--     Pythonlibs version  : 3.6.10
--     Python library      : /usr/local/lib/libpython3.6m.a
--     Python includes     : /usr/local/include/python3.6m
--     Python site-packages: lib/python3.6/site-packages
--   BUILD_SHARED_LIBS     : ON
--   BUILD_TEST            : True
--   BUILD_JNI             : OFF
--   BUILD_MOBILE_AUTOGRAD : OFF
--   INTERN_BUILD_MOBILE   : 
--   CODE_COVERAGE         : OFF
--   USE_ASAN              : OFF
--   USE_CUDA              : ON
--     CUDA static link    : OFF
--     USE_CUDNN           : 1
--     CUDA version        : 10.0
--     cuDNN version       : 7.6.5
--     CUDA root directory : /usr/local/cuda
--     CUDA library        : /usr/local/cuda/lib64/stubs/libcuda.so
--     cudart library      : /usr/local/cuda/lib64/libcudart.so
--     cublas library      : /usr/local/cuda/lib64/libcublas.so
--     cufft library       : /usr/local/cuda/lib64/libcufft.so
--     curand library      : /usr/local/cuda/lib64/libcurand.so
--     cuDNN library       : /usr/lib/x86_64-linux-gnu/libcudnn.so
--     nvrtc               : /usr/local/cuda/lib64/libnvrtc.so
--     CUDA include path   : /usr/local/cuda/include
--     NVCC executable     : /usr/local/cuda/bin/nvcc
--     NVCC flags          : -Xfatbin;-compress-all;-DONNX_NAMESPACE=onnx_torch;-gencode;arch=compute_75,code=sm_75;-Xcudafe;--diag_suppress=cc_clobber_ignored;-Xcudafe;--diag_suppress=integer_sign_change;-Xcudafe;--diag_suppress=useless_using_declaration;-Xcudafe;--diag_suppress=set_but_not_used;-Xcudafe;--diag_suppress=field_without_dll_interface;-Xcudafe;--diag_suppress=base_class_has_different_dll_interface;-Xcudafe;--diag_suppress=dll_interface_conflict_none_assumed;-Xcudafe;--diag_suppress=dll_interface_conflict_dllexport_assumed;-Xcudafe;--diag_suppress=implicit_return_from_non_void_function;-Xcudafe;--diag_suppress=unsigned_compare_with_zero;-Xcudafe;--diag_suppress=declared_but_not_referenced;-Xcudafe;--diag_suppress=bad_friend_decl;-std=c++14;-Xcompiler;-fPIC;--expt-relaxed-constexpr;--expt-extended-lambda;-Wno-deprecated-gpu-targets;--expt-extended-lambda;-gencode;arch=compute_75,code=sm_75;-Xcompiler;-fPIC;-DCUDA_HAS_FP16=1;-D__CUDA_NO_HALF_OPERATORS__;-D__CUDA_NO_HALF_CONVERSIONS__;-D__CUDA_NO_HALF2_OPERATORS__
--     CUDA host compiler  : /usr/bin/cc
--     NVCC --device-c     : OFF
--     USE_TENSORRT        : OFF
--   USE_ROCM              : OFF
--   USE_EIGEN_FOR_BLAS    : 
--   USE_FBGEMM            : ON
--     USE_FAKELOWP          : OFF
--   USE_FFMPEG            : OFF
--   USE_GFLAGS            : OFF
--   USE_GLOG              : OFF
--   USE_LEVELDB           : OFF
--   USE_LITE_PROTO        : OFF
--   USE_LMDB              : OFF
--   USE_METAL             : OFF
--   USE_MKL               : ON
--   USE_MKLDNN            : ON
--   USE_MKLDNN_CBLAS      : OFF
--   USE_NCCL              : ON
--     USE_SYSTEM_NCCL     : OFF
--   USE_NNPACK            : ON
--   USE_NUMPY             : ON
--   USE_OBSERVERS         : ON
--   USE_OPENCL            : OFF
--   USE_OPENCV            : OFF
--   USE_OPENMP            : ON
--   USE_TBB               : OFF
--   USE_VULKAN            : OFF
--   USE_PROF              : OFF
--   USE_QNNPACK           : ON
--   USE_PYTORCH_QNNPACK   : ON
--   USE_REDIS             : OFF
--   USE_ROCKSDB           : OFF
--   USE_ZMQ               : OFF
--   USE_DISTRIBUTED       : ON
--     USE_MPI             : OFF
--     USE_GLOO            : ON
--     USE_TENSORPIPE      : ON
--   Public Dependencies  : Threads::Threads;caffe2::mkl;caffe2::mkldnn
--   Private Dependencies : pthreadpool;cpuinfo;qnnpack;pytorch_qnnpack;nnpack;XNNPACK;fbgemm;fp16;gloo;tensorpipe;aten_op_header_gen;foxi_loader;rt;fmt::fmt-header-only;gcc_s;gcc;dl
-- Configuring incomplete, errors occurred!
See also "/pytorch/pytorch_build/nightly/pytorch_nightly/build/CMakeFiles/CMakeOutput.log".
See also "/pytorch/pytorch_build/nightly/pytorch_nightly/build/CMakeFiles/CMakeError.log".
Building wheel torch-1.7.0a0+7000c2e
-- Building version 1.7.0a0+7000c2e
cmake -GNinja -DBUILD_PYTHON=True -DBUILD_TEST=True -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/pytorch/pytorch_build/nightly/pytorch_nightly/torch -DCMAKE_PREFIX_PATH=/usr/local/lib/python3.6/site-packages -DNUMPY_INCLUDE_DIR=/usr/local/lib/python3.6/site-packages/numpy/core/include -DPYTHON_EXECUTABLE=/usr/bin/python -DPYTHON_INCLUDE_DIR=/usr/local/include/python3.6m -DPYTHON_LIBRARY=/usr/local/lib/libpython3.6m.a -DTORCH_BUILD_VERSION=1.7.0a0+7000c2e -DUSE_CUDNN=1 -DUSE_NUMPY=True /pytorch/pytorch_build/nightly/pytorch_nightly
[91m/usr/local/lib/python3.6/site-packages/pkg_resources/__init__.py:1900: UserWarning: /pytorch/pytorch_build/nightly/pytorch_nightly/._torch.egg-info could not be properly decoded in UTF-8
  warnings.warn(msg)
/usr/local/lib/python3.6/site-packages/pkg_resources/__init__.py:1900: UserWarning: /pytorch/pytorch_build/nightly/pytorch_nightly/._torch.egg-info could not be properly decoded in UTF-8
  warnings.warn(msg)
[0m[91mTraceback (most recent call last):
  File "setup.py", line 748, in <module>
    build_deps()
  File "setup.py", line 332, in build_deps
    cmake=cmake)
  File "/pytorch/pytorch_build/nightly/pytorch_nightly/tools/build_pytorch_libs.py", line 59, in build_caffe2
    rerun_cmake)
  File "/pytorch/pytorch_build/nightly/pytorch_nightly/tools/setup_helpers/cmake.py", line 329, in generate
    self.run(args, env=my_env)
  File "/pytorch/pytorch_build/nightly/pytorch_nightly/tools/setup_helpers/cmake.py", line 141, in run
    check_call(command, cwd=self.build_dir, env=env)
  File "/usr/local/lib/python3.6/subprocess.py", line 311, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['cmake', '-GNinja', '-DBUILD_PYTHON=True', '-DBUILD_TEST=True', '-DCMAKE_BUILD_TYPE=Release', '-DCMAKE_INSTALL_PREFIX=/pytorch/pytorch_build/nightly/pytorch_nightly/torch', '-DCMAKE_PREFIX_PATH=/usr/local/lib/python3.6/site-packages', '-DNUMPY_INCLUDE_DIR=/usr/local/lib/python3.6/site-packages/numpy/core/include', '-DPYTHON_EXECUTABLE=/usr/bin/python', '-DPYTHON_INCLUDE_DIR=/usr/local/include/python3.6m', '-DPYTHON_LIBRARY=/usr/local/lib/libpython3.6m.a', '-DTORCH_BUILD_VERSION=1.7.0a0+7000c2e', '-DUSE_CUDNN=1', '-DUSE_NUMPY=True', '/pytorch/pytorch_build/nightly/pytorch_nightly']' returned non-zero exit status 1.
[0m
