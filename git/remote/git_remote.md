# git remote

为了便于管理，Git要求每个远程主机都必须指定一个主机名。git remote命令就用于管理主机名。
## 列出远程主机
不带选项的时候，git remote命令列出所有远程主机。
```bash
$ git remote
origin
```
## 查看远程主机的网址
使用-v选项，可以参看远程主机的网址。
```bash
$ git remote -v
origin  git@github.com:lanlan2017/book.git (fetch)
origin  git@github.com:lanlan2017/book.git (push)
```
上面命令表示，当前只有一台远程主机，叫做origin，以及它的网址。
## 克隆仓库的时候指定远程主机名
克隆版本库的时候，所使用的远程主机自动被Git命名为origin。如果想用其他的主机名，需要用git clone命令的-o选项指定。
```bash
$ git clone -o jQuery https://github.com/jquery/jquery.git
$ git remote
jQuery
```
上面命令表示，克隆的时候，指定远程主机叫做jQuery。
## 查看远程主机的信息
git remote show命令加上主机名，可以查看该主机的详细信息。
```bash
git remote show <主机名>
```
显示效果:
```
$ git remote show origin
* remote origin
  Fetch URL: git@github.com:lanlan2017/book.git
  Push  URL: git@github.com:lanlan2017/book.git
  HEAD branch: master
  Remote branches:
    gh-pages new (next fetch will store in remotes/origin)
    master   tracked
  Local ref configured for 'git push':
    master pushes to master (up to date)

```
## 添加远程主机
git remote add命令用于添加远程主机。
```bash
git remote add <主机名> <网址>
```
## 删除远程主机
git remote rm命令用于删除远程主机。
```bash
git remote rm <主机名>
```
## 修改远程主机名
git remote rename命令用于远程主机的改名。
```bash
git remote rename <原主机名> <新主机名>
```