After install vim and neovim normally...

Copy and paste:

    .vimrc
    .vim/*
    .config/nvim/*

Install tmux

    $ sudo apt install tmux
    
Install vim-plug

    curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
    
Run this command in neovim:

    :PlugInstall
