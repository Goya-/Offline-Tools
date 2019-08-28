# MultiVAC离线使用工具

## 说明：

本项目适用于MultiVAC的离线工具，基于Go1.12版本，在离线下具有以下功能：

1. 随机生成适用于MultiVAC的私钥和对应的公钥(GenerateKeyByRandom)
2. 根据用户给的私钥生成对应的公钥(PrivateKeyToPublicKey)
3. 使用私钥对输入的交易进行签名(Signature)
4. 根据助记词生成私钥及其公钥
5. 将私钥保存到keystore
6. 根据（keystore+密码）或助记词找回私钥

## 使用方法：

根据源码编译好的二进制文件（可执行文件）位于/MultiVACTools/application文件夹内，用户可以根据自己的操作系统选择符合自己系统运行的二进制文件（可执行文件）。其中GenerateKeyByRandom、PrivateKeyToPublicKey、Signature这三个文件为旧版本的离线工具，没有助记词和keystore功能，MultiVACTools为新版本，新版和旧版在私钥、公钥和签名功能上完全兼容，两个版本完全互通，新版本的助记词功能和keystore功能在旧版上上无法使用，程序为命令行工具，打开工具根据提示输入编号即可，在输入编号时程序只会关注第一个输入的字符，所以在输入选择功能菜单的时候请确定您的输入是否正确,在输入助记词的时候每个单词之间请用一个空格字符分隔以方便区分输入结束以后按enter键结束输入；在输入私钥和需要签名的交易时根据提示输入，输入结束按enter键结束即可。 

## 源码编译：

源码的主程序位于项目的主目录下，项目需要的依赖已经放在了vendor目录下面，可以自行打开源码，在Go1.12以上版本进行编译。编译的时候跳转到项目目录下，在命令行（终端）输入：

```bash
go build main.go
```

## 注意事项：

1. 助记词和私钥具有等同地位，助记词泄漏意味着私钥泄漏，所以务必保存好助记词，不要让他人知晓。
2. keystore的密码请务必记清楚，keystore生成的json文件在window系统下位于"C:\MultiVACkeystore"文件夹内，读取的时候程序会自动该目录下的json文件；在Mac os和Linux系统中，json文件生成的文件夹为"user/username/MultiVACkeystore"文件夹（username为当前账户的用户名），keystore需要使用密码解密时请将keystore文件放到该目录下即可读取。
