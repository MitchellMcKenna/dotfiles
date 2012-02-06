VIM Setup
========

In your root directory (cd ~), get the latest code from the repo:

    git clone http://github.com/MitchellMcKenna/dotfiles.git

Create symbolic links so that ~/.vimrc points to the ~/.vim/vimrc file:

    ln -s ~/dotfiles/.vimrc ~/.vimrc

Create symbolic links so that ~/.vim/ points to the ~/dotfiles/.vim/ file:

    ln -s ~/dotfiles/.vim ~/.vim

Get all the plugins from their git repos:

    cd ~/dotfiles
    git submodule init
    git submodule update

Tell Git to ignore tags so you don't get dirty submodules when tags are built out:

    git config --global core.excludesfile '~/.cvsignore'
    echo tags >> ~/.cvsignore

Done!

You can add vim plugins as git submodules for easy updates:
-----------------------------------------------------------
    git submodule add https://github.com.com/tpope/vim-pathogen.git .vim/bundle/vim-pathogen
    git submodule add https://github.com/tpope/vim-fugitive.git bundle/fugitive
    git submodule add https://github.com/scrooloose/nerdtree.git .vim/bundle/nerdtree
    git submodule add https://github.com/tobyS/vip.git .vim/bundle/vip
    git submodule add https://github.com/tomtom/tcomment_vim.git .vim/bundle/tcomment_vim
    git submodule add https://github.com/vim-scripts/taglist.vim.git .vim/bundle/taglist
    git submodule add https://github.com/tpope/vim-surround.git .vim/bundle/vim-surround
    git submodule add https://github.com/ervandew/supertab.git .vim/bundle/supertab
    git submodule add https://github.com/Lokaltog/vim-easymotion.git .vim/bundle/vim-easymotion
    git submodule add https://github.com/garbas/vim-snipmate.git .vim/bundle/snipmate
    git submodule add https://github.com/tomtom/tlib_vim.git .vim/bundle/tlib_vim
    git submodule add https://github.com/MarcWeber/vim-addon-mw-utils.git .vim/bundle/vim-addon-mw-utils
    git submodule add https://github.com/honza/snipmate-snippets.git .vim/bundle/snipmate-snippets
    git submodule add https://github.com/vim-scripts/L9.git .vim/bundle/L9
    git submodule add https://github.com/vim-scripts/FuzzyFinder.git .vim/bundle/vim-fuzzyfinder

Taglist Requires Exuberant Ctags:
---------------------------------

Windows - if you get an error install in windows and add the following to vimrc:
  
    let Tlist_Ctags_Cmd = 'C:\ctags\ctags.exe'

Mac - install macports and then update ctags using: 

    sudo port install ctags

Linux:

    sudo apt-get install exuberant-ctags
