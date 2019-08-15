# VimAndShell
Vim + shellTools

# 1.vim
原则 双手不离开键盘位置 
#### 导航模式 ：调整光标位置的时候
#### 插入模式 ：输入内容的时候
#### 命令模式 ：调用linux命令的时候用
#### 粘贴模式 ：粘贴代码的时候格式不变形

### 指令
0.上k下j左h右l
1.Ctrl+f 向前翻一页
2.Ctrl+b 向后翻一页
3.选择多行 shift+v & v
4./word  ?/word    n搜索下一个关键字 shift+n搜索上一个关键字 
5.%s/word/new_word/   全局替换
6.选中要替换的行 shift+; 出现<,> 之后输入  s/work/new_word
7.%s/work/new_word/g   globle
8.ctrl+n 代码自动补全
9.shift+4 行尾
10.0   行首
11.shift+g  最后一行
12.gg       第一行
13.g;       上一次编辑的位置        g,    下一次编辑的位置
14.y 复制  p  粘贴      yy 一行   nyy 多行    
15.dd 删除 p  粘贴
16.Gsearch -F 'word' . -R --include=*rb
17.Greplace a  wa 
18.colorscheme dasert
19.vs垂直分屏 sp水平分屏  ctrl+ww 切换光标所在模块  ctrl+w+hjkl 跳动到不同的方向上
20.命令模式选中多行 shift+; s/^/\/\/   
21.rails插件
22.set number  set nonumber   显示隐藏行数
23.set wrap    set nowrap     折叠展开代码 横向过长
24.gg v shift+g =   代码格式化
25. :set paste    :set nopaste   粘贴代码
26. 选中代码 shift+>   shift+<     移动代码块
27. shift+j    多行代码合并成1行
28. yaw 复制当前单词  viep 替换当前单词

### vim 菜鸟和老鸟的区别
1.使用 / 做导航
2.不要使用树状菜单，多使用ctrl+f ,ctrl+e
3.多用w,b 少用一直按住 h,l
4.命令记载手指里面

### vim 配置
home/user/.vimrc
https://github.com/amix/vimrc

# 2.cat more less
cat是一次性显示整个文件的内容，还可以将多个文件连接起来显示，它常与重定向符号配合使用，适用于文件内容少的情况；
more和less一般用于显示文件内容超过一屏的内容，并且提供翻页的功能。
more比cat强大，提供分页显示的功能。
less比more更强大，提供翻页，跳转，查找等命令。而且more和less都支持：用空格显示下一页，按键b显示上一页。

### cat
1.cat file1 file2 > file
2.cat > filename 只能创建新文件,不能编辑已有文件.
3.cat -b filename 显示行号,只不过对于空白行不编号
4.cat -s 或 当遇到有连续两行以上的空白行，就代换为一行的空白行。

### more
1.Enter    向下n行，需要定义。默认为1行  
2.Ctrl+F   向下滚动一屏  
3.空格键   向下滚动一屏  
4.Ctrl+B   返回上一屏  
5.=        输出当前行的行号  
：f      输出文件名和当前行的行号  
v        调用vi编辑器  
!命令    调用Shell，并执行命令   
q        退出more 

### less
less 与 more 类似，但使用 less 可以随意浏览文件，而 more 仅能向前移动，却不能向后移动，而且 less 在查看之前不会加载整个文件。  
less -b <缓冲区大小> 设置缓冲区的大小  
less -e  当文件显示结束后，自动离开  
less -f  强迫打开特殊文件，例如外围设备代号、目录和二进制文件  
less -g  只标志最后搜索的关键词  
less -i  忽略搜索时的大小写  
less -m  显示类似more命令的百分比  
less -N  显示每行的行号</strong>  
less -o <文件名> 将less 输出的内容在指定文件中保存起来  
less -Q  不使用警告音  
less -s  显示连续空行为一行  
less -S  行过长时间将超出部分舍弃  
less -x <数字> 将“tab”键显示为规定的数字空格  
: /字符串：向下搜索“字符串”的功能  
?字符串：向上搜索“字符串”的功能</strong>  
n：重复前一个搜索（与 / 或 ? 有关）  
N：反向重复前一个搜索（与 / 或 ? 有关）  
<strong>b  向后翻一页  
d  向后翻半页</strong>  
h  显示帮助界面  
Q  退出less 命令  
u  向前滚动半页  
y  向前滚动一行  
<strong>空格键 滚动一页  
回车键 滚动一行</strong>


# 3.linux 三剑客
### grep 擅长查找功能
- 1.grep [-acinv] [--color=auto] '搜寻字符串' filename
- 2.grep root /etc/passwd  ;  cat /etc/passwd | grep root 将/etc/passwd，有出现 root 的行取出来
- 3.grep -n root /etc/passwd  将/etc/passwd，有出现 root 的行取出来,同时显示这些行在/etc/passwd的行号
- 4.grep -v root /etc/passwd  将/etc/passwd，将没有出现 root 的行取出来
- 5.grep -v root /etc/passwd | grep -v nologin  将没有出现 root 和nologin的行取出来
- 6.sudo dmesg | grep -n --color=auto 'ARPT' 列出核心信息，再以 grep 找出内含 ARPT 那行,要将捉到的关键字显色，且加上行号来表示
- 7.sudo dmesg | grep -n -A3 -B2 --color=auto 'ARPT' 列出核心信息，再以 grep 找出内含 eth 那行,在关键字所在行的前两行与后三行也一起捉出来显示
- 8.grep ‘energywise’ *          在当前目录搜索带'energywise'行的文件
- 9.grep -r ‘energywise’ *       在当前目录及其子目录下搜索'energywise'行的文件
- 10.grep -l -r ‘energywise’ *    在当前目录及其子目录下搜索'energywise'行的文件，但是不显示匹配的行，只显示匹配的文件


