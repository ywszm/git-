## git 六行配置

![](/Users/acw/Library/Application Support/typora-user-images/image-20200705214246493.png)



## git 本地仓库

- `git init` 会创建 .git 目录


- `git add 路径`

  选择哪些变动是需要提交的

  路径可以是绝对路径、相对路径、**.和***


- `.gitignore`

  描述哪些变动是**不需要**提交的

  常见的有`node_modules`; `.Ds_Store`; `.idea; .vscode`


- `git commit -m 字符串`

  提交，并说明提交的理由

  字符串里如果有空格，就要用引号包起来


- `git commit -v` 

  建议新手用这条命令

  它能帮我们回顾刚刚改了哪些代码

  迫使我们把提交的理由写的更详细些


- 已经创建了一个拷贝，可以通过 `git log` 查看

  `git log` 可以查看提交日志

  当我们想要回退版本时，可以通过它查看提交号


- `git reset --hard xxxxxx` 

  xxxxxx是提交号的前六位，也可以将提交号整个复制过来
  
  请一定要确保你已经把所有代码commit了
  
  因为这个操作会使没有commit过的变动消失
  
- `git log` 只会显示之前的提交，`使用git reflog` 可以查看所有的提交

- `git branch x` 

  可以创造平行时间线x

  术语叫分支

- `git branch`

  基于当前commit创建一个新的时间线（分支）

  我在哪个分支提交，代码就出现在哪个分支

- `git checkout` 

  用于切换另一个分支

  当前目录有未提交的代码，只要跟另一个分支不冲突，就不需要理会

  如果冲突了，可以使用通灵术 `git stash` ,也可以合并冲突

- `git merge` 

  将另一个分支合并到当前分支

### 解决冲突的办法

- 发现冲突

  你在合并分支的时候，会得到conflict提示

  使用`git status -sb` 查看哪个/哪些文件冲突了

- 解决冲突

  依次打开每个文件

  搜索====四个等于号

  在上下两个部分中选择要保留的代码

  可以只选上面，也可以只选下面，甚至可以都选

  删除不用的代码，删除==== >>>> <<<< 这些标记

  `git add` 对应的文件

  再次`git status -sb` ,解决下一个文件的冲突

  直到没有冲突，运行`git commit` （注意不需要选项）

- 分支可以合并

  进入要保留的分支

  运行git merge x

  合并完后删除无用的分支`git branch -d x` 

  