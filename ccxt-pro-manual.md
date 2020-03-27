# ccxt-pro-manual

## ccxt.pro.manual

[⌂首页](https://ccxt.pro/)

## 手册 <a id="manual"></a>

CCXT Pro堆栈基于[CCXT](https://ccxt.trade/)构建，并使用以下方法扩展了CCXT核心类：

* JavaScript原型级混合
* Python多重继承
* PHP特质

CCXT Pro在很大程度上依赖CCXT的编译器来提供[多语言支持](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md#multilanguage-support)。

```text
                                 用户​    + ------------------------------------------------- ------------ +    | CCXT Pro |    + ------------------------------ + ------------------ ------------ +    | 上市 。私人|    + ================================================= =========== +    │。|    │统一CCXT Pro API |    | 。|    | loadMarkets。watchBalance |    | watchTicker。watchCreateOrder |    | watchTickers。watchCancelOrder |    | watchOrderBook。watchOrder |    | watchOHLCV。watchOrders |    | watchStatus。wathgOpenOrders |    | watchTrades。watchClosedOrders |    | 。watchMyTrades |    | 。watchDeposit |    | 。watchWithdraw |    │。|    + ================================================= =========== +    │。|    | 底层特定于Exchange的API |    | （派生类及其实现）|    │。|    + ================================================= =========== +    │。|    | CCXT Pro基础交换类|    │。|    + ================================================= =========== +​    + ------------------------------------------------- ------------ +    | |    | CCXT |    | |    + ================================================= =========== +
```

## 交流交流 <a id="exchanges"></a>

CCXT Pro库当前支持以下18个加密货币交易市场和WebSocket交易API：

|        商标        | ID | 名称 | 看 | doc | 认证的 | 亲 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| ​[​![&#x5E01;&#x5B89;](https://user-images.githubusercontent.com/1294454/29604020-d5483cdc-87ee-11e7-94c7-d1a8d9169293.jpg)​](https://www.binance.com/?ref=10205187)​ | 币安 | [Binance](https://www.binance.com/?ref=10205187) | \* | [API](https://binance-docs.github.io/apidocs/spot/en) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x8FFD;&#x968F;](https://user-images.githubusercontent.com/1294454/54874009-d526eb00-4df3-11e9-928c-ce6a2b914cd1.jpg)​](https://www.binance.je/?ref=35047921)​ | 追随 | [Binance泽西](https://www.binance.je/?ref=35047921) | \* | [API](https://github.com/binance-exchange/binance-official-api-docs/blob/master/rest-api.md) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![Binanceus](https://user-images.githubusercontent.com/1294454/65177307-217b7c80-da5f-11e9-876e-0b748ba0a358.jpg)​](https://www.binance.us/?ref=35005074)​ | Binanceus | [Binance美国](https://www.binance.us/?ref=35005074) | \* | [API](https://github.com/binance-us/binance-official-api-docs) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x6BD4;&#x7279;&#x5E01;](https://user-images.githubusercontent.com/1294454/27766244-e328a50c-5ed2-11e7-947b-041416579bb3.jpg)​](https://www.bitfinex.com/?refcode=P61eYxFL)​ | 比特币 | [Bitfinex](https://www.bitfinex.com/?refcode=P61eYxFL) | 1个 | [API](https://docs.bitfinex.com/v1/docs) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x6BD4;&#x7279;&#x5E01;](https://user-images.githubusercontent.com/1294454/27766319-f653c6e6-5ed4-11e7-933d-f0bc3699ae8f.jpg)​](https://www.bitmex.com/register/upZpOX)​ | 比特币 | [BitMEX](https://www.bitmex.com/register/upZpOX) | 1个 | [API](https://www.bitmex.com/app/apiOverview) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x6BD4;&#x7279;&#x6233;](https://user-images.githubusercontent.com/1294454/27786377-8c8ab57e-5fe9-11e7-8ea4-2b05b6bcceec.jpg)​](https://www.bitstamp.net/)​ | 比特戳 | [Bitstamp](https://www.bitstamp.net/) | 2 | [API](https://www.bitstamp.net/api) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![Bittrex](https://user-images.githubusercontent.com/1294454/27766352-cf0b3c26-5ed5-11e7-82b7-f3826b7a97d8.jpg)​](https://bittrex.com/Account/Register?referralCode=1ZE-G0G-M3B)​ | Bittrex | [Bittrex](https://bittrex.com/Account/Register?referralCode=1ZE-G0G-M3B) | 1.1 | [API](https://bittrex.github.io/api/) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x539F;&#x59CB;&#x8D27;&#x5E01;](https://user-images.githubusercontent.com/1294454/44539184-29f26e00-a70c-11e8-868f-e907fc236a7c.jpg)​](https://prime.coinbase.com/)​ | 原始货币 | [总理Coinbase](https://prime.coinbase.com/) | \* | [API](https://docs.prime.coinbase.com/) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![coinbasepro](https://user-images.githubusercontent.com/1294454/41764625-63b7ffde-760a-11e8-996d-a6328fa9347a.jpg)​](https://pro.coinbase.com/)​ | coinbasepro | [Coinbase临](https://pro.coinbase.com/) | \* | [API](https://docs.pro.coinbase.com/) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![Gateio](https://user-images.githubusercontent.com/1294454/31784029-0313c702-b509-11e7-9ccc-bc0da6a0e435.jpg)​](https://www.gate.io/signup/2436035)​ | Gateio | [Gate.io](https://www.gate.io/signup/2436035) | 2 | [API](https://gate.io/api2) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![huobipro](https://user-images.githubusercontent.com/1294454/76137448-22748a80-604e-11ea-8069-6e389271911d.jpg)​](https://www.huobi.co/en-us/topic/invited/?invite_code=rwrd3)​ | huobipro | ​[Huobi Pro](https://www.huobi.co/en-us/topic/invited/?invite_code=rwrd3)​ | 1个 | [API](https://huobiapi.github.io/docs/spot/v1/cn/) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![huobiru](https://user-images.githubusercontent.com/1294454/52978816-e8552e00-33e3-11e9-98ed-845acfece834.jpg)​](https://www.huobi.com.ru/invite?invite_code=esc74)​ | huobiru | ​[Huobi Russia](https://www.huobi.com.ru/invite?invite_code=esc74)​ | 1个 | [API](https://github.com/cloudapidoc/API_Docs_en) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x6D77;&#x5996;](https://user-images.githubusercontent.com/51840849/76173629-fc67fb00-61b1-11ea-84fe-f2de582f58a3.jpg)​](https://www.kraken.com/)​ | 海妖 | [鲲](https://www.kraken.com/) | 0 | [API](https://www.kraken.com/features/api) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x9177;&#x5E01;](https://user-images.githubusercontent.com/1294454/57369448-3cc3aa80-7196-11e9-883e-5ebeb35e4f57.jpg)​](https://www.kucoin.com/?rcode=E5wkqe)​ | 酷币 | [KuCoin](https://www.kucoin.com/?rcode=E5wkqe) | 2 | [API](https://docs.kucoin.com/) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![okcoin](https://user-images.githubusercontent.com/1294454/27766791-89ffb502-5ee5-11e7-8a5b-c5950b68ac65.jpg)​](https://www.okcoin.com/account/register?flag=activity&channelId=600001513)​ | okcoin | [OKCoin](https://www.okcoin.com/account/register?flag=activity&channelId=600001513) | 3 | [API](https://www.okcoin.com/docs/en/) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x5965;&#x514B;&#x65AF;](https://user-images.githubusercontent.com/1294454/32552768-0d6dd3c6-c4a6-11e7-90f8-c043b64756a7.jpg)​](https://www.okex.com/join/1888677)​ | 奥克斯 | [OKEX](https://www.okex.com/join/1888677) | 3 | [API](https://www.okex.com/docs/en/) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![poloniex](https://user-images.githubusercontent.com/1294454/27766817-e9456312-5ee6-11e7-9b3c-b628ca5626a5.jpg)​](https://www.poloniex.com/?utm_source=ccxt&utm_medium=web)​ | poloniex | [Poloniex](https://www.poloniex.com/?utm_source=ccxt&utm_medium=web) | \* | [API](https://docs.poloniex.com/) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x4E0A;&#x884C;](https://user-images.githubusercontent.com/1294454/49245610-eeaabe00-f423-11e8-9cba-4b0aed794799.jpg)​](https://upbit.com/)​ | 上行 | [Upbit](https://upbit.com/) | 1个 | [API](https://docs.upbit.com/docs/%EC%9A%94%EC%B2%AD-%EC%88%98-%EC%A0%9C%ED%95%9C) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |

这是CCXT Pro中支持WebSockets API的交换列表。该列表将定期进行新的交流更新。

通过REST在CCXT中可用的交易所的完整列表：[受支持的加密货币交易所市场](https://github.com/ccxt/ccxt/#supported-cryptocurrency-exchange-markets)。

## 用法 <a id="usage"></a>

```text
-该文档的这一部分目前正在大量开发中-可能到处都有错别字，错误和信息遗漏-贡献，拉取请求和反馈表示赞赏
```

### 先决条件 <a id="prerequisites"></a>

理解CCXT Pro的最好方法是确保您掌握完整的CCXT手册并首先练习标准CCXT。CCXT Pro从CCXT借用。这两个库有很多共同点，包括：

* 公共API和私有认证API的概念
* 市场，符号，货币代码和ID
* 统一的数据结构和格式，订单簿，交易，订单，蜡烛，时间表，...
* 异常和错误映射
* 身份验证和API密钥（用于私人供稿和调用）
* 配置选项

CCXT Pro的受众主要由专业的算法交易者和开发人员组成。为了有效地使用此库，要求用户熟悉流的概念。必须了解基于连接的流式API（[WebSocket](https://en.wikipedia.org/wiki/WebSocket)，CCXT Pro）和基于请求响应的API（[REST](https://en.wikipedia.org/wiki/Representational_state_transfer)，CCXT）之间的根本区别。

CCXT应用程序的一般异步样式流程如下：

```text
//一个RESTful订单簿轮询请求-响应循环​而（条件）{  ​    尝试{ ​        //获取一些公共数据        订单= 等待交换。fetchOrderBook （symbol ，limit ）  ​        //根据该数据做某事或以某种方式做出反应        // ...​    } 抓住（e ）{   ​        //处理错误    }}
```

在CCXT Pro中，每个带有前缀的公共和私有统一RESTful方法也都有一个以开头的对应的基于流的对应方法，如下所示：`fetch*watch*`

* 公开API
  * `fetchStatus` → `watchStatus`
  * `fetchOrderBook` → `watchOrderBook`
  * `fetchTicker` → `watchTicker`
  * `fetchTickers` → `watchTickers`
  * `fetchOHLCV` → `watchOHLCV`
  * `fetchTrades` → `watchTrades`
  * `fetchStatus` → `watchStatus`
* 私人API
  * `fetchBalance` → `watchBalance`
  * `fetchOrders` → `watchOrders`
  * `fetchMyTrades` → `watchMyTrades`
  * `fetchTransactions` → `watchTransactions`
  * `fetchLedger` → `watchLedger`
  * `createOrder`→ _（注意前缀）_`watchCreateOrder` _`watch`_
  * `cancelOrder`→ _（注意前缀）_`watchCancelOrder` _`watch`_

Unified CCXT Pro Streaming API继承了CCXT使用模式，使迁移更加容易。

下面显示了CCXT Pro应用程序（与上面的CCXT应用程序相对）的一般异步样式流程：

```text
//基于流的（WebSocket）订单馈送循环​而（条件）{  ​    尝试{ ​        //观看一些公共数据        订单= 等待交换。watchOrderBook （符号，限制）  ​        //根据该数据做某事或以某种方式做出反应        // ...​    } 抓住（e ）{   ​        //处理错误    }}
```

该使用模式通常被包装到称为_“_ _功能”_的核心业务逻辑方法中，因为它重申了对传入事件（也称为_ticks_）的反应。从以上两个示例中可以明显看出，CCXT Pro和CCXT中的通用用法模式是相同的。_`tick()`_

许多CCXT规则和概念也适用于CCXT Pro：

* CCXT Pro将在首次调用统一API方法时加载市场并缓存市场
* 如有必要，CCXT Pro将在幕后调用CCXT RESTful方法
* CCXT Pro将在必要时引发标准CCXT异常
* ...

### 流细节 <a id="streaming-specifics"></a>

尽管存在众多共通点，但基于流的API由于具有基于连接的性质而具有其自身的特性。

具有基于连接的接口意味着连接处理机制。连接由CCXT Pro对用户透明管理。每个交换实例管理自己的一组连接。

首次调用任何方法时，库将建立与特定交换流/资源的连接并将维护该连接。如果连接已经存在–将被重用。如果请求的流是私有的，则库将处理订阅请求/响应消息传递序列以及身份验证/签名。`watch*()`

该库还将监视上行链路的状态，并使连接保持活动状态。在发生严重异常，断开连接或连接超时/失败时，tick函数的下一次迭代将调用将触发重新连接的方法。这样，库可以透明地为用户处理断开连接和重新连接。CCXT Pro应用必要的速率限制和指数补偿退回重新​​连接延迟。所有这些功能默认情况下都是启用的，并且可以像往常一样通过交换属性进行配置。`watch`

大多数交换仅具有用于流API的单个基本URL（通常是WebSocket，以或开头）。其中一些针对每个流可能具有多个URL，具体取决于相关的供稿。`ws://wss://`

交易所的流API可以分为两类：

* _子_或_订阅_仅允许接收
* _pub_或_publish_允许发送和接收

#### 子 <a id="sub"></a>

甲_子_接口通常允许订阅数据流和收听它。确实支持WebSocket的大多数交换将仅提供API 的_子_类型。该_子_类型包括流媒体公开的市场数据。有时交换还允许订阅私人用户数据。用户订阅数据馈送后，通道有效地开始工作，以单向方式从交换机向用户连续发送更新。

常见的公共数据流类型：

* 订单簿（最常见）-已添加，已编辑和已删除订单的更新（又称_更改增量_）
* 更新24小时统计信息后，行情自动更新
* 填充提要（也很常见）-实时进行的公共交易
* ohlcv烛台饲料
* 心跳
* 交流聊天/ trollbox

私人用户数据流的较不常见类型：

* 用户的私人交易流
* 实时订单更新
* 余额更新
* 自定义流
* 特定交易流和其他流

#### 酒馆 <a id="pub"></a>

一个_酒馆_接口通常允许用户发送往服务器的数据请求。这通常包括常见的用户操作，例如：

* 下订单
* 取消订单
* 提出提款要求
* 发布聊天/ trollbox消息
* 等等

**一些交易所不提供**_**pub**_ **WS API，它们仅提供**_**sub**_ **WS API。**但是，有些交易所也具有完整的Streaming API。在大多数情况下，仅使用Streaming API，用户无法有效地进行操作。交易所将流公开市场数据_sub_，而缺少部分的_pub_部分仍需要REST API 。

#### 增量数据结构 <a id="incremental-data-structures"></a>

在很多情况下，由于基础数据源的单向性，在客户端侦听的应用程序必须在内存中保留数据的本地快照，并将从交换服务器接收到的更新合并到本地快照中。来自交换的更新通常也称为_增量_，因为在大多数情况下，这些更新将仅包含数据的两个状态之间的更改，并且将不包含尚未更改的数据，因此有必要存储本地缓存的当前状态S所有相关数据对象。

CCXT Pro会为用户处理所有这些功能。要使用CCXT Pro，用户不必跟踪或管理订阅和相关数据。CCXT Pro将在内存中保留结构缓存，以处理潜在的麻烦。

每个传入的更新都说数据的哪些部分已更改，并且接收方通过将更新合并到当前状态S的顶部来“递增”本地状态S，然后移动到下一个本地状态S'。术语CCXT Pro（称为_“增量状态”）_和涉及存储和更新缓存状态的过程中涉及的结构称为_“增量结构”_。CCXT Pro引入了几个新的基类，以在必要时处理增量状态。

从CCXT Pro的统一方法返回的增量结构通常是以下两种类型之一：

1. JSON解码的对象（在JavaScript，Python，PHP中）。这种类型可以从公共和私有方法，如被退回，，，等。`objectdictarray()watchTickerwatchBalancewatchOrder`
2. 对象的数组/列表（通常按时间顺序排序）。这种类型的可从方法喜欢返回，，，，等。`watchOHLCVwatchTradeswatchMyTradeswatchOrders`

在后一种情况下，CCXT Pro库必须对内存中保留的对象数量保持合理的限制。允许的最大值可由用户在实例化或更高版本时配置。

### 连结中 <a id="linking"></a>

请参阅此处的安装说明：[CCXT Pro安装](https://ccxt.pro.install.md/)。

将CCXT Pro库包含到脚本中的过程与标准CCXT几乎相同，唯一的区别是实际JavaScript模块，Python包或PHP名称空间的名称。

```text
// JavaScriptconst ccxtpro = 要求（'ccxt.pro' ）  控制台。日志（“ CCXT Pro版本” ，ccxtpro 。版本） 控制台。日志（“支持的交换：” ，ccxtpro 。交换） 
```

```text
＃Python导入ccxtpro打印（'CCXT专业版' ，ccxtpro 。__version__ ）打印（“支持的交换：” ，ccxtpro 。交换）
```

```text
// PHP使用\ ccxtpro ; //可选，因为您可以使用完全限定的名称  回声'CCXT专业版' ，\ ccxtpro \ 交易所：：VERSION ，“\ n” ;  回声'支持的交流：' ，json_encode （\ ccxtpro \ 交易所：：$交流），“\ n” ;   
```

导入的CCXT Pro模块将CCXT包裹在自身内部–通过CCXT Pro实例化的每个交换都具有所有CCXT方法以及其他功能。

### 实例化 <a id="instantiation"></a>

CCXT Pro是专为异步/的await风格的语法和在很大程度上依赖于异步原语，如_承诺_和_期货_。

创建CCXT Pro交换实例与创建CCXT交换实例几乎相同。

```text
// JavaScriptconst ccxtpro = 要求（'ccxt.pro' ）  const exchange = 新的ccxtpro 。平衡（{ enableRateLimit ：true } ）     
```

CCXT Pro的Python实现尤其依赖于内置的[asyncio](https://docs.python.org/3/library/asyncio.html)和[Event Loop](https://docs.python.org/3/library/asyncio-eventloop.html)。在Python中，需要在构造函数参数中提供asyncio的事件循环实例，如下所示（与相同）：`ccxt.async support`

```text
＃Python导入ccxtpro导入异步​异步def main （循环）：      交换= ccxtpro 。kraken （{ 'enableRateLimit' ：True ，'asyncio_loop' ：loop } ）      而True ：         订单= 等待交换。watch_order_book （'BTC / USD' ）         打印（订单簿[ 'asks' ] [ 0 ] ，订单簿[ 'bids ] [ 0 ] ）    等待交流。关闭（）​循环= asyncio 。new_event_loop （）循环。run_until_complete （main （loop ））
```

在PHP中，异步原语是从[ReactPHP](https://reactphp.org/)借用的。CCXT Pro的PHP实现尤其依赖于[Promise](https://github.com/reactphp/promise)和[EventLoop](https://github.com/reactphp/event-loop)。在PHP中，要求用户在构造函数参数中提供ReactPHP的事件循环实例，如下所示：

```text
// PHP错误报告（E_ALL | E_STRICT ）;  date_default_timezone_set （'UTC' ）;require_once'vendor / autoload.php' ; ​$循环= \ 阵营\ 事件循环\ 厂：：创建（）; //事件循环在这里↓  $ exchange = 新\ ccxtpro \ kucoin （数组（'enableRateLimit' = > true ，'loop' = > $ loop ））;        
```

### 交换属性 <a id="exchange-properties"></a>

每个CCXT Pro实例都包含基础CCXT实例的所有属性。除了标准的CCXT属性外，CCXT Pro实例还包括以下内容：

```text
{    'has' ：{ //扩展交换功能的关联数组          'ws' ：true ，//仅在CCXT Pro中可用          'watchOrderBook' ：true ，         'watchTicker' ：是的，         'watchTrades' ：是的，         'watchOHLCV' ：是的，         'watchBalance' ：是的，         'watchCreateOrder' ：true ，         'watchCancelOrder' ：true ，         ...    } ，    'urls' ：{         'api' ：{ //将包含流API基础URL，具体取决于底层协议              'WS' ： 'WSS：//ws.exchange.com' ，// https://en.wikipedia.org/wiki/WebSocket                         'signalr' ：'https : //signalr.exchange.com'// https://en.wikipedia.org/wiki/SignalR              'socketio' ：'wss：//socket.exchange.io'// https://socket.io             } ，    } ，    'version' ：'1.21' ，     “流式” ：{         'keepAlive' ：30000 ，//整数保持存活率（以毫秒为单位）          'maxPingPongMisses' ：2.0 ，//有多少乒乓球未击中并重新连接          ... //其他流式传输选项     } ，    //增量数据结构    'orderbooks' ：{ } ，//用符号索引的增量订单        'ohlcvs' ：{ } ，//按时间范围按符号索引的标准CCXT OHLCV            'balance' ：{ } ，//标准CCXT余额结构，按货币代码索引的帐户           'orders' ：{ } ，//由订单ID索引的标准CCXT订单结构            'trades' ：{ } ，//通过符号索引的CCXT交易数组            ' tickers ' ：{ } ，//用符号索引的标准CCXT代码           'transactions' ：{ } ，//通过id或txid索引的标准CCXT存款和取款      ...}
```

### 统一API <a id="unified-api"></a>

与使用EventEmitters和回调相比，Unified CCXT Pro API鼓励直接控制流，以实现更好的代码样式，更易读和结构更出色的代码。后者在当今被认为是一种过时的方法，因为它需要控制权的倒置（人们不习惯于倒置的思维）。

CCXT Pro遵循现代方法，并且是为异步语法设计的。在后台，CCXT Pro有时仍将不得不使用反向控制流，这是由于依赖关系和WebSocket库无法做到的。

不仅对于JS / ES6，而且对于Python 3异步代码也是如此。在PHP中，异步原语是从[ReactPHP](https://reactphp.org/)借用的。

现代异步语法允许您将执行组合和拆分为并行路径，然后将其合并，分组，对它们进行优先级排序，以及不进行并行处理。有了promise，就可以轻松地从直接异步样式的控制流来回转换为反向回调样式的控制流。

#### 实时与节流 <a id="real-time-vs-throttling"></a>

CCXT Pro支持滴答功能循环的两种模式-实时模式和节流模式。两者都以伪代码显示如下：

```text
//实时模式const limit = 5 //可选  而（true ）{      尝试{         const orderbook = 等待交换。watchOrderBook （符号，限制）          //您对更新的反应发生在这里        //您是从交易所实时收到更新后到达的        控制台。日志（订单）//每次更新      } 抓住（e ）{           控制台。日志（e ）         //抛出e //取消注释以停止异常循环    }}
```

```text
//节流模式const limit = 5 //可选  // await是可选的，或者您也可以不使用await在bg中启动它等待交流。watchOrderBook （符号，限制） 而（true ）{      //您的反应在这里发生    //无论是否有更新，您每100毫秒到达一次    //在节流模式下，需要使用.limit（）卸载订单    控制台。日志（交换。订单（符号）。限制（限制））      等待睡眠（100 ）//每100毫秒   }
```

在**实时模式下**，一旦每个新的增量从交换中到达，CCXT Pro就会返回结果。实时循环中统一调用的一般逻辑是等待下一个增量，并一遍又一遍立即将统一结果结构返回给用户。当反应时间很关键或必须尽可能快时，这很有用。

但是，在同步多个并行滴答循环时，实时模式要求具有异步流编程经验。除此之外，在活跃或高波动时期，交易所可以流式传输大量更新。因此，开发实时算法的用户必须确保用户域代码能够快速消耗数据。有时，以实时模式工作可能对资源的要求更高。

在**节流模式下，** CCXT Pro将在后台接收和管理数据。用户有责任在必要时不时调用结果。节流循环的一般逻辑是大部分时间都处于睡眠状态，并偶尔唤醒以检查结果。这通常以某个固定频率或_“帧速率”完成_。节流循环中的代码通常更易于在多个交换之间进行同步。限制循环中所用时间的比例分配还有助于将资源使用降至最低。当您的算法繁重并且您想要精确地控制执行以避免过于频繁地运行它时，这非常方便。

节流模式的明显缺点是对更新的反应性或响应性较差。当交易算法必须等待几毫秒才能被执行时，一到两次更新可能会比该时间到期早。在节流模式下，用户仅在下一次唤醒（循环迭代）时检查这些更新，因此反应滞后可能会在一段时间内变化数毫秒。

#### 公开方法 <a id="public-methods"></a>

**市场数据**

**watchOrderBook**

所述的接口是相同的`watchOrderBook`。它接受三个参数：[`fetchOrderBook`](https://github.com/ccxt/ccxt/wiki/Manual#order-book)

* `symbol` –字符串，一个统一的CCXT符号，必填
* `limit` –整数，返回的最大出价/请求数，可选
* `params`- ASSOC词典，如在可选的覆盖[重写统一API PARAMS](https://github.com/ccxt/ccxt/wiki/Manual#overriding-unified-api-params)

通常，交易所可以分为两类：

1. 支持有限订单的交易所（仅流处理订单栈的顶部）
2. 只传送完整订单的交易所

如果交换接受限制参数，则在通过WebSocket连接订阅订单流后，将参数发送给交换。然后，交易所将仅发送指定数量的订单，这有助于减少流量。某些交易所可能只接受的某些值，例如10、25、50、100等。`limitlimit`

如果基础交易所不接受限制参数，则限制将在客户端进行。

该参数不能保证出价或要价的数量始终等于。它指定上限或最大值，因此有时可能会少于出价或要价，但决不会超过出价或要价。当交易所在订单簿上没有足够的订单时，或者在订单簿中最重要的订单之一被匹配并从订单簿中删除时，在出价方或要价方上的条目都少于条目时，就是这种情况。订单中的可用空间通常很快就会被新数据填充。`limitlimitlimitlimitlimit`

```text
// JavaScript如果（交换。有[ 'watchOrderBook' ] ）{      而（true ）{          尝试{             const orderbook = 等待交换。watchOrderBook （symbol ，limit ，params ）              控制台。日志（新Date （），符号，订单[ 'asks' ] [ 0 ] ，订单[ 'bids' ] [ 0 ] ）           } 抓住（e ）{               控制台。日志（e ）             //停止异常循环或将其保留为注释以重试            //抛出e        }    }}
```

```text
＃Python如果交换。具有[ 'watchOrderBook' ] ：    而True ：         尝试：            订单= 等待交换。watch_order_book （符号，限制，参数）             打印（交换。ISO8601 （交换。毫秒（）），符号，手持订单[ '询问' ] [ 0 ] ，手持订单[ '出价' ] [ 0 ] ）        除了Exception 作为e ：            打印（ē ）            ＃停止异常循环或将其保留以重试            ＃种族e
```

```text
// PHP如果（$交换- > 具有[ 'watchOrderBook' ] ）{      $ main = function （）use （＆$ exchange ，＆$ main ，$ symbol ，$ limit ，$ params ）{                  $交换- > watch_order_book （$符号，$限制，$ PARAMS ）- > 然后（函数（$手持订单）使用（＆$主，$符号）{                  echo date （'c' ），'' ，$ symbol ，'' ，json_encode （array （$ orderbook [ 'asks' ] [ 0 ] ，$ orderbook [ 'bids ] [ 0 ] ））），“ \ n” ;                   $ main （）;        } ）- > 否则（函数（\ Exception $ e ）使用（＆$ main ）{                 回波get_class （$ë ），'' ，$ë - > 的getMessage （），“\ n”个;                $ main （）;            //停止异常循环或将其保留为注释以重试            //抛出$ e;        } ）;    } ;    $环- > futureTick （$主）;}
```

**watchTicker**

```text
// JavaScript如果（交换。有[ 'watchTicker' ] ）{      而（true ）{          尝试{             const ticker = 等待交换。watchTicker （符号，参数）              控制台。日志（新的日期（），股票代码）           } 抓住（e ）{               控制台。日志（e ）             //停止异常循环或将其保留为注释以重试            //抛出e        }    }}
```

```text
＃Python如果交换。具有[ 'watchTicker' ] ：    而True ：         尝试：            股票报价= 等待交易。watch_ticker （符号，参数）             打印（交流。ISO8601 （交流。毫秒（）），股票代码）        除了Exception 作为e ：            打印（ē ）            ＃停止异常循环或将其保留以重试            ＃种族e
```

```text
// PHP如果（$交换- > 具有[ 'watchTicker' ] ）{      $ main = function （）use （＆$ exchange ，＆$ main ，$ symbol ，$ params ）{                 $交换- > watch_ticker （$符号，$ PARAMS ）- > 然后（函数（$股票）使用（＆$主）{                echo date （'c' ），'' ，json_encode （$ ticker ），“ \ n” ;                $ main （）;        } ）- > 否则（函数（\ Exception $ e ）使用（＆$ main ）{                 回波get_class （$ë ），'' ，$ë - > 的getMessage （），“\ n”个;                $ main （）;            //停止异常循环或将其保留为注释以重试            //抛出$ e;        } ）;    } ;    $环- > futureTick （$主）;}
```

**watchTickers**

```text
// JavaScript如果（交换。有[ 'watchTickers' ] ）{      而（true ）{          尝试{             const tickers = 等待交换。watchTickers （符号，参数）              控制台。日志（新的日期（），代码）           } 抓住（e ）{               控制台。日志（e ）             //停止异常循环或将其保留为注释以重试            //抛出e        }    }}
```

```text
＃Python如果交换。具有[ 'watchTickers' ] ：    而True ：         尝试：            股票报价= 等待交易。watch_tickers （符号，参数）             打印（交流。ISO8601 （交流。毫秒（）），行情）        除了Exception 作为e ：            打印（ē ）            ＃停止异常循环或将其保留以重试            ＃种族e
```

```text
// PHP如果（$交换- > 具有[ 'watchTickers' ] ）{      $ main = function （）use （＆$ exchange ，＆$ main ，$ symbols ，$ params ）{                 $交换- > watch_tickers （$符号，$ PARAMS ）- > 然后（函数（$行情）使用（＆$主）{                echo date （'c' ），'' ，json_encode （$ tickers ），“ \ n” ;                $ main （）;        } ）- > 否则（函数（\ Exception $ e ）使用（＆$ main ）{                 回波get_class （$ë ），'' ，$ë - > 的getMessage （），“\ n”个;                $ main （）;            //停止异常循环或将其保留为注释以重试            //抛出$ e;        } ）;    } ;    $环- > futureTick （$主）;}
```

**观看OHLCV**

```text
// JavaScript如果（交换。有[ 'watchOHLCV' ] ）{      而（true ）{          尝试{             常量蜡烛= 等待交换。watchOHLCV （符号，因为，极限，参数）              控制台。日志（新Date （），蜡烛）           } 抓住（e ）{               控制台。日志（e ）             //停止异常循环或将其保留为注释以重试            //抛出e        }    }}
```

```text
＃Python如果交换。具有[ 'watchOHLCV' ] ：    而True ：         尝试：            蜡烛= 等待交流。watch_ohlcv （符号，自，极限，参数）             打印（交流。ISO8601 （交流。毫秒（）），蜡烛）        除了Exception 作为e ：            打印（ē ）            ＃停止异常循环或将其保留以重试            ＃种族e
```

```text
// PHP如果（$交换- > 具有[ 'watchOHLCV' ] ）{      $ main = function （）use （＆$ exchange ，＆$ main ，$ symbol ，$ timeframe ，$ since ，$ limit ，$ params ）{                    $交换- > watch_ohlcv （$符号，$时间表，$以来，$限制，$ PARAMS ）- > 然后（                函数（$ candles ）使用（＆$ main ，$ symbol ，$ timeframe ）{                     echo date （'c' ），'' ，$ symbol ，'' ，$ timeframe ，'' ，json_encode （$ candles ），“ \ n” ;                        $ main （）;            }        ）- > 否则（函数（\ Exception $ e ）使用（＆$ main ）{                 回波get_class （$ë ），'' ，$ë - > 的getMessage （），“\ n”个;                $ main （）;            //停止异常循环或将其保留为注释以重试            //抛出$ e;        } ）;    } ;    $环- > futureTick （$主）;}
```

**watchTrades**

```text
// JavaScript如果（交换。有[ 'watchTrades' ] ）{      而（true ）{          尝试{             const trades = 等待交易。watchTrades （符号，自，极限，参数）              控制台。日志（新Date （），交易）           } 抓住（e ）{               控制台。日志（e ）             //停止异常循环或将其保留为注释以重试            //抛出e        }    }}
```

```text
＃Python如果交换。有[ 'watchTrades' ] ：    而True ：         尝试：            交易= 等待交易。watch_trades （符号，自，极限，参数）             打印（交流。ISO8601 （交流。毫秒（）），交易）        除了Exception 作为e ：            打印（ē ）            ＃停止异常循环或将其保留以重试            ＃种族e
```

```text
// PHP如果（$交换- > 具有[ 'watchTrades' ] ）{      $ main = function （）use （＆$ exchange ，＆$ main ，$ symbol ，$ since ，$ limit ，$ params ）{                   $交换- > watch_trades （$符号，$因为，$限制，$ PARAMS ）- > 然后（函数（$交易）使用（＆$主）{                  回显日期（'c' ），'' ，json_encode （$ trades ），“ \ n” ;                $ main （）;        } ）- > 否则（函数（\ Exception $ e ）使用（＆$ main ）{                 回波get_class （$ë ），'' ，$ë - > 的getMessage （），“\ n”个;                $ main （）;            //停止异常循环或将其保留为注释以重试            //抛出$ e;        } ）;    } ;    $环- > futureTick （$主）;}
```

#### 私人方法 <a id="private-methods"></a>

```text
-现在正在进行中
```

**认证方式**

在大多数情况下，身份验证逻辑是从CCXT借用的，因为交换对REST API和WebSocket API使用相同的密钥对和签名算法。有关更多详细信息，请参见[API密钥设置](https://github.com/ccxt/ccxt/wiki/Manual#api-keys-setup)。

**贸易**

**watchBalance**

```text
// JavaScript如果（交换。有[ 'watchBalance' ] ）{      而（true ）{          尝试{             常量余额= 等待交换。watchBalance （params ）              控制台。日志（新日期（），余额）           } 抓住（e ）{               控制台。日志（e ）             //停止异常循环或将其保留为注释以重试            //抛出e        }    }}
```

```text
＃Python如果交换。具有[ 'watchBalance' ] ：    而True ：         尝试：            余额= 等待交换。watch_balance （参数）             打印（交流。ISO8601 （交流。毫秒（）），平衡）        除了Exception 作为e ：            打印（ē ）            ＃停止异常循环或将其保留以重试            ＃种族e
```

```text
// PHP如果（$交换- > 具有[ 'watchBalance' ] ）{      $ main = function （）use （＆$ exchange ，＆$ main ，$ params ）{                $交换- > watch_balance （$ PARAMS ）- > 然后（函数（$ BALANCE ）使用（＆$主）{               回显日期（'c' ），'' ，json_encode （$ balance ），“ \ n” ;                $ main （）;        } ）- > 否则（函数（\ Exception $ e ）使用（＆$ main ）{                 回波get_class （$ë ），'' ，$ë - > 的getMessage （），“\ n”个;                $ main （）;            //停止异常循环或将其保留为注释以重试            //抛出$ e;        } ）;    } ;    $环- > futureTick （$主）;}
```

**watchOrders**

```text
-现在正在进行中
```

**watchCreateOrder**

```text
-现在正在进行中
```

**watchCancelOrder**

```text
-现在正在进行中
```

**watchMyTrades**

```text
-现在正在进行中
```

```text
// JavaScriptwatchMyTrades （符号= 未定义，因为= 未定义，限制= 未定义，参数= { } ）  
```

```text
＃Pythonwatch_my_trades （符号= 无，因为= 无，限制= 无，参数= { } ）
```

```text
// PHPwatch_my_trades （$ symbol = null ，$ since = null ，$ lmit = null ，$ params = array （））;           
```

**资金**

**watchTransactions**

```text
-现在正在进行中
```

### 错误处理 <a id="error-handling"></a>

如果发生错误，CCXT Pro将抛出标准CCXT异常，有关更多详细信息，请参见[错误处理](https://github.com/ccxt/ccxt/wiki/Manual#error-handling)。

