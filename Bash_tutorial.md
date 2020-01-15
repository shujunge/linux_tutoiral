Bash教程
====
Bash 别名
要使用你创建的 Bash 别名，你需要将其添加到 .bash_profile 中，该文件位于你的home目录中。
请注意，此文件是隐藏的，并只能从命令行访问。编辑此文件的最简单方法是使用 Vi 或 Nano 之类的东西。

* 解压文件

你有几次遇到需要解压 .tar 文件但无法记住所需的确切参数？别名可以帮助你！只需将以下内容添加到.
bash_profile 中，然后使用 untar FileName 解压缩任何 .tar 文件

alias untar='tar -zxvf'

* 下载文件
下载文件时，如果出现问题想要恢复下载？
alias wget='wget -c '

* 快速为新的帐户生成随机的 20 个字符的密码

alias getpass="openssl rand -base64 20"

* 对下载的文件进行校验和测试
alias sha='shasum -a 256 '

* ping 
alias ping='ping -c 5'

*  在命令行中快速获取你的外部 IP 地址。
alias ipe='curl ipinfo.io/ip'


