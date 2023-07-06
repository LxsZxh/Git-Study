# Git-Study

// 初始化仓库
git init

// 克隆仓库
git clone 主仓(URL / SSH)

// 查看所有分支列表
git branch -a

// 将本地分支推送到远程（本地有testing，远程没有）
git push --set-upstream origin testing

// 设置上游分支 
git branch --set-upstream-to=origin/main

// 合并没有共同base的分支
git merge --allow-unrelated-histories

// 查看本地分支对应的远程分支
git branch -vv

// 创建dev分支
git branch dev

// 删除当前分支
git branch -d hotfix

//强制删除某一分支
git branch -D testing

// 删除远程分支
git push origin -d testing

// 切换dev分支
git checkout dev  

// 创建并切换dev分支
git checkout -b dev

// 创建main分支并追踪到远程main分支
git checkout --track origin/main

// 创建dev分支并切换到dev分支
git switch -c dev （推荐）

// 将默认推送行为设置为upstream
git config push.default upstream

// 配置上游分支，找不到的话就在远程新建一个
git config push.default current
  
// 显示所有远程仓库
git remote -v
  
// 添加远程版本库（让本地的仓库和远程服务器仓库建立连接）
git remote add upstream 主仓(URL / SSH)

// 重命名远程仓库
git remote rename upstream upstream2

// 删除远程仓库
git remote rm 50products50day

// 添加文件到暂存区
git add .

// 将暂存区内容添加到仓库中
git commit -m "feat:项目初始化配置"  

// 一行命令提交(add + commit)
git commit -a -m "fix: 测试一行命令提交"
    
// 修改上次的提交信息 i：进入编辑模式 esc:退出编辑模式  :wq:保存并退出
git commit --amend

// 查看仓库当前状态，显示有变更的文件
git status

// 简短显示仓库当前状态
git status -s 

// 从远程仓库获取代码
git fetch 

git fetch origin main

// 将获取到的代码合并到本地仓库
git merge 

git merge origin/master

// 线性合并到dev 分支
git checkout dev 

git rebase main

git checkout main

git merge dev

// 拉取远程仓库dev分支代码
git pull upstream dev

git pull 是 git fetch 和 git merge 的同时执行

// 提交代码至私仓dev分支
// 加u参数就是推送的同时，绑定当前本地分支对应的远程分支，绑定后，后续只要push就好。
git push -u origin dev 

// 强制提交
git push origin dev -f    

// 绑定远程分支 + 强制提交
git push -u origin dev -f   
    
// 重命名分支  
git branch -m oldName newName

// 删除分支  
git branch -d dev

// 将未commit的修改保存到暂存
git stash

// 取出保存至暂存区中的修改
git stash pop

// 查看提交记录
git log （不带版本号）

// 一行显示
git log --pretty=oneline

git reflog （带版本号）

// 回退所有内容到某一版本，后续版本全无了,需要强制提交下
git reset --hard 1253105（这是版本号）
git push origin dev -f 

// 撤销之前的某一版本，并保留后续版本的更改
git revert 1253105

// 打标签
git tag v1.0.0

// 查看标签列表
git tag --list

// 推送单个tag到远程仓库
git push origin v1.0.0

// 推送所有tag
git push origin --tags

// 删除本地tag
git tag -d v1.0.0

// 删除远程tag
git push origin -d v1.0.0 

// 查看.git 文件夹下 objects 的内容
git cat-file -p 00d2

// 切换到该tag对应的版本
git tag checkout v1.0.0
  
/** 合并分支流程 */  
git checkout test  // 1. 切换至test分支

git pull           // 2. 从远程仓库拉取最新代码到test

git checkout dev   // 3. 切换至当前分支test

git merge test     // 4. 将test分支拉取下来的代码合并到dev