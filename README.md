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
