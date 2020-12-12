# Mac常用命令

### 终端

- 用户路径	～

- 历史路径    —

- 分区路径    /Vo

- 各种方法   

  - open   rm   mv    mkdir    c p

  #### 详细的终端命令

  - r 只读 ，  r+  读写
  - w 只写，w+ 读写   若文件不存在就新建
  - a 以方式打开文件      例如 open -a  webstorm ./文件夹

  ####  Vim设置alias（暂时不用）

  - 第一步打开base config        vim ~/.bashrc
  - Add  line            alias   ws='open -a  webstorm'
  - Source     source   ~/.bashrc

### Mac使用技巧

- 强制退出  command + Q  或者  alt + command + esc 
- 生词。 shift + 空格键
- 自定义工具     
- 剪贴板。    command +  shift  +  v

### webstorm

- 光标回到上次。                 command + alt  +  <—   —> 
- 选择所有相同的变量         command +   control   +  g   
- 导航到上次编辑的位置     command +   shift   +   delete
- 跳转制定行数。                command  + L
- 删除当前行                        command +  delete
- 注释                                   command +  /
- 下面空一行                       command  +    enter
- 下面收缩一行                   control   +   shift   +   j
- 把多行变成单行               control      +   alt     +     j
- 收缩代码块                      command  +   -   或者     command   +   shift   +   - 
- 关闭当前文件                  command    +     w