FTPS（基于 SSL 的FTP）与 SFTP（SSH 文件传输协议）对比
================================================== ==========

![](http://www.techmixer.com/pic/2015/07/ftps-sftp.png)

**<ruby>SSH 文件传输协议<rt>SSH File transfer protocol</rt></ruby>，SFTP 或称为<ruby>通过安全套接层的文件传输协议<rt>File Transfer protocol via Secure Socket Layer</rt></ruby>**， 以及 FTPS 都是最常见的安全 FTP 通信技术，用于通过 TCP 协议将计算机文件从一个主机传输到另一个主机。SFTP 和 FTPS 都提供高级别文件传输安全保护，通过强大的算法（如 AES 和 Triple DES）来加密传输的数据。

但是 SFTP 和 FTPS 之间最显着的区别是如何验证和管理连接。

FTPS 是使用安全套接层（SSL）证书的 FTP 安全技术。整个安全 FTP 连接使用用户 ID，密码和 SSL 证书进行身份验证。一旦建立 FTPS 连接，如果服务器的证书是可信的，[FTP 客户端软件][6]将检查目的地[ FTP 服务器] [7]。

如果证书由已知的证书颁发机构（CA）签发，或者证书由您的合作伙伴自己签发，并且您的信任密钥存储区中有其公开证书的副本，则 SSL 证书将被视为受信任的证书。FTPS 的所有用户名和密码信息将通过安全的 FTP 连接加密。

###以下是 FTPS 的优点和缺点：

优点：

- 通信可以被人们读取和理解
- 提供服务器到服务器文件传输的服务
- SSL/TLS 具有良好的身份验证机制（X.509 证书功能）
- FTP 和 SSL 支持内置于许多互联网通信框架中

缺点：

- 没有统一的目录列表格式
- 需要辅助数据通道，这使得难以在防火墙后使用
- 未定义文件名字符集（编码）的标准
- 并非所有 FTP 服务器都支持 SSL/TLS
- 没有标准的方式来获取和更改文件或目录属性

SFTP 或 SSH 文件传输协议是另一种安全的安全文件传输协议，设计为 SSH 扩展以提供文件传输功能，因此它通常仅使用 SSH 端口用于数据传输和控制。当 [FTP客户端] [8]软件连接到 SFTP 服务器时，它会将公钥传输到服务器进行认证。如果密钥匹配，提供任何用户/密码，身份验证就会成功。

###以下是 SFTP 优点和缺点：

优点：

*只有一个连接（不需要DATA连接）。
* FTP连接始终保持安全
* FTP目录列表是一致的和机器可读的
* FTP协议包括操作权限和属性操作，文件锁定和更多的功能。

缺点：

*通信是二进制的，不能“按原样”记录下来用于人类阅读
    并且SSH密钥更难以管理和验证。
*这些标准定义了某些可选或推荐的选项，这会导致不同供应商的不同软件之间存在某些兼容性问题。
*没有服务器到服务器的副本和递归目录删除操作
*在VCL和.NET框架中没有内置的SSH / SFTP支持。

大多数FTP服务器软件同时支持安全FTP技术与强大的身份验证选项。

但SFTP将是防火墙赢家，因为它很友好。SFTP只需要通过防火墙打开一个端口号（默认为22）。此端口将用于所有SFTP通信，包括初始认证，发出的任何命令以及传输的任何数据。

FTPS将更难以实现通过紧密安全的防火墙，因为FTPS使用多个网络端口号。每次进行文件传输请求（get，put）或目录列表请求时，需要打开另一个端口号。因此，它必须在您的防火墙中打开一系列端口以允许FTPS连接，这可能是您的网络的安全风险。

支持FTPS和SFTP的FTP服务器软件：

1. [Cerberus FTP服务器] [2]
2. [FileZilla  - 最着名的免费FTP和FTPS服务器软件] [3]
3. [Serv-U FTP服务器] [4]

-------------------------------------------------- ------------------------------

通过：http://www.techmixer.com/ftps-sftp/

作者：[Techmixer.com] [a]
译者：[Yuan0302]（https://github.com/Yuan0302）
校对：[jasminepeng]（https://github.com/jasminepeng）

本文由[LCTT]（https://github.com/LCTT/TranslateProject）原创编译，[Linux中国]（https://linux.cn/）荣誉推出

[a]：http：//www.techmixer.com/
[1]：http：//www.techmixer.com/ftps-sftp/#respond
[2]：http：//www.cerberusftp.com/
[3]：http：//www.techmixer.com/free-ftp-server-best-windows-ftp-server-download/
[4]：http：//www.serv-u.com/
[6]：http：//www.techmixer.com/free-ftp-file-transfer-protocol-softwares/
[7]：http：//www.techmixer.com/free-ftp-server-best-windows-ftp-server-download/
[8]：http：//www.techmixer.com/best-free-mac-ftp-client-connect-ftp-server/