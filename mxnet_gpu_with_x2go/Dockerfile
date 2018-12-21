# Start with cuDNN base image
FROM mxnet/python:1.3.1_gpu_cu90_mkl_py3
MAINTAINER daquexian <daquexian566@gmail.com>

# Switch to USTC mirrors. Comment if you are not in China.
RUN sed -i 's/archive.ubuntu.com/mirrors.ustc.edu.cn/' /etc/apt/sources.list

RUN apt-get update 

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get install -y openssh-server xubuntu-desktop 

RUN add-apt-repository ppa:x2go/stable

RUN apt-get update

RUN apt-get install x2goserver x2goserver-xsession pwgen -y

RUN mkdir -p /var/run/sshd && sed -i "s/UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g" /etc/ssh/sshd_config && sed -i "s/UsePAM.*/UsePAM no/g" /etc/ssh/sshd_config
RUN sed -i "s/PermitRootLogin.*/PermitRootLogin yes/g" /etc/ssh/sshd_config
RUN sed -i "s/#PasswordAuthentication/PasswordAuthentication/g" /etc/ssh/sshd_config

RUN mkdir -p /tmp/.X11-unix && chmod 1777 /tmp/.X11-unix

RUN sed -i "s/mesg n/tty -s \&\& mesg n/" /root/.profile

RUN echo "root:123456" | chpasswd

EXPOSE 22

RUN wget https://download-cf.jetbrains.com/python/pycharm-community-2018.3.2.tar.gz

CMD ["exec /usr/sbin/sshd -D"]

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

