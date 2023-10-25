## 00 魔法的使用

由于众所周知的原因，推荐在使用GitHub时使用魔法以加速连接。可以选用https://ikuuu.art/user这一v*n，30块三个月（亲测很好用，无广），安装方法可以参考该网站中的指引，全平台可用。（小声）

## 01 Git的安装

下载网址：https://git-scm.com/download/win

![image-20231017172707675](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017172707675.png)

一般是选择64位的那个，下载后可参考https://blog.csdn.net/mukes/article/details/115693833这个进行安装，有对每个选项的详细解释，如果没啥特殊需求直接一路下来就行，不用更改他的默认选项。

## 02 GitHub的注册与使用（如果已有账号可以跳过）

网址：https://github.com/

一般进去之后会显示如图界面，可以在右上角分别登录（sign in)与注册（sign up）

![image-20231017173311360](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017173311360.png)

登陆成功后界面一般如图所示：

![image-20231017173357682](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017173357682.png)

## 03 Git的全局设置

在开始菜单或鼠标右键（推荐在桌面或某文件夹下右键鼠标-显示更多选项）找到Git Bash并打开（Git Bash Here），会显示如下界面（以在桌面右键打开为例）：

！！首先注意这里的复制粘贴不是传统的CTRL+C/CTRL+V，建议选择完后右键copy/paste！！

！！注意每一行后都要敲空格代表提交这一行命令！！

![image-20231017174737790](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017174737790.png)

其中~/后面显示的是你打开git bash的目录，随后需要配置您的GitHub账号名并在GitHub中设置SSH。

1）设置GitHub用户名：

```bash
git config --global user.name “用户名”
```

2）设置Github邮箱：

```bash
git config --global user.email “邮箱”
```

3）配置ssh

```bash
ssh-keygen -t rsa -C “邮箱”
```

执行后一直回车即可，随后获取ssh key公钥内容（id_rsa.pub）

```bash
cd ~/.ssh
cat id_rsa.pub
```

如下图所示，复制该内容

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210630110507976.png)

4）在GitHub账号上添加ssh公钥

点击右上角头像，进入settings

![image-20231017180201637](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017180201637.png)

然后选择左边SSH and GPG keys

![image-20231017180245407](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017180245407.png)

点击New SSH key

![image-20231017180318570](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017180318570.png)

添加刚刚复制的ssh公钥，名字随便命名，点击Add SSH Key

![image-20231017180520476](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017180520476.png)

随后在gitbash中输入

```
ssh -T git@github.com
```

![image-20231017180610480](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017180610480.png)

如图显示即为成功添加。

## 04 对GitHub中个人项目的使用

1）创建GitHub仓库，如图依次点击加号和new repository

![image-20231017181801120](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017181801120.png)

随后填写一些相关信息，repository name是项目名，只能使用中文；description是项目说明，不是必填项；add a readme file是初始化时加入说明文档，推荐勾上，最后点击右下角创建项目。示例如下，我创建了一个名为another test的项目，

![image-20231017182518909](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017182518909.png)

点击create repository，会跳转到如下所示界面：

![image-20231017182600512](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017182600512.png)

点击右上角绿色“code”，选择SSH，复制链接（点击右边按钮）备用。

![image-20231017182710043](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017182710043.png)

2）在本地克隆该项目

在桌面右键打开git bash，输入

```bash
git clone git@github.com:YiyuanYing/sync_test.git(更换为自己要clone的项目链接)
```

随后桌面上就会出现sync_test的文件夹（其他项目同理）

3）进行推送与同步操作

打开刚刚克隆的文件夹，右键打开git bash

可以先进行一些操作，例如新建文件、更改文件等等

0.更改branch

建议使用下列命令更改默认branch为main（git默认master，github默认main，如果显示~/桌面/sync_test (main)则不用改）

```bash
git checkout -b main
```

1.推送操作

首先在git bash中输入

```bash
git add .
```

（注意.前有空格）

随后输入

```bash
git commit -m "xxx"
```

xxx是你本次推送要显示的注释，中英文皆可

随后输入

```bash
git push origin main
```

如图显示则上传成功！![image-20231017190417856](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017190417856.png)

网页中可以看到有更新的时间和更新的注释

![image-20231017190547947](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017190547947.png)

2.同步操作

输入

```bash
git pull origin main
```

稍等待出现新的空行即为完成。

这样就能在本地对仓库中的代码或者其他文件进行修改了。



## 05 对GitHub中他人项目的使用（重要）

前面已经简单讲述了如何在GitHub上创建自己的仓库并与本地同步，现在讲述的是如何同步别人的项目并进行推送操作。

以我个人创建的一个测试项目https://github.com/YiyuanYing/sync_test为例，我用一个小号演示：

![image-20231017192314880](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017192314880.png)

点击右上角的fork，出现如下界面

![image-20231017192351626](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017192351626.png)

一般无需更改直接点击create fork

稍等片刻之后就会出现仓库界面，注意左上侧会有一行小字是forked form xxx

![image-20231017192439068](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017192439068.png)

此时就可以按照04中介绍的步骤进行克隆、推送与同步操作，此处不再赘述。

由于此仓库是fork过来的，相当于您的个人项目，您对此的任何更改，原仓库的所有者都不会知道，当然原仓库的所有者以及其他贡献者的更改操作您的这个仓库中也不会更改。

要向原仓库同步您的更改，需要pull request。

![image-20231017192648315](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017192648315.png)

在进行了更改后，该页面上方会出现xx commit ahead of xxx，表示您的更新领先于原仓库，可以向原仓库的所有者提出合并请求。

![image-20231017192832288](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017192832288.png)

点击contribute，点击open pull request

![image-20231017192905770](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017192905770.png)

可以在箭头所指处提出您的修改内容和请求，以便原仓库的所有者核对并通过/拒绝您的申请。

当您填写完后，点击右下方的create pull request，然后就可以等待原仓库的所有者通过/拒绝您的请求了。

当然还有一种可能是原仓库的所有者/其他贡献者对仓库内容进行了一些更改，而您的fork仓库没有更改，需要进行同步，如下图所示：

![image-20231017193232901](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017193232901.png)

此处操作较为简单，点击sync fork，点击update branch，稍等即可

![image-20231017193312342](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017193312342.png)

如下图显示即同步完成！

![image-20231017193325723](https://raw.githubusercontent.com/YiyuanYing/md-imgs/main/image-20231017193325723.png)

## 06 其他

这里讲解的都是一些最基本的操作，还有一些操作本人也还不熟悉（前两天刚摸索出来的），可以尝试自行百度或谷歌（有魔法了建议多用用谷歌，比百度好多了），csdn/菜鸟教程上有很多详细的操作方法，当然遇到报错也可以去使用chatgpt。

互勉！

开源万岁！