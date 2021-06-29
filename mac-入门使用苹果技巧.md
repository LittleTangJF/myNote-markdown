# Mac

## 环境

1. ```
   uname -m //查看当前架构
   arch -x86_64 zsh  // x64
   arch -arm64e zsh  // arm
   ```

## Mac-终端代理

- vi ～/.zshrc

  - ```
    # proxy list
    alias proxy='export all_proxy=socks5://127.0.0.1:1080'
    alias unproxy='unset all_proxy'
    ```

- Source  ~/.zshrc

- curl cip.cc     查看IP

## mac- SSH

1. 1、cd ~/.ssh 
2. cat id_rsa.pub

## Mac-环境安装

- 配置GitHub翻墙
  - git config --global http.https://github.com.proxy socks5://127.0.0.1:1080
  - git config --global https.https://github.com.proxy socks5://127.0.0.1:1080

- 配置git密钥

  - ssh-keygen -t rsa -C 18681268108@163.com
  - open ~/.ssh

- 安装homebrew (M1)

  - sudo mkdir -p /opt/homebrew

  - sudo chown -R $(whoami) /opt/homebrew

  - cd /opt

  - curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew

  - vi ~/.zshrc

    - ```
      path=('/opt/homebrew/bin' $path)
      export PATH
      ```

  - source ~/.zshrc

  - brew install -s git

  - 问题443

    - sudo vi /etc/hosts
    - 199.232.28.133 raw.githubusercontent.com

## Mac-终端

- 用户路径	～

- 历史路径    —

- 分区路径    /Vo

- 各种方法   

  - open   rm   mv    mkdir    c p
  - mv     dist/*  .   移动dist文件下所有文件到当前目录
#### 详细的终端命令

  - r 只读 ，  r+  读写
  - w 只写，w+ 读写   若文件不存在就新建
- a 以方式打开文件      例如 open -a  webstorm ./文件夹
####  Vim设置alias（暂时不用）

  - 第一步打开base config        vim ~/.zshrc
  - Add  line            alias   ws='open -a  webstorm'
  - Source     source   ~/.zshrc

## Mac-Mac使用技巧

- 强制退出  command + Q  或者  alt + command + esc 
- 生词。 shift + 空格键
- 自定义工具     
- 剪贴板。    command +  shift  +  v
- 上一页      shift + control   +   tab
- 下一页   control   +   tab    
- 查看隐藏文件   command +  shift.  +   .

## Mac-webstorm

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

## Mac - vi

- dd       删除一行
- U。 撤销上一步
- `i` → *Insert* 模式，按 `ESC` 回到 *Normal* 模式.
- `a` → 在光标后插入
- `o` → 在当前行后插入一个新行
- `:wq` → 存盘 + 退出 (`:w` 存盘, `:q` 退出)  （陈皓注：:w 后可以跟文件名）
- `x` → 删当前光标所在的一个字符
- `p` → 粘贴剪贴板
- `yy` → 拷贝当前行当行于 `ddP`
- `:q!` → 退出不保存 `:qa!` 强行退出所有的正在编辑的文件，就算别的文件有更改。

## Mac-破解类

[地址](http://www.sdifen.com/8136/)

## Mac-录屏

#### o b s方式

- ​	使用第三方录屏软件obs 

- ​	下载地址：https://obsproject.com/ 安装后需要设置参数

#### 	问题： 

- ​	只能录制麦克风 想同时录制电脑声音的话要使用第三方软件soundflower
  - soundflower：https://github.com/mattingalls/Soundflower/releases/tag/2.0b2

