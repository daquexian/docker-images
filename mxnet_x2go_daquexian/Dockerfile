FROM mxnet_x2go
MAINTAINER daquexian <daquexian566@gmail.com>

RUN wget https://github.com/neovim/neovim/releases/download/v0.3.1/nvim.appimage -O /root/nvim 
RUN chmod +x /root/nvim && mv /root/nvim /usr/local/bin
RUN echo "alias vim=nvim" >> /root/.profile
RUN apt install -y git automake pkg-config libevent-dev libncurses5-dev
RUN wget https://github.com/tmux/tmux/releases/download/2.8/tmux-2.8.tar.gz && tar xf tmux-2.8.tar.gz && cd tmux-2.8 && ./configure && make -j$(nproc) && make install
RUN apt install -y zsh
RUN sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
RUN git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
RUN echo "plugins=(" >> /root/.zshrc  &&  echo "git" >> /root/.zshrc  &&  echo "history" >> /root/.zshrc  &&  echo "pip" >> /root/.zshrc  &&  echo "python" >> /root/.zshrc  &&  echo "vi-mode" >> /root/.zshrc  &&  echo ")" >> /root/.zshrc  &&  echo "bindkey -v" >> /root/.zshrc  &&  echo "bindkey '^f' autosuggest-accept" >> /root/.zshrc  &&  echo "bindkey '^j' autosuggest-execute" >> /root/.zshrc  &&  echo "bindkey "${terminfo[khome]}" beginning-of-line" >> /root/.zshrc  &&  echo "bindkey "${terminfo[kend]}" end-of-line" >> /root/.zshrc  &&  echo "bindkey '^[[Z' reverse-menu-complete" >> /root/.zshrc  &&  echo "xcape -e 'Control_L=Escape'" >> /root/.zshrc  &&  echo "xmodmap -e "keycode 66 = Shift_L NoSymbol Shift_L"" >> /root/.zshrc  &&  echo "export EDITOR=vim" >> /root/.zshrc  &&  echo "export VISUAL=vim" >> /root/.zshrc  &&  echo "export SUDO_EDITOR=vim" >> /root/.zshrc  &&  echo "[[ -e ~/.profile ]] && emulate sh -c 'source ~/.profile'" >> /root/.zshrc  &&  chsh -s $(which zsh)

RUN git clone https://github.com/daquexian/dot_files /root/dot_files
RUN ln -s /root/dot_files/.vimrc /root/.vimrc && cp /root/dot_files/.vimrc.local /root/ && ln -s /root/dot_files/.gitconfig /root/.gitconfig
