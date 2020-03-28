---
description: ccxt-pro-install
---

# ccxt-专业版-安装

## ccxt.pro.install

[⌂首页](https://ccxt.pro/)

## 如何安装 <a id="how-to-install"></a>

安装CCXT Pro要求访问[https://ccxt.pro](https://ccxt.pro/)网站并获得CCXT Pro许可证。该许可证使您可以访问私有GitHub存储库中的CCXT Pro代码库。

```text
-该文档的这一部分目前正在进行中-到处可能存在一些问题-感谢反馈和请求请求
```

### 的JavaScript <a id="javascript"></a>

```text
＃在您的项目目录中​＃如果您使用的是Git / HTTPS身份验证npm安装git + https：//github.com/kroitor/ccxt.pro.git​＃如果您使用SSH连接到GitHubnpm安装ssh：//git@github.com/kroitor/ccxt.pro.git＃ 要么npm安装git @ ssh：//github.com/kroitor/ccxt.pro.git＃或〜/ .ssh / config中是否有git和github.comnpm安装ssh：//github.com/kroitor/ccxt.pro.git
```

#### JavaScript依赖性 <a id="javascript-dependency"></a>

通过以上命令自动完成将CCXT Pro作为依赖项添加到Node.js项目或程序包中。要手动添加它，请在您的列表中或照常列出：`package.jsonpackage.jsondependenciesdevDependencies`

```text
// package.json{  // ...  “依赖关系” ：{     “ ccxt.pro” ：“ git + https：//github.com/kroitor/ccxt.pro.git”   }  // ...}
```

添加上述内容后，在同一个文件夹中运行会将CCXT Pro安装到您的。要更新它，请稍后运行。`npm installpackage.jsonnode_modules/npm update ccxt.pro`

### 蟒蛇 <a id="python"></a>

```text
＃如果您使用的是Git / HTTPS身份验证pip3安装git + https：//github.com/kroitor/ccxt.pro.git#subdirectory=python​＃如果您使用SSH连接到GitHubpip3安装git + ssh：//git@github.com/kroitor/ccxt.pro.git#subdirectory=python
```

#### Python依赖 <a id="python-dependency"></a>

使用[setuptools](https://setuptools.readthedocs.io/en/latest/)将CCXT Pro作为依赖`setup.py`[项](https://setuptools.readthedocs.io/en/latest/)添加到您的Python包中，可以通过在[需求文件](https://pip.pypa.io/en/latest/user_guide/#requirements-files)中或其中列出它来完成：

```text
＃setup.py设置（    ＃...    install_requires = [        ＃安装最新版本        'ccxtpro @ git + https：//github.com/kroitor/ccxt.pro.git#subdirectory=python'        ＃安装特定的版本号        ＃'ccxtpro @ git + https：//github.com/kroitor/ccxt.pro.git@0.1.13#subdirectory=python'    ]    ＃...）
```

### 的PHP <a id="php"></a>

```text
＃在您的项目目录中composer config repositories.ccxtpro'{“ type”：“ git”，“ url”：“ https://github.com/kroitor/ccxt.pro.git”}'作曲者需要ccxt / ccxtpro
```

#### PHP依赖 <a id="php-dependency"></a>

通过以上命令，CCXT Pro作为依赖项自动添加到您的PHP软件包中。要手动添加它，请像往常一样将其列出：`composer.jsoncomposer.json`

```text
// composer.json{    // ...    “要求” ：{         “ ccxt / ccxtpro” ：“ ^ 0.0.70”     } ，    “存储库” ：{         “ ccxtpro” ：{             “ type” ：“ git” ，             “ url” ：“ https://github.com/kroitor/ccxt.pro.git”         }    }    // ...}
```

