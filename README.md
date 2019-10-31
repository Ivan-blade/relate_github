# relate_github
+ 在github上创建仓库
    ```
        如果在创建仓库的时候增加了readme文件，后面在gitbash中同步时需要输入git pull
    ``` 

+ 使用gitbash在本地创建存放仓库的文件夹
    ```
        cd F
        mkdir relate_github
    ```

+ 开始初始化操作
    ```
        cd relate_github
        git init
        git remote add origin https://xxxxx
        //这边是远程仓库的路径推荐https的ssh可能报错
        git add .  
        //将所有变动增加到暂存区
        git commit -m "这边是更新提示信息"
        //此次远程仓库中变动的文件会有提示备注
        git status
        //查看此次同步的更新变动
        git push -u origin master
        //将暂存区文件同步至远程仓库，之后同步只需要git push就可以了
    ```

+ 同步仓库到本地
    ```
        切换到已经关联仓库的本地文件夹
        git pull
    ```

+ 合并仓库并提交
    ```
        git pull origin master //GitHub的仓库存在文件需要合并
        git push -u origin master

        使用git pull origin master 命令操作时，会遇到这样的错误：fatal: refusing to merge unrelated histories。
        这是因为远程仓库已经存在代码记录了(例如markdown文件)，并且那部分代码没有和本地仓库进行关联，我们可以使用如下操作允许pull未关联的远程仓库旧代码：git pull origin master --allow-unrelated-histories
    ```