#初始的vim 文件和目录结构
    ~/.vim/
    ~/.vim/vimrc
    ~/.vim/.gitignore

#使用 github
在github上创建一个repository，名为dotvim，然后在本机执行以下命令:

    git init
    git remote add git@github.com:{youraccountname}/dotvim.git
    git push

#使用 Pathogen 管理插件
插件地址： https://github.com/tpope/vim-pathogen
安装方法： 

    mkdir -p ~/.vim/autoload/ ~/vim/bundle; \
    curl -Sso ~/.vim/autoload/pathogen.vim \
        https://raw.github.com/tpope/vim-pathogen/master/autoload/pathogen.vim

如果是windows则创建目录$HOME\vimfiles\autoload和$HOME\vimfiles\bundle，然后下载pathogen.vim到autoload下。
修改 ~/vim/vimrc，添加以下内容：

    call pathogen#infect()
    syntax on
    filetype plugin indent on

#使用 vundle 安装插件
vundle可以自动帮你到github上下载plugin到bundle目录下。
插件地址： https://github.com/gmarik/vundle
安装方法： 

    cd ~/.vim
    git submodule add https://github.com/gmarik/vundle.git bundle/vundle

修改 ~/.vim/vimrc，添加以下内容：

    set nocompatible
    filetype off
    if has("unix")
        set rtp+=~/.vim/bundle/vundle/
        call vundle#rc()
    else 
        set rtp+=~/vimfiles/bundle/vundle/
        call vundle#rc('$HOME/vimfiles/bundle/')
    endif
    Bundle 'gmarik/vund'
    Bundle 'plasticbo/vim-markdown' " optional
    Bundle 'AutoComplPop' " optional
    filetype on

如果想安装插件，比如vim-markdown，插件地址：https://github.com/plasticboy/vim-markdown ，只需要在vimrc中添加以下一行：

    Bundle 'plasticboy/vim-markdown'
plasticboy是用户名，如果插件是属于vim-scripts的则可以省略用户名。
然后执行

    vim +BundleInstall

当提示Done!时，插件就都安装到~/.vim/bundle中了。
