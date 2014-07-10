# Git Set up
	~/.gitconfig
	
	[user]
		name = Yongqinchuan Du
		email = Yongqinchuan.du@ericsson.com
	[github]
		user = duqcyxwd
		password = 
	[diff]
		tool = winmerge
	[difftool "winmerge"]
		cmd = C:/Program\\ Files/WinMerge/WinMergeU.exe \"$LOCAL\" \"$REMOTE\"
	[difftool]
		prompt = false
	[color]
		ui = true
		diff = always
		status = always
		branch = always
		interactive = always
		ui = always
		pager = true
	[core]
		autocrlf = true

### Check SSH Key
	cat $HOME/.ssh/id_rsa.pub
	/proj/lterbsSwdi/bbtools/bin/setupSshWithNoPassword.sh
### Who am I
	java -jar /proj/lterbsSwdi/ltegit_admin/jenkins-cli.jar -s https://esekilx5088.rnd.ki.sw.ericsson.se:8080/ who-am-i

### Set up Git Configuration

#### Procedure:

	1. Set your git user name
		git config --global user.name $user
	2. Set your git email
		git config --global user.email yongqinchuan.du@ericsson.com
	3. Add a little color
		git config --global color.status auto
		git config --global color.diff auto
	4. For color, you may need to add this to your .cshrc.user file
		setenv LESS '-M -I -R'
	5. Set your merge tool
		git config --global merge.tool kdiff3

#### Module
1. Add the git module, and some other modules in your $HOME/.cshrc.user (or your .modules file)
	module add git
	module add kdiff3
2. Start a fresh shell, or issue the following command in your current shell
	source ~/.cshrc.user
3. Check that the above modules are added
	module list

## Setup your editor

	Procedure: xemacs

	To setup xemacs as your editor
	git config --global core.editor "xemacs"


	Procedure: gvim

	To setup gvim as your editor
	git config --global core.editor "gvim -f"

	See Also
	• pagers
	Your pager is the command that git will use to send its command output.
	Use one of the following procedures:


	Procedure: cat

	If you want all info to be output in the shell set:
	git config --global core.pager "cat"
	Next: If you use this you need to use limiting flags on some command to avoid getting too much info. Ex: git log -n 5


	Procedure: less

	To be able to see coloured SHA1 tags instead of ESC codes (for example in git log) set
	git config --global core.pager "less -r"
	The less utility is a vast improvement over the default pager more. It can be configured using the LESS environment variable. Here is a example configuration. If you configure the git core.pager to use less, you will probably prefer to use --QUIT-AT-EOF instead of --quit-at-eof.
	For cshell:
	setenv PAGER less
	setenv LESS "--ignore-case --quit-at-eof --LONG-PROMPT --squeeze-blank-lines --HILITE-UNREAD --search-skip-screen --RAW-CONTROL-CHARS"
	For bash:
	export PAGER=less|export LESS="--ignore-case --quit-at-eof --LONG-PROMPT --squeeze-blank-lines --HILITE-UNREAD --search-skip-screen --RAW-CONTROL-CHARS"
	The last option is necessary on the 2100 Phoenix pool.
	Next: Continue.



# Git Commands
## Git Gerrit
### Git Aliases source
	source /proj/lterbsSwdi/ltegit_admin_jenkins/aliases/.gitaliases
	source /lteworkspace/eyonduu/lrat/gitenv.csh

	/proj/lterbsLablogOT/eyonduu/Sample_Script/good_node_check
### push to Gerrit
	git push origin personal/eyonduu/GitCert/Warrior
	git push origin HEAD:refs/for/personal/eyonduu/GitCert/Warrior
## Other
	list of repo: grr -l


# Git Trick
## checkout
	git log --grep=<pattern>
	git log -1
	git log -1 master
	git log --oneline

	git log | grep CXP | head
	git config --list
## Branch delete
	git branch -D <branch>

## Git gui gitk
	- gitk --all
	- git gui
