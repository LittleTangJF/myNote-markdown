#### 一、pull失败

> - 当其他人修改了该文件提交到版本库中，而我本地也修改了该文件，致使拉去代码的时候发生冲突
>
> 1. `git stash`    将工作区恢复到上次提交的内容，同时备份本地所做的修
> 2. `git pull `     拉取
> 3. `git stash pop`  弹出自己最近保存的内容



#### 二、 撤销对文件的修改

> - 修改了一个复杂的index.vue文件，修改之后觉得自己写得乱糟糟的，没有一丝头绪，但这个修改文件**未提交**，我想恢复到它最开始的样子。
>
> 1. git checkout -- 文件完整路径（好像不加--这两个横线也能使）



#### 三、 代码被覆盖问题

> 1. git  log 或者git  log  --stat                        找到最近一次提交
> 2. git   reset  -- hard    commit编码            回到commit编码的那一次提交

#### 四、pull冲突，回到冲突前的状态

> 1. git   merge  --abort         回到冲突前的状态

#### 五、 撤销commit 

> 1. git  reset --soft  HEAD^           
>
> - HEAD^的意思是上一个版本，也可以写成HEAD~1
>
>   如果你进行了2次commit，想都撤回，可以使用HEAD~2
>
>   - --mixed      不删除工作空间改动代码，撤销commit，并且撤销git add . 操作    =>>git  reset  HEAD^
>   - --soft     不删除工作空间改动代码，撤销commit，不撤销git add . 
>   - --hard     删除工作空间改动代码，撤销commit，撤销git add . 

#### 六、Fork操作

1. 添加远程的分支到本地

   ```
   git remote add update https://github.com/Jacky-Summer/personal-blog.git
   ```

2. 运行命令

   ```
   git remote -v
   ```

3. 把远程分支代码拉到本地

   ```
   git fetch update
   ```

4. 合并对方远程分支的代码

   ```
   git merge update/master
   ```

5. 如果要Pull Request

   ```
   点击Pull Request -> 点击New Pull Request -> 输入Title和功能说明 -> 点击Send pull request
   ```



