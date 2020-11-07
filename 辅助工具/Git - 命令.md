#### 本地回退

```
git reset --hard 版本号
git reset --hard origin/master 回退本地跟远程master
```

#### 删除分支

> - git push origin --delete dev 删除远程
> - git branch -d dev 删除本地   git branch -D 可以删除没有合并到master上的分支
> - git remote show origin 获取远程信息，查看不同步
> - git remote prune origin  同步远程的分支到本地

#### 强制推送

```
git push -f -u origin maste
```

#### 初始化

```
1. git init
2. git add .
3. git commit -m 'first信息'
4. git remote add origin https.....地址 =>连接远程厂库
5. git push origin master =>推送到origin master分支
```

#### Git常用

```
1. git log =>打印日志 git 					log --stat简要日志
4. git checkout -b dev 					 新建分支
5. git merge dev => 					合并dev 分支到当前
5. git commit --amend  					对最新的一条commit进行修正
```



****

#### Git系列——Fork用法

> 1. 添加远程的分支到本地
>
>    ```
>    git remote add update https://github.com/Jacky-Summer/personal-blog.git
>    ```
>
> 2. 运行命令
>
>    ```
>    git remote -v
>    ```
>
> 3. 把远程分支代码拉到本地
>
>    ```
>    git fetch update
>    ```
>
> 4. 合并对方远程分支的代码
>
>    ```
>    git merge update/master
>    ```
>
> 5. 如果要Pull Request
>
>    ```
>    点击Pull Request -> 点击New Pull Request -> 输入Title和功能说明 -> 点击Send pull request
>    ```
>
> 
>
> 