
---
# Git Set up
	~/.gitconfig


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

### Setup your editor

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
	git stash 
	git stash list
	git stash apply <stash@{2}>
	git stash drop
	git stash apply --index 
	git config --global alias.stash-unapply '!git stash show -p | git apply -R'
	git stash-unapply

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
# Vim
	:Version
	:<C-n> <C-p> auto complete
	:enew new file
	:set guifont=
## config
	:Syntax On
	Line Number: set number, set nonumber
	ruler:set ruler
## open buffer
	:ls 		//	for list of open buffers

	:ls  give a list of current open file
	:bp  	previous buffer
	:bn  	next buffer
	:bn  	(n a number) move to nth buffer
	:b 		with tab-key providing auto-completion (awesome !!)
	:bd 	(delete buffer)
## Explore:
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
## index
	J → 把所有的行连接起来（变成一行）
	< 或 > → 左右缩进
	= → 自动给缩进 （陈皓注：这个功能相当强大，我太喜欢了）
## Split
	:split → 创建分屏 (:vsplit创建垂直分屏)
	<C-w><dir> : dir就是方向，可以是 hjkl 或是 ←↓↑→ 中的一个，其用来切换分屏。
	<C-w>_ (或 <C-w>|) : 最大化尺寸 (<C-w>| 垂直分屏)
	<C-w>+ (或 <C-w>-) : 增加尺寸

## Others
cs f s 

	gd will take you to the local declaration.
	gD will take you to the global declaration.
	g* search for the word under the cursor (like *, but g* on 'rain' will find words like 'rainbow').
	g# same as g* but in backward direction.
	gg goes to the first line in the buffer (or provide a count before the command for a specific line).
	G goes to the last line (or provide a count before the command for a specific line



