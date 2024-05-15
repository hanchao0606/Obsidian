查看远程仓库及其 URL：
`git remote -v`
命令获取最新信息

`git fetch` 

列出所有远程分支: 包括未跟踪的分支
`git ls-remote` 

更新本地跟踪分支:如果远程分支已重命名
`git branch --set-upstream-to`

列出所有本地分支，并指示当前分支
`git branch`

输出当前分支的简短名称
`git rev-parse --abbrev-ref HEAD`

If the changes in these files are temporary or you don't want to commit them yet, you can stash them. Stashing creates a temporary snapshot of your uncommitted changes, allowing you to switch branches without losing them. Later, you can apply the stashed changes back to your working directory.
`git stash`
更新远程仓库
`git pull`
`git revert <name of bad commit>`
