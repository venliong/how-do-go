# I.配置Vim-go语法高亮

vim 配置，Vim-go是当前使用最为广泛的用于搭建Golang开发环境的vim插件，于是我们采用vim-go插件。vim-go利 用开源Vim插件管理器安装，gmarik/Vundle.vim是目前被推荐次数更多的Vim插件管理器。可以参照官方介绍

[https://github.com/VundleVim/Vundle.vim](https://github.com/VundleVim/Vundle.vim)

\(1\)下载Vundle.vim（vim安装插件的工具）.

```bash
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

\(2\)配置。在~/.vimrc粘贴如下代码即可\(实际上是从Vundle.vim/README.md中得知\)

```markdown
"--------------------------------------"
"  Vundle.vim 
"--------------------------------------
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" plugin on GitHub repo
" Plugin 'tpope/vim-fugitive'
" plugin from http://vim-scripts.org/vim/scripts.html
" Plugin 'L9'
" Git plugin not hosted on GitHub
" Plugin 'git://git.wincent.com/command-t.git'
" git repos on your local machine (i.e. when working on your own plugin)
" Plugin 'file:///home/gmarik/path/to/plugin'
" The sparkup vim script is in a subdirectory of this repo called vim.
" Pass the path to set the runtimepath properly.
" Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" Install L9 and avoid a Naming conflict if you've already installed a
" different version somewhere else.
" Plugin 'ascenator/L9', {'name': 'newL9'}
Plugin 'fatih/vim-go'

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line
"--------------------------------------
"  Vundle.vim (end)
"--------------------------------------
```

\(3\)安装vim-go插件。

       在vim中使用`:PluginInstall`命令进行vim-go的安装，注意：在上一步的配置中，我已经了进行vim-go插件的添加。安装完成后，就可以有go语言的字符高亮显示了。

![](/assets/go2.png)

\(4\)之后打开一个go文件

vim hello.go

![](/assets/go3.png)

# 

# II.配置go语法自动补齐



