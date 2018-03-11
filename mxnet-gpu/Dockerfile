# Start with cuDNN base image
FROM daquexian/cudnn-python:cuda9.1_cudn7_python3.6
MAINTAINER daquexian <daquexian566@gmail.com>

# Switch to USTC mirrors. Comment if you are not in China.
RUN mkdir /root/.pip/ && printf "[global]\nindex-url = https://mirrors.ustc.edu.cn/pypi/web/simple\nformat = columns" > /root/.pip/pip.conf && \
    pip3 install --upgrade pip

RUN pip3 install mxnet-cu91

# The following is the way building from source, but failed
# Clone MXNet repo
# RUN cd /root && git clone --recursive --depth=1 https://github.com/apache/incubator-mxnet.git mxnet 

# RUN apt install -y gcc-4.8 g++-4.8

# RUN apt install -y software-properties-common 
# RUN add-apt-repository ppa:ubuntu-toolchain-r/test && apt update
# RUN apt install -y gcc-6 g++-6
# CMake and make with jemalloc
# RUN mkdir /root/mxnet/build && cd /root/mxnet/build && \
    # JEMALLOC_ROOT=/usr/lib/x86_64-linux-gnu/ cmake -DUSE_MKL_IF_AVAILABLE=OFF ..  && make -j $(nproc)

# make
# RUN cd /root/mxnet && make CC=/usr/bin/gcc-4.8 CXX=/usr/bin/g++-4.8 -j $(nproc) USE_OPENCV=1 USE_BLAS=openblas USE_CUDA=1 USE_CUDA_PATH=/usr/local/cuda USE_CUDNN=1

# Install Python package
# RUN apt install -y libgfortran3 && cd /root/mxnet/python && pip3 install .

# Set ~/mxnet as working directory
WORKDIR /root/mxnet
