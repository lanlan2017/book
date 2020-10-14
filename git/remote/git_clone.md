# git clone

git clone命令将存储库克隆到新目录中。
![Git命令](/images/git/remote/1.jpg)

## 默认克隆方式
远程操作的第一步，通常是从远程主机克隆一个版本库，这时就要用到git clone命令。
```bash
 git clone <版本库的网址>
```
这种方式会默认克隆主分支,Git会先在当前目录下创建一个与远程仓库同名的目录,然后将远程仓库中的所有内容下载到该同名目录中.
例如:
```bash
git clone git@github.com:lanlan2017/book.git
```
运行效果:
```
lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test
$ git clone git@github.com:lanlan2017/book.git
Cloning into 'book'...
remote: Enumerating objects: 246, done.
remote: Counting objects: 100% (246/246), done.
remote: Compressing objects: 100% (139/139), done.
remote: Total 246 (delta 98), reused 235 (delta 87), pack-reused 0
Receiving objects: 100% (246/246), 735.76 KiB | 17.00 KiB/s, done.
Resolving deltas: 100% (98/98), done.

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test
$ ls
book/

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test
$ cd book/

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book (master)
$ ls -a
./  ../  .git/  book.json  java/  myWebStyle.css  README.md  SUMMARY.md
```

## 克隆到指定目录
```bash
 git clone <版本库的网址> <本地目录名>
```
例如,克隆远程仓库到当前目录下的book2目录中:
```
git clone git@github.com:lanlan2017/book.git book2
```
运行效果:
```
lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test
$ git clone git@github.com:lanlan2017/book.git book2
Cloning into 'book2'...
remote: Enumerating objects: 246, done.
remote: Counting objects: 100% (246/246), done.
remote: Compressing objects: 100% (139/139), done.
remote: Total 246 (delta 98), reused 235 (delta 87), pack-reused 0
Receiving objects: 100% (246/246), 735.76 KiB | 8.00 KiB/s, done.
Resolving deltas: 100% (98/98), done.

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test
$ ls -a
./  ../  book/  book2/

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test
$ cd book2

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book2 (master)
$ ls -a
./  ../  .git/  book.json  java/  myWebStyle.css  README.md  SUMMARY.md
```
## 克隆远程仓库的指定分支
```bash
git clone -b 分支名 仓库地址
```
这种情况下,Git会在当前目录下创建一个与远程仓库同名的目录,然后将远程仓库中的内容下载到这个同名的目录中.

例如克隆远程仓库的gh-pages分支:
```bash
git clone -b gh-pages git@github.com:lanlan2017/book.git
```
运行效果:
```
lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test
$ git clone -b gh-pages git@github.com:lanlan2017/book.git
Cloning into 'book'...
remote: Enumerating objects: 246, done.
remote: Counting objects: 100% (246/246), done.
remote: Compressing objects: 100% (139/139), done.
remote: Total 246 (delta 98), reused 235 (delta 87), pack-reused 0
Receiving objects: 100% (246/246), 735.76 KiB | 7.00 KiB/s, done.
Resolving deltas: 100% (98/98), done.

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test
$ ls
book/

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test
$ cd book/

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book (gh-pages)
$ ls -a
./   .git/       gitbook/    java/           package-lock.json
../  .gitignore  index.html  myWebStyle.css  search_plus_index.json
```

可以看到

## 克隆远程仓库的指定分支到指定目录
```bash
git clone -b 分支名 远程仓库地址 本地目录地址
```
例如,克隆远程仓库的gh-pages分支到当前目录下:
```bash
git clone -b gh-pages git@github.com:lanlan2017/book.git .
```
运行效果:
```
lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test
$ git clone -b gh-pages git@github.com:lanlan2017/book.git .
Cloning into '.'...
remote: Enumerating objects: 246, done.
remote: Counting objects: 100% (246/246), done.
remote: Compressing objects: 100% (139/139), done.
Receremote: Total 246 (delta 98), reused 235 (delta 87), pack-reused 0
Receiving objects: 100% (246/246), 735.76 KiB | 11.00 KiB/s, done.
Resolving deltas: 100% (98/98), done.

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test (gh-pages)
$ ls
gitbook/  index.html  java/  myWebStyle.css  package-lock.json  search_plus_index.json
```
## 克隆远程仓库的子目录
1. 初始化本地仓库,并进入
```bash
git init book &&cd book
```
2. 设置允许克隆子目录
```bash
git config core.sparsecheckout true
```
3. 设置要克隆的仓库的子目录路径
```bash
echo 'java/*' >> .git/info/sparse-checkout
```
这里的`java/*`,就是要复制的子目录.
4. 添加远程仓库的地址
```bash
git remote add origin git@github.com:lanlan2017/book.git
```
5. 拉去远程仓库
```bash
git pull origin master
```

运行效果:
```
lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test
$ git init book &&cd book
Initialized empty Git repository in G:/Desktop/Test/book/.git/

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book (master)
$ git config core.sparsecheckout true

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book (master)
$ echo 'java*' >> .git/info/sparse-checkout

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book (master)
$ git remote add origin git@github.com:lanlan2017/book.git

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book (master)
$ git pull origin master
remote: Enumerating objects: 16, done.
remote: Counting objects: 100% (16/16), done.
remote: Compressing objects: 100% (16/16), done.
remote: Total 16 (delta 0), reused 16 (delta 0), pack-reused 0
Unpacking objects: 100% (16/16), done.
From github.com:lanlan2017/book
 * branch            master     -> FETCH_HEAD
 * [new branch]      master     -> origin/master

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book (master)
$ ls -a
./  ../  .git/  java/
```

## 克隆远程仓库的子目录的子目录
步骤和上面的一样,修改第3步的子目录的地址即可:
```bash
echo 'java/algorithm/sort/*' >> .git/info/sparse-checkout
```
运行效果:
```
lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test
$ git init book &&cd book
Initialized empty Git repository in G:/Desktop/Test/book/.git/

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book (master)
$ git config core.sparsecheckout true

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book (master)
$ echo 'java/algorithm/sort/*' >> .git/info/sparse-checkout

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book (master)
$ git remote add origin git@github.com:lanlan2017/book.git

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book (master)
$ git pull origin master
remote: Enumerating objects: 16, done.
remote: Counting objects: 100% (16/16), done.
remote: Compressing objects: 100% (16/16), done.
remote: Total 16 (delta 0), reused 16 (delta 0), pack-reused 0
Unpacking objects: 100% (16/16), done.
From github.com:lanlan2017/book
 * branch            master     -> FETCH_HEAD
 * [new branch]      master     -> origin/master

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book (master)
$ ls
java/

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book (master)
$ cd java/

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book/java (master)
$ ls
algorithm/

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book/java (master)
$ cd algorithm/

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book/java/algorithm (master)
$ ls
sort/

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book/java/algorithm (master)
$ cd sort/

lan@DESKTOP-8ISAT6B MINGW64 /g/Desktop/Test/book/java/algorithm/sort (master)
$ ls
BubbleSort.md  InsertSort.md  QuickSort.md  README.md  SelectSort.md
```

# 参考资料
[https://www.yiibai.com/git/git_clone.html](https://www.yiibai.com/git/git_clone.html)

[https://juejin.im/post/6844903585533313032](https://juejin.im/post/6844903585533313032)