### sed 全称是：Stream EDitor sed 擅长取行和替换（mac 上sed有问题 需要 brew install gnu-sed,用gsed ）
sed 是一种在线编辑器，它一次处理一行内容。处理时，把当前处理的行存储在临时缓冲区中，称为“模式空间”（pattern space），接着用sed命令处理缓冲区中的内容，处理完成后，把缓冲区的内容送往屏幕。接着处理下一行，这样不断重复，直到文件末尾。文件内容并没有 改变，除非你使用重定向存储输出。Sed主要用来自动编辑一个或多个文件；简化对文件的反复操作；编写转换程序等。

- 1.nl /etc/passwd | sed -e '2,5d'  将 /etc/passwd 的内容列出并且列印行号，同时，请将第 2~5 行删除！
- 2.nl /etc/passwd | sed -e '3,$d'  删除第3行到最后一行
- 3.nl /etc/passwd | sed '2a drink tea'         第2行后添加
- .nl /etc/passwd | sed '2a Drink tea or ......\    第2行后添加多行
> drink beer ?'
- 5.nl /etc/passwd | sed '2,5c No 2-5 number'     把第2行到第5行替换成‘No 2-5 number’
- 6.nl /etc/passwd | sed -n '5,7p'       仅列出 /etc/passwd 文件内的第 5-7 行
- 7.nl /etc/passwd | sed -n '/root/p'       搜索 /etc/passwd有root关键字的行
- 8.nl /etc/passwd | sed -n '/root/{s/bash/blueshell/;p}'     执行后面花括号中的一组命令，每个命令之间用分号分隔，这里把bash替换为blueshel
- 9.sed 's/要被取代的字串/新的字串/g'
- 10.nl /etc/passwd | sed -e '3,$d' -e 's/bash/blueshell/'    
- 11.sed -i 's/\.$/\!/g' regular_express.txt       （危险动作 请勿用在系统文件上）

### awk 因为其取了三位创始人 Alfred Aho，Peter Weinberger, 和 Brian Kernighan 的Family Name的首字符。擅长取列。

awk是一个强大的文本分析工具，相对于grep的查找，sed的编辑，awk在其对数据分析并生成报告时，显得尤为强大。
##### awk内置变量
ARGC               命令行参数个数
ARGV               命令行参数排列
ENVIRON            支持队列中系统环境变量的使用
FILENAME           awk浏览的文件名
FNR                浏览文件的记录数
FS                 设置输入域分隔符，等价于命令行 -F选项
NF                 浏览记录的域的个数
NR                 已读的记录数
OFS                输出域分隔符
ORS                输出记录分隔符
RS                 控制记录分隔符
$0变量是指整条记录。$1表示当前行的第一个域,$2表示当前行的第二个域,......以此类推。
$NF是number finally,表示最后一列的信息，跟变量NF是有区别的，变量NF统计的是每行列的总数

##### awk常用指令
- 1.awk  '/root/' /etc/passwd                   搜索/etc/passwd有root关键字的所有行
- 2.awk -F: '/root/ {print $7}' /etc/passwd     搜索/etc/passwd有root关键字的所有行，并显示对应的shell
- 3.cat /etc/passwd | awk -F ':' '{print $1}'   同上
- 4.awk  -F ':'  '{print "filename:" FILENAME ",linenumber:" NR ",columns:" NF ",linecontent:"$0}' /etc/passwd   统计/etc/passwd:文件名，每行的行号，每行的列数，对应的完整行内容
- 5.awk -F: '{printf ("filename:%10s, linenumber:%3s,column:%3s,content:%3f\n",FILENAME,NR,NF,$0)}' /etc/passwd     
awk -F ":" '{print $1}' /etc/passwd     
awk -F ":" '{print $NF}' /etc/passwd
- 6.ls -lF | awk '/^d/'                          
- 7.awk -F ":" '{print $NF}' /etc/passwd         指定特定的分隔符，查询最后一列    
awk -F ":" '{print $NF-1}' /etc/passwd
awk -F ":"  '{if(NR<31 && NR >12) print $1}' /etc/passwd
- 8.awk -F '[:]' '{print $4}' /etc/passwd        多个分隔符
- 9 .cat /etc/passwd | awk -F: 'BEGIN{print "name, shell"} {print $1,$NF} END{print "hello  world"}'    首尾各加一段命令
- 10.last | awk '{S[$3]++} END{for(a in S ) {print S[a],a}}' |uniq| sort -rh                          查看最近登录最多的IP信息
- 11.ifconfig |grep eth* | awk -F '[ ]+' '{print $1}                                                利用正则过滤多个空格
- 12.ls -l| awk '{if($5>100){count++; sum+=$5}} {print "Count:" count,"Sum: " sum}'                   显示整个过程
ls -l|awk '{if($5>100){count++; sum+=$5}} END{print "Count:" count,"Sum: " sum}'                     只显示最后的结果
- 13.awk -F ':' 'BEGIN {count=0;} {name[count] = $1;count++;}; END{for (i = 0; i < NR; i++) print i, name[i]}' /etc/passwd  统计显示/etc/passwd的账户
