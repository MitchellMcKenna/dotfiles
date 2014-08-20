# VIM

## What VIM plugins are included?

* [Pathogen](https://github.com/tpope/vim-pathogen) - Plugin manager for all these plugins.
* [Fugitive](https://github.com/tpope/vim-fugitive) - Git commands in VIM
* [NERD Tree](https://github.com/scrooloose/nerdtree) - Folder explorer panel to find/open/create/etc files (F2).
* [Tag List](https://github.com/vim-scripts/taglist.vim) - See a list of functions in class and jump to them (F3).
* [NERD Commenter](https://github.com/scrooloose/nerdcommenter) - Easily comment-out/uncomment code (,ci)
* [PDV](https://github.com/tobyS/pdv) - PHP docblock generator (ctrl+d).
* [surround.vim](https://github.com/tpope/vim-surround) - Change surrounding items, eg. "Hello" to 'Hello' (cs"').
* [EasyMotion](https://github.com/Lokaltog/vim-easymotion) - Jump to a word fast, eg. if it starts with 's' (,,fs).
* [Snipmate](https://github.com/garbas/vim-snipmate) - Textmate-like snippets engine, eg. create a for loop (for&lt;tab&gt;).
* [Vim Snippets](https://github.com/honza/vim-snippets) - Snippets for Snipmate.
* [Solarized](https://github.com/altercation/vim-colors-solarized) - Colorscheme for Vim.
* [Syntastic](https://github.com/scrooloose/syntastic) - Syntax error checking.
* [phpcs.vim](https://github.com/vim-scripts/phpcs.vim) - PHP_CodeSniffer.
* [CtrlP](https://github.com/kien/ctrlp.vim) - Fuzzy file finder (ctrl+p).
* [vim-airline](https://github.com/bling/vim-airline) - vim status bar, lightweight powerline.
* [vim-gitgutter](https://github.com/airblade/vim-gitgutter) - Shows git diff symbols in the 'gutter' [sign column].
* [YouCompleteMe](https://github.com/Valloric/YouCompleteMe) - Code autocompletion as-you-type (&lt;tab&gt;).
* [phpcomplete-extended](https://github.com/m2mdas/phpcomplete-extended) - Autocomplete improvements for PHP, works with YouCompleteMe.
* [vim-php-namespace](https://github.com/arnaud-lb/vim-php-namespace) - Automatically add 'use' statements for class under cursor (,u).
* [vim-multiple-cursors](https://github.com/terryma/vim-multiple-cursors) - Sublime Text-like multiple curors (ctrl+n to go to next word).

## Setup

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

Create a symbolic link so that ~/.gitconfig points to ~/dotfiles/.gitconfig (update with your git creds)

    mv ~/.gitconfig ~/.gitconfig.bak
    ln -s ~/dotfiles/.gitconfig ~/.gitconfig

Create a symbolic link so that ~/.git-completion points to ~/dotfiles/.git-completion (update with your git creds)

    ln -s ~/dotfiles/.git-completion.sh ~/.git-completion.sh
    ln -s ~/dotfiles/.git-prompt.sh ~/.git-prompt.sh

Create a symbolic link so that ~/.bashrc points to ~/dotfiles/.bashrc

    mv ~/.bashrc ~/.bashrc.bak
    ln -s ~/dotfiles/.bashrc ~/.bashrc
    source ~/.bashrc

Done!

### Taglist Requires Exuberant Ctags:

Windows - if you get an error install in windows and add the following to vimrc:

    let Tlist_Ctags_Cmd = 'C:\ctags\ctags.exe'

Mac - install brew and then update ctags using:

    brew install ctags

    open up ~/.profile and add /usr/local/bin to your path so it looks something like this:
    export PATH=/opt/local/bin:/opt/local/sbin:/usr/local/bin:$PATH

Linux:

    sudo apt-get install exuberant-ctags

### Setup ctags for vim-php-namespace

    ctags-exuberant -R --PHP-kinds=+cf

or

    ctags -R --PHP-kinds=+cf

### Compile vimproc.vim for phpcomplete-extended

    cd ~/.vim/bundle/vimproc.vim
    make

### Setup YouCompleteMe - As-You-Type Code Completion

[Install guide](https://github.com/Valloric/YouCompleteMe). Requires Vim 7.3.584, if you using a lower Vim version and can't upgrade it, use [neocomplecache](https://github.com/Shougo/neocomplcache.vim) instead.

### Setup JS/CSS Linting

Install NodeJS if you don't have it already then run:

    npm install -g csslint
    npm install -g jshint

### Setting Up Airline (Powerline)

In order to get the fancy arrows and symbols in the statusbar powered by vim-airline, you need to patch the font, follow the instructions on [vim-airline - Integrating with powerline fonts](https://github.com/bling/vim-airline#integrating-with-powerline-fonts).

Don't forget to update your terminal settings to use the new font as well after you've patched it.

## You can add vim plugins as git submodules for easy updates

Example:

    git submodule add https://github.com/tpope/vim-pathogen.git ~/.vim/bundle/vim-pathogen

## Remove a vim plugin

Example:

    git deinit .vim/bundle/plugin-name.vim
    git rm .vim/bundle/plugin-name.vim

## Update All Git Submodules

    git submodule foreach git pull

## Entering Insert Mode Causes Delay

This can be caused by vim-airline in older versions on Vim 7.3. Either update to a newer version, disable airline, or use Powerline instead.

## Typing 'vi' Not Opening Vim

Add the following to your ~/.profile

    alias vi="vim"

## Tell Git to ignore dirty submodules

Git will say there is changes to submodules when tags are built out. Just add "ignore = dirty" to any submodules in .gitmodules for each submodule it complains about.

Not working? You probably need to update your git to the latest version

## phpcs.vim Ignoring Settings to set PHP_CodeSniffer to use PSR2

Just force PSR2 to phpcs' default standard:

    sudo phpcs --config-set default_standard PSR2