## merge multiple commit
	b2
	|
	b1 
	|
	b0 49687a0a646954afdf3f4dae1f914ea793341ea2

	$ git rebase -i 49687a0a646954afdf3f4dae1f914ea793341ea2
	pick 033beb4 b1
	squash d426a8a b2
## reverse commit
1. Recommit `git commit --amend`
2. Delete recent `git reset --hard HEAD~1`  `git reset --hard HEAD~`
3. keep changes but cancel commit `git reset HEAD~1`

## Other
	gitk --unnittest/unnittest.php //Check the change of single file. 
	git branch --remotes/-r
	git branch -r | fgrep task | wc -l
	git branch -a
	gas alias|grep git
	git diff --cached ?? 

## git Stash
* git stash 
* git stash list
* git stash apply 'stash@{2}'
* git stash drop
* git stash apply --index 
* git config --global alias.stash-unapply '!git stash show -p | git apply -R'
* git stash-unapply
* git save <name>
	

## Notes
	find . | wc -l
	find ../suites -type f -name '*.erl' >> ~/Run_tests/files.txt


---
# shell Command

	- less <fileName>
	ssh eselivm2v382l -l eyonduu // server for Git.... I guess

	git log | grep CXP | head
	ll | grep cshrc

	!! // repleat last

	printenv
	wc byte/words/line count

	sed -i '/pattern/d' filename
	grep -v "pattern" filename > filename2; mv filename2 filename

	setenv MY_GIT_TOP `top`

	` is not '

	find ../suites -type f -name '*.erl' >> ~/Run_tests/files.txt
## shell vi module
	- bindkey -v
	- bindkey -e emacs model 
	- bindkey "^R" i-search-back
## Key binding	Action

	- Ctrl-r	History reverse search

	- Ctrl-a	Jump to BOL
	- Ctrl-e	Jump to EOL
	- Ctrl-l	Clear terminal

	- Ctrl-k	Delete from cursor to EOL
	- Ctrl-w	Delete word left from cursor
	- Ctrl-u	Delete from BOL to cursor
	- Ctrl-y	Paste content of the kill ring undo

	- Ctrl-p	Previous command in history
	- Ctrl-n	Next command in history

	- Ctrl-f	Move forward a char
	- Ctrl-b	Move backward a char
	- Alt-f	Move forward a word
	- Alt-b	Move backward a word

	- Ctrl-d	Delete char under cursor
	- Alt-d	Delete afterward word

	- *Alt-u	Uppercase word at cursor*
	- *Alt-l	Lowercase word at cursor*

	- Shift-PgUp	Scroll screen up
	- Shift-PgDn	Scroll screen down
## Task commands
	- jobs - an alternate way of listing your own processes  -l
	- ps - list the processes running on the system
	- kill %# / PID - send a signal to one or more processes (usually to "kill" a process)
	- bg $%#- put a process in the background
	- fg %1 - put a process in the forground
## check disk size
	df <dir>  // report file system disk space usage
		-h //human readable
	du  <dir> --max-depth=1 -h // estimate file space usage
	top
	free -l -t
## ssh transfer file sftp
	- ssh <Host>
	- sftp <Host>
	- mget * //copy it to current file Directory
	- help
## NX Client Server Host pool
Clear-Case:
	lts-lmrrasam.lmera.ericsson.se
Git:
	esekilxxen2100.rnd.ericsson.se

## [Stack Directory](http://unix.stackexchange.com/questions/77077/how-do-i-use-pushd-and-popd-commands)
	-pushd
	-popd
	-dirs

## Alias
	gas: aliased to alias|grep git // Check alias
	alias
	alias good-node-check '/proj/lterbsLablogOT/eyonduu/Sample_Script/good_node_check'
## Script
	chmod 777

## Search
1. find
	find dir/ -iname "Full name"
	find . -name 'my*' -ls
	find . -iname *git*

	find . -iname *vi* -maxdepth 1 -ls  // find file in current folder

	iname: case careless
3. whereis

	whereis命令只能用于程序名的搜索，而且只搜索二进制文件（参数-b）、man说明文件（参数-m）和源代码文件（参数-s）。如果省略参数，则返回所有信息。
	whereis命令的使用实例：
	　　$ whereis grep	
---
---
# Vim

## Basic

    :Version
    :<C-n> <C-p> auto complete
    :enew new file
    :set guifont=

## Basic moving
    %	to matched brace

## Basic search and replace
    :%s/foo/bar/g       Find each occurrence of 'foo' (in all lines), and replace it with 'bar'. 
    :s/foo/bar/g       Find each occurrence of 'foo' (in the current line only), and replace it with 'bar'. 
    :%s/foo/bar/gc       Change each 'foo' to 'bar', but ask for confirmation first. 
    :%s/\<foo\>/bar/gc       Change only whole words exactly matching 'foo' to 'bar'; ask for confirmation. 
    :%s/foo/bar/gci       Change each 'foo' (case insensitive) to 'bar'; ask for confirmation. 
    :%s/foo/bar/gcI       Change each 'foo' (case sensitive) to 'bar'; ask for confirmation. 

## Indent or unindent
    [http://stackoverflow.com/questions/235839/how-do-i-indent-multiple-lines-quickly-in-vi]
    ={

    >>   Indent line by shiftwidth spaces
    <<   De-indent line by shiftwidth spaces
    5>>  Indent 5 lines
    5==  Re-indent 5 lines

    >%   Increase indent of a braced or bracketed block (place cursor on brace first)
    =%   Reindent a braced or bracketed block (cursor on brace)
    <%   Decrease indent of a braced or bracketed block (cursor on brace)
    ]p   Paste text, aligning indentation with surroundings

    =i{  Re-indent the 'inner block', i.e. the contents of the block
    =a{  Re-indent 'a block', i.e. block and containing braces
    =2a{ Re-indent '2 blocks', i.e. this block and containing block

    >i{  Increase inner block indent
    <i{  Decrease inner block indent

    J → 把所有的行连接起来（变成一行）
	< 或 > → 左右缩进
	= → 自动给缩进 （陈皓注：这个功能相当强大，我太喜欢了）

### Go   
    gd will take you to the local declaration.
         <C-o> or '' jump back    
    gD will take you to the global declaration.
    g* search for the word under the cursor (like *, but g* on 'rain' will find words like 'rainbow').
    g# same as g* but in backward direction.
    gg goes to the first line in the buffer (or provide a count before the command for a specific line).
    G  goes to the last line (or provide a count before the command for a specific line
    gf will go to the file under the cursor 
 
### Scope search 
    cs f s 
    <c-\>g      Find defination 
    <c-\>s      Find from all scope
    <c-]>s      Find from all scope and open it in seprate window


## Plugin

* :so ~/.vimrc
* :BundleInstall / :PluginInstall

## config
    :Syntax On
    :set number / set nonumber        Line Number:
    :set ruler                        ruler
## open buffer

    :ls      give a list of current open file
    :bp      previous buffer
    :bn      next buffer
    :bn      (n a number) move to nth buffer
    :b         with tab-key providing auto-completion (awesome !!)
    :bd     (delete buffer)
    :Bclose  close with out close window

## Explore:

    :Exp explore current dir
    :e Home/eyonduu/Desktop
    :E Explore directory of current file
    :e! //reopen th file
    :Sex
    :[N]Explore[!]  [dir]... Explore directory of current file      *:Explore*
    :[N]Hexplore[!] [dir]... Horizontal Split & Explore             *:Hexplore*
    :Rexplore            ... Return to Explorer                     *:Rexplore*
    :[N]Sexplore[!] [dir]... Split&Explore current file's directory *:Sexplore*
    :Texplore       [dir]... Tab              & Explore             *:Texplore*
    :[N]Vexplore[!] [dir]... Vertical   Split & Explore             *:Vexplore*

## Folding 

* zc       折叠
* zC       对所在范围内所有嵌套的折叠点进行折叠
* zo       展开折叠
* zO       对所在范围内所有嵌套的折叠点展开
* zm       关闭所有折叠
* zM       关闭所有折叠及其嵌套的折叠
* zr       打开所有折叠
* zR       打开所有折叠及其嵌套的折叠
* za zf 
* nnoremap <space> za 

* zd       删除当前折叠
* zE       删除所有折叠
* [z       到当前打开的折叠的开始处。
* ]z       到当前打开的折叠的末尾处。
* zj       向下移动。到达下一个折叠的开始处。关闭的折叠也被计入。
* zk       向上移动到前一折叠的结束处。关闭的折叠也被计入。

* if unable to fold, check fold method

** Folder for C **
:set foldmethod=syntax

**Markdown-Navagation**
* ]]: go to next header.
* [[: go to previous header. Contrast with ]c.
* ][: go to next sibling header if any.
* []: go to previous sibling header if any.
* ]c: go to Current header.
* ]u: go to parent header (Up).


## Visual Block edit
	^ → 到行头
	<C-v> → 开始块操作
	<C-d> → 向下移动 (你也可以使用hjkl来移动光标，或是使用%，或是别的)
	I-- [ESC] → I是插入，插入“--”，按ESC键来为每一行生效。
## 宏 Ma
	宏录制： qa 操作序列 q, @a, @@
	qa 把你的操作记录在寄存器 a。
	于是 @a 会replay被录制的宏。
	@@ 是一个快捷键用来replay最新录制的宏。

	在一个只有一行且这一行只有“1”的文本中，键入如下命令：

Example:
	qaYp<C-a>q→
	qa 开始录制
	Yp 复制行.
	<C-a> 增加1.
	q 停止录制.
	@a → 在1下面写下 2
	@@ → 在2 正面写下3
	现在做 100@@ 会创建新的100行，并把数据增加到 103.
## Split
	:split → 创建分屏 (:vsplit创建垂直分屏)
	<C-w>s create screen horizontal
	<C-w>v create screen vertical
	<C-w><dir> : dir就是方向，可以是 hjkl 或是 ←↓↑→ 中的一个，其用来切换分屏。
	<C-w>_ (或 <C-w>|) : 最大化尺寸 (<C-w>| 垂直分屏)
	<C-w>+ (或 <C-w>-) : 增加尺寸


## Registers

- <C-r> */+	    Paste from Register in insert model
- "+p "*p	    Paste from Register in normal model
- <C-r> register    paster from register in command model 
- "*yy or "+yy	    copy a line to your clipboard
- "kyy		    copy line to register k
- "*		    the contents of the system clipboard
- "/ -		    last search command
- ": -		    last command.
- "xp		    你也可以使用p命令，将x寄存中的文本粘贴到光标之后：

- let @*=@a	    copy from register to register

### Register function
未命名寄存器 	   “ 	    上一次复制或删除的文本
数字寄存器 	       0-9 	    文本删除历史
短删除寄存器 	   - 	    删除少于一行的文本
命名寄存器 	       a-z,A-Z 	存放文本
只读寄存器 	       % 	    当前文件的名字
                   # 	    交替文件的名字
                   . 	    上一次插入的文本
                   : 	    上一次执行的命令
表达式寄存器 	   ＝ 	    返回表达式结果
选择和拖拽寄存器   * 	    系统剪切板
                   + 	    系统剪切板（X11）
                   ~ 	    拖拽的文本
黑洞寄存器 	       _ 	    永久删除的文本
搜索模式寄存器 	   / 	    搜索模式


### yy & add
yy -> Register "
   -> register 0
dd ->Register "
   ->Register 1
   Register 1-> register 2
## Others

   :set variable   - shows vars different from defaults
   :w !diff % -    Show different before save

### Session

    :mksession ~/mysession.vim
    :source ~/mysession.vim or open vim with the -S option:
    $ vim -S ~/mysession.vim

    
# Sublime
sublime.log_commands(True)

