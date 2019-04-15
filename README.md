# -GCP-shadowsocks-
前期准备：

google帐号，mastercard信用卡

正式工作：

1、申请注册GCP帐号：
  按照真实信息填写，“国家/地区”一栏已经没有“中国”的选项，建议填写“香港”或者“澳门”。



2、修改防火墙：
  进入控制台后，依次点击菜单–网络–防火墙规则。然后点击右上角的“创建防火墙规则”。名字随便起一个就好，然后中间部分不用动。“目标”选“网络中的所有实例”，“来源过滤”选择“IP地址范围”，并在下方填写“0.0.0.0/0”，然后最下方选择“指定的协议和端口”，并在下方填入“tcp:0-65535;udp:0-65535”。然后点击创建。




ps:1、一定要注意选中---所有实例,或者自己配置要翻的那个实例。

      2、流量方向“出站”，“入站”各设置一条。



3、创建VM实例 (要注意选择ip和要允许https和http)
然后再回到菜单，选择“计算引擎”—“VM实例”—“创建实例”。名字随便起一个，地区建议选“asia-east1-a”（台湾地区，速度比较快），机器类型选最低配的“微型”即可，启动磁盘建议选ubuntu 16.4 因为以下教程是这个操作系统的，防火墙允许HTTP/HTTPS流量。然后点击下方的“网络”选项卡，选择“外部IP”—“新建静态IP地址”，起个名字后就会分配到一个IP地址（每个地区仅限1个），完成后点击“创建”即可。






4.SSH连接服务器
等待几十秒配置成功后，就可以在列表中看到创建的实例了，点击右侧的“SSH”，在弹出的终端里搭建SS服务器。





5.安装S_s
在弹出的终端里，依次输入以下代码：

第一步：获取权限
sudo su
第二步：wegt安装
wget --no-check-certificate -O shadowsocks.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh
第三步：执行权限
chmod +x shadowsocks.sh
第四步：写入文件
./shadowsocks.sh 2>&1 | tee shadowsocks.log
等待安装，安装完成后，脚本提示如下：

Congratulations, Shadowsocks-python server install completed!
Your Server IP        :your_server_ip
Your Server Port      :your_server_port
Your Password         :your_password
Your Encryption Method:your_encryption_method

Welcome to visit:https://teddysun.com/342.html
Enjoy it!
