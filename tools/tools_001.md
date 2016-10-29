## Vim常用配置
~~~
set nu
set expandtab
set tabstop=4
set softtabstop=4
set autoindent
set hlsearch
set fileencodings=utf-8,ucs-bom,gb18030,gbk,gb2312,cp936
set termencoding=utf-8
set encoding=utf-8
set mouse=a
syntax on
set autochdir
set tags=tags;
set backspace=indent,eol,start
nnoremap <silent> <F2> :NERDTreeToggle<CR>
nnoremap <silent> <F3> :copen<CR>
nnoremap <silent> <F4> :cclose<CR>
inoremap <silent> <C-h> <Left>
inoremap <silent> <C-j> <Down>
inoremap <silent> <C-k> <Up>
inoremap <silent> <C-l> <Right>
inoremap <silent> <C-w> <C-Right>
inoremap <silent> <C-b> <C-Left>
inoremap <silent> <C-a> <C-o>0
inoremap <silent> <C-e> <C-o>$
"自动加载cscope.out
if has("cscope")
	set csprg=/usr/local/bin/cscope
	set csto=0
	set cst
	set nocsverb
	" add any database in current directory
	if filereadable("cscope.out")
	    cs add cscope.out
	" else add database pointed to by environment
	elseif $CSCOPE_DB != ""
	    cs add $CSCOPE_DB
	endif
	set csverb
endif
"查找C代码符号
nmap <C-\>s :cs find s <C-R>=expand("<cword>")<CR><CR> 
"查找本定义
nmap <C-\>g :cs find g <C-R>=expand("<cword>")<CR><CR> 
"查找调用本函数的函数
nmap <C-\>c :cs find c <C-R>=expand("<cword>")<CR><CR> 
"查找调用本函数的函数
nmap <C-\>t :cs find c <C-R>=expand("<cword>")<CR><CR> 
"查找本字符串
nmap <C-\> :cs find t <C-R>=expand("<cword>")<CR><CR> :copen<CR> 
"查找本egrep模式
nmap <C-\>e :cs find e <C-R>=expand("<cword>")<CR><CR> 
"查找本文件
nmap <C-\>f :cs find f <C-R>=expand("<cfile>")<CR><CR> 
"查找包含本文件的文件
nmap <C-\>i :cs find i <C-R>=expand("<cfile>")<CR><CR> 
"找本函数调用的函数
nmap <C-\>d :cs find d <C-R>=expand("<cword>")<CR><CR> 
"cscope结果加入到quickfix list
set cscopequickfix=s-,c-,d-,i-,t-,e-
~~~