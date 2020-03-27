# install安装

## 安装

## 安装 <a id="install"></a>

安装ccxt库的最简单方法是使用内置的软件包管理器：

* [ccxt在**NPM**](http://npmjs.com/package/ccxt)（JavaScript的/节点V7.6 +）
* [在ccxt **的PyPI**](https://pypi.python.org/pypi/ccxt)（Python 2和3）

该库作为具有最小依赖性和要求的多模块模块实现提供：

* 在JavaScript[`ccxt.js`](https://github.com/ccxt/ccxt/blob/master/ccxt.js)
* 在Python（从JS生成）[`./python/`](https://github.com/ccxt/ccxt/blob/master/python/)
* 在PHP（从JS生成）[`ccxt.php`](https://github.com/ccxt/ccxt/blob/master/ccxt.php)

您也可以将其从[ccxt GitHub存储](https://github.com/ccxt/ccxt)库克隆到项目目录中，并使用适合您环境的语言扩展[名将](https://github.com/ccxt/ccxt)文件手动复制到工作目录中。

```text
git clone https://github.com/ccxt/ccxt.git
```

安装该库的另一种方法是从源代码构建自定义捆绑包。选择您需要的交流。`exchanges.cfg`

### JavaScript（NPM） <a id="javascript-npm"></a>

ccxt的JavaScript版本可在Node和Web浏览器中使用。需要ES6和语法支持（节点7.6.0+）。使用Webpack和Babel进行编译时，请确保`async/await`[未](https://github.com/ccxt-dev/ccxt/issues/225#issuecomment-331582275)在配置中[排除](https://github.com/ccxt-dev/ccxt/issues/225#issuecomment-331582275)它。`babel-loader`

[ccxt在NPM密码交易库](http://npmjs.com/package/ccxt)

```text
npm安装ccxt
```

```text
var ccxt = require （'ccxt' ）  ​控制台。日志（ccxt 。交流）//打印所有可用的交流  
```

#### Node.js + Windows <a id="node-js-windows"></a>

其安装困难Windows用户，或对ccxt库的依赖，尝试安装第一：`w3scryptnode-gypscrypt`

```text
npm install -g web3 --unsafe-perm = true --allow-root
```

要么

```text
须藤npm install -g web3 --unsafe-perm = true --allow-root
```

然后使用照常安装ccxt 。`npm install ccxt`

如果没有帮助，请按以下网址：[https://github.com/nodejs/node-gyp\#on-windows](https://github.com/nodejs/node-gyp#on-windows)

### JavaScript（用于标记）：`<script>` <a id="javascript-for-use-with-the-less-than-script-greater-than-tag"></a>

通过您选择的CDN提供的多合一浏览器捆绑包（包括依赖项）：

* jsDelivr：[https://cdn.jsdelivr.net/npm/ccxt@1.25.27/dist/ccxt.browser.js](https://cdn.jsdelivr.net/npm/ccxt@1.25.27/dist/ccxt.browser.js)
* unpkg：[https://unpkg.com/ccxt@1.25.27/dist/ccxt.browser.js](https://unpkg.com/ccxt@1.25.27/dist/ccxt.browser.js)

您可以通过从URL（事物）中删除版本号来获取捆绑包的实时更新版本-但是，我们不建议这样做，因为它最终可能会破坏您的应用程序。另外，请记住，我们对这些CDN服务器的正确操作不承担任何责任。`@a.b.c`

```text
< 脚本类型=“ text / javascript ” src =“ https://cdn.jsdelivr.net/npm/ccxt@1.25.27/dist/ccxt.browser.js ” > </ 脚本>  
```

创建一个全局对象：`ccxt`

```text
控制台。日志（ccxt 。交流）//打印所有可用的交流  
```

### 蟒蛇 <a id="python"></a>

[ccxt中的PyPI algotrading库](https://pypi.python.org/pypi/ccxt)

```text
点安装ccxt
```

```text
导入ccxt打印（ccxt 。交流）＃打印所有可用的交换类的列表 
```

该库在Python 3.5.3+中支持asyncio和async / await的并发异步模式。

```text
导入ccxt 。async_support as ccxt ＃链接到ccxt的异步版本
```

### 的PHP <a id="php"></a>

ccxt的自动加载版本可以与[**Packagist / Composer**](https://packagist.org/packages/ccxt/ccxt)（PHP 5.4+）一起安装。

它也可以从源代码安装：[**`ccxt.php`**](https://raw.githubusercontent.com/ccxt/ccxt/master/php)

它需要通用的PHP模块：

* 卷曲
* mbstring（强烈建议使用UTF-8）
* 聚四氟乙烯
* 图标
* gmp（这是PHP 7.2+的内置扩展）

```text
包括“ ccxt.php” ； 的var_dump （\ ccxt \ 交易所：：$交流）; //打印所有可用交换类的列表 
```

### 码头工人 <a id="docker"></a>

您可以将CCXT以及所有支持的语言和依赖项安装在容器中。如果您想为CCXT做出贡献，这可能会很有用（例如，运行构建脚本和测试- 有关详细信息，请参阅[贡献](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md)文档）。

使用（在克隆的CCXT存储库中）：`docker-compose`

```text
docker-compose运行--rm ccxt
```

或者：

```text
码头工人建设。--tag ccxt泊坞窗运行-it ccxt
```

## 代理 <a id="proxy"></a>

在某些特定情况下，如果您遇到[Cloudflare的DDoS保护](https://github.com/ccxt/ccxt/wiki/Manual#ddos-protection-by-cloudflare)问题，或者您的网络/国家/ IP被其过滤器拒绝，则可能需要代理。

**请记住，每个添加的中介都会导致总体延迟和往返时间。较长的延迟会导致价格下滑。**

### JavaScript代理 <a id="javascript-proxies"></a>

为了将代理与JavaScript一起使用，需要将代理选项传递给交换类实例构造函数（或在运行时实例化之后再设置属性）：`agentexchange.agent`

```text
const ccxt = require （'ccxt' ）      ，HttpsProxyAgent = require （'https-proxy-agent' ）  ​const proxy = 进程。ENV 。http_proxy || 'http://168.63.76.32:3128'// 连接到的HTTP / HTTPS代理  const agent = new HttpsProxyAgent （proxy ）   ​crack const = new ccxt 。破解（{ agent } ）   
```

### Python代理 <a id="python-proxies"></a>

该库的python版本将[python-requests](https://python-requests.org/)包用于基础HTTP，并支持包中可用的所有自定义方式，包括代理。`requests`

您可以通过设置环境变量HTTP\_PROXY和HTTPS\_PROXY来配置代理。

```text
$ export HTTP_PROXY =“ http://10.10.1.10:3128”$ export HTTPS_PROXY =“ http://10.10.1.10:1080”
```

使用代理设置导出上述变量后，ccxt中的所有请求都将通过这些代理进行路由。

您还可以通过编程方式设置它们：

```text
导入ccxt交换= ccxt 。poloniex （{    “代理” ：{         'http' ：'http : //10.10.1.10 : 3128' ，＃这些代理对您不起作用，例如，它们在这里           'https' ：'https : //10.10.1.10 : 1080' ，     } ，} ）
```

要么

```text
导入ccxt交换= ccxt 。poloniex （）交换。代理= {   'http' ：'http : //10.10.1.10 : 3128' ，＃这些代理对您不起作用，例如，它们在这里    'https' ：'https : //10.10.1.10 : 1080' ， }
```

#### Python 2和3同步代理 <a id="python-2-and-3-sync-proxies"></a>

* [https://github.com/ccxt/ccxt/blob/master/examples/py/proxy-sync-python-requests-2-and-3.py](https://github.com/ccxt/ccxt/blob/master/examples/py/proxy-sync-python-requests-2-and-3.py)

```text
＃-*-编码：utf-8-*-​导入它们导入系统导入ccxt从pprint 导入pprint​​交换= ccxt 。poloniex （{    ＃    ＃↓以下“ proxy”属性设置仅适用于CORS代理！    ＃如果您不知道CORS代理是什么，请不要使用它。    ＃https://github.com/ccxt/ccxt/wiki/Install#cors-access-control-allow-origin    ＃只有在Access-Control-Allow-Origin遇到问题时，才应使用“代理”设置    ＃在Python中，您根本不需要使用它（如果有的话）。    ＃    ＃'proxy'：'https://cors-anywhere.herokuapp.com/'，    ＃    ＃↓另一方面，“代理”设置用于HTTP（S）代理（SOCKS等）    ＃这是通过代理发送请求的标准方法    ＃这直接传递给python-requests实现    ＃您还可以使用环境变量启用它，如下所述：    ＃http://docs.python-requests.org/zh/master/user/advanced/#proxies    ＃这是您应在Python 2和3中与ccxt的同步版本一起使用的设置    ＃    “代理” ：{         'http' ：'http : //10.10.1.10 : 3128' ，         'https' ：'http : //10.10.1.10 : 1080' ，     } ，} ）​＃您的代码在这里...​pprint （交换。fetch_ticker （'ETH / BTC' ））
```

#### Python 3.5+ asyncio / aiohttp代理 <a id="python-3-5-asyncio-aiohttp-proxy"></a>

* [https://github.com/ccxt/ccxt/blob/master/examples/py/proxy-asyncio-aiohttp-python-3.py](https://github.com/ccxt/ccxt/blob/master/examples/py/proxy-asyncio-aiohttp-python-3.py)

```text
＃-*-编码：utf-8-*-​导入异步导入它们导入系统导入ccxt 。async_support 作为ccxt从pprint 导入pprint​​异步def test_gdax （）：  ​    交换= ccxt 。poloniex （{        ＃        ＃↓以下“ proxy”属性设置仅适用于CORS代理！        ＃如果您不知道CORS代理是什么，请不要使用它。        ＃https://github.com/ccxt/ccxt/wiki/Install#cors-access-control-allow-origin        ＃只有在Access-Control-Allow-Origin遇到问题时，才应使用“代理”设置        ＃在Python中，您根本不需要使用它（如果有的话）。        ＃        ＃'proxy'：'https://cors-anywhere.herokuapp.com/'，        ＃        ＃↓“ aiohttp_proxy”设置用于HTTP（S）代理（SOCKS等）。        ＃这是通过代理发送请求的标准方法        ＃这直接传递给`asyncio`和`aiohttp`实现        ＃您可以使用此处记录的此设置：        ＃https://docs.aiohttp.org/en/stable/client_advanced.html#proxy-support        ＃这是您应该在Python 3.5+中使用ccxt异步版本的设置        ＃        'aiohttp_proxy' ：'http : //proxy.com ' ，         ＃'aiohttp_proxy'：'http：// user：pass@some.proxy.com'，        ＃'aiohttp_proxy'：'http://10.10.1.10:3128'，    } ）​    ＃您的代码在这里...​    股票报价= 等待交易。fetch_ticker （'ETH / BTC' ） ​    ＃当您不再需要使用的资源时，请不要忘记释放它们    等待交流。关闭（）​    返回行情​如果__name__ == ' __main__ ' ：     pprint （ASYNCIO 。get_event_loop （）。run_until_complete （test_gdax （）））
```

可以在以下位置找到有关将代理与ccxt库的python同步版本一起使用的更详细的文档：

* [代理](http://docs.python-requests.org/en/master/user/advanced/#proxies)
* [SOCKS](http://docs.python-requests.org/en/master/user/advanced/#socks)

#### Python aiohttp SOCKS代理 <a id="python-aiohttp-socks-proxy"></a>

```text
点安装aiohttp_socks
```

```text
导入ccxt 。async_support 作为ccxt导入aiohttp导入aiohttp_socks​异步def 测试（）：  ​    连接器= aiohttp_socks 。ProxyConnector 。from_url （'socks5：// user：password@127.0.0.1：1080' ）    会话= aiohttp 。ClientSession （连接器= 连接器）​    交换= ccxt 。搜索（{        'session' ：会话，        'enableRateLimit' ：真，         ＃...    } ）​    ＃...​    等待会议。close （）＃不要忘记关闭会话  ​    ＃...
```

## CORS（访问控制允许来源） <a id="cors-access-control-allow-origin"></a>

如果需要CORS代理，请使用包含http（s）代理的基本URL 的属性（字符串文字）。它可与Web浏览器一起使用，也可在受阻止的位置使用。`proxy`

CORS是[跨域资源共享](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing)。使用ccxt库从浏览器访问交换的HTTP REST API时，您可能会收到警告或异常消息，说。这意味着交易所管理员尚未启用从任意Web浏览器页面访问其API的权限。`No 'Access-Control-Allow-Origin' header is present on the requested resource`

您仍然可以通过CORS代理从浏览器中使用ccxt库，该库很容易设置或安装。互联网上也有公共CORS代理。

在将HTTP请求发送到交换之前，将绝对交换端点URL附加到字符串。默认情况下，该设置为空字符串。以下是非空字符串的示例（必须使用最后一个斜杠！）：`proxyproxy''proxy`

* `kraken.proxy = 'https://crossorigin.me/'`
* `gdax.proxy = 'https://cors-anywhere.herokuapp.com/'`

要在本地运行自己的CORS代理，您可以设置一个现有的CORS代理，也可以制作自己的快速脚本，如下所示。

### Node.js CORS代理 <a id="node-js-cors-proxy"></a>

```text
// JavaScript CORS代理//将其保存在cors.js之类的文件中，并通过`node cors [port]`运行//默认情况下，它将在您通过命令行传递的端口或端口8080上侦听您的请求让端口= （处理。ARGV 。长度> 2 ）？parseInt函数（过程。的argv [ 2 ] ）：8080 ; //默认        require （'cors-anywhere' ）。createServer （）。侦听（port ，'localhost' ）    
```

### Python CORS代理 <a id="python-cors-proxy"></a>

```text
＃！/ usr / bin / env python＃Python CORS代理＃将其保存在cors.py之类的文件中，并以`python cors.py [port]`或`cors [port]`运行尝试：    ＃Python 3    来自http 。服务器导入HTTPServer ，SimpleHTTPRequestHandler ，测试为test_orig    导入系统    def 测试（* args ）：          test_orig （* ARGS ，端口= INT （SYS 。的argv [ 1 ] ）如果len个（SYS 。的argv ）> 1 别的8080 ）         除了ImportError ：＃Python 2     从BaseHTTPServer 导入HTTPServer ，进行测试    从SimpleHTTPServer 导入SimpleHTTPRequestHandler​类CORSRequestHandler （SimpleHTTPRequestHandler ）：      def end_headers （self ）：          自我。send_header （'Access-Control-Allow-Origin' ，'*' ）         SimpleHTTPRequestHandler 。end_headers （self ）​如果__name__ == ' __main__ ' ：     测试（CORSRequestHandler ，HTTPServer ）
```

### 测试CORS <a id="testing-cors"></a>

设置并运行它之后，可以通过代理查询交换端点的目标URL来对其进行测试（例如[https：// localhost：8080 / https：//exchange.com/path/to/endpoint](https://localhost:8080/https://exchange.com/path/to/endpoint)）。

要测试CORS，您可以执行以下任一操作：

* 在浏览器设置中的某处设置代理，然后转到端点URL `https://exchange.com/path/to/endpoint`
* 直接在地址栏中输入该URL为 `https://localhost:8080/https://exchange.com/path/to/endpoint`
* 从命令像cURL `curl https://localhost:8080/https://exchange.com/path/to/endpoint`

为了让ccxt知道代理，可以在交换实例上设置属性。`proxy`

