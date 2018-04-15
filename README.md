﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿# Git总结---### 创建版本库| 命令 | 作用 ||------|------||`mkdir <目录名>`|创建目录||`pwd`|显示当前目录||`git init`| 初始化仓库 |### 添加文件到仓库|命令|作用||------|------||`git add */filename`|添加文件到索引||`git commit -m "提交信息"`|提交到控制系统||`git status` |查询当前工作区状态|### 回退版本|命令|作用||---|---||`git reset --hard commit_id/HEAD^`|回退版本||`git log <--pretty=oneline> <--graph>`|查看版本历史||`git reflog`|查看历史命令|> 注：版本回退之后再使用checkout检出### 管理修改1. 当改乱了工作区内容，想直接丢弃工作区的修改时，直接使用`git checkout -- filename`2. 当不仅改乱了工作区某个文件内容，而且还`add`到暂存区，使用`git reset HEAD file`，就回到了上一步。3. 当提交到了版本库时，需要使用版本回退。### 删除文件|命令|效果||---|---||`rm filename`|从磁盘中删除文件||`git rm filename`|从版本库中删除||`git checkout -- filename`|误删时恢复下来|### 远程仓库|命令|效果||---|---||`ssh-keygen -t rsa -C "youremailexample.com"`|创建公钥||`git remote add origin git@github.com:NAME/repo.git`|克隆到本地远程库||`git push <-u> origin master`|将本地分支推送到远程库`master`分支上||`git pull`|拉取远程库代码||`git remote -v`|查看远程仓库信息||`git checkout -b branch_name origin/<name>`|将远程库中的`name`分支检出到本地||`git branch --set-upstream dev origin/<branch>`|设置本地分支和远程分支的链接|### 创建与合并分支|命令|效果||------|------||`git checkout -b branch_name`|创建并检出到`branch_name分支`||`git branch`|查看分支||`git checkout branch_name`|将工作区检出到`branch_name`分支||`git branch -d branch_name`|删除分支||`git merge branch_name`|将指定分支合并到当前分支||`git log --graph`|查看分支合并图||`gitk`|可视化图形界面||`git merge --no-ff -m <message> branch_name`|将分支合并并且不适用快速合并（fast forward）||`git stash`|将工作区暂存||`git stash list`|查看暂存的列表||`git stash pop`|将最上层储存弹出，然后删除||`git stash apply stash@{?}`|将指定的储存取出，但不删除||`git stash drop`|删除指定的储存|> 合并冲突解决流程：当前分支发生了修改->要合并的分支也发生了修改->merge时出现冲突（远程时需要先pull下来）->手动合并冲突->重新提交->合并完成