---
description: install
---

# 安装

### 安装 CCXT

The easiest way to install the ccxt library is to use builtin package managers:

安装 CCXT 库最简单的办法，就是直接使用内嵌的包管理工具：

* [ccxt in **NPM**](http://npmjs.com/package/ccxt) \(JavaScript / Node v7.6+\)
* [通过 **NPM** 安装 ccxt](http://npmjs.com/package/ccxt) \(JavaScript / Node v7.6+\)
* [ccxt in **PyPI**](https://pypi.python.org/pypi/ccxt) \(Python 2 and 3\)
* [通过 **PyPI** 安装 ccxt](https://pypi.python.org/pypi/ccxt) \(Python 2 and 3\)

This library is shipped as an all-in-one module implementation with minimalistic dependencies and requirements:

通过不断地精简 ccxt 所依赖的库和组件，我们把它封装成了一个高度一体化的模块。

* [`ccxt.js`](https://github.com/ccxt/ccxt/blob/master/ccxt.js) in JavaScript
* [`./python/`](https://github.com/ccxt/ccxt/blob/master/python/) in Python \(generated from JS\)
* [`ccxt.php`](https://github.com/ccxt/ccxt/blob/master/ccxt.php) in PHP \(generated from JS\)

You can also clone it into your project directory from [ccxt GitHub repository](https://github.com/ccxt/ccxt):

你也从 [ccxt 官方仓库](https://github.com/ccxt/ccxt)将其克隆到自己的工程目录下：

```text
git clone https://github.com/ccxt/ccxt.git
```

An alternative way of installing this library into your code is to copy a single file manually into your working directory with language extension appropriate for your environment.

还有一种集成方式，你可以将某个需要使用的代码文件直接拷贝到你的工程目录下。同一个功能文件可能有不同编程语言的多种实现方式，请注意筛选。

#### JavaScript \(NPM\)

JavaScript version of ccxt works both in Node and web browsers. Requires ES6 and `async/await` syntax support \(Node 7.6.0+\). When compiling with Webpack and Babel, make sure it is [not excluded](https://github.com/ccxt-dev/ccxt/issues/225#issuecomment-331582275) in your `babel-loader` config.

JavaScript版本的 ccxt 同时支持在 Node 环境和浏览器环境中运行。需要支持 ES6 和 `async/await` 语法 \(Node 7.6.0+\) 。在你使用 Webpack 和 Babel 进行编译前，请确认当前 `babel-loader` 配置项没有把库文件夹[排除在外](https://github.com/ccxt-dev/ccxt/issues/225#issuecomment-331582275)。

[ccxt crypto trading library in npm](http://npmjs.com/package/ccxt)

[在 npm 中安装加密货币交易库 ccxt](http://npmjs.com/package/ccxt)

```text
npm install ccxt
```

```text
var ccxt = require ('ccxt')

console.log (ccxt.exchanges) // 输出所有可用交易所
```

#### JavaScript \(通过 `<script>` 标签调用\):

[All-in-one browser bundle](https://unpkg.com/ccxt) \(dependencies included\), served from [unpkg CDN](https://unpkg.com/), which is a fast, global content delivery network for everything on NPM.

[一体化浏览器 js 文件](https://unpkg.com/ccxt) \(包括所有依赖项\), 挂靠在 [unpkg CDN](https://unpkg.com/) 下，本 CDN 作为 NPM 内容分发节点之一，速度快、全球均可访问。

```text
<script type="text/javascript" src="https://unpkg.com/ccxt"></script>
```

Creates a global `ccxt` object:

创建全局 `ccxt` 对象:

```text
console.log (ccxt.exchanges) // 输出所有可用交易所
```

#### Python

[ccxt algotrading library in PyPI](https://pypi.python.org/pypi/ccxt)

[PyPI 中的 ccxt 库主页](https://pypi.python.org/pypi/ccxt)

```text
pip install ccxt
```

```text
import ccxt
print(ccxt.exchanges) # 输出一个list，内容为所有可用的交易所
```

The library supports concurrent asynchronous mode with asyncio and async/await in Python 3.5.3+

ccxt 库支持通过 concurrent 库的 asyncio 和 async/await 语法实现异步操作（Python 3.5.3+）

```text
import ccxt.async as ccxt # link against the asynchronous version of ccxt 引入异步版本的ccxt
```

#### PHP

The autoloadable version of ccxt can be installed with [**Packagist/Composer**](https://packagist.org/packages/ccxt/ccxt) \(PHP 5.3+\).

可自动加载的 ccxt PHP 组件 [**Packagist/Composer**](https://packagist.org/packages/ccxt/ccxt) \(PHP 5.3+\).

It can also be installed from the source code: [**`ccxt.php`**](https://raw.githubusercontent.com/ccxt/ccxt/master/php)

也可以直接下载代码文件： [**`ccxt.php`**](https://raw.githubusercontent.com/ccxt/ccxt/master/php)

It requires common PHP modules:

依赖的 PHP 模块：

* cURL
* mbstring \(建议使用 UTF-8 编码\)
* PCRE
* iconv

```text
include "ccxt.php";
var_dump (\ccxt\Exchange::$exchanges); // 输出一个list，内容为所有可用的交易所的类
```

### Proxy 代理服务器

In some specific cases you may want a proxy, if you experience issues with [DDoS protection by Cloudflare](https://github.com/ccxt/ccxt/wiki/Manual#ddos-protection-by-cloudflare) or your network / country / IP is rejected by their filters.

在某些情况下你可能需要使用代理服务器，例如：[Cloudflare 的 DDoS 保护机制](https://github.com/ccxt/ccxt/wiki/Manual#ddos-protection-by-cloudflare) ；你所在的网络、国家或你的IP地址已被屏蔽。

If you need a proxy, use the `proxy` property \(a string literal\) containing base URL of http\(s\) proxy. It is for use with web browsers and from blocked locations.

如果你需要配置代理服务器，请使用 `proxy` 参数，内容为一串包含 http\(s\) 的代理地址的字符串。这个功能通常在浏览器上使用，以解决锁区的情况。

**Bear in mind that each added intermediary contributes to the overall latency and roundtrip time. Longer delays can result in price slippage.**

**请注意，每增加一道中转网络都会导致整体延迟变高、通信周期变长，较长的延迟可能造成价格变动。**

The absolute exchange endpoint URL is appended to `proxy` string before HTTP request is sent to exchange. The proxy setting is an empty string `''` by default. Below are examples of a non-empty proxy string \(last slash is mandatory!\):

配置了代理服务器后，每个访问某交易所的 HTTP 请求都会先经过代理服务器，然后再被转发至目的地址。参数代理服务器的默认值为 `''` 。 代理服务器的配置方法如下（目的URL必须以斜杠‘/’结尾）:

* `kraken.proxy = 'https://crossorigin.me/'`
* `gdax.proxy = 'https://cors-anywhere.herokuapp.com/'`

#### Python 代理服务器

The python version of the library uses the [python-requests](https://github.com/bilibilihuangyifan/ccxtcn/blob/CN-TRANSLATION/wiki/python-requests.org) package for underlying HTTP and supports all means of customization available in the `requests` package, including proxies.

Python 版本的 ccxt 库使用 [python-requests](https://github.com/bilibilihuangyifan/ccxtcn/blob/CN-TRANSLATION/wiki/python-requests.org) 包处理底层 HTTP 通信，并且兼容 `requests` 包中所有的自定义方法，包括代理服务器的相关功能。

You can configure proxies by setting the environment variables HTTP\_PROXY and HTTPS\_PROXY.

你可以通过修改环境变量 HTTP\_PROXY 和 HTTPS\_PROXY 的值来设置代理服务器。

```text
$ export HTTP_PROXY="http://10.10.1.10:3128"
$ export HTTPS_PROXY="http://10.10.1.10:1080"
```

After exporting the above variables with your proxy settings, all reqeusts from within ccxt will be routed through those proxies.

设置完代理服务器后，所有从 ccxt 发出的请求都会被指向代理服务器。

You can also set them programmatically:

当然也可以在代码中动态设置代理服务器：

```text
import ccxt
exchange = ccxt.poloniex({
    'proxies': {
        'http': 'http://10.10.1.10:3128',
        'https': 'http://10.10.1.10:1080',
    },
})
```

或：

```text
import ccxt
exchange = ccxt.poloniex()
exchange.proxies = {
  'http': 'http://10.10.1.10:3128',
  'https': 'http://10.10.1.10:1080',
}
```

**Python 2 和 3 同步代理**

* [https://github.com/ccxt/ccxt/blob/master/examples/py/proxy-sync-python-requests-2-and-3.py](https://github.com/ccxt/ccxt/blob/master/examples/py/proxy-sync-python-requests-2-and-3.py)

```text
# -*- coding: utf-8 -*-

import os
import sys
import ccxt
from pprint import pprint


exchange = ccxt.poloniex({
    #
    # ↓ The "proxy" property setting below is for CORS-proxying only!
    # Do not use it if you don't know what a CORS proxy is.
    # https://github.com/ccxt/ccxt/wiki/Install#cors-access-control-allow-origin
    # You should only use the "proxy" setting if you're having a problem with Access-Control-Allow-Origin
    # In Python you rarely need to use it, if ever at all.
    #
    # 'proxy': 'https://cors-anywhere.herokuapp.com/',
    #
    # ↓ On the other hand, the "proxies" setting is for HTTP(S)-proxying (SOCKS, etc...)
    # It is a standard method of sending your requests through your proxies
    # This gets passed to the `python-requests` implementation directly
    # You can also enable this with environment variables, as described here:
    # http://docs.python-requests.org/en/master/user/advanced/#proxies
    # This is the setting you should be using with synchronous version of ccxt in Python 2 and 3
    #
    # ↓ 以下参数设置方法仅适用于 CORS-proxying 代理服务器！
    # 如果你不清楚什么是 CORS 代理服务器，请不要使用这种方法去设置。
    # https://github.com/ccxt/ccxt/wiki/Install#cors-access-control-allow-origin
    # 建议仅当在你配置 Access-Control-Allow-Origin 后都无法实现跨域访问的情况下再使用本功能。
    # 在 Python 中你只有在极少数情况下才会需要这个功能，甚至可能完全用不着。
    #
    # 'proxy': 'https://cors-anywhere.herokuapp.com/',
    #
    # ↓ 另外，配置 "proxies" 是为了使 HTTP(S)、SOCKS 等数据协议能够正常通信。
    # 这是通过代理服务器发送网络请求的标准做法
    # 你可以通过使用 `requests` 包快捷方便地实现该需求
    # 你也可以通过设置环境变量来启用代理功能，使用方法如下：
    # http://docs.python-requests.org/en/master/user/advanced/#proxies
    # 在 ccxt 同步版本中方可使用本方法配置代理服务器， 环境为 Python 2 或 3
    #
    'proxies': {
        'http': 'http://10.10.1.10:3128',
        'https': 'http://10.10.1.10:1080',
    },
})

# 在这里编写你的代码

pprint(exchange.fetch_ticker('ETH/BTC'))
```

**Python 3.5+ asyncio/aiohttp proxy**

* [https://github.com/ccxt/ccxt/blob/master/examples/py/proxy-asyncio-aiohttp-python-3.py](https://github.com/ccxt/ccxt/blob/master/examples/py/proxy-asyncio-aiohttp-python-3.py)

```text
# -*- coding: utf-8 -*-

import asyncio
import os
import sys
import ccxt.async as ccxt
from pprint import pprint


async def test_gdax():

    exchange = ccxt.poloniex({
        #
        # ↓ The "proxy" property setting below is for CORS-proxying only!
        # Do not use it if you don't know what a CORS proxy is.
        # https://github.com/ccxt/ccxt/wiki/Install#cors-access-control-allow-origin
        # You should only use the "proxy" setting if you're having a problem with Access-Control-Allow-Origin
        # In Python you rarely need to use it, if ever at all.
        #
        # 'proxy': 'https://cors-anywhere.herokuapp.com/',
        #
        # ↓ The "aiohttp_proxy" setting is for HTTP(S)-proxying (SOCKS, etc...)
        # It is a standard method of sending your requests through your proxies
        # This gets passed to the `asyncio` and `aiohttp` implementation directly
        # You can use this setting as documented here:
        # https://docs.aiohttp.org/en/stable/client_advanced.html#proxy-support
        # This is the setting you should be using with async version of ccxt in Python 3.5+
        #
        #
        # ↓ 以下参数设置方法仅适用于 CORS-proxying 代理服务器！
        # 如果你不清楚什么是 CORS 代理服务器，请不要使用这种方法去设置。
        # https://github.com/ccxt/ccxt/wiki/Install#cors-access-control-allow-origin
        # 建议仅当在你配置 Access-Control-Allow-Origin 后都无法实现跨域访问的情况下再使用本功能。
        # 在 Python 中你只有在极少数情况下才会需要这个功能，甚至可能完全用不着。
        #
        # 'proxy': 'https://cors-anywhere.herokuapp.com/',
        #
        #
        # ↓ 配置 "aiohttp_proxy" 是为了使 HTTP(S)、SOCKS 等数据协议能够正常通信。
        # 这是通过代理服务器发送网络请求的标准做法
        # 你可以通过使用 `asyncio` 和 `aiohttp` 包快捷方便地实现该需求
        # 你也可以通过设置环境变量来启用代理功能，使用方法如下：
        # https://docs.aiohttp.org/en/stable/client_advanced.html#proxy-support
        # 在 ccxt 异步版本中方可使用本方法配置代理服务器， 环境为 Python 3.5+
        #
        'aiohttp_proxy': 'http://proxy.com',
        # 'aiohttp_proxy': 'http://user:pass@some.proxy.com',
        # 'aiohttp_proxy': 'http://10.10.1.10:3128',
    })

    # 在这里编写你的代码

    ticker = await exchange.fetch_ticker('ETH/BTC')

    # 不要忘了在使用完成后释放该资源
    await exchange.close()

    return ticker

if __name__ == '__main__':
    pprint(asyncio.get_event_loop().run_until_complete(test_gdax()))
```

A more detailed documentation on using proxies with the sync python version of the ccxt library can be found here:

如果希望进一步了解如何在 ccxt 库 Python 同步版本中使用 proxies 可以访问以下地址查看更多说明文档：

* [Proxies](http://docs.python-requests.org/en/master/user/advanced/#proxies)
* [SOCKS](http://docs.python-requests.org/en/master/user/advanced/#socks)

### CORS 跨域资源共享 \(Access-Control-Allow-Origin\)

CORS is [Cross-Origin Resource Sharing](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing). When accessing the HTTP REST API of an exchange from browser with ccxt library you may get a warning or an exception, saying `No 'Access-Control-Allow-Origin' header is present on the requested resource`. That means that the exchange admins haven't enabled access to their API from arbitrary web browser pages.

CORS 的全称是 [跨域资源共享](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing). 当你使用 ccxt 库通过浏览器访问某交易所的 HTTP REST API 时，你可能会收到一个报警甚至报错信息， 提示 `该请求没有包含 'Access-Control-Allow-Origin' 头部信息`。 这说明该交易所服务器不允许通过网页浏览器访问他们的 API 接口。

You can still use the ccxt library from your browser via a CORS-proxy, which is very easy to set up or install. There are also public CORS proxies on the internet, like [https://crossorigin.me](https://crossorigin.me/).

你可以通过配置 CORS-proxy 代理服务器，继续在浏览器上使用 ccxt 库，CORS-proxy 代理服务器的安装和配置方法非常简单。公网上也有公共的 CORS 代理服务器可以使用，详见： [https://crossorigin.me](https://crossorigin.me/)。

To run your own CORS proxy locally you can either set up one of the existing ones or make a quick script of your own, like shown below.

若你想在本地搭建 CORS 代理服务器，你可以使用现成的工具，也可以简单编辑一个脚本，脚本代码如下：

#### Node.js 版本的 CORS 代理服务器

```text
// JavaScript CORS Proxy
// Save this in a file like cors.js and run with `node cors [port]`
// It will listen for your requests on the port you pass in command line or port 8080 by default
// JavaScript CORS Proxy
// 将代码保存到 cors.js 文件，并通过命令 `node cors [port]` 执行
// 该脚本将会监听你的网络请求，监听端口可以在命令行运行脚本时配置，默认端口为8080
let port = (process.argv.length > 2) ? parseInt (process.argv[2]) : 8080; // default
require ('cors-anywhere').createServer ().listen (port, 'localhost')
```

#### Python 版本的 CORS 代理服务器

```text
#!/usr/bin/env python
# Python CORS Proxy
# Save this in a file like cors.py and run with `python cors.py [port]` or `cors [port]`
# Python CORS Proxy
# 将代码保存到 cors.py 文件，通过命令 `python cors.py [port]` 或 `cors [port]` 执行脚本
try:
    # Python 3
    from http.server import HTTPServer, SimpleHTTPRequestHandler, test as test_orig
    import sys
    def test (*args):
        test_orig (*args, port = int (sys.argv[1]) if len (sys.argv) > 1 else 8080)
except ImportError: # Python 2
    from BaseHTTPServer import HTTPServer, test
    from SimpleHTTPServer import SimpleHTTPRequestHandler

class CORSRequestHandler (SimpleHTTPRequestHandler):
    def end_headers (self):
        self.send_header ('Access-Control-Allow-Origin', '*')
        SimpleHTTPRequestHandler.end_headers (self)

if __name__ == '__main__':
    test (CORSRequestHandler, HTTPServer)
```

#### 测试 CORS 功能

After you set it up and run it, you can test it by querying the target URL of exchange endpoint through the proxy \(like [https://localhost:8080/https://exchange.com/path/to/endpoint](https://localhost:8080/https://exchange.com/path/to/endpoint)\).

代理服务器安装配置完毕后，你可以通过输入 URL 测试能否正常访问目标交易所，URL 的组成包含代理服务器地址和目标交易所地址\(例如： [https://localhost:8080/https://exchange.com/path/to/endpoint\)。](https://localhost:8080/https://exchange.com/path/to/endpoint%29%E3%80%82)

To test the CORS you can do either of the following:

或者通过以下任意一种方法测试：

* set up proxy somewhere in your browser settings, then go to endpoint URL `https://exchange.com/path/to/endpoint`
* 在浏览器中配置代理服务器， 然后直接访问目的 URL `https://exchange.com/path/to/endpoint`
* type that URL directly in the address bar as `https://localhost:8080/https://exchange.com/path/to/endpoint`
* 在地址栏中直接输入以下地址 `https://localhost:8080/https://exchange.com/path/to/endpoint`
* cURL it from command like `curl https://localhost:8080/https://exchange.com/path/to/endpoint`
* 使用 cURL 命令测试 `curl https://localhost:8080/https://exchange.com/path/to/endpoint`

To let ccxt know of the proxy, you can set the `proxy` property on your exchange instance.

你可以在具体的交易所实例中设置 `proxy` 参数，让 ccxt 库能够正常使用代理服务器。

