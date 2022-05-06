#   密钥登录
各位同学，因前段时间服务器被盗用，实验室决定更换服务器的登录方式，使用密钥进行登录。

## 1.制作密钥对
进入个人账户后，输入以下命令：
~~~shell
ssh-keygen
ENTER # 这里是回车，不是输入字符
ENTER # 这里是回车，不是输入字符
ENTER # 这里是回车，不是输入字符
~~~

## 2. 安装公钥
~~~shell
cd .ssh
cat id_rsa.pub >> authorized_keys #如此便完成了公钥的安装。为了确保连接成功，请保证以下文件权限正确：
chmod 600 authorized_keys
chmod 700 ~/.ssh
~~~

## 3. 保存私钥
！ 在保存私钥前，请重新打开终端，确保上一步的chmod生效

请把.ssh/文件夹下载到本地，之后会使用

如果在多台服务器上拥有账户，请把每一台服务器上的私钥保存到本地，并予以区分。

## 4. ssh登录服务器
shell命令行登录:
~~~shell
ssh -i RootToid_rsa user@10.106.14.226 # RootToid_rsa是id_rsa(私钥)在本地的路径
~~~

如果使用vscode,在本地的config设置如下:
~~~shell
Host 10.106.14.226
  HostName 10.106.14.226
  IdentityFile C:\\Users\\wangjie\\Desktop\\10.106.14.226\\wangjie\\id_rsa
  User wangjie
~~~

## 4. 测试密钥
完成以上步骤后，请大家测试能否通过密钥登录服务器。[测试密钥](/测试密钥/测试密钥.md)


@author: Jie Wang & Shenwang Jiang & Yuncheng Wang

Email: jwang991020@gmail.com



## 测试密钥
请大家使用本地的shell命令行进行测试: windows用户按win + R弹出一个窗口，然后输入cmd进入终端。mac用户直接进入终端即可

### 1. 进入终端

### 2. 使用密钥登录
shell命令行登录:
~~~shell
ssh -i RootToid_rsa user@10.106.14.226 # RootToid_rsa是id_rsa(私钥)在本地的路径
~~~

如果不用输入密码即可直接登录进账户，那么测试通过。

如果出现以下问题：
![](微信图片_20220506124110.png)
则需要更改密钥在本地的拥有权限。

##### 修改方法如下：
##### Step 1: 打开文件夹 属性-安全
![](属性_安全.png)

##### Step 2: 点击 高级-禁用继承-从此对象中删除所有已继承的权限
![](高级_禁用继承.png)

##### Step 3: 点击 添加主体 添加电脑中的一个用户
![](添加主体.png)

##### Step 4: 点击 完全控制
![](完全控制.png)

##### Step 5: 再次尝试登录，登录成功！
![](登录成功.png)