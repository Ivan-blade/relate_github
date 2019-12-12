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

+ git命令
    ```
        git config --global user.name "yourname"
        git config --global user.email "your_email@example.com"

        git config –list
    ```

+ gitbash中git-clone使用准备
    ```
        创建ssh密钥
        ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

        查看ssh是否执行
        $　eval "$(ssh-agent -s)"

        私钥添加到代理
        ssh-add ~/.ssh/id_rsa

        查看文件夹内容
        ls ~/.ssh
        如果有三个文件基本没问题了，如果只有两个。。。下面就会用到yes了
        
        找到id_rsa.pub文件将当中的密钥复制粘贴到github中

        测试连接
        ssh -T git@github.com
        执行之后万一报错可能会出现一个选择选yes，不要回车基本稳
    ```
+ 分支
    ```
        github上分支的合并
        几个人合作用开发项目时，代码保存到GitHub上，我们不可能在原有代码上直接修改调试，这时就要创建一个新的分支，在分支上改自己的代码，修改完成后，把分支上修改的代码合并到主分支master上就好了。这个过程需要经过以下几个步骤：

        1、创建一个分支test

        　　git branch test

        2、查看分支创建是否成功，下面的命令可以得到现在仓库中的分支列表

        　　git branch
            git branch -v


        3、master分支是仓库默认的主分支，把工作从master分支下切换到test分支下

        　　git checkout test

        4、内容修改完成后，通过下面命令把内容提交给test分支下

        　　git add -a

        　　git push -u origin test

        5、再把工作从test分支下切换到master下

        　　git checkout master

        6、因为是合作开发项目，这时远程仓库中的内容有可能已经发生了变化，所以我们需要将远程仓库中的内容和本地分支中的内容进行合并

        　　git pull origin master

        7、接下来要做的是将test分支合并到master上

        　　git merge test

        8、查看分支中内容提交的状态

        　　git status

        9、最后一步，我们把修改的内容提交到主分支上

        　　git push origin master

        如果你感觉合并后的内容有问题，你可以通过撤销合并恢复到以前状态。

        　　git reset --hard HEAD

        代码已经提交，撤销的方法是

        　　git reset --hard ORIG_HEAD

        删除分支
        git branch -d 分支名
        处理冲突的方式：手动修改文件内容删除特殊字符以及不需要的语句
    ```
+ 版本记录
    + 显示详细日志信息
        ```
            git log
        ```
    + 每条日志显示一行信息
        ```
            git log --pretty=oneline
        ```
    + 显示回退到该版本的步数
        ```
            git reflog
        ```

    + 回滚版本
        + 哈希值回滚
            ```
                git reset --hard <哈希值/索引>
                通过reflog查询哈希值
            ```
        + 异或回滚(只能后退)
            ```
                git reset --hard HEAD^^ (^个数为回滚步数)
            ```
        + ~回滚(只能后退)
            ```
                git reset --hard HEAD~n (n数值为回滚步数)
            ```
+ 差异对比
    + 将工作区与暂存区文件进行对比
        ```
            git diff 文件名
        ```
    + 将工作区与历史文件进行对比
        ```
            git diff 历史版本哈希值 文件名
        ```  