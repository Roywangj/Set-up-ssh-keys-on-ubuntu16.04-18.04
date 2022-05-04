#   密钥登录(管理员)


## 1.制作密钥对
进入root账户后，输入以下命令：
~~~shell
su user
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
请把.ssh/文件夹下载到本地，之后会使用

## 4. ssh登录服务器
~~~shell
ssh -i RootToid_rsa user@10.106.14.226 # RootToid_rsa是id_rsa(私钥)在本地的路径
~~~

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
