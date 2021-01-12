# GitHub上传下拉仓库

## 一、在github上新建一个仓库

## 二、 在本地创建一个仓库

- git init

## 三、 添加SSH Key

- 在本地仓库的文件下 右键gitbush here
- 打开gitbush
- 输入命令 ssh-keygen -t rsa -C ‘1371444344@qq.com(即自己的邮箱地址)’
- 一直回车
- 然后会在该目录下生成两个文件 ### ###.pub
- 复制这两个文件黏贴到 C:/用户/当前登录电脑的账户名/.ssh 并修改两个文件的名称分别为id_rsa id_rsa.pub
- 执行shh-add id_rsa 将生成的key添加
- 打开d_rsa.pub 复制里面的公钥
- 到github上 选择setting->SSH and GPG keys，点击New SHH key，任意输入名字 然后把复制的公钥黏贴到key 完成SSH的创建

## 四、下拉github仓库文件进行与本地仓库的关联

- 添加远程仓库地址 将本地仓库与github仓库进行关联
   git remote add origin git@github.com:[HRBUST-EmbeddedLaboratoryTeam1](https://github.com/HRBUST-EmbeddedLaboratoryTeam1)/**[RobotFightingContest](https://github.com/HRBUST-EmbeddedLaboratoryTeam1/RobotFightingContest)**  
   **可以通过 git remote -v查看已经添加的，可以通过git remote rm origin删除，修改默认的remote.url和remote.origin可以通过git config --global remote.url '修改的值’进行修改**
- 下拉远程仓库 使本地和远程保留一致 这点很重要 如果不保留一致 就无法进行上传
   git pull origin master
- 添加本地需要上传的文件至缓存区
   git add . 表示添加所有
- 提交至本地仓库
   git commit -m ‘这是第一次提交’
- 上传至github远程仓库
   git push origin master

## 五、删除github上的文件

- 还是先下拉github上的远程仓库至本地仓库
   git pull origin master
- 将文件从仓库中移除 但是不删除
   git rm --cached 文件名
- 提交至本地仓库
   git commit -m ‘这是删除了文件的修改’
- 上传至github远程仓库 
   git push origin master