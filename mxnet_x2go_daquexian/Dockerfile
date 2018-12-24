FROM mxnet_x2go
MAINTAINER daquexian <daquexian566@gmail.com>

RUN apt install -y git automake pkg-config libevent-dev libncurses5-dev
RUN wget https://github.com/tmux/tmux/releases/download/2.8/tmux-2.8.tar.gz && tar xf tmux-2.8.tar.gz && cd tmux-2.8 && ./configure && make -j$(nproc) && make install
RUN apt install -y zsh
COPY oh-my-zsh-install.sh /root/
COPY oh-my-zsh-master.zip /root/
WORKDIR /root/
RUN unzip /root/oh-my-zsh-master.zip && mv oh-my-zsh-master .oh-my-zsh && rm /root/oh-my-zsh-master.zip
COPY .zshrc /root/
COPY zsh-autosuggestions-master.zip /root/
RUN unzip /root/zsh-autosuggestions-master.zip && mv zsh-autosuggestions-master ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions && rm zsh-autosuggestions-master.zip
RUN chsh -s $(which zsh)
RUN git clone https://github.com/daquexian/dot_files /root/dot_files
RUN ln -s /root/dot_files/.gitconfig /root/.gitconfig && ln -s /root/dot_files/.tmux.conf && ln -s /root/dot_files/.tmux.conf.local
RUN apt install xcape && pip3 install pynvim
RUN echo "export PATH=/usr/local/nvidia/bin/:/usr/local/cuda/bin:$PATH" >> /root/.profile && echo "export LD_LIBRARY_PATH=/usr/local/nvidia/lib:/usr/local/nvidia/lib64:$LD_LIBRARY_PATH" >> /root/.profile
