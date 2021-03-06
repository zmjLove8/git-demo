# *git-demo*
使用***git***和***github***进行协同开发流程。  
 - 准备 :octocat:
1. :arrow_down:[下载git](https://git-scm.com/downloads)
2. [安装git](https://git-scm.com/doc)(`RTFM`)
3. [使用GitHub](https://guides.github.com/activities/hello-world/)(`STFW`)
 -  [分支最佳实践](doc/branch_of_best_practices.md)
 -  [开发者使用建议(仓库、分支)](doc/Suggestions-for-repository-branches-used-in-development.md)
 - [`git-workflows`](doc/git-workflows-and-tutorials/)@author :point_right:[*oldratlee*](https://github.com/oldratlee)
1. [集中式工作流](doc/git-workflows-and-tutorials/workflow-centralized.md)  
1. [功能分支工作流](doc/git-workflows-and-tutorials/workflow-feature-branch.md)  
1. [`Gitflow`工作流](doc/git-workflows-and-tutorials/workflow-gitflow.md)  
1. [`Forking`工作流](doc/git-workflows-and-tutorials/workflow-forking.md)  
1. [`Pull Requests`](doc/git-workflows-and-tutorials/pull-request.md)  

---------------------------------
# 速成指南 :point_down:
---------------------------------
## 新建`repository`  
 创建永久分支：`master`、`develop`
![图](doc/images/create_master_develop_branch.png)
## 在本地clone仓库  
checkout到develop分支
```bash
$ git clone git@github.com:gongice/git-demo.git
$ cd git-demo/
$ git branch
 master
$ git checkout develop
 ranch develop set up to track remote branch develop from origin.
 Switched to a new branch 'develop'
```
### 检查develop分支是否有更新  
  有更新则提交。
```bash
$ git status
      modified:   README.md
Untracked files:
(use "git add <file>..." to include in what will be committed)
      src/
no changes added to commit (use "git add" and/or "git commit -a")
$ git add *
$ git commit -m "add doc/images/create_master_develop_branch.png and update README.md"
$ git push origin develop
```
## 从develop分支checkout到新的功能分支进行开发
例如：`feature-discuss`
```bash
$ git checkout -b feature-discuss
# checkout -b 创建并切换到新的分支
```
### 进行`feature-discuss`分支开发
```bash
$ touch discuss.js
```
### 开发完成，提交分支开发的新功能
```bash
$ git add discuss.js
$ git status
Changes to be committed:
(use "git reset HEAD <file>..." to unstage)
      new file:   discuss.js
$ git commit -m 'finish discuss feature'
```
## 合并`feature-discuss`代码
### 回到`develop`分支
```bash
$ git checkout develop
```
###   `merge feature-discuss`代码
```bash
$ git merge --no-ff feature-discuss
```
### 删除`feature-discuss`分支
```bash
$ git branch -d feature-discuss
```
### `push develop`分支
```bash
$ git push origin develop
```
![图](doc/images/finish_feature-discuss.png)
