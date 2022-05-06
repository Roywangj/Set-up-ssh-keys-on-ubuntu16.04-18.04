#   密钥登录(管理员)

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

@author: Jie Wang & Shenwang Jiang & Yuncheng Wang

Email: jwang991020@gmail.com


## 5.设置SSH,打开密钥登录功能
~~~shell
编辑 /etc/ssh/sshd_config 文件，进行如下设置：

RSAAuthentication yes
PubkeyAuthentication yes
另外，请留意 root 用户能否通过 SSH 登录：

PermitRootLogin yes
当你完成全部设置，并以密钥方式登录成功后，再禁用密码登录：

PasswordAuthentication no
最后，重启 SSH 服务：

[root@host .ssh]$ service sshd restart
~~~


@author: Jie Wang & Shenwang Jiang & Yuncheng Wang

Email: jwang991020@gmail.com