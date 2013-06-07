VIM Setup
========

Make sure your VIM is up-to-date (this is only test with VIM >7.3), eg. for linux:

    sudo apt-get install vim

In your root directory (cd ~), get the latest code from the repo:

    git clone git@github.com/MitchellMcKenna/dotfiles.git

Create symbolic link so that ~/.vimrc points to the ~/dotfiles/.vimrc file:

    ln -s ~/dotfiles/.vimrc ~/.vimrc

Create symbolic link so that ~/.vim/ points to the ~/dotfiles/.vim/ file:

    ln -s ~/dotfiles/.vim ~/.vim

Get all the plugins from their git repos:

    cd ~/dotfiles
    git submodule init
    git submodule update

Create a symbolic link so that ~/.bashrc points to ~/dotfiles/.bashrc

    mv ~/.bashrc ~/.bashrc.bak
    ln -s ~/dotfiles/.bashrc ~/.bashrc

Create a symbolic link so that ~/.gitconfig points to ~/dotfiles/.gitconfig (update with your git creds)

    mv ~/.gitconfig ~/.gitconfig.bak
    ln -s ~/dotfiles/.gitconfig ~/.gitconfig

Create a symbolic link so that ~/.git-completion points to ~/dotfiles/.git-completion (update with your git creds)

    ln -s ~/dotfiles/.git-completion ~/.git-completion

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
    git submodule add https://github.com/honza/vim-snippets.git .vim/bundle/vim-snippets
    git submodule add https://github.com/vim-scripts/L9.git .vim/bundle/L9
    git submodule add https://github.com/altercation/vim-colors-solarized.git .vim/bundle/vim-colors-solarized
    git submodule add https://github.com/Lokaltog/vim-powerline.git .vim/bundle/vim-powerline
    git submodule add https://github.com/scrooloose/syntastic.git .vim/bundle/syntastic
    git submodule add https://github.com/vim-scripts/phpcs.vim.git .vim/bundle/phpcs
    git submodule add https://github.com/rmanalan/jshint.vim.git .vim/bundle/jshint.vim
    git submodule add https://github.com/vim-scripts/csslint.vim.git .vim/bundle/csslint.vim
    git submodule add https://github.com/kien/ctrlp.vim .vim/bundle/ctrlp.vim

Taglist Requires Exuberant Ctags:
---------------------------------

Windows - if you get an error install in windows and add the following to vimrc:

    let Tlist_Ctags_Cmd = 'C:\ctags\ctags.exe'

Mac - install brew and then update ctags using:

    brew install ctags

    open up ~/.profile and add /usr/local/bin to your path so it looks something like this:
    export PATH=/opt/local/bin:/opt/local/sbin:/usr/local/bin:$PATH

Linux:

    sudo apt-get install exuberant-ctags

Tell Git to ignore dirty submodules
-----------------------------------

Git will say there is changes to submodules when tags are built out. Just add "ignore = dirty" to any submodules in .gitmodules for each submodule it complains about.

Not working? You probably need to update your git to the latest version

