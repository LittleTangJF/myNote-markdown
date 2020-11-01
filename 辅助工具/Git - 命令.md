#### 本地回退

```
git reset --hard 版本号
```

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

#### 二次提交

```
1. git add .
2. git commit -m 'second'
3. git push origin master
```

#### GitAPI

```
1. git log =>打印日志
2. git status =>查看状态，例如修改东西可以查看到
3. git branch  dev = >新建分支dev
4. git checkout dev => 去dev  (git checkout -b dev)（3、4）步骤的简写
5. git merge dev => 合并dev 分支到当前
6. git branch -d dev => 删除dev 分支
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