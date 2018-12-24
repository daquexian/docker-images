FROM mxnet_x2go
MAINTAINER daquexian <daquexian566@gmail.com>

RUN wget https://github.com/neovim/neovim/releases/download/v0.3.1/nvim.appimage -O /root/nvim 
RUN chmod +x /root/nvim && mv /root/nvim /usr/local/bin
RUN echo "alias vim=nvim" >> /root/.profile
RUN apt install -y git automake pkg-config libevent-dev libncurses5-dev
RUN wget https://github.com/tmux/tmux/releases/download/2.8/tmux-2.8.tar.gz && tar xf tmux-2.8.tar.gz && cd tmux-2.8 && ./configure && make -j$(nproc) && make install
RUN apt install -y zsh
COPY oh-my-zsh-install.sh /root/
COPY oh-my-zsh-master.zip /root/
WORKDIR /root/
RUN unzip /root/oh-my-zsh-master.zip && mv oh-my-zsh-master .oh-my-zsh && rm /root/oh-my-zsh-master.zip
COPY .zshrc /root/
RUN git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
RUN chsh -s $(which zsh)

RUN git clone https://github.com/daquexian/dot_files /root/dot_files
RUN ln -s /root/dot_files/.vimrc /root/.vimrc && cp /root/dot_files/.vimrc.local /root/ && ln -s /root/dot_files/.gitconfig /root/.gitconfig
