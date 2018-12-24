FROM mxnet_x2go
MAINTAINER daquexian <daquexian566@gmail.com>

RUN wget https://github.com/neovim/neovim/releases/download/v0.3.1/nvim.appimage -O /root/nvim && chmox +x nvim && mv nvim /usr/local/bin
RUN echo "alias vim=nvim" >> /root/.profile
RUN apt install -y git automake pkg-config libevent-dev libncurse5-dev
RUN wget https://github.com/tmux/tmux/releases/download/2.8/tmux-2.8.tar.gz && tar xf tmux-2.8.tar.gz && cd tmux-2.8 && ./configure && make -j$(nproc) && make install
RUN apt install zsh
RUN sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
RUN git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
RUN echo "plugins=(" >> /root/.zshrc
RUN echo "git" >> /root/.zshrc
RUN echo "history" >> /root/.zshrc
RUN echo "pip" >> /root/.zshrc
RUN echo "python" >> /root/.zshrc
RUN echo "vi-mode" >> /root/.zshrc
RUN echo ")" >> /root/.zshrc
RUN echo "bindkey -v" >> /root/.zshrc
RUN echo "bindkey '^f' autosuggest-accept" >> /root/.zshrc
RUN echo "bindkey '^j' autosuggest-execute" >> /root/.zshrc
RUN echo "bindkey "${terminfo[khome]}" beginning-of-line" >> /root/.zshrc
RUN echo "bindkey "${terminfo[kend]}" end-of-line" >> /root/.zshrc
RUN echo "bindkey '^[[Z' reverse-menu-complete" >> /root/.zshrc
RUN echo "xcape -e 'Control_L=Escape'" >> /root/.zshrc
RUN echo "xmodmap -e "keycode 66 = Shift_L NoSymbol Shift_L"" >> /root/.zshrc
RUN echo "export EDITOR=vim" >> /root/.zshrc
RUN echo "export VISUAL=vim" >> /root/.zshrc
RUN echo "export SUDO_EDITOR=vim" >> /root/.zshrc
RUN echo "[[ -e ~/.profile ]] && emulate sh -c 'source ~/.profile'" >> /root/.zshrc
RUN chsh -s $(which zsh)

RUN git clone https://github.com/daquexian/dot_files
RUN ln -s dot_files/.vimrc && cp dot_files/.vimrc.local . && ln -s dot_files/.gitconfig
