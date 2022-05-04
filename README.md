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
请把.ssh/文件夹下载到本地，之后会使用

## 4. ssh登录服务器
~~~shell
ssh -i RootToid_rsa user@10.106.14.226 # RootToid_rsa是id_rsa(私钥)在本地的路径
~~~

@author: Jie Wang & Shenwang Jiang & Yuncheng Wang

Email: jwang991020@gmail.com
